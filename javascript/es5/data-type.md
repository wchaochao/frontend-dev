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

* 字面量法：如10, 0xFF, 1.2
* 科学计数法：数值[eE]数值，如123e-3

### 字面量

#### 整数

* 十进制：`([+-])?([1-9]\d*|0)`
* 二进制：`([+-])?0[bB][01]+`
* 八进制：`([+-])?0[0-7]+`, 严格模式下使用八进制会抛出`SyntaxError`
* 十六进制：`([+-])?0[xX][0-9A-Fa-f]+`

#### 浮点数

* 小数：`([+-])?([1-9]\d*\.\d*|0\.\d*|\.\d+)`

#### 特殊数

* `+0`：正零，运算时相当于`0+`
* `-0`：负零，运算时相当于`0-`
* `Infinity`：正无穷大，运算时相当于`+∞`
* `-Infinity`：负无穷大，运算时相当于`-∞`
* `NaN`：非数字，运算时返回`NaN`，且`NaN!==NaN`

### 转换为数字

* `Undefined`：`undefined`转换为`NaN`
* `Null`：`null`转换为`0`
* `Number`
  * 其他进制自动转换为十进制
  * 小数点前的数字超过21位或小数点后紧跟的0超过5位，自动转换为科学计数法表示
* `String`: 忽略前置后置空格
  * 空字符串转换为`0`, `"Infinity"`转换为`Infinity`
  * 十进制数字字符串转换为相应的十进制数字，忽略前导零
  * 十六进制字符串转换为十进制整数
* `Boolean`: `true`转换为`1`，`false`转换为`0`
* `Object`：调用`valueOf()`方法
  * 若返回值为原始值类型，则自动转换为数字
  * 若返回值不为原始值类型，则继续调用`toString()`方法
    * 若返回值为原始值类型，则自动转换为数字
    * 若返回值不为原始值类型，则报错

转换方式

* 强制转换：`Number(value)`
* 自动转换：数字环境自动转换为`Number`类型

### 相关全局方法

#### isNaN()

```
语法：isNaN(value)
解释：判断值能否转换为NaN
参数：value, 值，自动转换为Number类型
返回值：转换为NaN，返回true
       不能转换为NaN，返回false
```

#### isFinite()

```
语法：isFinite(value)
解释：判断值能否转换为有限数值
参数：value, 值，自动转换为Number类型
返回值：转换为NaN、Infinity、-Infinity，返回false
       转换为其他值，返回true
```

#### parseInt()

```
语法：parseInt(string,radix)
解释：按照指定基数将字符串解析成整数
参数：string, 字符串，自动转换为String类型，并忽略前置空格
     radix, 进制数，自动转换为整数
        radix为0、NaN、Infinity、-Infinity
          string为"0x"或"0X"开头按十六进制解析
          string为"0"开头，ES3按八进制解析，ES5按十进制解析
          其他按十进制解析，无法正确解析科学计数法
        radix为2~36之间的整数，按照radix进制解析
        radix为其他，返回NaN
返回值：能解析，返回解析的整数
       不能解析，返回NaN
```

#### parseFloat()

```
语法：parseFloat(string)
解释：按照十进制将字符串解析成数字，可以解析科学计数法
参数：string，字符串，自动转换为String类型，并忽略前导空格
返回值：能解析，返回解析的十进制数字
       不能解析，返回NaN
```

## String类型

值为字符串

### 存储

以`UTF-16`的编码方式存储字符

### 表示

* 短字符串：'字符*'或"字符*"
* 长字符串

```
"短字符串" + "短字符串"

"短字符串\
短字符串"
```

### 字面量

* 普通字符：字母、数字、符号、中文等
* 转义字符
  * `\0`: `NUL`字符
  * `\r`: 回车符
  * `\n`: 换行符
  * `\t`: 水平制表符
  * `\v`: 垂直制表符
  * `\b`: 退格符
  * `\f`: 换页符
  * `\'`: 单引号
  * `\"`: 双引号
  * `\\`: 反斜杠
  * `\三位八进制`: 对应的Unicode字符
  * `\x两位十六进制`: 对应的Unicode字符
  * `\u四位十六进制`: 对应的Unicode字符
  * `\其他`: 忽略\

### 多字节问题

* JavaScript是用`UCS-2`编码的，按`2`字节来识别字符
* 字符串是用`UTF-16`编码的，存在`2`字节或`4`字节字符
  * 字符串的长度是按两字节为1个长度算的，不一定等于真正的字符数
  * 字符为`2`字节字符时，可以用`str[index]`来表示
  * 字符为`4`字节字符时，需要要用`str[index]+str[index+1]`来表示

### 转换为字符串

* `Undefined`：`undefined`转换为`"undefined"`
* `Null`：`null`转换为`"null"`
* `Number`
  * 其他进制自动转换为十进制
  * 小数点前的数字超过21位或小数点后紧跟的0超过5位，自动转换为科学计数法表示
  * 转换为`"自动处理后的数字"`
* `String`: Unicode码转换为对应的字符
* `Boolean`: `true`转换为`"true"`，`false`转换为`"false"`
* `Object`：调用`toString()`方法
  * 若返回值为原始值类型，则自动转换为字符串
  * 若返回值不为原始值类型，则继续调用`valueOf()`方法
    * 若返回值为原始值类型，则自动转换为字符串
    * 若返回值不为原始值类型，则报错

转换方式

* 强制转换：`String(value)`
* 自动转换：字符串环境自动转换为`String`类型

## Boolean类型

值为布尔值

* 字面量：`true`, `false`

### 转换为布尔值

* `Undefined`：`undefined`转换为`false`
* `Null`：`null`转换为`false`
* `Number`：`0`或`NaN`转换为`false`，其他转换为`true`
* `String`: 空字符串转换为`false`，其他转换为`true`
* `Object`: 有引用转换为`true`，没引用转换为`false`

转换方式

* 强制转换：`Boolean(value)`
* 自动转换：布尔环境自动转换为`Boolean`类型

## Object类型

键值对的集合

### 分类

* 内置对象：ECMAScript里内置的对象，如`Object, Function, Array, Number, String, Boolean, Date, RegExp, Error`等构造函数，`Global, Math, Json`等单体对象
* 宿主对象：由宿主环境提供的对象，如浏览器提供的`window, document`等对象
* 原生对象：通过ECMAScript创建的对象

### 转换为引用类型

强制转换

* `Number`：`Object(num)`或`new Number(num)`
* `String`：`Object(str)`或`new String(str)`
* `Boolean`：`Object(boo)`或`new Boolean(boo)`
* `Object`：`Object(obj)`

自动转换

* `Undefined, Null`类型自动转换为`Object`类型时会抛出`TypeError`
* `Number, String, Boolean`自动转换为对应的包装对象

## 区分数据类型

使用`typeof`运算符检测原始值类型

* 返回`"undefined"`：值未定义
* 返回`"number"`：值为数字
* 返回`"string"`：值为字符串
* 返回`"boolean"`：值为布尔值
* 返回`"function"`：值为函数
* 返回`"object"`：值为对象或`null`

使用`Object.prototype.toString.call()`方法检测引用类型

```
Undefined类型               "[object Undefined]"
Null类型                    "[object Null]"
Number类型或Number对象       "[object Number]"
Booelan类型或Boolean对象     "[object Boolean]"
String类型或String对象       "[object String]"
Object对象                  "[object Object]"
Array对象                   "[object Array]"
Function对象                "[object Function]"
RegExp对象                  "[object RegExp]"
Date对象                    "[object Date]"
Error对象                   "[object Error]"
Arguments对象               "[object Arguments]"
Math对象                    "[object Math]"
JSON对象                    "[object JSON]"
其他对象                     "[object Object]"
```

使用`instanceof`运算符检测引用类型

```
语法：obj instanceof constructor
解释：判断对象是否是某个构造函数的实例
参数：obj，对象，原始值类型返回false
     constructor，构造函数，不为Function类型抛出TypeError
返回值：constructor.prototype在对象obj的原型链上，返回true
       constructor.prototype不在对象obj的原型链上，返回false
```