# Math对象

数学对象，用于数学运算

## 静态属性

* `Math.PI`: `π`, 约为 3.14159
* `Math.SQRT2`: `根号2`, 约为 1.414
* `Math.SQRT1/2`: `根号1/2`, 约为 0.707
* `Math.E`: `常量e`, 约为 2.718
* `Math.LN2`: `ln2`, 约为0.693
* `Math.LN10`: `ln10`, 约为 2.303
* `Math.LOG2E`: `log2(e)`, 约为 1.443
* `Math.LOG10E`: `log10(e)`, 约为 0.434

## 静态方法

* 参数自动转换为`Number`类型
* `NaN`经过运算后返回`NaN`

### 最值方法

#### Math.min()

```
语法：Math.min([...args])
解释：返回一组数值中的最小值
参数：args, 数值，自动转换为Number类型，不传入返回Infinity
```

description

```javascript
Math.min = function () {
  var args = Array.prototype.slice.call(arguments);
  var result = Infinity;

  for (var i = 0; i < arr.length; i++) {
    if (isNaN(arr[i])) {
      return NaN;
    }

    if (arr[i] < result) {
      result = arr[i];
    }
  }

  return result;
}
```

应用

```javascript
// 设定最小边界
var x = Math.min(y, boundary);
```

#### Math.max()

```
语法：Math.max([...args])
解释：返回一组数值中的最大值
参数：args, 数值，自动转换为Number类型，不传入返回-Infinity
```

description

```javascript
Math.max = function () {
  var args = Array.prototype.slice.call(arguments);
  var result = -Infinity;

  for (var i = 0; i < arr.length; i++) {
    if (isNaN(arr[i])) {
      return NaN;
    }

    if (arr[i] > result) {
      result = arr[i];
    }
  }

  return result;
}
```

应用

```javascript
// 设定最大边界
var x = Math.max(y, boundary);
```

### 舍入方法

#### Math.floor()

```
语法：Math.floor(value)
解释：返回数值向下舍入的最接近的整数
```

#### Math.ceil()

```
语法：Math.ceil(value)
解释：返回数值向上舍入的最接近的整数
```

#### Math.round()

```
语法：Math.round(value)
解释：返回数值四舍五入后的整数
     小数部分为.5，向上舍入
     小数部分不为.5，四舍五入
```

### 随机方法

#### Math.random()

```
语法：Math.random()
解释：返回[0,1)之间的随机数
```

应用

```javascript
// 两数之间的随机整数
function getRandom(min, max) {
  min = Math.ceil(min);
  max = Math.floor(max);

  return Math.floor(Math.random() * (max - min + 1) + min);
}
```

### 运算方法

#### Math.abs()

```
语法：Math.abs(x)
解释：返回x的绝对值
```

#### Math.pow()

```
语法：Math.pow(x,y)
解释：返回x的y次幂
```

#### Math.sqrt()

```
语法：Math.sqrt(x)
解释：x>=0, 返回x的平方根
     x<0，返回NaN
```

#### Math.exp()

```
语法：Math.exp(x)
解释：返回e的x次幂
```

#### Math.log()

```
语法：Math.log(x)
解释：x>=0, 返回lnx
     x<0，返回NaN
```

应用

```javascript
// logx(y)
var num = Math.log(y) / Math.log(x);
```

#### Math.sin()

```
语法：Math.sin(x)
解释：返回sin(x)
```

#### Math.cos()

```
语法：Math.cos(x)
解释：返回cos(x)
```

#### Math.tan()

```
语法：Math.tan(x)
解释：返回tan(x)
```

#### Math.asin()

```
语法：Math.asin(x)
解释：-1<=x<=1, 返回arcsin(x)
     其他，返回NaN
```

#### Math.acos()

```
语法：Math.acos(x)
解释：-1<=x<=1, 返回arccos(x)
     其他，返回NaN
```

#### Math.atan()

```
语法：Math.atan(x)
解释：返回arctan(x)
```

#### Math.atan2()

```
语法：Math.atan(y,x)
解释：返回arctan(y/x)
```