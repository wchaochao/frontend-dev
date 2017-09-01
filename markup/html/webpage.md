# 网页

在浏览器上显示的`HTML`文档

## 编码

`<meta>`中的编码要和文件编码、浏览器编码一致，推荐使用`UTF-8`

## 兼容性

主流浏览器：`IE`, `Chrome`, `Firefox`, `Opera`, `Safari`

* 不同浏览器对`HTML`元素的支持不同，可到[Can I Use](http://caniuse.com/#)上查看浏览器的支持性
* 不同浏览器的默认样式不同，可通过设置`CSS`统一样式


## 空格

`html`中大部分连续的空格或空行都会被算作一个空格显示

## 转义

`html`文档中的某些字符在网页中显示时会被转义，如：

```
&amp; -> &
&nbsp; -> 空格
&lt; -> <
&gt; -> >
&quot; -> "
&cent; -> ￠
&pound; -> £
&yen; -> ¥
&euro; -> €
&sect; -> §
&copy; -> ©
&reg; -> ®
&trade; -> ™
&times; -> ×
&divide; -> ÷
```