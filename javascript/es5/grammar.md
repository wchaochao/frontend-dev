# 语法

## 字符集

[Unicode](unicode.md)字符集

## 编码方式

UCS-2

## 注释

```javascript
// 单行注释

/*
  多行注释
 */
```

## 严格模式

为JavaScript容易出错的地方施加了限制

### 整个JavaScript中

```javascript
"use strict";

//statement
```

### 函数中

```javascript
function foo(){
  "use strict";

  //statement
}
```

## 标识符

变量、函数、属性的名字，或者函数的参数

* 字母、数字、下划线、$组成
* 数字不开头
* 大小写不同
* 不为关键字、保留字
* 尽量语义化

## 关键字

具有特定用途的单词

 列1 | 列2 | 列3 | 列4
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

 列1 | 列2 | 列3 | 列4
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
age = 29; //全局变量，严格模式下会抛出ReferenceError

//声明多个变量
var message = "hi",
  found = false,
  age;
```

## 数据类型

* 原始值类型：`Undefined, Null, Number, String, Boolean`，存储值
* 引用类型：`Object`，存储值的引用

## 操作符

进行某种运算

* 算术运算符
* 比较运算符
* 逻辑运算符
* 条件运算符
* 位运算符
* 赋值运算符
* 类型运算符
* 对象运算符
* 属性运算符
* 逗号运算符
* 圆括号运算符

## 表达式

由数据和操作符组成，进行某种运算，返回运算结果

## 语句

执行某个操作

* 空语句：`;`
* 单语句：以分号结尾，不加分号时由解析器确定语句的结尾
* 多语句：组合到代码块(`{...}`)中

## 函数

封装任意条语句，实现某个功能

## 对象

所有数据都可以视为对象

### Object对象

普通对象

### Function对象

函数也是对象

### 数组

按次序排列的一组值

* 数组长度和数组元素动态关联

### 类数组对象

具有`length`属性的对象，可通过`call(), apply()`调用数组的一些方法

* String对象
* arguments对象
* DOM元素集

### 基本包装对象

`Number, String, Boolean`类型对应的包装对象

* `Number, String, Boolean`类型当作对象使用时，会被包装成相应包装对象，使用完后销毁该对象
  * `Number, String, Boolean`类型当作对象使用时，相应的包装对象是只读的，无法设置属性
  * `Number`直接量当作对象使用时，其后的点会被解释成小数点，需要使用圆括号括起来
* `Undefined, Null`类型没有相应的包装对象，不能当作对象使用，会抛出`TypeError`

### Date对象

用于处理日期和时间

* 使用自1970年1月1日00:00:00(UTC时间)开始经过的毫秒数来保存日期，范围为该时间的前后1亿天
* UTC时间：世界协调时间，UTC时间 = GMT时间
* 本地时`：本地时区时间，UTC时间 + 时区 = 本地时间

### RegExp对象

正则表达式，用于模式匹配

### Error对象

用于错误处理

### 单体内置对象

无须实例化，直接提供的对象

* Global对象：提供全局属性和全局方法
* Math对象：用于数学运算
* JSON对象：用于解析和转换JSON字符串

