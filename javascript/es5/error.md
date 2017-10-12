# Error对象

类型为`Error`的对象

## 构造函数

### Error

```
语法：new Error([message[,fileName[,lineNumber]]])
解释：创建一个错误对象
参数：message, 错误信息，自动转换为字符串，默认为空字符串
     fileName, 错误所在的文件名称，非标准
     lineNumber, 错误所在的文件行号，非标准
返回值：返回创建的错误对象

Error([message])等同于new Error([message])
```

### 子类

* `SyntaxError`: 语法错误
* `ReferenceError`: 无效引用
* `RangeError`: 超出有效范围
* `TypeError`: 类型错误
* `URIError`: `URI`解码或编码错误
* `EvalError`: `eval()`有关错误

### 静态属性

* `length`:`1`, 可接受的参数个数
* `prototype`: `Error`实例对象的原型对象，是个`Object`对象
* `__proto__`: `Function.prototype`, 原型，非标准属性

## 原型对象

### 获取

```
Error.prototype
err.__proto__
err.constructor.prototype
Object.getPrototypeOf(err)
```

### 原型属性

* `constructor`: `Error`, 构造函数
* `__proto__`: `Object.prototype`, 原型，非标准属性

### 原型方法

#### Error.prototype.toString()

```
语法：Error.prototype.toString()
解释：返回当前Error对象的字符串表示
返回值：一般返回this.name + ": " + this.message
```

description

```javascript
Error.prototype.toString = function () {
  "use strict";

  var name = this.name;
  name = (name === undefined) ? "Error" : String(name);

  var msg = this.message;
  msg = (msg === undefined) ? "" : String(msg);

  return name + (name !== "" && msg !== "" ? ": " : "") + msg;
}
```

## 实例对象

### 创建

```
构造函数法
var arr=new Error([message[,fileName[,lineNumber]]]);
var arr=Error([message[,fileName[,lineNumber]]]);
```

### 实例属性

* `__proto__`: `Error.prototype`, 原型，非标准属性
* `name`: 错误名
* `message`: 错误信息
* `stack`: 错误堆栈, 非标准属性
* `fileName`: 错误所在的文件名称, 非标准属性
* `lineNumber`: 错误所在的文件行号, 非标准属性
* `columnNumber`: 错误所在的文件列号, 非标准属性
