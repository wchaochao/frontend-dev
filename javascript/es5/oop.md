# 面向对象编程

## 构造函数

用于创建实例对象

* 任一函数都可以作为构造函数使用
* 约定使用大驼峰命名法命名

## 原型对象

用于包含实例对象共享的属性和方法

* 函数创建时会创建对应的原型对象
* `函数.prototype=原型对象`，`原型对象.constructor=函数`

## 实例对象

* 通过构造函数创建的对象
* `实例对象.__proto__=原型对象`

## 原型链

实现继承

* 原型对象也是一个对象，也有自己的原型`__proto__`
  * 原型对象的原型默认为`Object.prototype`
  * `Object.prototype`的原型为`null`
* 原型对象、原型对象的原型...构成原型链
* 实例对象可以继承原型链上的属性
  * 查找对象属性时，先查找对象本身的，再沿着原型链查找

## 自定义类型

构造函数-原型模式

* 构造函数模式用于定义实例属性
* 原型模式用于定义方法和共享的属性

### 混合模式

```javascript
function Person(name, age, job) {
  this.name = name;
  this.age = age;
  this.job = job;
}

Person.prototype.sayName = function () {
  console.log(this.name);
}
```

### 动态模式

```javascript
function Person(name, age, job) {
  this.name = name;
  this.age = age;
  this.job = job;

  if (typeof this.sayName !== "function") {
    Person.prototype.sayName = function () {
      console.log(this.name);
    }
  }
}
```

工厂模式

* 抛弃构造函数模式，直接在函数内创建一个新对象
* 设置该对象的属性和方法并返回该对象

### 寄生模式

```javascript
function Person(name, age, job) {
  var o = new Object();

  o.name = name;
  o.age = age;
  o.job = job;

  o.sayName = function () {
    console.log(this.name);
  }

  return o;
}
```

### 稳妥模式

```javascript
function Person(name, age, job) {
  var o = new Object();

  //可以在这里定义私有变量和函数

  o.sayName = function () {
    console.log(name);
  }

  return o;
}
```

## 继承

使用原型链实现对原型属性和方法的继承

### 组合继承

常用的继承方式

```javascript
function SuperType(name) {
  this.name = name;
  this.colors = ["red", "blue", "green"];
}

Super.prototype.sayName = function () {
  console.log(this.name);
}

function SubType(name, age) {
  SuperType.call(this, name);

  this.age = age;
}

SubType.prototype = new SuperType();

SubType.prototype.sayAge = function () {
  console.log(this.age);
}
```

### 原型式继承

```javascript
function object(o) {
  function F() {};
  F.prototype = o;
  return new F();
}
```

### 寄生式继承

```javascript
function object(o) {
  function F() {};
  F.prototype = o;
  return new F();
}

function createAnother(o) {
  var clone = object(o);
  clone.sayHi = function () {
    console.log("hi");
  }

  return clone;
}
```

### 寄生组合式继承

最理想的继承方式

```
function object(o) {
  function F() {};
  F.prototype = o;
  return new F();
}

function inheritPrototype(subType, superType) {
  var prototype = object(super.prototype);
  subType.prototype = prototype;
  prototype.constructor = subType;
}

function SuperType(name) {
  this.name = name;
  this.colors = ["red", "blue", "green"];
}

Super.prototype.sayName = function () {
  console.log(this.name);
}

function SubType(name, age) {
  SuperType.call(this, name);

  this.age = age;
}

inheritPrototype(SubType, SuperType);

SubType.prototype.sayAge = function () {
  console.log(this.age);
}
```