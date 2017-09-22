# String对象

String类型的包装对象

## 构造函数

### String

```
语法：Function String([value]){...}
解释：创建一个String对象
参数：value，值，自动转换为String类型，未传入时为空字符串
返回值：返回创建的String对象

String([value])将value强制转换为String类型，与new String([value])不同
```

### 静态属性

* `length`:`1`, 必须要传入的参数个数
* `prototype`: `String`实例对象的原型对象，也是个`String`对象

### 静态方法

#### String.formCharCode()

```
语法：String.fromCharCode([...num])
解释：通过Unicode值创建字符串
参数：num, Unicode值，自动转换为整数，进行%65536处理，NaN、Infinity、-Infinity当做0
返回值：返回Unicode值按UTF-16编码转换的字符串
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
语法：String.prototype.charAt([index])
解释：返回当前String对象指定位置的字符
参数：index, 索引，自动转换为整数，NaN当作0，默认为0
返回值：字符存在，返回字符
       字符不存在，返回空字符串

字符为辅助平面的字符时，charAt(index)+charAt(index+1)才能返回这个字符
```

##### String.prototype.charCodeAt()

```
语法：String.prototype.charCodeAt([index])
解释：返回当前String对象指定位置的字符对应的Unicode值
参数：index, 索引，自动转换为整数，NaN当作0，默认为0
返回值：字符存在，返回字符对应的Unicode值
       字符不存在，返回NaN

字符为辅助平面的字符时，charAt(index)、charAt(index+1)经过UTF-16到Unicode的转换后才能返回这个字符的Unicode值
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
* `<index>`: 索引对应的字符，只读, 不存在时为空元素
* `length`: 字符串长度，只读，两字节为1个长度
