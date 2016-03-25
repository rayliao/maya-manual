# 官网切图注意事项

### Photoshop使用技巧
* [Cutterman](http://www.cutterman.cn/v2/cutterman)切图工具导出图层挺方便的。
* 把图层的名称改成带格式的名称，例如`xx.png`或者`xx.jpg`，然后选择“文件”-“生成”-“图像资源”，会在当前psd的目录中生成一个文件夹，里面是对应图层的图片。
* 用切图工具，在“存储为web所用格式”的操作中，`jpg`可以适当调整品质，大尺寸的图片选择`连续`，`png`则选择`交错`。

### sublime text使用技巧
* 编辑器界面底部的状态栏右侧有个叫`Space：*`可以调整缩进，统一规范使用4个空格缩进。
* 安装`package control`之后可以方便安装插件包，如[Emmet](http://emmet.io/)这个插件很好用，更多插件待你发掘。
* 按住`alt` + `shift` + 2，可以把版面拆成两个，同理`1`则合并成一个，`3`则拆成三个。

### TortoiseSVN使用提醒

* 请经常拉取代码，每次修改之前请先拉取代码。
* 在提交代码之前，请先拉取代码，尽量避免需要合并的操作。

### official目录介绍

```
official
  |--app
  |   |--common
  |   |   |--css  //公共样式，诸如日期，弹出层，验证插件的样式，也包括index和member的公共样式。
  |   |   |--img  //公共图片
  |   |   |--js
  |   |      |--common //公共脚本
  |   |      |--lib  //第三方插件
  |   |      |--app.js //requirejs配置
  |   |
  |   |--oldthemes //旧版模板，备份用
  |   |--themes
  |       |--default  //模板名称default
  |       |   |--css  //模板css，注意里面css会引用公共部分的样式，公共有定义的样式就没必要重复写了，所以最好先了解下公共部分的样式定义。
  |       |   |--img
  |       |   |   |--icon  //用于合并雪碧图的图片文件夹，这个会生成_icon.scss的样式
  |       |   |   |--member //存放member的图片，里面也有类似icon的用于雪碧图的文件夹
  |       |   |   |--logo.jpg
  |       |   |   
  |       |   |--js
  |       |   |--member  //存放member的页面
  |       |   |--index.html
  |       |
  |       |--themes1
  |       |--themes2
  |       
  |--gulpfile.js
  |--sprite-tpl.mustache //旧版，弃用
  |--sprity-css.hbs  //雪碧图生成样式的模板
```

### 样式编写提醒

* 请先查看变量文件`_variables.scss`的变量定义，可通过修改变量的值达到样式的定义。

```
//$img是当前图片路径，$img-common是公共图片的路径
//$icon-sprite-path是用于合并雪碧图的路径
$img: '../img/';
$img-common: '../../../common/img/';
$icon-sprite-path: '../img';

//这个是基本布局宽度，用于wrapper
$base-width: 1200px;

//随机版本号，记得加在图片后面
$version: unique-id();

//文本颜色的样式变量，写在公共的layout里
$text-default: #edc2a2;
$text-primary: #c5201e;
$text-success: #3c3c3c;
$text-info: #909090;
$text-warning: #FEAB03;
$text-danger: #c33;

//弹出层的样式变量
$art-dialog-background: #001028;
$art-dialog-border: #104aa0;
$art-dialog-header-background: #02307d;
$art-dialog-header-border: #104aa0;
$art-dialog-footer-button: #fff;
...
```

* 合并图的样式，如`icon`，`bg`等，请在公共样式`layout`之前引入。

* 请先了解公共样式已经定义的样式，不必再重复定义。

公共样式`_layout.scss`说明：
```
//首页的公共样式，慎重修改
@import "variables";

@import "reset";

@import "dialog";

@import "ywz";

@import "validator";

@import "scrollbar";

//移除outline的样式
button, a {
    outline: none;
}

//像这样常用的浮动，相对定位的class已经定义了，就没必要再重复定义了
.fl {
    float: left;
}

.fr {
    float: right;
}

.hide {
    display: none;
}

.hider {
    display: none !important;
}

.relative {
    position: relative;
}

```

* 请把几乎每个分站都会用上的模块(例如头部钱包下拉样式，表单样式，弹出层样式，在线客服样式等)放在前面，便于修改，整理，移除。

* 请把样式写工整一点，便于查看。

该有的空格间隙要加上，看起来舒服点。
```
//bad
.animation1{
  -webkit-animation-duration:1s ;
  -o-animation-duration:1s ;
  animation-duration:1s ;
}

//good
.animation1 {
    -webkit-animation-duration: 1s;
    -o-animation-duration: 1s;
    animation-duration: 1s;
}
```

* 尽量避免使用颜色来定义样式。

```
//bad
.red {
  color: red;
}

.btn-red {
  background: red;
}
```
