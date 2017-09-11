# 函数

## 分类

### 函数声明

```
语法: function fnName([arg1[,arg2[,...argN]]]){...}
位置: 全局上下文或函数上下文中
创建: 初始化上下文时
```

### 函数表达式

```
语法: 匿名函数表达式 function([arg1[,arg2[,...argN]]]){...}
      命名函数表达式 function fnName([arg1[,arg2[,...argN]]){...}
位置: 表达式位置
创建: 执行上下文代码时
```

### Function构造

```
语法: new Function([arg1[,arg2[,...argN]],][functionBody])
     Function([arg1[,arg2[,...argN]],][functionBody])
位置: 表达式位置
创建: 执行上下文代码时
```

## 创建

```
F = new NativeObject();


// 属性[[Class]]是"Function"
F.[[Class]] = "Function"


// 函数对象的原型是Function的原型
F.[[Prototype]] = Function.prototype


// 用到函数自身
// 调用表达式F的时候激活[[Call]]
// 并且创建新的执行上下文
F.[[Call]] = <reference to function>


// 在对象的普通构造器里编译
// [[Construct]] 通过new关键字激活
// 并且给新对象分配内存
// 然后调用F.[[Call]]初始化作为this传递的新创建的对象
F.[[Construct]] = internalConstructor


// 当前执行上下文的作用域链
// 例如，创建F的上下文
F.[[Scope]] = activeContext.Scope
// 如果函数是命名函数，
// 那么
F.[[Scope]] = activeContext.Scope+fnName.Scope
// 如果函数通过new Function(...)来创建，
// 那么
F.[[Scope]] = globalContext.Scope


// 传入参数的个数
F.length = countParameters


// F对象创建的原型
__objectPrototype = new Object();
__objectPrototype.constructor = F // {DontEnum}, 在循环里不可枚举x
F.prototype = __objectPrototype


return F
```

## 参数

### 形参

* 函数创建时定义的参数
* 重名时后面的会覆盖前面的，严格模式下会抛出`TypeError`

### 实参

* 函数调用时传递的参数
* 函数调用时，会将所有的实参组成一个数组传给`arguments`对象和形参

### arguments对象

* 类数组对象，用于存储实参，`arguments.length`为实参个数
* 非严格模式下，`arguments[x]`改变时，相应的形参也会变

## 调用

```
直接调用：fnName(实参)
递归调用：在函数内调用函数本身
立即调用: (function(){})();或(function(){}());
```

* 传递参数
* 执行函数代码
* 返回值

## 返回值

```
有return，return value
无return，return undefined
```

## 闭包

* 上下文加代码块组成闭包
* 任何函数都是闭包

读取内部变量

```
var data=[];
for(var i=0;i<10;i++){
     data[i]=(function(index){
          return function(){
              console.log(index);
          }
     })(i);
}
```

封装私有属性

```
function Person(name) {
  var _age;
  function setAge(n) {
    _age = n;
  }
  function getAge() {
    return _age;
  }

  return {
    name: name,
    getAge: getAge,
    setAge: setAge
  };
}
```