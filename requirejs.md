# requirejs

> 官方站点[http://requirejs.org/](http://requirejs.org/)


## 中文翻译
> [http://makingmobile.org/docs/tools/requirejs-api-zh/#usage](http://makingmobile.org/docs/tools/requirejs-api-zh/#usage)


*简单理解为一个脚本加载器 :D*

1. [如何加载一个模块(文件)](http://makingmobile.org/docs/tools/requirejs-api-zh/#jsfiles)

2. [如何定义一个模块](http://makingmobile.org/docs/tools/requirejs-api-zh/#define)

## 项目

`requirejs`配置在`app/scripts/main.js` 包含一些常用的别名配置

## 定义模块
> 项目里面的模块全都定义成匿名模块，就是不要手动添加模块id，这个id后面用工具自动生成 例如：

`xx/page/cash/settings` 该模块对应的是视图下面-> Cash -> Settings页面的业务逻辑

```js
define(['jquery'],function($){
    //所有模块里面的内容跟之前的写法一样，只是要使用什么模块要先加载过来
    //这里要用到jQuery,所以就加载jquery（这是一个通用别名）进来赋值给$ 变量
    function Settings(options){
        ...

        this.initialize();
    };

    ...
    ...
    ...
    Settings.prototype.initialize = function(){
        $(function(){
            //这里是jQuery的初始化，不过一般不要这样写，这里只是一个例子
            //关于页面业务逻辑代码请[参考注释部分的代码段]
        })
    }

    return Settings

});
```

## 代码目录结构
> 所有代码都按照自定目录存放

1. 所有目录名称小写，有分隔的用中画线分隔 path-to-module
2. 所有开发的同事只负责页面业务逻辑的编写，公共部分的代码与前端沟通，由其负责编写
3. 目录结构

| app |  |  |
| -- | -- | -- |
| .. | lib | 一些第三方的框架 |
| .. | scripts | 项目模块 |
| .. | styles | 样式表 |
| .. | fonts | 一些图标字体文件 |
| .. | images | 图片 |

**scripts 部分**

| scripts |   |  |
| -- | -- | -- |
| .. | main.js | `requirejs`的配置，一些别名配置都在这里 |
| .. | common | 项目公共模块（pager等） |
| .. | nls | 本地化语言 |
| .. | page | 对应视图文件的模块，文件夹结构跟views下面的相对应，注意大小写以及命名规范 |

**page部分**

| page |   |  |
| -- | -- | -- |
| .. | main.js | iframe里面`_Layout`使用的模块，主要提供一些常用模块初始化 |
| .. | layout.js | 项目外层`_Layout`使用的模块 |
| .. | cash | 对应视图文件夹 |
| .. | ... | 其他结构跟cash类似 |




## 怎样在页面上加载并初始化一个模块
> 例如cash下面的settings页面 对应的模块是 `xx/page/cash/settings/main`

在`Razor`视图里面这样调用即可
```js
@section Assets{
    <script>
        require(['xx/page/cash/settings/main'],function(Settings){
            //如果有参数就通过options传递进去给模块内部使用,没有的话不用传递
            var options = {};
            new Settings(options)
        })
    </script>
}
```
> 一般在模块里面引用jquery 并把事件注册在 document ready事件里面，这样在页面上就直接初始化就可以了,视图里面尽量少写脚本
