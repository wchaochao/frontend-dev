# Array对象

类型为`Array`的对象

## 构造函数

### Array

```
语法：new Array(arrayLength)
     new Array([...element])
解释：创建一个数组对象
参数：arrayLength, 数组长度，必须是Number类型，不是0~2^31-1之间的整数时抛出RangeError
     element, 数组元素，可为任意值
返回值：返回创建的数组

Array([...args])等同于new Array([...args])
```

### 静态属性

* `length`:`1`, 必须要传入的参数个数
* `prototype`: `Array`实例对象的原型对象，也是个`Array`对象

### 静态方法

#### Array.isArray()

```
语法：Array.isArray(value)
解释：判断值是否是数组
参数：value, 值
返回值：value是数组，返回true
       value不是数组，返回false
```

polyfill

```javascript
if (typeof Array.isArray !== "function") {
  Array.isArray = function (value) {
    return Object.prototype.toString.call(value) === "[object Array]";
  }
}
```

## 原型对象

### 获取

```
Array.prototype
arr.__proto__
arr.constructor.prototype
Object.getPrototypeOf(arr)
```

### 原型属性

* `constructor`: `Array`, 构造函数
* `__proto__`: `Object.prototype`, 原型，非标准属性
* `length`: `0`，数组长度为`0`

### 原型方法



## 实例对象

### 创建

```
字面量法
var arr=[...element];

构造函数法
var arr=new Array([...args]);
var arr=Array([...args]);
```

### 实例属性

* `<index>`: 数组元素，元素不存在时为空元素
* `length`: 数组长度，动态值，值为最大的`index`加`1`
  * 最大的`index`变化时，`length`跟着变化
  * `length`变化时，数组跟着延长或截短
  * 数组元素被删除时，`length`不变