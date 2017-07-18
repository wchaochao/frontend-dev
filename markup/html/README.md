# HTML

定义网页的内容和结构

## 目录

## 推荐资料

* [w3school-html教程](http://www.w3school.com.cn/web/web_html.asp)


# 概述

超文本标记语言(Hyper Text Markup Language), 描述网页的一种语言

> 超：可通过链接相互跳转
> 文本：文本格式
> 标记：使用标记标签
> 语言：解释型语言


# 概念

## 标签

* 单标签：`<tag/>`
* 双标签：`<tag></tag>`

## 元素

开始标签到结束标签的所有代码

```html
<tag>...</tag>
<tag/>
```

* 块元素：默认width为100%
* 内联元素：默认width不为100%

## 嵌套

元素里嵌套着另一个元素

```html
<tag1>
  <tag2>...</tag2>
</tag1>
```

## 属性

为元素提供附加的信息

```html
<tag key="value">...</tag>
<tag key="value"/>
```

## 通用属性

* `id`: 元素的唯一id
* `class`: 元素的类名
* `style`: 元素的行内样式
* `title`: 元素的title信息(移到元素上时显示)
* `name`: 元素的名字

# XHTML

可扩展的超文本标记语言，更严格的HTML版本

## 文档结构

```html
<!doctype html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
  <title>Document</title>
</head>
<body>

</body>
</html>
```

## 元素语法

* 必须正确嵌套
* 必须始终关闭
* 必须小写
* 文档必须有一个根元素

## 属性语法

* 属性必须使用小写
* 属性值必须用引号包围
* 禁止属性简写


# 网页

在浏览器中显示的html文档

1. 打开文本编辑器，编辑html文件
2. 保存为html格式，并用浏览器打开

## 编码

网页编码、html文档编码、浏览器编码要一致，一般使用`UTF-8`

## 空格

html文档中所有连续的空格或空行都会被算作一个空格显示

## 转义

html文档中的以下字符在网页中显示时会被转义

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


# HTML文档

```html
<!doctype html> <!--文档类型声明-->
<html xmlns="http://www.w3.org/1999/xhtml"> <!--网页-->
<head> <!--网页头部-->
  <meta charset="UTF-8">
  <title>Document</title>
</head>
<body> <!--网页内容-->

</body>
</html>
```

## 文档类型声明

HTML5

```html
<!DOCTYPE html>
```

HTML 4.01

```html
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
"http://www.w3.org/TR/html4/loose.dtd">
```

HTML 1.0

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
```

## 头部

```

```

### meta

规定页面的描述、关键词、文档的作者、最后修改时间以及其他元数据

```html
<meta charset="utf-8"/>
<meta name="description" content="Free Web tutorials on HTML, CSS, XML" />
<meta name="keywords" content="HTML, CSS, XML" />
```

### title

网页标题

```html
<title>网页标题</title>
```

### base

网页链接的默认地址和默认目标

```html
<base href="http://www.w3school.com.cn/images/" />
<base target="_blank" />
```

### link

外部资源

```html
<link rel="stylesheet" type="text/css" href="mystyle.css" />
```

### script

脚步文件

```html
<script src="myscript"></script>
```

### style

网页样式

```html
<style type="text/css">
  body {background-color:yellow}
  p {color:blue}
</style>
```


# 文本标签

## 注释

```html
<!--注释-->
```

## 标题

```html
<h1>标题1</h1>
<h2>标题2</h2>
<h3>标题3</h3>
<h4>标题4</h4>
<h5>标题5</h5>
<h5>标题5</h5>
```

## 分隔线

```html
<hr/>
```

## 段落

```html
<p>段落</p>
```

## 换行

```html
<p>行1<br/>行2</p>
```

## 文本格式化

```html
<b>粗体</b>
<i>斜体</i>
<em>着重文字</em>
<strong>加重语气</strong>
<big>大号字</big>
<small>小号字</small>
<sup>上标</sup>
<sub>下标</sub>
<ins>插入</ins>
<del>删除</del>
```

## 计算机输出

```html
<code>计算机代码</code>
<kbd>键盘码</kbd>
<samp>计算机输出示例</samp>
<var>数学变量</var>
<pre>预格式化文本</pre>
```

## 引用

```html
<abbr title="缩写">缩写</abbr>
<address>联系信息</address>
<dbo dir="rtl">文字方向</dbo>
<blockquote cite="url">长引用</blockquote>
<q>短引用</q>
<cite>著作标题</cite>
<dfn>定义</dfn>
```

## 分组

```html
<div>普通块元素</div>
<span>普通内联元素</span>
```


# 链接标签

## 链接

```html
<a href="url">链接</a>
```

属性

* `href`: 链接的地址
  * `<protocol>://<user>:<password>@<host>:<port>/<path>?<query>#<hash>`: 链接到某个地址的某个锚点
  * `mailto:<email>`: 发送邮件
  * `""`: 跳转到页面顶部
  * `javascript:void(0);`: 不跳转
* `target`: 链接文档在何处显示，默认本页面显示
  * `_self`: 本页面显示
  * `_blank`: 新页面显示
  * `_<frame>`: 指定框架显示

## 锚点

```html
<a name="tip">锚点</a>
<a href="#tip">跳转到锚点</a>
```

## 图片标签

```html
<img src="url" alt="图片加载失败时显示的文字">
```

属性

* width: 图片宽
* height: 图片高
* usemap: 使用某个图像地图

## 图片地图

```html
<img src="url" alt="替换文字" usemap="#map">

<map name="map">
  <area shape="形状" coords="顶点坐标" href="url" alt="替换文字">
</map>
```


# 列表

## 无序列表

```html
<ul>
  <li>Coffee</li>
  <li>Milk</li>
</ul>
```

ul属性

* `type`: 列表符号，默认为实心圆
  * `disc`: 实心圆
  * `circle`: 空心圆
  * `square`: 实心方块

## 有序列表

```html
<ol>
  <li>Coffee</li>
  <li>Milk</li>
</ol>
```

ol属性

* `type`: 列表符号，默认为数字
  * `1`: 阿拉伯数字
  * `A`: 大写字母
  * `a`: 小写字母
  * `I`: 大写罗马字母
  * `i`: 小写罗马字母

## 自定义列表

```html
<dl>
  <dt>Coffee</dt>
  <dd>Black hot drink</dd>
  <dt>Milk</dt>
  <dd>White cold drink</dd>
</dl>
```

## 嵌套列表

```html
<li>咖啡</li>
<li>茶
  <ul>
    <li>红茶</li>
    <li>绿茶</li>
  </ul>
</li>
<li>牛奶</li>
```

## 表格标签

```html
<table>
  <caption>表格标题</caption>
  <thead>
    <tr>
      <th>列1</th>
      <th>列2</th>
      <th>列3</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>单元格1</td>
      <td>单元格2</td>
      <td>单元格3</td>
    </tr>

    <tr>
      <td>单元格4</td>
      <td>单元格5</td>
      <td>单元格6</td>
    </tr>
  </tbody>

  <tfoot>
    <tr>
      <th>列1</th>
      <th>列2</th>
      <th>列3</th>
    </tr>
  </tfoot>
</table>
```

* `table`: 表格
  * `border`: 边框
  * `cellpadding`: 单元格边距
  * `cellspacing`: 单元格间距
* `caption`: 表格标题，可省略
* `thead`: 表头，可省略
* `tbody`: 表格内容，可省略
* `tfoot`: 表尾，可省略
* `tr`: 行
* `td/th`: 单元格/加粗的单元格
  * `colspan`: 跨列
  * `rowspan`: 跨行


# 表单

```html
```

## form

属性

* `action`: 提交数据到哪
* `method`: 提交的HTTP方法，默认`GET`
* `target`: action的目标，默认`_self`
* `accept-charset`: 表单使用的字符集，默认页面字符集

## fieldset

分组

```html
<fieldset>
  <legend>Personal information:</legend>
  First name:<br>
  <input type="text" name="firstname" value="Mickey">
  <br> Last name:<br>
  <input type="text" name="lastname" value="Mouse">
  <br><br>
  <input type="submit" value="Submit">
</fieldset>
```

## 输入框

```
<input type="text" name="text" />
```

属性

* name: 名称

## 密码框

```
<input type="password" name="password" />
```

属性

* name: 名称

## 单选按钮

```
<input type="radio" name="sex" value="male" checked>Male
<br>
<input type="radio" name="sex" value="female">Female
```

属性

* name: 名称
* value: 值
* checked: 选中

## 



# 脚本

```html
<script type="text/javascript">
  console.log('javascript');
</script>

<noscript>不支持脚本时显示</noscript>
```

# 框架

## 框架划分

```html
<frameset rows="50%,50%">
  <frame src="/example/html/frame_a.html" noresize="noresize">

  <frameset cols="25%,75%">
    <frame src="/example/html/frame_b.html">
    <frame src="/example/html/frame_c.html">
  </frameset>
</frameset>
```

frameset属性

* `rows`: 按行分
* `cols`: 按列分

frame属性

* `noresize`: 不能调整大小

## 内联框架

```html
<iframe src="URL"></iframe>
```

属性

* `width`: 宽度
* `height`: 高度
* `frameborder`: 边框
* `name`: 框架名字