# Boolean对象

Boolean类型的包装对象

## 构造函数

### Boolean

```
语法：Function Boolean([value]){...}
解释：创建一个Boolean对象
参数：value，值，自动转换为Boolean类型，未传入时为false
返回值：返回创建的Boolean对象

Boolean([value])将value强制转换为Boolean类型，与new Boolean([value])不同
```

### 静态属性

* `length`:`1`, 可接受的参数个数
* `prototype`: `Boolean`实例对象的原型对象，也是个`Boolean`对象

## 原型对象

### 获取

```
Boolean.prototype
boo.__proto__
boo.constructor.prototype
Object.getPrototypeOf(boo)
```

### 原型属性

* `constructor`: `Boolean`, 构造函数
* `__proto__`: `Object.prototype`, 原型，非标准属性
* `[[PrimitiveValue]]`: false，对应的原始值，内部属性

### 原型方法

#### Boolean.prototype.valueOf()

```
语法：Boolean.prototype.valueOf()
解释：返回当前Boolean对象的原始值
返回值：返回[[PrimitiveValue]]值
```

#### Boolean.prototype.toString()

```
语法：Boolean.prototype.toString()
解释：返回当前Boolean对象的字符串表示
返回值：返回[[PrimitiveValue]]值转换的字符串
```

## 实例对象

### 创建

```
// 构造函数法
var num = new Boolean([value]);
var num = new Object(boo);
```

### 实例属性

* `__proto__`: `Boolean.prototype`, 原型，非标准属性
* `[[PrimitiveValue]]`: 对应的原始值，内部属性
