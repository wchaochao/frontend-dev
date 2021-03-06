# 对象

键值对的无序集合

## 创建

通过构造函数创建实例对象

```
/*
 * 创建实例对象
 */

// 调用构造函数F的[[Construct]]方法创建空实例对象
F.[[Construct]](initialParameters):

O = new NativeObject();

// 对象类别设置为构造函数名
O.[[Class]] = "[[构造函数名]]"

// 原型对象
var __objectPrototype = F.prototype;
// 如果__objectPrototype是对象，就:
O.[[Prototype]] = __objectPrototype
// 否则:
O.[[Prototype]] = Object.prototype;

/*
 * 初始化实例对象
 */

// 调用构造函数的[[Call]]方法初始化该实例对象
// 这里R是[[Call]]的返回值
// 相当于R = F.apply(O, initialParameters);
R = F.[[Call]](initialParameters); this === O;

/*
 * 返回实例对象
 */

// 如果R是对象
return R
// 否则
return O
```

## 属性

一对键值对

* `key`：属性名
  * 纯数值、关键字、保留字也可为属性名，其他不符合命名规范的需要加引号才能为属性名
  * 属性名相同时，后面的会覆盖前面的
* `value`：属性值
  * 可为任意值
  * 属性值为函数时，该属性称为方法

分类

* 静态属性：不需实例化的对象的属性
* 静态方法：不需实例化的对象的方法
* 实例属性：实例对象的属性
* 实例方法：实例对象的方法

## 属性描述对象

保存属性元信息的对象

### 元属性

* `value`：属性值，默认为`undefined`
* `writable`：是否可写，默认为`false`
  * `true`: 可修改`value`
  * `false`: 不可修改`value`，设置属性在严格模式下会抛出`TypeError`
* `enumerable`：是否可枚举，默认为`false`
  * `true`：可枚举，在`for/in, Object.Keys, JSON.stringify`中使用枚举属性
  * `false`: 不可枚举
* `configurable`：是否可配置，默认为`false`
  * `true`: 可配置
    * 其他描述属性都可修改，`writable`为`false`时, 也可修改`value`
    * 属性可删除
  * `false`: 不可配置
    * `writable`为`true`时，`writable, value`可修改
    * 其他情况描述属性都不可修改，该属性也不可删除，否则严格模式会抛出`TypeError`
* `get`：属性的访问器函数，只能为函数或`undefined`，否则会抛出`TypeError`，默认为`undefined`
  * `get`为`undefined`时，属性不可读，读取属性在严格模式下会抛出`TypeError`
* `set`：属性的设置器函数，只能为函数或`undefined`，否则会抛出`TypeError`，默认为`undefined`
  * `set`为`undefined`时，属性不可写，设置属性在严格模式下会抛出`TypeError`

### 描述符

属性描述对象只能是下列描述符中的一种，混合会抛出`TypeError`，默认为数据描述符

* 数据描述符：使用`value、writable、enumerable、configurable`等元属性的属性描述对象
* 存取描述符：使用`get、set、enumerable、configurable`等元属性的属性描述对象

### 默认描述

* 内置对象的内置属性的`writable、enumerable、configurable`都为`false`
* var声明的变量的`writable、enumerable`为`true`，`configurable`为`false`
* 直接添加的属性的`writable、enumerable、configurable`都为`true`

## 访问属性

* 点标记法：`obj.key`
  * `key`不符合命名规范时不能用点标记法
* 索引标记法：`obj["key"]`
  * `[]`内可以为表达式

## 读取属性

```
O.[[Get]](P):

/*
 * 属性在对象本身上，直接返回
 */

if (O.hasOwnProperty(P)) {
  return O.P;
}


/*
 * 属性不在对象本身上，查找原型链
 */

var __proto = O.[[Prototype]];

// 如果原型是null，返回undefined
if (__proto === null) {
  return undefined;
}

// 否则，对原型链递归调用[[Get]]，在各层的原型中查找属性，直到原型为null
return __proto.[[Get]](P)
```

## 设置属性

```
O.[[Put]](P, V):

/*
 * 属性不可设置，直接退出
 */

if (!O.[[CanPut]](P)) {
  return;
}


/*
 * 属性可设置
 * 属性不存在，添加属性
 * 属性存在，修改属性
 */

// 如果对象没有该属性，就创建它
if (!O.hasOwnProperty(P)) {
  createNewProperty(O, P, attributes: {
    value:V,
    writable:true,
    enumerable:true,
    configurable:true
  });
}

// 如果属性存在就设置值，但不改变attributes特性
O.P = V

return;
```

## 删除属性

### delete prop

```
语法：delete prop
解释：删除对象本身的可删除属性
参数：prop, 对象本身的属性，如obj.key或obj["key"]
返回值：prop不是对象本身的属性，返回true
       prop是对象本身的属性且可删除，删除该属性并返回true
       prop是对象本身的属性且不可删除，返回false，严格模式下抛出TypeError

var声明的变量、内置对象的内置属性不可删除
数组元素被删除时并不影响数组长度
```

## 检测属性

### obj.hasOwnProperty()

```
语法：obj.hasOwnProperty(key)
解释：判断是否是对象本身的属性
参数：key，属性名，自动转换为String类型
     obj，对象，自动转换为对象
返回值：key是对象本身的属性，返回true
       key不是对象本身的属性，返回false
```

### obj.propertyIsEnumerable()

```
语法：obj.propertyIsEnumerable(key)
解释：判断是否是对象本身的可枚举属性
参数：key，属性名，自动转换为String类型
     obj，对象，自动转换为对象
返回值：key是对象本身的可枚举属性，返回true
       key不是对象本身的可枚举属性，返回false
```

### in

```
语法：key in obj
解释：判断是否是对象本身及其原型链上的属性
参数：key，属性名，自动转换为String类型
     obj，对象，必须是Object类型，否则会抛出TypeError
返回值：key是对象本身及其原型链上的属性，返回true
       key不是对象本身及其原型链上的属性，返回false
```

## 查看属性

### Object.getOwnPropertyNames()

```
语法：Object.getOwnPropertyNames(obj)
解释：获取对象本身的所有属性名
参数：obj，对象，自动转换为Object类型
返回值：返回对象本身所有属性名组成的数组
```

### Object.keys()

```
语法：Object.keys(obj)
解释：获取对象本身的所有可枚举属性名
参数：obj，对象，自动转换为Object类型
返回值：返回对象本身的所有可枚举属性名组成的数组
```

## 遍历属性

```
语法：for(var key in obj)
解释：遍历对象及对象的原型链上所有可枚举的属性
```
