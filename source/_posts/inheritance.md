---
title: 继承
date: 2016-04-14
tags: ['继承']
description: 关键字：继承 原型 原型链
---

## ES5中的继承

![image](http://img.keenwon.com/2016/03/20160314212504_39150.png)

prototype: 在函数身上，指向原型对象

\__proto__: 在对象身上（包括函数创建的对象, 函数本身和原型对象），指向自身的原型

constructor: 在原型对象上，指向构造函数, 在多级继承的时候，指明构造函数方便在对象上扩展原型属性

Object.\__proto__: 为null，原型的顶端

```
function Super() {}

function Sub() {}
Sub.prototype = new Super();
Sub.prototype.constructor = Sub;

var sub = new Sub();

Sub.prototype.constructor === Sub; // ② true
sub.constructor === Sub; // ④ true
sub.__proto__ === Sub.prototype; // ⑤ true
Sub.prototype.__proto__ == Super.prototype; // ⑦ true
```
ES5中这种最简单的继承，实质上就是将子类的原型设置为父类的实例。

## ES6中的继承

![image](http://img.keenwon.com/2016/01/20160116201909_44777.png)

```
class Super {}

class Sub extends Super {}

var sub = new Sub();

Sub.prototype.constructor === Sub; // ② true
sub.constructor === Sub; // ④ true
sub.__proto__ === Sub.prototype; // ⑤ true
Sub.__proto__ === Super; // ⑥ true
Sub.prototype.__proto__ === Super.prototype; // ⑦ true
```

ES6和ES5的继承是一模一样的，只是多了class和extends（本质上ES6是ES5的语法糖）。ES6的子类和父类，子类原型和父类原型，通过\__proto__连接。

ref:

* [ES5和ES6中的继承](http://keenwon.com/1524.html)