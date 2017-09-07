# 函数

## 创建

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

## 参数

### 形参

* 函数创建时定义的参数
* 重名时后面的会覆盖前面的，严格模式下会抛出`TypeError`

### 实参

* 函数调用时传递的参数
* 函数调用时，会将所有的实参组成一个数组传给`arguments`对象和形参

### arguments对象

* 类数组对象，用于存储实参
* 非严格模式下，`arguments[x]`改变时，相应的形参也会变

## 调用

`fnName(实参)`

* 传递参数
* 执行函数代码
* 返回值

## 返回值

```
有return，return value
无return，return undefined
```