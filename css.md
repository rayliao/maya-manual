# css规范

在VS Code安装了扩展之后，在根目录添加`stylelintrc`配置文件，具体配置规则可以参考其官网，配置好之后，打开样式文件，会自动检测规范，右下角的状态栏会针对不规范的写法提示警告提示。

**合理声明字体**

首先因为设计稿都会有统一的基本字体，所以字体统一在`body`声明就可以了，避免到处声明字体，除非里面内容需要用到其他字体，才需要在内容那重写字体的声明。

下面给个合理声明字体的写法：
```
font-family: Helvetica, Tahoma, Arial, STXihei, "华文细黑", "Microsoft YaHei", "微软雅黑", SimSun, "宋体", Heiti, "黑体", sans-serif;
```

上面的写法适用于手机端兼容各平台设备，PC端有几点参考下就可以了。

* 同时声明中文字体的字体名称（英文）和显示名称（中文）。
* 英文字体在中文字体之前。
* 最后补充英文字体族。`serif`或`sans-serif`。
* 有空格的英文字体名称和中文字体名称加上双引号。如`"Microsoft YaHei", "微软雅黑"`。

**css规范写法**

* 使用2个空格作为缩进
* 类名使用破折号代替驼峰法
* 不要使用ID选择器
* 在一个规则声明中应用了多个选择器时，每个选择器独占一行
* 在规则声明的左大括号 { 前加上一个空格
* 在属性的冒号 : 后面加上一个空格，前面不加空格
* 规则声明的右大括号 } 独占一行
* 规则声明之间用空行分隔开

```
// Bad

.avatar{
    border-radius:50%;
    border:2px solid white; }
.no, .nope, .not_good {
    // ...
}
#lol-no {
  // ...
}

// Good

.avatar {
  border-radius: 50%;
  border: 2px solid white;
}

.one,
.selector,
.per-line {
  // ...
}
```

**JavaScript钩子**

避免在 CSS 和 JavaScript 中绑定相同的类。否则开发者在重构时通常会出现以下情况：轻则浪费时间在对照查找每个要改变的类，重则因为害怕破坏功能而不敢作出更改。

我们推荐在创建用于特定 JavaScript 的类名时，添加 .j- 前缀：
```
<button class="btn btn-primary j-request-to-book">Request to Book</button>
```

### sass规范写法

**属性声明的顺序**

1.属性声明

首先列出除去`@include`和嵌套选择器之外的所有属性声明。

```
.btn-green {
  background: green;
  font-weight: bold;
  // ...
}
```

2.`@include`声明，紧随的是`@include`声明。

```
.btn-green {
  background: green;
  font-weight: bold;
  @include transition(background 0.5s ease);
  // ...
}
```

3.接着是嵌套选择器。

* scss可以嵌套写，但不要嵌套太多层（最好最好不要超过3层），一来不美观，二来影响渲染。

```
// bad
.main {
    .wrapper {
        .guideconbox {
            .guide-line {
                .guide-lines {
                    .guide-linefi {
                        // 我的天啊！！！
                    }
                }
            }
        }
    }
}

// good，只要跟其他样式不会有混淆，就没必要嵌套
.main {
    .wrapper {

    }
    .guideconbox {

    }
    .guide-line {

    }
    .guide-lines {

    }
    .guide-linefi {

    }
}
// 另外说一下，上面class的命名不建议，line、lines和linefi，含义模糊，让人看了一头雾水，不知道是同辈的还是父子辈的。
```
* 永远不要嵌套ID选择器！

* `ImageMagick Display`和`GraphicsMagick Display`这两个软件不要删除，因为之前有同事删掉，然后雪碧图的task用不了，所以这里提一下。（这个不需要了）

* css应该要一个模块一个模块标识清楚，公共的样式统一放在前面，便于自己和他人修改。

* 请先检查variables里面有什么变量，直接修改变量值就可以了，不用重复写

* 合并图的样式请在layout之前引入

* 请先检查引入的样式已经有了什么，像常见的浮动，对齐方式等都有了，没必要又重新写一遍

* 请把几乎每个分站都会用上的模块(例如头部钱包下拉样式，表单样式，弹出层样式，在线客服样式等)放在前面，便于修改，整理，移除。

* 请不要使用大小驼峰式命名法命名class名称