# 严格模式

## 显示报错

一些静默失败的操作会显示报错

### 只读属性不能写

```javascript
(function () {
  "use strict";

  var obj = {};
  Object.defineProperty(obj, "x", {
    value: 1
  })
  obj.x = 2; //TypeError: Cannot assign to read only property 'x' of object '#<Object>'

  var obj = {};
  Object.defineProperty(obj, "x", {
    get: function () {
      return 1
    }
  });
  obj.x = 2; //TypeError: Cannot set property x of #<Object> which has only a getter

})();
```

### 不可配置属性不能删除

```javascript
(function () {
  "use strict";

  var obj = {};
  Object.defineProperty(obj, "x", {
    value: 1
  })
  Object.defineProperty(obj, "x", {
    configurable: true
  }); //TypeError: Cannot redefine property: x

  var obj = {};
  Object.defineProperty(obj, "x", {
    value: 1
  })
  delete obj.x; //TypeError: Cannot delete property 'x' of #<Object>

  var x = 1;
  delete x; //SyntaxError: Delete of an unqualified identifier in strict mode.

})();
```

### 冻结对象不能添加、修改、删除属性

```javascript
(function () {
  "use strict";

  var o = {
    a: 1
  };
  Object.freeze(o);

  o.b = 2; //TypeError: Cannot add property b, object is not extensible

  delete o.a; //TypeError: Cannot delete property 'a' of #<Object>

  o.a = 2; //TypeError: Cannot assign to read only property 'a' of object '#<Object>'
})();
```

### eval、arguments不可用作标识符

```
(function () {
  "use strict";

  // SyntaxError: Unexpected eval or arguments in strict mode

  var eval = 1;

  function arguments() {}

  function foo(arguments) {}

})();
```

### 函数参数不能重名

```javascript
(function () {
  "use strict";

  // SyntaxError: Duplicate parameter name not allowed in this context

  function foo(a, a, b) {
    return a + b;
  }

})();
```

## 禁止事项

### 禁止使用八进制

```
(function () {
  "use strict";

  var x = 0100; //Uncaught SyntaxError: Octal literals are not allowed in strict mode.

})();
```

### 禁止使用fn.caller, fn.arguments, arguments.callee

```javascript
(function () {
  "use strict";

  // Uncaught TypeError: 'caller', 'callee', and 'arguments' properties may not be accessed on
  // strict mode functions or the arguments objects for calls to them   

  function f1() {

    f1.caller;

    f1.arguments;

    arguments.callee;
  }

  f1();

})();
```

### 禁止给原始值类型设置属性

```javascript
(function () {
  "use strict";

  "sty".you = 1; // TypeError: Cannot create property 'you' on string

})()
```

### 禁止使用with语句

```javascript
(function () {
  "use strict";

  with(o) { // Uncaught SyntaxError: Strict mode code may not include a with statement
    v = 2;
  }

})();
```

## 增强措施

### 变量一定要用var声明

```javascript
(function () {
  "use strict";

  x = 1; //Uncaught ReferenceError: x is not defined

})();
```

### this不自动转换

```
函数单纯作为函数调用时，this为undefined，不转换为全局对象
函数调用call(), apply(), bind()时，this为设置的值，不转换为Object类型
```

### arguments对象与形参不再共享值

```javascript
function f(a) {
  a = 2;
  return [a, arguments[0]];
}

f(1); // 正常模式为[2, 2]

function f(a) {
  "use strict";
  a = 2;
  return [a, arguments[0]];
}

f(1); // 严格模式为[2, 1]
```

### 创建eval作用域

```javascript
(function () {
  'use strict';

  var x = 2;

  console.log(eval('var x = 5; x')) // 5
  console.log(x) // 2

})();
```

### 不要在块中声明函数

```javascript
(function () {
  "use strict";

  if (true) {
    function f1() {}
  }

})();
```
