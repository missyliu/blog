---
title: 闭包
date: 2016-04-14
tags: ['闭包']
description: 关键字：闭包 作用域 作用域链 立即执行函数表达式（IIFE）
---

## 作用域

* js是词法作用域、函数作用域(局部作用域)
* 变量的作用域是由它在源码中所处位置决定的，并且嵌套的函数可以访问到其外层作用域中声明的变量(词法作用域，闭包)

## 作用域链

在创建函数时，会先创建一个包含全局变量对象的作用域链，作用域链保存在内部[[Scope]]属性中。调用函数时，创建一个执行环境并复制[[Scope]]属性构建执行环境作用域链，同时将当前活动对象推入执行环境作用域链前端。

创建函数：
![image](https://segmentfault.com/image?src=http://7xnxzw.com1.z0.glb.clouddn.com/js%E4%BD%9C%E7%94%A8%E5%9F%9F%E9%93%BE_01.jpg&objectId=1190000003934412&token=11b2459a5d155faf25055b629831ae2b)

调用函数：
![image](https://segmentfault.com/image?src=http://7xnxzw.com1.z0.glb.clouddn.com/js%E4%BD%9C%E7%94%A8%E5%9F%9F%E9%93%BE_02.jpg&objectId=1190000003934412&token=a87c0ae7fee2d0eac31fdb493d874508)

作用域链本质上是一个指向变量对象的指针列表，它只引用但不包含变量对象。

### 执行环境（执行上下文环境）

调用函数时，每个函数都有一个执行上下文环境。它包含文法环境、变量环境、this绑定

## 闭包

指的是有权访问另一个函数作用域中的变量的函数

### 闭包类型

* 模块模式：允许你模拟公共，私有以及特权成员。

```
function Module(){

}
var Module = (function(){
    var privateProperty = "foo";
    function privateMethod(args){
        //do something
    }
    return {
        publicProperty: "",
        publicMethod: function(args){
            //do something
        },
        privilegedMethod: function(args){
            privateMethod(args);
        }
    }
})();
```

* 立即执行函数表达式（IIFE）：仅是一个在window上下文中自我调用的匿名函数。

```
￼var name = "World";
(function(){
    if(typeof name === "undefined"){
      var name = "Jack";
      console.log("Goodbye " + name);
    }else {
      console.log("Hello " + name);
    }
})();
```