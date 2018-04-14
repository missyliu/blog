---
title: less学习笔记
date: 2016-04-29
description: 关键字：less
---

## 文件扩展名，后缀

.less

## 变量与作用域

* 变量以”@”作为前缀标识，变量名由字母、数字、\_和-组成。
* 用法:

```
// 声明
@color: red;

// 调用
h1 {
	color: @color;
}
```

* 作用域: 存在块级作用域（局部作用域），在当前作用域内值后者覆盖前者。
* 用于选择器或属性名以及字符串拼接时必须使用”@{变量名}”方式调用。
* less仅支持单值类型以及列表类型变量。不支持对象类型，若需要支持需安装插件less-plugin-lists

```
例子：列表类型通过内置函数extract()访问值

@colors: #fff, #ff0, #f00;

.dialog {
  color: extract(@colors, 1);
  font-size: 12px * length(@colors);
}
```

## 混合（mixin）

mixin会将样式规则内联到调用的位置中。

* .XXX或#XXX会自动被定义为mixin，而且具有命名空间
* 不带参数、带参数无默认值、带参数有默认值的mixin
* mixin内置两个特殊的对象 @arguments(所有mixin输入参数) 和 @reset(mixin的…输入参数数组)
* 重载：根据输入参数数量不同去选择调用相应mixin

## @import

## extend

```
<selector>:extend<parentSelector>{}
或者
<selector>{ &:extend(<parentSelector>); }
```

## when

处理逻辑

ref:

* [http://www.cnblogs.com/fsjohnhuang/p/4187675.html#a42](http://www.cnblogs.com/fsjohnhuang/p/4187675.html#a42)