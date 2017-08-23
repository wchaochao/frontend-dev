# 概述

层叠样式表(`Cascading Style Sheets`)

> * 继承：子元素会继承祖先元素的一些样式，如字体样式、文本样式、不透明度
> * 层叠：同一元素可设置多种样式，按优先级确定应用哪一样式

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