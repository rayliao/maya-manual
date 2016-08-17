# MAYA使用的框架和库

> 在开发项目之前请花点时间阅读其他章节，以下章节列出了一些我们开发中用到的库或框架

> 选择库或者框架的前提：
* 开源并且有足够的文档
* 社区是否获取，个人的看最近是否有更新，如果使用`github`的话，看最近的一些`issue`是否有解决
* 能解决问题即可，不要多余的东西


| 名称 | 官网 | 说明 |
| -- | -- | -- |
| `jquery 1.8.3` | [jquery](http://jquery.com/) | 跨浏览器兼容的一个基本库，提供了一组简洁强大API，用来处理`DOM`、`AJAX`等模块 |
| `requirejs` | [http://requirejs.org/](http://requirejs.org/) | 一个AMD模块加载器，用来组织项目代码 |
| `handlebars` | [handlebarsjs](http://handlebarsjs.com/) | 一个模板引擎，跟`Mustache`语法一致，提供了一组更强大的功能 |
| `Art Dialog 5.0` | [Art Dialog](http://aui.github.com/artDialog) | `AUI`的一个对话框组件，兼容性良好，使用简单 |
| `knockoutjs` | [knockoutjs](http://knockoutjs.com) | 一个MVVM框架，其双向绑定给开发带来很多便利性，兼容 `ie6` |
|`ko-ui`| [gvas](http://gvas.github.io/knockout-jqueryui/) | juqery ui for knockout |
| `json 3` | [json 3](http://bestiejs.github.io/json3) | 对于一些低版本浏览器没有内置`JSON`对象的一个兼容处理，项目开发中不用手动引用了，已经统一处理了，可以放心使用`JSON.parse()`等方法 |
| `es5-shim` | [es5-shim](https://github.com/es-shims/es5-shim) | 对低版本浏览器没有提供`es5`的一些方法的兼容处理 |
| `ueditor` | [ueditor](http://fex-team.github.io/ueditor/) | 富文本编辑器 |
| `datetimepicker` | [datetimepicker](http://xdsoft.net/jqplugins/datetimepicker/) | 一个日期选择插件 |
|`validation-engine` | [validation-engine](http://posabsolute.github.io/jQuery-Validation-Engine/#validators/ajax-selector) | jquery验证插件 |
| `iCheck` | [http://fronteed.com/iCheck/](http://fronteed.com/iCheck/) | 一个`checkbox`,`radio`的美化插件  |
| `jquery.serializeJSON` | [jquery.serializeJSON](https://github.com/marioizquierdo/jquery.serializeJSON) | 序列化`form`表单为`JSON`的一个插件 |
| `blueimp-file-upload` |[https://github.com/blueimp/jQuery-File-Upload](https://github.com/blueimp/jQuery-File-Upload) | 上传插件 |

## 项目内部一些公共模块说明

| 名称 | 别名或路径  | 说明 |
| -- | -- | -- |
| `pager` | `ko-pager`  | 一个`knockout`分页模块  |
| `ajax` | `xx/common/ajax`  | 加了loading效果的ajax方法  |
| `clip` | `xx/common/clip`  | 整合`zeroclipboard`的flash复制解决方案 |
| `datepicker` | `datepicker` | jQuery ui datepicker 默认配置，已包含多语言处理 |
| `datetimepicker` | `datetimepicker` | 时间日期选择插件 |
| `dialog` | `dialog` | 对话框的一些默认配置以及扩展  |
| `editor` | `xx/common/editor` | ueditor编辑器的一些默认配置  |
| `handlebar` | `hb` | handelbar的扩展配置 |
| `icheck` | `ko-icheck`  | `icheck`默认配置，以及`ko`的一个自定义绑定 |
| `ko-with-mapping` | `ko`  | `ko`的一些自定义绑定  |
| `reg` | `xx/common/reg`  | 项目中用到的正则表达式集合 |
| `state-bar` | `ko`  | 自定义状态条，支持自定义数据 |
| `tip` | `xx/common/tip`  | 提示框 |
| `upload` | `upload`  | 上传插件的默认配置  |
| `utils` | `utils`  | 项目中用到的一些公共方法，包括String.fomart的扩展等 |


## 扩展阅读

1. [什么是commonjs](http://wiki.commonjs.org/wiki/CommonJS) &  [阮老师的博客](http://javascript.ruanyifeng.com/nodejs/commonjs.html)
2. [什么是iconfont](http://blog.wpjam.com/m/iconfont/)

> 注

`xx`代表项目 

