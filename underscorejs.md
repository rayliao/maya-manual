# underscorejs

> 是一个JavaScript实用库，提供了80多个函数以及一些专业辅助函数

1. [官网地址 1.6.0](http://underscorejs.org/)
2. [中文翻译 1.5.2](http://learningcn.com/underscore/)

> 项目中的别名是 `_` (下划线),加载模块的时候保持一致，例如
```js
define(['jquery','_'],function($,_){
    //underscore现在已经可以使用了
    var even = _.find([1, 2, 3, 4, 5, 6], function(num){ return num % 2 == 0; });
    => 2
})
```

**更多实用函数请阅读文档，项目中不会再另外写一些跟`Array,Object,Function`相关的公共函数，一律使用`_`**


## 来看几个例子
1. `_.keys(object)`
> 获取 object 对象的所有属性名.
```js
_.keys({one: 1, two: 2, three: 3});
=> ["one", "two", "three"]
```
2. `_.values(object)`
> 获取 object 对象的所有属性值.
```js
_.values({one: 1, two: 2, three: 3});
=> [1, 2, 3]
3. `_.pairs(object)`
> 把一个对象转换成一个 [key, value] 形式的数组.
```js
_.pairs({one: 1, two: 2, three: 3});
=> [["one", 1], ["two", 2], ["three", 3]]
```
4. `_.has(object, key) `
> 判断对象 object 包含指定的属性 key 吗? 和 object.hasOwnProperty(key) 相同, 但是使用了 hasOwnProperty 函数的安全引用, 更多请参考 [意外重写](http://www.devthought.com/2012/01/18/an-object-is-not-a-hash/).
```js
_.has({a: 1, b: 2, c: 3}, "b");
=> true
```


更多有用的方法等着你哈～





