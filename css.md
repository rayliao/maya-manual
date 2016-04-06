# css规范

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

**sass规范写法**

* scss可以嵌套写，但不要嵌套太多层，一来不美观，二来影响渲染。

```
// bad
.main {
    .wrapper {
        .guideconbox {
            .guide-line {
                .guide-lines {
                    .guide-linefi {
                        // OMG
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
