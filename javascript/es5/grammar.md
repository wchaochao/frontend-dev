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

具有特定用途的单词

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

## 语句

* 空语句：`;`
* 单语句：以分号结尾，不加分号时由解析器确定语句的结尾
* 多语句：组合到代码块(`{...}`)中