# 官网切图注意事项

### Photoshop使用技巧
* [Cutterman](http://www.cutterman.cn/v2/cutterman)切图工具导出图层挺方便的。
* 把图层的名称改成带格式的名称，例如`xx.png`或者`xx.jpg`，然后选择“文件”-“生成”-“图像资源”，会在当前psd的目录中生成一个文件夹，里面是对应图层的图片。
* 用切图工具，在“存储为web所用格式”的操作中，`jpg`可以适当调整品质，大尺寸的图片选择`连续`，`png`则选择`交错`。

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