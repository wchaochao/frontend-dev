# Object对象

类型为`Object`的对象

## 构造函数

### Object

```
语法：function Object([value]){...}
解释：给value创建一个对象包装器
参数：value，值
返回值：value为Undefined、Null型，返回空Object对象
       value为Number、String、Boolean类型，返回对应的Number、String、Boolean对象
       value为Object类型，返回value本身

Object([value])等同于new Object([value])
```

### 静态属性

* `length`:`1`, 必须要传入的参数个数
* `prototype`: `Object`实例对象的原型对象，也是个`Object`对象

### 静态方法

#### Object.assign()

```
语法：Object.assign(target[,...sources])
解释：将源对象本身的可枚举属性复制到目标对象
参数：target, 目标对象，自动转换为对象
     sources, 源对象，可多个，自动转换为对象，null、undefined忽略
返回值：返回target

目标对象的只读属性被覆盖时，抛出异常停止复制
```

polyfill

```javascript
if (typeof Object.assign !== "function") {
  Object.assign = function (target) {
    "use strict";

    if (target == null) {
      throw new TypeError("Cannot convern undefined or null to object");
    }

    target = Object(target);
    for (var i = 1; i < arguments.length; i++) {
      var source = arguments[index];
      if (source != null) {
        for (var key in source) {
          if (Object.prototype.hasOwnProperty.call(source, key)) {
            target[key] = source[key];
          }
        }
      }
    }

    return target;
  }
}
```

#### Object.is()

```
语法：Object.is(value1, value2)
解释：判断两个值是否是相同的值
参数：value1, 值1
     value2, 值2
返回值：进行严格相等比较
       0和+0是相同的值，和-0是不同的值
       NaN和NaN是相同的值

Object.is(0,+0)=true, Object.is(0,-0)=false, Object.is(+0,-0)=false
Object.is(NaN,NaN)=true
```

polyfill

```javascript
if (typeof Object.is !== "function") {
  Object.is = function (x, y) {
    if (x === y) {
      return x !== 0 || 1 / x === 1 / y;
    } else {
      return x !== x && y !== y;
    }
  }
}
```

#### Object.create()

```
语法：Object.create(proto[,propertiesObject])
解释：使用指定原型和属性创建一个新对象
参数：proto，原型对象，不为Object、Null类型抛出TypeError
     propertiesObject, 属性对象{...key:descriptor}，自动转换为对象
        key，属性名，自动转换为String类型
        descriptor, 属性描述对象，必须是Object类型，否则会抛出TypeError
返回值：返回创建的对象
```

polyfill

```javascript
if (typeof Object.create !== "function") {
  Object.create = function (proto, propertiesObject) {
    if (!(typeof proto === "obejct" || typeof proto === "function")) {
      throw TypeError("Argument must be an object, or null");
    }

    var temp = new Object();
    temp.__proto__ = proto;
    Object.defineProperties(temp, propertiesObject);

    return temp;
  }
}
```

#### Object.getPrototypeOf()

```
语法：Object.getPrototypeOf(obj)
解释：获取对象的原型
参数：obj, 对象，自动转换为Object类型
返回值：返回obj的原型
```

#### Object.setPrototypeOf()

```
语法：Object.setPrototypeOf(obj, prototype)
解释：设置对象的原型
参数：obj, 对象，必须是Object类型，Null、Undefined类型抛出TypeError，Number、String、Boolean类型直接返回obj
     prototype, 原型对象，不为Object、Null类型抛出TypeError
返回值：返回obj
```

polyfill

```javascript
if (typeof Object.setPrototypeOf !== "function") {
  Object.setPrototypeOf = function (obj, prototype) {
    if (obj == null) {
      throw new TypeError("Object.setPrototypeOf called on null or undefined");
    }

    if (!(typeof obj === "object" || typeof obj === "function")) {
      return obj;
    }

    if (!(typeof prototype === "object" || typeof prototype === "function")) {
      throw new TypeError("Object prototype may only be an Object or null")
    }

    obj.__proto__ = prototype;
    return obj;
  }
}
```

#### Object.getOwnPropertyNames()

```
语法：Object.getOwnPropertyNames(obj)
解释：获取对象本身的所有属性名
参数：obj，对象，自动转换为Object类型
返回值：返回对象本身所有属性名组成的数组
```

#### Object.keys()

```
语法：Object.keys(obj)
解释：获取对象本身的所有可枚举属性名
参数：obj，对象，自动转换为Object类型
返回值：返回对象本身的所有可枚举属性名组成的数组
```

#### Object.getOwnPropertyDescriptor()

```
语法：Object.getOwnPropertyDescriptor(obj,key)
解释：获取对象本身属性的属性描述对象
参数：obj，对象，自动转换为Object类型
     key，属性名，自动转换为String类型
返回值：key为obj本身的属性，返回属性的属性描述对象
       key不为obj本身的属性，返回undefined
```

#### Object.defineProperty()

```
语法：Object.defineProperty(obj,key,descriptor)
解释：设置对象的某个属性
参数：obj，对象，必须是Object类型，否则会抛出TypeError
     key，属性名，自动转换为String类型
     descriptor, 属性描述对象，必须是Object类型，否则会抛出TypeError
返回值：返回obj
```

#### Object.defineProperties()

```
语法：Object.defineProperties(obj,propertiesObject)
解释：设置对象的多个属性
参数：obj，对象，必须是Object类型，否则会抛出TypeError
     propertiesObject, 属性对象{...key:descriptor}，自动转换为对象
        key，属性名，自动转换为String类型
        descriptor, 属性描述对象，必须是Object类型，否则会抛出TypeError
返回值：返回obj
```

#### Object.preventExtensions()

```
语法：Object.preventExtensions(obj)
解释：阻止对象扩展，即对象不可添加属性，不可更换原型
     使用用defineProperty()、defineProperties()添加属性，抛出TypeError
     直接添加属性，严格模式下抛出TypeError
参数：obj，对象，原始值类型直接返回原始值
返回值：返回obj
```

#### Object.isExtensibel()

```
语法：Object.isExtensibel(obj)
解释：判断对象是否是不可扩展的
参数：obj，对象，原始值类型返回false
返回值：obj是可扩展的，返回true
       obj是不可扩展的，返回false
```

#### Object.seal()

```
语法：Object.seal(obj)
解释：密封对象，即对象不可扩展、不可配置
参数：obj，对象，原始值类型直接返回原始值
返回值：返回obj
```

#### Object.isSealed()

```
语法：Object.isSealed(obj)
解释：判断对象是否是密封的
参数：obj，对象，原始值类型直接返回true
返回值：obj是密封的，返回true
       obj不是密封的，返回false
```

#### Object.freeze()

```
语法：Object.freeze(obj)
解释：冻结对象，即对象不可扩展、不可配置、不可修改
     使用用defineProperty()、defineProperties()修改属性，抛出TypeError
     直接修改属性，严格模式下抛出TypeError
参数：obj，对象，原始值类型直接返回原始值
返回值：返回obj

属性值为Object类型时，该属性值非冻结
```

#### Object.isFrozen()

```
语法：Object.isFrozen(obj)
解释：判断对象是否是冻结的
参数：obj，对象，原始值类型直接返回true
返回值：obj是冻结的，返回true
       obj不是冻结的，返回false
```

## 原型对象

### 获取

```
Object.prototype
obj.__proto__
obj.constructor.prototype
Object.getPrototypeOf(obj)
```

### 原型属性

* `constructor`: `Object`, 构造函数
* `__proto__`: `null`, 原型，非标准属性

### 原型方法

#### Object.prototype.hasOwnProperty()

```
语法：Object.prototype.hasOwnProperty(key)
解释：判断是否是当前对象本身的属性
参数：key，属性名，自动转换为String类型
返回值：key是当前对象本身的属性，返回true
       key不是当前对象本身的属性，返回false
```

#### Object.prototype.prototypeIsEnumerable()

```
语法：Object.prototype.propertyIsEnumerable(key)
解释：判断是否是当前对象本身的可枚举属性
参数：key，属性名，自动转换为String类型
返回值：key是当前对象本身的可枚举属性，返回true
       key不是当前对象本身的可枚举属性，返回false
```

#### Object.prototype.isPrototypeOf()

```
语法：Object.prototype.isPrototypeOf(obj)
解释：判断当前对象否在指定对象的原型链上
参数：obj，对象，原始值类型自动返回false
返回值：当前对象在obj的原型链上，返回true
       当前对象不在obj的原型链上，返回false
```

#### Object.prototype.valueOf()

```
语法：Object.prototype.valueOf()
解释：返回当前对象的原始值
返回值：无原始值时返回当前对象
```

#### Object.prototype.toString()

```
语法：Object.prototype.toString()
解释：返回当前对象的字符串表示
返回值：返回"[object "+type+"]", type为当前对象类型
```

#### Object.prototype.toLocalString()

```
语法：Object.prototype.toLocaleString()
解释：返回当前对象的本地字符串表示
返回值：调用toString()方法
```

## 实例对象

### 创建

```
// 字面量法
var o = { ...nameValuePair};

// 构造函数法
var o = new Object([value]);
var o = Object([value]);

// create方法
var o = Object.create(proto[, propertiesObject])

// {}出现在句首解释为语句
```

### 常用操作

遍历对象本身的可枚举属性

```
for (var key in obj) {
  if (Object.prototype.hasOwnProperty.call(obj, key)) {
    // statement
  }
}

// 或者
Object.keys(obj).forEach(function (key) {
  // statement
})
```

判断对象类型

```
function type(obj) {
  var str = Object.prototype.toString.call(obj);
  return str.match(/\[object (.*?)\]/)[1].toLowerCase();
}

var arr = ["Undefined", "Null", "Number", "String", "Boolean", "Object", "Function", "Array", "Date", "RegExp", "Error", "Math"];
arr.forEach(function (value) {
  type["is" + value] = function (obj) {
    return type(obj) === value.toLowerCase();
  }
})
```