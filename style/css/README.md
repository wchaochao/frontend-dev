# CSS

定义如何显示`HTML`元素

## 目录

## 推荐资料

* [w3school-css](http://www.w3school.com.cn/css/index.asp)


# 概述

层叠样式表(`Cascading Style Sheets`)

> * 层叠：同一元素可设置多种样式，按优先级确定应用哪一样式
> * 继承：子元素会继承祖先元素的样式

## 插入

### 外部样式表

某个页面的样式

```html
<head>
  <link rel="stylesheet" href="css/site.css">
</head>
```

### 内部样式表

当前页面的样式

```html
<head>
  <style type="text/css">
    body {background-color:yellow}
    p {color:blue}
  </style>
</head>
```

### 内联样式

当前元素的样式

```html
<div style="background:#f8f8f8;"></div>
```

# 概念

## selector

选择器，需要设置样式的`HTML`元素

## declaration

声明，要设置的样式，由属性和属性值组成

## rule

规则，对某个或某类`HTML`元素设置样式，由选择器和声明组成

```CSS
selector {
  property1:value1;
  ...
}
```

## sheet

样式表，规则的集合

```CSS
selector1 {
  property1:value1;
  ...
}

selector2 {
  property1:value1;
  ...
}
```


# 选择器

## 通配符选择器

* `*`: 所有元素

## 元素选择器

* `tag`: 某类元素

## id选择器

* `#id`: 拥有指定`id`的元素
* `selector#id`: 拥有指定`id`的某个选择器

## 类选择器

* `.class`: 拥有指定类的元素
* `selector.class`: 拥有指定类的某个选择器

## 属性选择器

* `[attribute]`: 拥有指定属性的元素
* `[attribute=value]`: 指定属性的属性值为指定值的元素
* `[attribute~=value]`: 指定属性的属性值包含指定词汇的元素
* `[attribute|=value]`: 指定属性的属性值以指定值或指定值-开头的元素
* `[attribute^=value]`: 指定属性的属性值以指定值开头的元素
* `[attribute$=value]`: 指定属性的属性值以指定值结尾的元素
* `[attribute*=value]`: 指定属性的属性值包含指定值的元素
* `selector[attribute]`: 拥有指定属性的某个选择器

## 分组选择器

* `selector1,selector2...`: 多个选择器应用同一套规则

## 后代选择器

* `ancestorSelector selector`: 某个选择器的后代选择器

## 子代选择器

* `parentSelector>selector`: 某个选择器的子代选择器

## 相邻兄弟选择器

* `siblingSelector~selector`: 某个选择器的下一个兄弟选择器

## 伪类选择器

添加特殊效果

* `:link`: 未访问的链接
* `:visited`: 已访问的链接
* `:hover`: 鼠标悬停
* `:focus`: 获取焦点
* `:active`: 激活
* `:first-child`: 作为第一个子元素
* `:lang(value)`: `lang`属性为指定值

## 伪元素

元素的某一部分

* `:first-letter`: 首字母
* `:first-line`: 首行
* `:before`: 前面
* `:after`: 后面

# 优先级

## 样式表优先级

越晚应用优先级越高

浏览器缺省设置<外部样式表<内部样式表<内联样式

## 选择器优先级

描述的越精确优先级越高

普通选择器：所有元素选择器<元素选择器<类选择器<`id`选择器
其他选择器：计算`id`选择器、类选择器、元素选择器的个数，并依次比较

## 样式优先级

普通样式<`!important`样式


# 样式

## 颜色

`CSS`用以下方式表示颜色

* 十六进制颜色：`#RRGGBB`, RR（红色）、GG（绿色）、BB（蓝色）, 值`00~FF`之间
* RGB颜色: `rgb(red, green, blue)`，值`0~256`或`0% ~100%`之间
* RGBA颜色:`rgba(red, green, blue, alpha)`, `alpha`为不透明度，值`0~1`之间

## 背景

* `background-color:<color>`: 背景颜色，默认为`transparent`
* `background-image:url("<url>")`: 背景图片，默认为`none`
