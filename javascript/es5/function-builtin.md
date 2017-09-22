# Function对象

类型为`Function`的对象

## 构造函数

### Function

```
语法：function Function([...args,][functionBody]){...}
解释：创建一个Function对象
参数：args，函数形参，自动转换为字符串类型，如"a"(参数a)或"a,b"(参数a,b)
     functionBody，函数代码，传入的最后一个参数，自动转换为字符串类型
返回值：返回创建的函数

Function([...args,][functionBody])等同于new Function([...args,][functionBody])
```

### 静态属性

* `length`:`1`, 必须要传入的参数个数
* `prototype`: `Function`实例对象的原型对象，也是个`Function`对象
* `caller`: 调用函数的函数，非标准属性
* `name`: 函数的名称，非标准属性

## 原型对象

### 获取

```
Function.prototype
fn.__proto__
fn.constructor.prototype
Object.getPrototypeOf(fn)
```

### 原型属性

* `constructor`: `Function`, 构造函数
* `__proto__`: `Object.prototype`, 原型，非标准属性
* `length`: `0`，必须传入的参数个数为`0`

### 原型方法

#### function.prototype.call()

```
语法：Function.prototype.call(thisArg[,...args]])
解释：执行当前函数，并指定this指针和实参
参数：thisArg，this对象，非严格模式下，Undefined、Null类型自动转换为全局对象，Number、String、Boolean类型自动转换为相应的内置对象
     args，实参
返回值：返回当前函数执行后的返回值
```

#### function.prototype.apply()

```
语法：Function.prototype.apply(thisArg[,argsArray]])
解释：执行当前函数，并指定this指针和实参数组
参数：thisArg，this对象，非严格模式下，Undefined、Null类型自动转换为全局对象，Number、String、Boolean类型自动转换为相应的内置对象
     argsArray，实参数组或类数组
返回值：返回当前函数执行后的返回值
```

应用

```javascript
// 找出数组的最大元素，最小元素
var arr = [10, 2, 4, 15, 9];

var min = Math.min.apply(null, arr);
var max = Math.max.apply(null, arr);

// 将类数组对象转换为叔祖对象
function foo() {
  console.log(Array.prototype.slice.apply(arguments))
}
```

#### function.prototype.bind()

```
语法：Function.prototype.bind(thisArg[,...args]]])
解释：指定当前函数的this指针和形参，以此生成一个新的函数
参数：thisArg，this对象，非严格模式下，Undefined、Null类型自动转换为全局对象，Number、String、Boolean类型自动转换为相应的内置对象
     args，形参
返回值：返回生成的函数
```

polyfill

```javascript
if (typeof Function.prototype.bind !== "function") {
  Function.prototype.bind = function () {
    var fn = this,
      context = arguments[0],
      args = Array.prototype.slice.call(arguments, 1);

    return function () {
      return fn.apply(context, args);
    }
  }
}
```

应用

```javascript
// 与call结合
var slice=Function.prototype.call.bind(Array.prototype.slice);
slice([1, 2, 3], 0, 1) // [1]

function f() {
  console.log(this.v);
}

var o = { v: 123 };
var bind=Function.prototype.call.bind(Function.prototype.bind);
bind(f, o)() // 123
```

### Function.prototype.toString()

```
语法：Function.prototype.toString()
解释：返回当前函数的字符串表示
返回值：返回函数的源码
```

## 实例对象

### 创建

```
函数声明
function fnName([...args]){...}

表达式法
var foo=function([...args]){...}
var foo=function fnName([...args){...}

构造函数法
var foo=new Function([...args,][functionBody])
var foo=Function([...args,][functionBody])

function出现在句首解释为语句
```

### 实例属性

* `__proto__`: `Function.prototype`, 原型，非标准属性
* `prototype`: 函数的`prototype`属性，是个`Object`对象
* `length`: 必须要传入的参数个数
* `caller`: 调用函数的函数，非标准属性
* `name`: 函数的名称，非标准属性
