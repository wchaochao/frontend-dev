# 语法

## selector

选择器，需要设置样式的某个或某类`HTML`元素

## declaration

声明，要设置的样式，由属性和属性值组成, 以`;`结束

## rule

规则，对某个或某类`HTML`元素设置样式，由选择器和声明块组成

```css
selector {
  property1:value1;
  ...
}
```

![rule](images/rule.png)

## sheet

样式表，规则的集合

```css
selector1 {
  property1:value1;
  ...
}

selector2 {
  property1:value1;
  ...
}
```

## media

媒体类型，在某种媒体上应用样式, 默认为`all`

* `all`: 所有媒体设备
* `screen`: 显示器
* `print`: 打印机

限制

* `min-device-width`: 屏幕最小宽度
* `max-device-width`: 屏幕最大宽度
* `min-width`: 浏览器最小宽度
* `max-width`: 浏览器最大宽度

```css
@media screen{
  selector1 {
    property1:value1;
    ...
  }

  selector2 {
    property1:value1;
    ...
  }
}

@media print{
  selector1 {
    property1:value1;
    ...
  }

  selector2 {
    property1:value1;
    ...
  }
}

@media screen and (min-width:768px) and (max-width:992px){
  selector1 {
    property1:value1;
    ...
  }

  selector2 {
    property1:value1;
    ...
  }
}

```