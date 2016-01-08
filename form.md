# 常用自定义表单元素使用说明

## 状态条

> 用来显示自定义状态,如果加载了ko的话可以直接使用 `xxStateBar`,具体配置选项如下

```js

    /**
      * 当前激活选项，默认没有选择任何状态，传递state值进行选中
      */
     active: null,
     /**
      * 是否显示确认对话框 默认显示
      */
     confirm: true,
     /**
      * 显示状态的数据，默认显示如下,可以自定义数据，但是key value必须保持一致
      */
     data: [{
                    state: 2,
                    text: '开放'
                },
                {
                    state: 1,
                    text: '试营'
                },
                {
                    state: 0,
                    text: '关闭'
                }       ],
     /**
      * 服务器端接收地址
      */
     url: '',
     /**
      * 传递到服务器端的数据，默认已经处理state了
      */
     formData: {},
     /**
      * 更新状态成功后的回调函数，一般用不到此选项 基本上都处理好了
      */
     success: function() {

     }


```

**两种配置方式**
1. 行内配置
> 例如下面这个模板，状态条使用的是默认值
```js
<script type="text/x-jquery-tmpl" id="j-siteGamelist">
       ...
    <td>
       <span data-bind="ryStateBar: { active: GameState(), url: '/site/UpdateSiteGameState', formData: { SiteNo: $data.SiteNo(), GameClassID: $data.GameClassID() } }">
</span>
   ...
    </script>
```


2. 使用自定义方法返回配置信息（推荐）
> 使用ViewModel里面的一个自定义方法返回参数配置
```js
function XXXViewModel(){}
...
ViewModel.prototype.stateBar = function (data) {
                //当前行数据
                console.log(data);
                //formData 要转换成js对象，如果使用了mapping的话，使用ko.mapping.toJS(data)转换，我那边用JSON.stringify(formData)将数据传送给服务器
                return {
                    url: '/url',
                    data: [{ state: 1, text: 'some text' }],
                    formData: xxx,
                    active: 1
                }
            }
```

**formData**
要传递的数据







