# String对象

String类型的包装对象

## 构造函数

### String

```
语法：Function String([value]){...}
解释：创建一个String对象
参数：value，值，自动转换为String类型，为空时当作空字符串
返回值：返回创建的String对象

String([value])将value强制转换为String类型，与new String([value])不同
```

### 静态属性

* `length`:`1`, 可接受的参数个数
* `prototype`: `String`实例对象的原型对象，也是个`String`对象
* `__proto__`: `Function.prototype`, 原型，非标准属性

### 静态方法

#### String.formCharCode()

```
语法：String.fromCharCode([...num])
解释：根据Unicode值创建字符串
参数：num, Unicode值，自动转换为整数，进行%65536处理，负数加65536, NaN、Infinity、-Infinity当做0，为空时返回空字符串
返回值：返回Unicode值对应的字符串
```

## 原型对象

### 获取

```
String.prototype
str.__proto__
str.constructor.prototype
Object.getPrototypeOf(str)
```

### 原型属性

* `constructor`: `String`, 构造函数
* `__proto__`: `Object.prototype`, 原型，非标准属性
* `[[PrimitiveValue]]`: 空字符串，对应的原始值，内部属性
* `length`: `0`, 字符串长度，只读

### 原型方法

* 不会改变原字符串
* 大部分方法会存在多字节问题
* 空字符串匹配时，将字符串当作是由空字符串隔开的

#### 转换方法

##### String.prototype.valueOf()

```
语法：String.prototype.valueOf()
解释：返回当前String对象的原始值
返回值：返回[[PrimitiveValue]]值
```

##### String.prototype.toString()

```
语法：String.prototype.toString()
解释：返回当前String对象的字符串表示
返回值：返回[[PrimitiveValue]]值
```

#### 字符方法

##### String.prototype.charAt()

```
语法：String.prototype.charAt(index)
解释：返回字符串指定位置的字符
参数：index, 索引，自动转换为整数，NaN当作0，默认为0
返回值：字符存在，返回字符
       字符不存在，返回空字符串

字符为辅助平面的字符时，charAt(index)+charAt(index+1)才能返回这个字符
```

##### String.prototype.charCodeAt()

```
语法：String.prototype.charCodeAt(index)
解释：返回字符串指定位置的字符对应的Unicode值
参数：index, 索引，自动转换为整数，NaN当作0，默认为0
返回值：字符存在，返回字符对应的Unicode值
       字符不存在，返回NaN

字符为辅助平面的字符时，charAt(index)、charAt(index+1)经过UTF-16到Unicode的转换后才能返回这个字符的Unicode值
```

#### 操作方法

##### String.prototype.concat()

```
语法：String.prototype.concat([...str])
解释：拼接字符串
参数：str, 自动转换为字符串，为空时当作空字符串
返回值：返回拼接后的新字符串

一般使用+来拼接字符串
```

##### String.prototype.slice()

```
语法：String.prototype.slice(begin, end)
解释：提取字符串的一段子串组成新字符串
参数: begin, 开始位置，自动转换为整数，负数为倒数，NaN当作0，默认为0
     end, 结束位置，自动转换为整数，负数为倒数，NaN当作0，默认为length
返回值：返回[begin,end)之间的字符组成的新字符串，没字符时返回空字符串
```

##### String.prototype.substring()

```
语法：String.prototype.substring(begin, end)
解释：提取字符串的一段子串组成新字符串
参数: begin, 开始位置，自动转换为整数，负数、NaN当作0，默认为0
     end, 结束位置，自动转换为整数，负数、NaN当作0，默认为length
返回值：返回[min(begin,end),max(begin,end))之间的字符组成的新字符串，没字符时返回空字符串
```

##### String.prototype.substr()

```
语法：String.prototype.substr(begin, count)
解释：提取字符串的一段子串组成新字符串
参数: begin, 开始位置，自动转换为整数，负数为倒数，NaN当作0，默认为0
     count, 字符数目，自动转换为整数，负数、NaN当作0，默认为length
返回值：返回begin之后的count个字符组成的新字符串，没字符时返回空字符串
```

#### 位置方法

##### String.prototype.indexOf()

```
语法：String.prototype.indexOf(search[, fromIndex])
解释：从左往右查找指定字符串在字符串中第一次出现的位置
参数：search, 要查找的字符串，自动转化为字符串，使用===判断
     fromIndex, 开始查找的位置，自动转换为整数，负数当作0，NaN当作0，为空时当作0
返回值：search能找到，返回第一次出现的索引
       search不能找到，返回-1

str.indexOf("",index), index<=length, 返回index; index>length, 返回length
```

应用

```
// 遍历匹配的子串
var str = 'To be, or not to be, that is the question.';
var arr = [];
var pos = str.indexOf("e");

while (pos !== -1) {
  arr.push(pos);
  pos = str.indexOf("e", pos + 1);
}
```

##### String.prototype.lastIndexOf()

```
语法：String.prototype.lastIndexOf(search[, fromIndex])
解释：从右往左查找指定字符串在字符串中第一次出现的位置
参数：search, 要查找的字符串，自动转化为字符串，使用===判断
     fromIndex, 开始查找的位置，自动转换为整数，负数当作0，NaN当作length, 为空时当作length
返回值：search能找到，返回第一次出现的索引
       search不能找到，返回-1
```

#### 去空格方法

##### String.prototype.trim()

```
语法：String.prototype.trim()
解释：删除字符串的前置和后置空白字符
返回值：返回删除了前置和后置空白字符的新字符串
```

polyfill

```javascript
if (typeof String.prototype.trim !== "function") {
  String.prototype.trim = function () {
    return this.replace(/^\s+|\s+$/g, "");
  }
}
```

#### 大小写转换方法

##### String.prototype.toLowerCase()

```
语法：String.prototype.toLowerCase()
解释：将字符串转换为小写字符串
返回值：返回转换后的新小写字符串
```

##### String.prototype.toUpperCase()

```
语法：String.prototype.toUpperCase()
解释：将字符串转换为大写字符串
返回值：返回转换后的新大写字符串
```

##### String.prototype.toLocaleLowerCase()

```
语法：String.prototype.toLocaleLowerCase()
解释：将字符串转换为本地的小写字符串
返回值：返回转换后的本地的新小写字符串
```

##### String.prototype.toLocaleUpperCase()

```
语法：String.prototype.toLocaleUpperCase()
解释：将字符串转换为本地的大写字符串
返回值：返回转换后的本地的新大写字符串
```

#### 比较方法

##### String.prototype.localeCompare()

```
语法：String.prototype.localeCompare(compareString[, locales[, options])
解释：按字母表的顺序比较两个字符串
参数：compareString, 要比较的字符串，自动转换为字符串
     locales, 区域
     options, 可选配置
返回值：当前字符串在字母表的位置排在compareString前面，返回负数
       当前字符串在字母表的位置排在compareString后面，返回正数
       当前字符串等于compareString，返回0

Unicode字符集中大写字母是在小写字母的前面的，但localeCompare()按字母表顺序比较，大写字母是在小写字母后面的
```

#### 模式匹配方法

##### String.prototype.match()

```
语法：String.prototype.match(regexp)
解释：对字符串进行正则匹配
参数：regexp, 匹配正则，自动转换为正则对象(隐式调用new RegExp(value))，匹配后lastIndex置为0
返回值：有匹配，非全局匹配，返回[匹配子串, ...捕获组的匹配项]且arr.index=匹配子串的索引，arr.input=原始字符串
              全局匹配，返回[...匹配子串]
       无匹配，返回null
```

应用

```javascript
// 非全局匹配
var str = 'For more information, see Chapter 3.4.5.1';
var re = /see (chapter \d+(\.\d)*)/i;
var found = str.match(re);

console.log(found);

// logs [ 'see Chapter 3.4.5.1',
//        'Chapter 3.4.5.1',
//        '.1',
//        index: 22,
//        input: 'For more information, see Chapter 3.4.5.1' ]

// 'see Chapter 3.4.5.1' 是整个匹配。
// 'Chapter 3.4.5.1' 被'(chapter \d+(\.\d)*)'捕获。
// '.1' 是被'(\.\d)'捕获的最后一个值。
// 'index' 属性(22) 是整个匹配从零开始的索引。
// 'input' 属性是被解析的原始字符串。

// 全局匹配
var str = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz';
var regexp = /[A-E]/gi;
var matches_array = str.match(regexp);

console.log(matches_array);
// ['A', 'B', 'C', 'D', 'E', 'a', 'b', 'c', 'd', 'e']

// 不传参数
var str = "Nothing will come of nothing.";

str.match();   // ["", index: 0, input: "Nothing will come of nothing."]
str.match(undefined);   // ["", index: 0, input: "Nothing will come of nothing."]
```

##### String.prototype.search()

```
语法：String.prototype.search(regexp)
解释：对字符串进行正则查找
参数：regexp, 匹配正则，自动转换为正则对象(隐式调用new RegExp(value))
返回值：有匹配，返回从左往右第一次匹配的索引
       无匹配，返回-1
```

##### String.prototype.replace()

```
语法：String.prototype.replace([pattern, replacement])
解释：对字符串进行字符串替换或正则替换
参数：pattern, 字符串或正则，为空时不替换
        substr, 字符串，非正则对象自动转换为字符串，只替换首个匹配
        pattern, 正则对象，根据全局模式决定替换单个还是替换全部
     replacement, 字符串或函数
        newSubStr, 替换字符串，非函数自动转换为字符串，可以插入一些特殊变量
          $$  插入一个 "$"
          $&  插入当前匹配子串
          $`  插入当前匹配子串左边的内容
          $'  插入当前匹配子串右边的内容
          $n  插入第n个捕获组的匹配项，n属于1~99，捕获组不存在时插入$n，匹配项不存在时插入空字符串
        function, 回调函数，每匹配一次调一次，参数为
          match, 当前匹配子串
          ...$n, 捕获组的匹配项
          index, 当前匹配的索引
          string, 被匹配的原字符串
返回值：返回替换后的字符串
```

应用

```javascript
// 交换单词
var re = /(\w+)\s(\w+)/;
var str = "John Smith";
var newstr = str.replace(re, "$2, $1"); // Smith, John

// 温度转换
function f2c(x) {
  function convert(str, p1, offset, s) {
    return ((p1 - 32) * 5 / 9) + "C";
  }
  var s = String(x);
  var test = /(\d+(?:\.\d*)?)F\b/g;
  return s.replace(test, convert);
}
```

##### String.prototype.split()

```
语法：String.prototype.split(separator, limit)
解释：使用匹配的分隔符将字符串分隔成数组
参数：separator, 分隔符，字符串或正则，默认返回由原字符串组成的数组
        subStr, 字符串，非正则对象自动转换为字符串，空字符串返回由原字符串字符组成的数组
        regexp, 正则，有捕获组时，捕获组的匹配项也要添加到数组中，捕获组未捕获到内容时添加undefined(对捕获组的处理存在兼容性问题)
     limit, 限制数组长度，自动转换为整数，NaN当作0，负数不限制，默认不限制
返回值：有匹配的分隔符，返回分隔后的数组
       无匹配的分隔符，返回由原字符串组成的数组
```

## 实例对象

### 创建

```
// 构造函数法
var num = new String([value]);
var num = new Object(str);
```

### 实例属性

* `__proto__`: `String.prototype`, 原型，非标准属性
* `[[PrimitiveValue]]`: 对应的原始值，内部属性
* `<index>`: 索引对应的字符，只读
* `length`: 字符串长度，只读，两字节为1个长度
