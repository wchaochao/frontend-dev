# 兼容性

* 不同浏览器对样式的支持不同，可到[Can I Use](http://caniuse.com/#)上查看浏览器的支持性
* 不同浏览器对样式的实现不同，可能会造成bug
* 不同显示屏的分辨率不同，页面显示会有差别

## IE的bug

IE6及以下使用布局概念来控制元素的尺寸和定位，是许多bug的根源

* `width`相当于`min-width`, `height`相当于`min-height`
* 布局元素的外边距不叠加
* 布局元素对浮动进行自动清理
* 相对定位元素没有布局时绝对定位元素无法定位
* 没有布局的块级链接上，单击区域只覆盖文本
* 滚动时，列表项上的背景图片间歇性显示和消失

### 常见bug及修复

IE9以下不支持`opacity`

```css
selector{
  opacity:0.8;
  filter:alpha(opacity=80);
}
```

IE6的宽高指的是`border-box`

```css
selector{
  box-sizing:border-box;
}
```

IE6不支持`PNG`透明度

```css
selector{
  filter:progid:DXImageTransform.Microsoft.AlphaImageLoader(src="image/test.png", sizingMethod="crop");
  background:none;
}

/* or */
selector{
  behavior:url(iepngfix.utc);
}
```

IE6列表项上下添加了额外的空间

```css
selector{
  display:inline;
}
```

IE6不显示内容隐藏在屏幕之外的链接

```
selector{
  background-image:url("img/shim.gif"); /*一个透明的图片*/
}
```

IE6不支持`margin:0 auto`

```css
parent{
  text-align:center;
}

child{
  margin:0 auto;
  text-align:left;
}
```

IE6的浮动元素的外边距加倍

```css
selector{
  float:left;
  margin-left:20px;
  display:inline;
}
```

IE6的浮动元素间有超过两个注释时，最后一个浮动元素的最后几个字符会重复出现

## 解决方法

### IE条件注释

根据条件显示代码块

```html
<!--[if IE]>只有IE才能看到<![endif]-->
<!--[if IE 6]>只有IE6才能看到<![endif]-->
<!--[if lt IE7]>只有比IE7更低(lower than，不包括IE7)的IE才能看到<![endif]-->
<!--[if gte IE7]>只有大于等于IE7 (greater than or equal to)的IE才能看到<![endif]-->
<!--[if (gte IE6)&(lt IE 8)]>只有大于等于IE6，且小于IE8的IE能看到<![endif]-->
<!--[if (IE 7)|(IE6)]>只有IE6和IE7能看到<![endif]-->
```