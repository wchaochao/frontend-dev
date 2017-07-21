# HTML

描述网页的结构

## 目录

## 推荐资料

* [w3school-html教程](http://www.w3school.com.cn/web/web_html.asp)
* [codecademy-html-css](https://www.codecademy.com/learn/learn-html-css)
* 《Head First HTML and CSS》

# 概述

超文本标记语言(`Hyper Text Markup Language`), 描述网页的一种语言

> 超：可通过链接相互跳转
> 文本：文本格式
> 标记：使用标签
> 语言：解释型语言

## 运行

### 本地

1. 打开文本编辑器，新建文件，进行编辑
2. 保存为html格式，并用浏览器打开

### 在线

使用[codepen](https://codepen.io)等在线工具实现在线编辑和实时预览

### 服务器

1. 将本地代码发布到服务器上
2. 打开相应的网站浏览网页


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

* 块元素：默认`width`为100%
* 内联元素：默认`width`不为100%

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

通用属性

* `id`: 元素的唯一`id`
* `class`: 元素的类名
* `style`: 元素的行内样式
* `title`: 元素的提示信息(移到元素上时显示)
* `name`: 元素的名称

# XHTML

可扩展的超文本标记语言，更严格的`HTML`版本

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

在浏览器上显示的HTML文档

## 编码

HTML头部编码，HTML文件编码要一致，一般使用`UTF-8`

## 兼容性

不同浏览器显示网页时可能会有些细微的差别

主流浏览器：IE, Chrome, Firefox, Opera, Safari

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


# 结构

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Document</title>
</head>
<body>

</body>
</html>
```

## 注释

```html
<!--注释-->
```

## DOCYTYPE

文档类型声明，指定html版本

### HTML5

```html
<!DOCTYPE html>
```

### HTML 4.01 Strict

不包括展示性的和弃用的元素，不允许框架集

```html
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
```

### HTML 4.01 Transitional

包括展示性的和弃用的元素，不允许框架集

```html
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
```

### HTML 4.01 Frameset

包括展示性的和弃用的元素，允许框架集

```html
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Frameset//EN" "http://www.w3.org/TR/html4/frameset.dtd">
```

### XHTML 1.0 Strict

不包括展示性的和弃用的元素，不允许框架集，以格式正确的`XML`来编写标记

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
```

### XHTML 1.0 Transitional

包括展示性的和弃用的元素，不允许框架集，以格式正确的`XML`来编写标记

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
```

### XHTML 1.0 Frameset

包括展示性的和弃用的元素，允许框架集，以格式正确的`XML`来编写标记

## html

文档的根元素，指定文档为`HTML`

* `xmlns`: 指定文档的命名空间，默认`http://www.w3.org/1999/xhtml`

## head

文档头部，描述文档的信息

### title

页面标题

```html
<title>页面标题</title>
```

### meta

指定页面的描述、关键词、作者、最后修改时间以及其他元数据

```html
<meta name="author" content="Lxxyx,841380530@qq.com">
<meta name="description" content="Free Web tutorials on HTML, CSS, XML" />
<meta name="keywords" content="HTML, CSS, XML" />
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="robots" content="none">
<meta name="generator" content="Sublime Text3">
<meta http-equiv="content-Type" content="text/html;charset=utf-8">  <!--旧的HTML，不推荐-->
<meta charset="utf-8"> <!--HTML5设定网页字符集的方式，推荐使用UTF-8-->
<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1"/>
<meta http-equiv="cache-control" content="no-cache">
<meta http-equiv="expires" content="31 Dec 2008">
<meta http-equiv="refresh" content="2;URL=http://www.lxxyx.win/">
<meta http-equiv="Set-Cookie" content="User=Lxxyx; path=/; expires=Sunday, 10-Jan-16 10:00:00 GMT">
```

属性

* `content`: 定义与`http-equiv`或`name`属性相关的元信息
* `name`: 把`content`属性关联到一个名称
  * `author`: 作者
  * `description`: 描述
  * `keywords`: 关键字
  * `viewport`: 窗口
  * `robots`: 搜索引擎爬虫的索引方式
  * `generator`: 网页制作软件
* `http-equiv`: 把`content`属性关联到`HTTP`头部
  * `content-Type`: 内容类型
  * `X-UA-Compatible`: 采取何种版本渲染当前页面
  * `cache-control`: 缓存方式
  * `expires`: 网页到期时间
  * `refresh`: 自动刷新并指向某页面
  * `Set-Cookie`: cookie设定

### base

页面链接的相对地址和默认目标

```html
<base href="http://www.w3school.com.cn/images/" />
<base target="_blank" />
```

### link

外部资源

```html
<link rel="stylesheet" type="text/css" href="mystyle.css" />
<link rel="icon" type="image/x-icon" href="favicon.ico">
```

属性

* `rel`: 当前文档与外部资源的关系
  * `stylesheet`: 样式表
  * `icon`: 图标
* `type`: 外部资源的`MIME`类型
* `href`: 外部资源的地址

### style

页面样式

```html
<style type="text/css">
  body {background-color:yellow}
  p {color:blue}
</style>
```

属性

* `type`: 样式表的MIME类型，默认`text/css`

## body

文档主体，包含文档的所有内容

### 常见内容

* 文本
* 超链接
* 图片
* 列表
* 表格
* 表单


# 文本标签

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

## 样式

```html
<b>粗体</b>
<i>斜体</i>
<big>大号字</big>
<small>小号字</small>
<ins>插入</ins>
<del>删除</del>
<sup>上标</sup>
<sub>下标</sub>
```

## 短语

```html
<em>强调</em>
<strong>重要</strong>
<dfn>术语</dfn>
<code>计算机代码文本</code>
<kbd>键盘文本</kbd>
<samp>计算机输出文本</samp>
<var>变量</var>
<cite>作品标题</cite>
<abbr title="缩写">缩写</abbr>
<address>联系信息</address>
<dbo dir="rtl">文字方向</dbo>
<pre>预格式化文本</pre>
```

## 引用

```html
<blockquote cite="url">块引用</blockquote>
<q>内联引用</q>
```

## 架构

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
  * `#`: 跳转到页面顶部
  * `javascript:void(0);`: 不跳转
* `target`: 链接文档在何处显示，默认本页面显示
  * `_self`: 本页面显示
  * `_blank`: 新页面显示
  * `_<frame>`: 指定框架显示
  * `_parent`: 父框架显示
  * `_top`: 顶层框架显示

## 锚点

```html
<a name="tip">锚点</a>
<a href="#tip">跳转到锚点或`id="tip"`的地方</a>
```

# 图片标签

## 格式

* `BMP`: 无损的、既支持索引色又支持直接色的点阵图，文件较大
* `GIF`: 无损的、采用索引色的点阵图，文件小，支持动画和透明，只存在256种颜色
* `JPEG`: 有损的、采用直接色的点阵图，色彩丰富，适合存储照片
* `PNG-8`: 无损的、采用索引色的点阵图，GIF格式的替代者，动画效果较差
* `PNG-24`: 无损的、采用直接色的点阵图，支持透明，文件比`JPEG`大
* `SVG`: 无损矢量图，适合Logo、Icon

## 图片

```html
<img src="url" alt="图片加载失败时显示的文字">
```

属性

* `src`: 图片地址
* `alt`: 替换文本
* `width`: 图片宽
* `height`: 图片高
* `usemap`: 图片映射

## 图片映射

```html
<img src="url" alt="替换文字" usemap="#map">

<map name="map" id="map">
  <area shape="形状" coords="坐标" href="url" alt="替换文字">
</map>
```

area属性

* `shape`: 区域形状
  * `rect`: 四边形
  * `circ`: 圆
  * `poly`: 多边形
* `coords`: 区域坐标
* `href`: 链接地址
* `target`: 链接目标
* `alt`: 替换文本


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
  * `1`: 数字
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
  * `width`: 宽度
  * `border`: 边框
  * `cellpadding`: 单元格内间距
  * `cellspacing`: 单元格外间距
* `caption`: 表格标题
* `thead`: 表头
* `tbody`: 表格主体，可多个
* `tfoot`: 表注
* `tr`: 行
* `td/th`: 单元格/表头单元格
  * `colspan`: 跨列
  * `rowspan`: 跨行


# 表单


## form

```html
<form action="form_action.asp" method="get">
  <p>First name: <input type="text" name="fname" /></p>
  <p>Last name: <input type="text" name="lname" /></p>
  <input type="submit" value="Submit" />
</form>
```

属性

* `name`: 表单名称
* `action`: 表单提交到哪
* `method`: 表单提交的HTTP方法，默认`GET`
* `target`: 表单提交的目标，默认`_self`
* `accept-charset`: 表单数据的编码方式，默认页面编码
* `enctype`: 表单数据的类型，默认`application/x-www-form-urlencoded`
* `novalidate`: 禁止默认验证

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

属性

* `name`: 名称

## label

```html
<label for="male">Male</label>
<input type="radio" name="sex" id="male" />
```

属性

* `for`: 将`label`绑定到哪个表单元素

## input

属性

* `type`: 类型
* `name`: 名称
* `value`: 初始值
* `autofocus`: 自动获取焦点
* `placeholder`: 输入提示
* `readonly`: 只读
* `disabled`: 禁用
* `checked`: 选中
* `required`: 必填
* `min`: 最小值
* `max`: 最大值
* `maxlength`: 允许输入的最大长度
* `minlength`: 允许输入的最小长度

### 输入框

```html
<input type="text" name="text" />
```

### 密码框

```html
<input type="password" name="password" />
```

### 单选框

```html
<input type="radio" name="sex" value="male" checked>Male
<br>
<input type="radio" name="sex" value="female">Female
```

### 复选框

```html
<input type="checkbox" name="vehicle" value="Bike" checked>I have a bike
<br>
<input type="checkbox" name="vehicle" value="Car">I have a car
```

### 文件

```html
<input type="file" name="file">
```

### 隐藏

```html
<input type="hidden" name="hidden">
```

## select

```html
<select name="cars">
  <option value="volvo">Volvo</option>
  <option value="saab" selected>Saab</option>
  <option value="fiat">Fiat</option>
  <option value="audi">Audi</option>
</select>
```

select属性

* `name`: 名称
* `autofocus`: 自动获取焦点
* `disabled`: 禁用
* `required`: 必选
* `multiple`: 多选
* `size`: 可见的选项数目

option属性

* `value`: 选项值
* `selected`: 选中

## textarea

```html
<textarea name="message" rows="10" cols="30">
The cat was playing in the garden.
</textarea>
```

属性

* `name`: 名称
* `autofocus`: 自动获取焦点
* `placeholder`: 输入提示
* `readonly`: 只读
* `disabled`: 禁用
* `required`: 必填
* `maxlength`: 最大字符数
* `rows`: 可见行
* `cols`: 可见列

## button

```html
<button type="button">普通按钮</button>
<button type="submit">提交按钮</button>
<button type="reset">重置按钮</button>
```

属性

* `type`: 按钮类型，默认普通按钮
  * `button`: 普通按钮
  * `submit`: 提交按钮
  * `reset`: 重置按钮
* `disabled`: 禁用


# 脚本

可放置在`head`和`body`中

```html
<script type="text/javascript">
  console.log('javascript');
</script>

<script src="myscript"></script>

<noscript>不支持脚本时显示</noscript>
```

* `type`: 脚本的`MIME`类型, 默认`text/javascript`
* `src`: 脚本地址


# 框架

## 框架集

```html
<frameset rows="50%,50%">
  <noframes>不支持框架</noframes>

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

* `name`: 名称
* `src`: 文档地址
* `frameborder`: 边框
* `noresize`: 禁止调整大小
* `scrolling`: 是否显示滚动条

## 内联框架

```html
<iframe src="URL"></iframe>
```

属性

* `name`: 框架名字
* `src`: 文档地址
* `frameborder`: 边框
* `width`: 宽度
* `height`: 高度
* `scrolling`: 是否显示滚动条
