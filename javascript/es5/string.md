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
* `[[PrimitiveValue]]`: 对应的原始值，内部属性

### 静态方法

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

#### String.formCharCode()

```
语法：String.fromCharCode([...num])
解释：通过Unicode值创建字符串
参数：num, Unicode值，自动转换为整数
返回值：返回Unicode值对应的字符拼接成的字符串
```

## 实例对象

### 创建

```
// 构造函数法
var num = new String([value]);
var num = new Object(str);
```

### 实例属性

* `<index>`: 索引对应的字符，只读
* `length`: 字符长度，只读