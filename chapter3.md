# 编码规范

## 嵌套函数、if、for

### 嵌套函数

> 嵌套函数很有用, 比如,减少重复代码, 隐藏帮助函数, 等. 没什么其他需要注意的地方, 随意使用

```js
 function myFunction() {
            //do something here
            myHelpFunction();

            function myHelpFunction() {
                //I am nested function
            }
    }
```

### if、for语句的大括号
> 即使只有一条语句，也请加上大括号

```js

    if (true) {
        //do something here...
    }

    for (var i = 0; i < length; i++) {
        //do something here...
    }

```
**不要这样写**

```js
    if (true) xxx
    else xxxx
```


## 注释
> 写给同事看，也是写给自己看

1. 给方法注释
2. 给带有参数的方法详细注释
3. 给复杂的操作注释
4. 简练的注释，不写无意义的注释

```js
/**
 * 声明一个模块
 * @param  {[type]} $ [依赖项目]
 * @return {[type]}   [返回对象供其他模块使用]
 */
define(['jquery'], function($) {



    /**
     * [Item 负责商品页面操作的业务逻辑类]
     * @param {[type]} options [从页面传递给模块使用的对象]
     */
    function Item(options) {

        if (!(this instanceof Item)) {
            return new Item();
        }

        var defaults = {
            pager: true
        };

        /**
         * 该操作是将页面上面传递进来的值跟默认值做一个合并，页面参数优先
         * @type {[type]}
         */
        this.options = $.extend(true, defaults, options);


        //每次实例化的时候在这里初始化，页面上只需加载模块后实例化，如果有参数的话传递给options
        this.initialize();

    }
    /**
     * [get 获取商品的方法]
     * @param  {[type]} id [商品id]
     * @return {[type]}    [返回一个jQuery promise 对象]
     */
    Item.prototype.get = function(id) {
        //示例
        return $.getJSON('/path/to/item', {
            id: id
        })
    }

    /**
     * [initPager 初始化分页函数]
     * @return {[type]} [description]
     */
    Item.prototype.initPager = function() {

        /**
         * 在类里面通过this引用当前对象，如果是嵌套的函数，注意作用域问题
         */
        if (this.options.pager) {
            //do something
        }

        return this
    }

    /**
     * [registerEvents 绑定事件处理]
     * @return {[type]} [description]
     */
    Item.prototype.registerEvents = function() {

        /**
         * 给.j-action 绑定一个click事件，以后所有的事件绑定都用 on off trigger 来完成
         * @param  {[type]} e [description]
         * @return {[type]}   [description]
         */
        $(document).on('click', '.j-action', function(e) {
            e.preventDefault();
            //do something...
            //
        })

        return this

    }

    /**
     * [initialize 初始化方法，在Item类实例化的时候调用，该方法负责一些事件的初始化工作]
     * @return {[type]} [description]
     */
    Item.prototype.initialize = function() {
        /**
         * [self 当前Item类的一个引用，以便在内嵌函数里面访问]
         * @type {[type]}
         */
        var self = this;
        $(function() {
            self.registerEvents.initPager();
        })

    }



    /**
     * 返回Item对象
     */
    return Item

})

```

> 在页面上初始化时使用

```js

/**
 * 加载模块
 * @param  {[type]} Item [该模块提供的对象]
 *
 */
require(['path/to/item-file'], function(Item) {
    //有参数就传递给模块内部使用
    new Item()
})
```




## 参考


[bootstrap编码规范](http://codeguide.bootcss.com/)

[Airbnb JavaScript Style Guide](https://github.com/sivan/javascript-style-guide/blob/master/es5/README.md)
