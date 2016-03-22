# 官网绑页面注意事项

### TortoiseHg使用提醒

* 请经常拉取代码，每次修改之前请先拉取代码。
* 在提交代码之前，请先拉取代码，尽量避免需要合并的操作。
* 遇到合并的情况，如果不能用工具解决，就先采用他人的版本，自己的再加上去。
* 添加删除文件，记得提交工程文件`XX.Official.Web.csproj`

### 复制新站

没用上的文件记得删掉。

**修改文件**

修改`theme.config`，就是改`themes7`这个值:
````
<?xml version="1.0" encoding="utf-8" ?>
<Theme title="themes7"
	  themeType="custom"
      previewImageUrl="~/themes/themes7/preview.jpg"
      previewText="themes7"> 
</Theme>
````
修改`_ViewStart.cshtml`，就是改`themes7`这个值：
````
@{
    Layout = "~/themes/themes7/Views/Shared/_Layout.cshtml"; 
}
````
**保留图片**

img文件夹下：
````
favicon.ico，loading.gif, noactivity.png
````
member文件夹下:
````
freeze.png, level.gif，loading.gif, noaccess.png，valid_false.png, valid_true.png，valid_warn.png
````
### 多语言
多语言分数据库多语言和文本多语言，前者用于重复性较高的每个站都会有的，后者是针对自己站的特殊的多语言。
##### 数据库多语言命名规则
````
分类名：
Common //用于公共和首页
Member //会员中心专用

属性名：
Tips //用于提示方面，诸如弹出框，内容提示
Label //用于文本描述
Button //用于按钮
Valid //用于验证
Title //用于标题
````
##### 文本多语言
命名写法
````
//Index.cshtml
Model.Add("Special-lang-zh_cn", "我就是特殊多语言！");
Model.Add("Special-lang-zh_tw", "我就是特殊多語言！");
Model.Add("Special-lang-en", "Wo jiu shi te shu duo yu yan!");
````
用法
````
@{
  var currentLang = Configuration.Default.ClientLang;
  var lDic = new Dictionary<string, string>();
}

@Html.Partial("_PatialLang", lDic)

@Html.Raw(lDic["Special-lang-" + currentLang])
````