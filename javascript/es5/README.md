# ES5

ECMAScript第5版

## 目录

* [概述](overview.md)
* [语法](grammar.md)
* [数据类型](data-type.md)
* [操作符](operator.md)
* [语句](statement.md)
* [函数](function.md)
* [上下文](context.md)
* [对象](object.md)
* [面向对象编程](oop.md)
* [Object对象](object-builtin.md)
* [Function对象](function-builtin.md)
* [Array对象](array.md)
* [Number对象](number.md)
* [String对象](string.md)
* [Boolean对象](boolean.md)
* [Date对象](date.md)
* [RegExp对象](regexp.md)
* [Error对象](error.md)
* [Global对象](global.md)
* [Math对象](math.md)
* [JSON对象](json.md)
* [console对象](console.md)
* [严格模式](strict.md)

## 推荐资料

* 《JavaScript高级程序设计》
* [JavaScript 标准参考教程](http://javascript.ruanyifeng.com/)
* [JavaScript 标准库](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects)

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

* 原型对象也是一个对象，也有自己的原型对象`__proto__`
  * 原型对象的原型对象一般为`Object.prototype`
  * `Object.prototype`的原型对象为`null`
* 原型对象、原型对象的原型对象...构成原型链
* 实例对象可以继承原型链上的属性
  * 查找对象属性时，先查找对象本身的，再沿着原型链查找

## 自定义类型

### 构造函数-原型模式

* 构造函数模式用于定义实例属性
* 原型模式用于定义方法和共享的属性

#### 混合模式

```javascript
function Person(name,age,job){
  this.name=name;
  this.age=age;
  this.job=job;
}

Person.prototype.sayName=function(){
  console.log(this.name);
}
```

#### 动态模式

```javascript
function Person(name,age,job){
  this.name=name;
  this.age=age;
  this.job=job;

  if(typeof this.sayName!=="function"){
    Person.prototype.sayName=function(){
      console.log(this.name);
    }
  }
}
```

### 工厂模式

* 抛弃构造函数模式，直接在函数内创建一个新对象
* 设置该对象的属性和方法并返回该对象

#### 寄生模式

```javascript
function Person(name,age,job){
  var o=new Object();

  o.name=name;
  o.age=age;
  o.job=job;

  o.sayName=function(){
    console.log(this.name);
  }

  return o;
}
```

#### 稳妥模式

```javascript
function Person(name,age,job){
  var o=new Object();

  //可以在这里定义私有变量和函数

  o.sayName=function(){
    console.log(name);
  }

  return o;
}
```



