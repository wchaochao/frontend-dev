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

#### 嵌入脚本

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

## 语句

* 空语句：`;`
* 单语句：以分号结尾，不加分号时由解析器确定语句的结尾
* 多语句：组合到代码块(`{...}`)中


# 数据类型

## Undefined类型

值未定义

* 字面量：`undefined`

## Null类型

值为空对象指针

* 字面量：`null`

## Number类型

值为数字

### 存储

64位浮点数存储

* 第1位：符号位
* 第2~12位：指数位
* 第13~64位：小数位

* 数值：`(-1)^符号位*1.小数位*2^指数位`
* 精度：53位有效数字
* 误差：有些值64位浮点数无法精确表示
* 正数范围：`2^-1023到2^1024，大于2^1024为Infinity，小于2^-1023为0`

### 表示

* 字面量法：如10,0xFF,1.2
* 科学计数法：数值[eE]数值，如123e-3

### 字面量

#### 整数

* 十进制：`-?[1-9]\d*|0`
* 二进制：`-?0[bB][01]+`
* 八进制：`-?0[0-7]+`, 严格模式下使用八进制会抛出`SyntaxError`
* 十六进制：`-?0[xX][0-9A-Fa-f]+`

#### 浮点数

* 小数：-?[1-9]\d*\.\d*|0\.\d*

#### 特殊数

* `+0`：正零, 运算时相当于`0+`
* `-0`：负零, 运算时相当于`0-`
* `Infinity`：正无穷大, 运算时相当于`+∞`
* `-Infinity`：负无穷大, 运算时相当于`-∞`
* `NaN`：非数字，运算时返回`NaN`，且`NaN!==NaN`

### 转换为数字

* `Undefined`：`undefined`转换为`NaN`
* `Null`：`null`转换为`0`
* `Number`
  * 其他进制自动转换为十进制
  * 小数点前的数字超过21位或小数点后紧跟的0超过5位，自动转换为科学计数法表示
* `String`: 忽略前置后置空格
  * 空字符串转换为`0`
  * 十进制数字字符串转换为相应的十进制数字，忽略前导零
  * 十六进制字符串转换为十进制整数
* `Boolean`: `true`转换为`1`，`false`转换为`0`
* `Object`：调用`valueOf()`方法
  * 若返回值为原始值类型，则自动转换为数字
  * 若返回值不为原始值类型，则继续调用`toString()`方法
    * 若返回值为原始值类型，则自动转换为数字
    * 若返回值不为原始值类型，则报错

### 相关全局方法

#### isNaN()

```
语法：isNaN(testValue)
解释：检测值是否是NaN
参数：testValue, 被检测的值，自动转换为Number类型
返回值：是NaN，返回true
       不是NaN，返回false
```

#### isFinite()

```
语法：isFinite(testValue)
解释：判断值是否是有限数值
参数：testValue, 被检测的值，自动转换为Number类型
返回值：是NaN、Infinity、-Infinity，返回false
       其他值，返回true
```

#### parseInt()

```
语法：parseInt(string,radix)
解释：按照指定基数将字符串解析成整数并返回该整数
参数：string，字符串，自动转换为String类型，并忽略前置空格
     radix，进制数，自动转换为Number类型
        radix为0、NaN
          string为"0x"或"0X"开头按十六进制解析
          string为"0"开头，ES3按八进制解析，ES5按十进制解析
          其他按十进制解析，无法解析科学计数法
        radix为2~36之间的整数，按照radix进制解析
        radix为其他，返回NaN
返回值：能解析，返回对应的整数
       不能解析，返回NaN
```

#### parseFloat()

```
语法：parseFloat(string)
解释：按照十进制将字符串解析成浮点数并返回该浮点数，可以解析科学计数法
参数：string，字符串，自动转换为String类型，并忽略前导空格
返回值：能解析，返回对应的浮点数
       不能解析，返回NaN
```

## String类型

### 存储

以`UTF-16`格式存储字符

### 表示

* 短字符串：'字符*'或"字符*"
* 长字符串
  * "短字符串" + "短字符串"
  * "短字符串\（换行）短字符串"

### 字面量

* 普通字符：字母、数字、符号、中文等
* 转义字符
  * `\0`: null
  * `\b`: 后退键
  * `\r`: 回车键
  * `\n`: 换行键
  * `\t`: 水平制表符
  * `\v`: 垂直制表符
  * `\f`: 换页符
  * `\'`: 单引号
  * `\"`: 双引号
  * `\\`: 反斜杠
  * `\x两位十六进制`: 对应的Unicode码
  * `\u四位十六进制`: 对应的Unicode码
  * `\其他`: 忽略\

### 转换为字符串

* `Undefined`：`undefined`转换为`"undefined"`
* `Null`：`null`转换为`"null"`
* `Number`：调用`toString()`方法
  * 其他进制自动转换为十进制
  * 小数点前的数字超过21位或小数点后紧跟的0超过5位，自动转换为科学计数法表示
  * 转换为`"自动处理后的数字"`
* `String`: 调用`toString()`方法，Unicode码转换为对应的字符
* `Boolean`: 调用`toString()`方法，`true`转换为`"true"`，`false`转换为`"false"`
* `Object`：调用`toString()`方法
  * 若返回值为原始值类型，则自动转换为字符串
  * 若返回值不为原始值类型，则继续调用`valueOf()`方法
    * 若返回值为原始值类型，则自动转换为字符串
    * 若返回值不为原始值类型，则报错

## Boolean类型

值为布尔值

* 字面量：`true`, `false`

### 转换为布尔值

* `Undefined`：`undefined`转换为`false`
* `Null`：`null`转换为`false`
* `Number`：`0`或`NaN`转换为`false`，其他转换为`true`
* `String`: 空字符串转换为`false`，其他转换为`true`
* `Object`: 有引用转换为`true`，没引用转换为`false`

## Object类型

键值对的集合

## 区分数据类型

使用`typeof`运算符

* 返回`"undefined"`: 值未声明或未初始化
* 返回`"number"`: 值为数字
* 返回`"string"`: 值为字符串
* 返回`"boolean"`: 值为布尔值
* 返回`"function"`: 值为函数
* 返回`"object"`: 值为对象或`null`


# 操作符

对数据进行某种运算，返回运算结果

