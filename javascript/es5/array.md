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

#### 转换方法

##### Array.prototype.join()

```
语法：Array.prototype.join(separator)
解释：将当前数组转换为字符串并用指定分隔符分隔
参数：separator, 分隔符，自动转换为String类型，undefined转换为","
返回值：数组的每个元素调用toString()转换为字符串拼接起来，并用分隔符分隔
       null, undefined转换为空字符串
```

应用

```javascript
// 使用call(), apply()方法时，根据指定this指针的length属性来进行操作
// length自动转换为自然数，无法转换时转换为0
// 能用于字符串，因为没有更改字符串

// 用于字符串
Array.prototype.join.call("hello","-") // "h-e-l-l-o"

// 用于类数组对象
var obj = { 0: 'a', 1: 'b', length: 2 };
Array.prototype.join.call(obj, '-') // "a-b"
```

##### Array.prototype.toString()

```
语法：Array.prototype.toString()
解释：返回当前数组的字符串表示
返回值：数组的每个元素调用toString()转换为字符串拼接起来，并用逗号分隔
       null, undefined转换为空字符串
```

##### Array.prototype.toLocalString()

```
语法：Array.prototype.toLocalString()
解释：返回当前数组的本地字符串表示
返回值：数组的每个元素调用toLocalString()转换为字符串拼接起来，并用逗号分隔
       null, undefined转换为空字符串
```

#### 栈方法

##### Array.prototype.push()

```
语法：Array.prototype.push([...args])
解释：将值添加到当前数组末尾
参数：args，值
返回值：返回push后当前数组的长度
```

##### Array.prototype.pop()

```
语法：Array.prototype.pop()
解释：移除当前数组最后一个元素
返回值：返回移除的元素，数组为空时返回undefined
```

##### 栈方法应用

```javascript
// 使用call(), apply()方法时，根据指定this指针的length属性来进行操作
// length自动转换为自然数，无法转换时转换为0
// 不能用于字符串，因为字符串不能被更改

// 合并数组
var vegetables = ['parsnip', 'potato'];
var moreVegs = ['celery', 'beetroot'];

Array.prototype.push.apply(vegetables, moreVegs);

// 像数组一样使用对象
var obj = {
  addElem: function () {
    Array.prototype.push.apply(this, arguments);
  },
  pop: function () {
    return Array.prototype.pop.call(this);
  }
}
console.log(obj.pop()); // undefined
obj.addElem({}, null, []);
console.log(obj); // Object {0: Object, 1: null, 2: Array(0), length: 3, addElem: function, pop: function}
console.log(obj.pop()); // []
console.log(obj); // Object {0: Object, 1: null, length: 2, addElem: function, pop: function}
```

#### 队列方法

##### Array.prototype.unshift()

```
语法：Array.prototype.unshift([...args])
解释：将值添加到当前数组开头
参数：args，值
返回值：返回unshift后当前数组的长度
```

##### Array.prototype.shift()

```
语法：Array.prototype.shift()
解释：移除当前数组第一个元素
返回值：返回移除的元素，数组为空时返回undefined
```

##### 队列方法应用

```javascript
// 使用call(), apply()方法时，根据指定this指针的length属性来进行操作
// length自动转换为自然数，无法转换时转换为0
// 不能用于字符串，因为字符串不能被更改
```

#### 重排序方法

##### Array.prototype.reverse()

```
语法：Array.prototype.reverse()
解释：颠倒当前数组元素的顺序
返回值：返回经过排序后的当前数组
```

##### Array.prototype.sort()

```
语法：Array.prototype.sort([compareFunction])
解释：按指定比较函数给当前数组排序
参数：compareFunction, 比较函数
返回值：返回经过排序后的当前数组
```

比较函数

```
compareFunction不为函数
将数组元素转化为字符串，按字符串升序排列

compareFunction为函数
compareFunction(a,b)返回值小于0，a排在b前面
compareFunction(a,b)返回值大于0，a排在b后面
compareFunction(a,b)返回值等于0，a、b的相对位置不变

按数字大小升序排列
arr.sort(function (a, b) {
  return a - b;
})

按某个属性升序排序
arr.sort(function (a, b) {
  if (a.key < b.key) {
    return -1;
  } else if (a.key > b.key) {
    return 1;
  } else {
    return 0
  }
})
```

#### 操作方法

##### Array.prototype.concat()

```
语法：Array.prototype.concat([...args])
解释：创建当前数组的一个副本，并将传入的参数添加到副本的末尾
参数：args, 值或数组，将值或数组的元素添加到副本的末尾
返回值：返回创建的副本数组
```

##### Array.prototype.slice()

```
语法：Array.prototype.slice([begin[,end]])
解释：抽取当前数组的一段元素组成新数组
参数: begin, 开始位置，自动转换为整数，负数为倒数，NaN当作0，默认为0
     end, 结束位置，自动转换为整数，负数为倒数，NaN当作0，默认为length
返回值：返回[start,end)之间的数组元素组成的新数组
```

##### Array.prototype.splice()

```
语法：Array.prototype.splice(start[,deleteCount[,...args]])
解释：在当前数组的某个位置删除或插入某些项
参数：start, 开始位置，自动转换为整数，负数为倒数，NaN当作0
     deleteCount, 要删除的数组元素个数，自动转换为整数，负数、NaN当作0，默认为`length-start`
     args，要插入的元素
返回值：返回删除元素组成的数组
```

#### 位置方法

##### Array.prototype.indexOf()

```
语法：Array.prototype.indexOf(searchElement[,fromIndex])
解释：从左往右查找指定元素在当前数组中第一次出现的位置
参数：searchElement, 要查找的元素，使用===判断
     fromIndex, 开始查找的位置，自动转换为整数，负数为倒数，NaN当作0，默认为0
返回值：searchElement能找到，返回第一次出现的索引
       searchElement不能找到，返回-1
```

##### Array.prototype.lastIndexOf()

```
语法：Array.prototype.lastIndexOf(searchElement[,fromIndex])
解释：从右往左查找指定元素在当前数组中第一次出现的位置
参数：searchElement, 要查找的元素，使用===判断
     fromIndex, 开始查找的位置，自动转换为整数，负数为倒数，NaN当作0，默认为length-1
返回值：searchElement能找到，返回第一次出现的索引
       searchElement不能找到，返回-1
```

#### 迭代方法

在使用迭代方法时最好不要修改数组

* 新添加的元素不会被迭代
* 未被迭代的元素被修改，迭代时值为修改后的元素
* 未被迭代的元素被delete删除，迭代时会跳过该元素
* 元素被数组方法移除时，index对应的元素将受到影响

```
参数：callback, 数组中每个元素都要执行的函数，会跳过空元素，必须是Function类型，接收三个参数
        currentValue, 当前元素
        index, 当前元素对应的索引
        array, 当前数组
      thisArg, callback的this指针
```

##### Array.prototype.forEach()

```
语法：Array.prototype.forEach(callback[,thisArg])
解释：遍历当前数组
返回值：无返回值，返回undefined
```

##### Array.prototype.every()

```
语法：Array.prototype.every(callback[,thisArg])
解释：判断当前数组的元素是否都满足条件
返回值：对每个元素执行callback()，都返回true，返回ture
       对每个元素执行callback()，有一个返回false，直接返回false,
```

##### Array.prototype.some()

```
语法：Array.prototype.some(callback[,thisArg])
解释：判断当前数组中是否有满足条件的元素
返回值：对每个元素执行callback()，有一个返回true，直接返回true
       对每个元素执行callback()，都返回false，返回false
```

##### Array.prototype.filter()

```
语法：Array.prototype.filter(callback[,thisArg])
解释：过滤当前数组
返回值：返回执行callback()后返回true的数组元素组成的新数组
```

##### Array.prototype.map()

```
语法：Array.prototype.filter(callback[,thisArg])
解释：映射当前数组
返回值：返回执行callback()后返回值组成的新数组
```

#### 缩小方法

##### Array.prototype.reduce()

```
语法：Array.prototype.reduce(callback[,initivalValue])
解释：从左往右对当前数组进行迭代操作
参数：callback, 迭代函数，会跳过空元素，必须是Function类型，接收四个参数
        accumulator, 迭代值，上一次调用回调返回的值
        currentValue, 当前元素
        index, 当前元素的索引
        array, 当前数组
     initivalValue, accumulator的初始值
        不存在时，accumulator=arr[0], 从第二项元素开始迭代
        空数组initivalValue不存在时会报错
返回值：返回accumulator
```

##### Array.prototype.reduceRight()

```
语法：Array.prototype.reduceRight(callback[,initivalValue])
解释：从右往左对当前数组进行迭代操作
参数：callback, 迭代函数，会跳过空元素，必须是Function类型，接收四个参数
        accumulator, 迭代值，上一次调用回调返回的值
        currentValue, 当前元素
        index, 当前元素的索引
        array, 当前数组
     initivalValue, accumulator的初始值
        不存在时，accumulator=arr[arr.length-1], 从倒数第二项元素开始迭代
        空数组initivalValue不存在时会报错
返回值：返回accumulator
```

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