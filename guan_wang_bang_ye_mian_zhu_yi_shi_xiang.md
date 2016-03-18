# 官网绑页面注意事项

### 多语言
多语言分数据库多语言和文本多语言，前者用于重复性较高的，后者是针对自己的站的多语言。
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