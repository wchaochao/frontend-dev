# Object对象

通过构造函数`Object`生成的对象

## 构造函数

### Object

```
语法：function Object([value]){...}
解释：给value创建一个对象包装器
参数：value，值
返回值：value为Undefined、Null型，返回空Object对象
       value为Number、String、Boolean类型，返回对应的Number、String、Boolean对象
       value为Object类型，返回Object类型本身

Object([value])等同于new Object([value])
```

### 静态属性

* `length`:`1`,形参个数
* `prototype`: `object`实例对象的原型对象，也是个`object`对象

### 静态方法

#### Object.assign

```
语法：Object.assign(target[,...sources])
解释：将源对象本身的可枚举属性复制到目标对象
参数：target, 目标对象，自动转换为对象
     sources, 源对象，可多个，自动转换为对象，null、undefined忽略
返回值：返回目标对象

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

#### Object.create

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