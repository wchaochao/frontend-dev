# Global对象

全局对象，内置全局属性和全局方法

## 全局属性

* `undefined`: 特殊值`undefined`
* `null`: 特殊值`null`
* `NaN`: 特殊值`NaN`
* `Infinity`: 特殊值`Infinity`
* `Object`: 构造函数`Object`
* `Function`: 构造函数`Function`
* `Array`: 构造函数`Array`
* `Number`: 构造函数`Number`
* `String`: 构造函数`String`
* `Boolean`: 构造函数`Boolean`
* `Date`: 构造函数`Date`
* `RegExp`: 构造函数`RegExp`
* `Error`: 构造函数`Error`
* `SyntaxError`: 构造函数`SyntaxError`
* `ReferenceError`: 构造函数`ReferenceError`
* `RangeError`: 构造函数`RangeError`
* `TypeError`: 构造函数`TypeError`
* `URIError`: 构造函数`URIError`
* `EvalError`: 构造函数`EvalError`

## 全局方法

### 数值方法

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
语法：parseInt(string, radix)
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
参数：string，字符串，自动转换为String类型，并忽略前置空格
返回值：能解析，返回解析的十进制数字
       不能解析，返回NaN
```

### URI方法

#### encodeURI()

```
语法：encodeURI(URI)
解释：对URI进行编码
     非转义字符(字母 数字 - _ . ! ~ * ' ( ))、保留字符(; , / ? : @ & = + $)、数字符号(#)不进行编码
     其他都使用%utf-8字节(16进制)的方式编码
参数：URI，要编码的URI，自动转换为字符串
返回值：返回编码后的URI
```

#### encodeComponentURI()

```
语法：encodeComponentURI(URI)
解释：对URI的组成部分进行编码
     非转义字符(字母 数字 - _ . ! ~ * ' ( ))不进行编码
     其他都使用%utf-8字节(16进制)的方式编码
参数：URI，要编码的URI，自动转换为字符串
返回值：返回编码后的URI
```

#### decodeURI()

```
语法：decodeURI(encodedURI)
解释：解码encodeURI()后的URI
参数：encodedURI，要解码的URI，自动转换为字符串
返回值：返回解码后的URI
```

#### decodeComponentURI()

```
语法：decodeComponentURI(encodedURI)
解释：解码encodeComponentURI()后的URI
参数：encodedURI，要解码的URI，自动转换为字符串
返回值：返回解码后的URI
```

### Eval方法

#### eval()

```
语法：eval(string)
解释：解析执行JavaScript语句字符串
参数：string, JavaScript语句字符串，不是字符串类型直接返回string参数
返回值：返回解析执行JavaScript语句字符串后的返回值
```
