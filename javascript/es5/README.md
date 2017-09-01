# ES5

ECMAScript第5版

## 目录


## 推荐资料

* 《JavaScript高级程序设计》


# 概述

一门嵌入式、弱类型、解释型、面向对象的脚本语言

> * 嵌入式: 依赖宿主环境提供API
> * 弱类型：无类型声明，可任意转换
> * 解释型: 解释执行，非编译
> * 面向对象: 适合面向对象和函数式编程

## 使用

### 网页中

按出现的先后顺序依次解析

#### 嵌入

```html
<script type="text/javascript">
  console.log('javascript');
</script>

<noscript>本页面需要浏览器支持（启用）JavaScript</noscript>
```

#### 外部脚本文件

一般放在`body`元素的最后面

```html
<body>
  <!--内容-->
  <script src="myscript"></script>
</body>
```

### nodejs中

使用`nodejs`执行`js`文件

### 在线

使用[codepen](https://codepen.io), [jsbin](http://jsbin.com/?html,output),[jsfiddle](https://jsfiddle.net/)等在线工具进行在线编辑和实时预览


# 语法

## 注释

```javascript
// 单行注释

/*
  多行注释
 */
```

## 严格模式

整个`js`中

```javascript
"use strict";

//statement
```

函数中

```javascript
function foo(){
  "use strict";

  //statement
}
```

## 标识符

变量、函数、属性的名字，或者函数的参数

* 字母、数字、下划线、`$`组成
* 数字不开头
* 大小写不同
* 不为关键字、保留字
* 尽量语义化

## 关键字

具有特定用途的关键字

---------|----------|---------|----------
 break | do | instanceof | typeof
 case | else | new | var
 catch | finally | return | void
 continue | for | switch | while
 debugger | function | this | with
 default | if | throw | delete
 in | try

## 保留字

还没有特定用途，但可能在将来被用作关键字

---------|----------|---------|----------
 abstract | enum | int | short
 boolean | export | interface | static
 byte | extends | long | super
 char | final | native | synchronized
 class | float | package | throws
 implements | protected | volatile | double
 import | public | let | yield

## 变量

松散类型，可以用来保存任何类型的数据

```javascript
//声明
var message //值为undefined

//先声明再赋值
var number;
// ...statement
number = 10;

//声明并赋值
var flag = true;

//直接赋值不声明
age = 29; //全局变量，不推荐

//声明多个变量
var message = "hi",
  found = false,
  age;
```

## 数据类型

* 原始值类型：`Undefined, Null, Number, String, Boolean`，存储值
* 引用类型：`Object`，存储值的引用

### Undefined类型

* 表示：值未定义
* 字面量：`undefined`

### Null类型

* 表示：值为空对象指针
* 字面量：`null`

### Number类型

* 表示：值为数字
* 

### Boolean类型

* 表示：值为布尔值
* 字面量：`true`, `false`

### 区分数据类型

使用`typeof`运算符

* 返回`"undefined"`: 值未声明或未初始化
* 返回`"number"`: 值为数字
* 返回`"string"`: 值为字符串
* 返回`"boolean"`: 值为布尔值
* 返回`"function"`: 值为函数
* 返回`"object"`: 值为对象或`null`

## 语句

* 空语句：`;`
* 单语句：以分号结尾，不加分号时由解析器确定语句的结尾
* 多语句：组合到代码块(`{...}`)中