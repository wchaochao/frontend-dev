# Number对象

Number类型的包装对象

## 构造函数

### Number

```
语法：Function Number([value]){...}
解释：创建一个Number对象
参数：value，值，自动转换为Number类型，为空时当作0
返回值：返回创建的Number对象

Number([value])将value强制转换为Number类型，与new Number([value])不同
```

### 静态属性

* `length`:`1`, 可接受的参数个数
* `prototype`: `Number`实例对象的原型对象，也是个`Number`对象
* `__proto__`: `Function.prototype`, 原型，非标准属性
* `EPSILON`: 可表示数字间的最小间隔
* `MAX_SAFE_INTEGER`: 2^53-1, 最大的安全整数
* `MAX_VALUE`: 能表示的最大的正数
* `MIN_VALUE`: 能表示的最小的正数
* `NAN`: 非数字
* `POSITIVE_INFINITY`: 正无穷大，大于`MAX_VALUE`的值会被转换为`POSITIVE_INFINITY`
* `NEGATIVE_INFINITY`: 负无穷大，小于`-MAX_VALUE`的值会被转换为`NEGATIVE_INFINITY`

### 静态方法

#### Number.isNaN()

```
语法：Number.isNaN(value)
解释：判断值是否是数字NaN
参数：value, 值，不自动转换
返回值：是数字且是NaN，返回true，其他返回false
```

polyfill

```javascript
if (typeof Number.isNaN !== "function") {
  Number.isNaN = function (value) {
    return typeof value === "number" && isNaN(value);
  }
}
```

#### Number.isFinite()

```
语法：isFinite(value)
解释：判断值是否是有限数字
参数：value, 值，不自动转换
返回值：是有限数字，返回true，其他返回false
```

polyfill

```javascript
if (typeof Number.isFinite !== "function") {
  Number.isFinite = function (value) {
    return typeof value === "number" && isFinite(value);
  }
}
```

#### Number.isInteger()

```
语法：Number.isInteger(value)
解释：判断值是否是整数
参数：value，值，不自动转换
返回值：值是整数，返回true，其他返回false
```

polyfill

```javascript
if (typeof Number.isInteger !== "function") {
  Number.isInteger = function (value) {
    return Number.isFinite(value) && Math.floor(value) === value;
  }
}
```

#### Number.isSafeInteger()

```
语法：Number.isSafeInteger(value)
解释：判断值是否是安全整数，即[-Number.MAX_SAFE_INTEGER, Number.MAX_SAFE_INTEGER]之间的整数
参数：value，值，不自动转换
返回值：值是安全整数，返回true，其他返回false
```

polyfill

```javascript
if (typeof Number.isSafeInteger !== "function") {
  Number.isSafeInteger = function (value) {
    return Number.isInteger(value) && Math.abs(value) <= Number.MAX_SAFE_INTEGER;
  }
}
```

#### Number.parseInt()

同`ParseInt()`

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

#### Number.parseFloat()

同`parseFloat()`

```
语法：parseFloat(string)
解释：按照十进制将字符串解析成数字，可以解析科学计数法
参数：string，字符串，自动转换为String类型，并忽略前导空格
返回值：能解析，返回解析的十进制数字
       不能解析，返回NaN
```

## 原型对象

### 获取

```
Number.prototype
num.__proto__
num.constructor.prototype
Object.getPrototypeOf(num)
```

### 原型属性

* `constructor`: `Number`, 构造函数
* `__proto__`: `Object.prototype`, 原型，非标准属性
* `[[PrimitiveValue]]`: 0，对应的原始值，内部属性

### 原型方法

#### 格式化方法

##### Number.prototype.toFixed()

```
语法: Number.prototype.toFixed(digists)
解释：将数字格式化为数字形式的字符串，保留指定位数的小数
参数：digists, 位数，自动转换为整数，NaN转换为0，不在0~20之间抛出RangeError，默认为0
返回值：当前Number对象的原始值大于等于1e+21时，直接调用Number.prototype.toString()
       当前Number对象的原始值不大于1e+21时，返回保留指定位数小数的数字形式的字符串

因为浮点数不是精确存储的，所以四舍五入有时有用，有时没用
```

##### Number.prototype.toExponential()

```
语法：Number.prototype.toExponential(digists)
解释：将数字格式化为指数形式的字符串，保留指定位数的小数
参数：digists, 位数，自动转换为整数，NaN转换为0，不在0~20之间抛出RangeError，默认为原指数式的小数位数
返回值：返回保留指定位数小数的指数形式的字符串

因为浮点数不是精确存储的，所以四舍五入有时有用，有时没用
```

##### Number.prototype.toPrecision()

```
语法：Number.prototype.toPrecison(precision)
解释：将数字格式化为合适形式的字符串以保留指定位数的有效数字
参数：precision, 有效数字，自动转换为整数，NaN转换为0，不在1~21之间抛出RangeError，默认调用Number.prototype.toString()
返回值：返回保留指定位数有效数字的字符串

因为浮点数不是精确存储的，所以四舍五入有时有用，有时没用
```

#### 转换方法

##### Number.prototype.valueOf()

```
语法：Number.prototype.valueOf()
解释：返回当前Number对象的原始值
返回值：返回[[PrimitiveValue]]值
```

##### Number.prototype.toString()

```
语法：Number.prototype.toString(radix)
解释：根据指定的进制数返回当前Number对象的字符串表示
参数：radix, 进制数，自动转换为整数，不在2~36之间抛出RangeError，默认为10
返回值：返回[[PrimitiveValue]]值的radix进制字符串
```

##### Number.prototype.toLocaleString()

```
语法：Number.prototype.toLocaleString([locales[, options]])
解释：根据指定格式返回当前Number对象的字符串表示
参数：locales, 区域
     options, 可选配置
返回值：返回[[PrimitiveValue]]值对应的指定格式的字符串
```

## 实例对象

### 创建

```
// 构造函数法
var num = new Number([value]);
var num = new Object(num);
```

### 实例属性

* `__proto__`: `Number.prototype`, 原型，非标准属性
* `[[PrimitiveValue]]`: 对应的原始值，内部属性