# 常用样式

## 链接

* `a:link`: 未访问的链接
* `a:visited`: 访问了的链接
* `a:focus`: 获取焦点的链接，得放在`a:link`, `a:visited`后面
* `a:hover`: 鼠标移上去的链接，得放在`a:focus`后面
* `a:active`: 点中的链接，得放在`a:hover`后面
* `a[href^="http:"]:not([href^="http://yoursite"])`: 外部链接样式
* `a[href^="mailto"]`: 邮箱链接样式
* `a[href$=".doc"]`: 下载`doc`文件的链接样式

## 列表

### 垂直导航条

```html
<ul class="nav">
  <li><a href="home.html">Home</a></li>
  <li><a href="product.html">Product</a></li>
  <li><a href="news.html">News</a></li>
  <li><a href="about.html">About</a></li>
</ul>
```

```css
/* 关键点
a: display:block
*/
```

### 水平导航条

```html
<ul class="nav">
  <li><a href="home.html">Home</a></li>
  <li><a href="product.html">Product</a></li>
  <li><a href="news.html">News</a></li>
  <li><a href="about.html">About</a></li>
</ul>
```

```css
/* 关键点
ul: 去浮动
li: float:left;
a: display:block;
*/
```

### 下拉菜单

```html
<ul class="nav">
  <li><a href="home.html">Home</a></li>
  <li>
    <a href="product.html">Product</a>
    <ul>
      <li><a href="product/disk">Disk</a></li>
      <li><a href="product/ip">Ip</a></li>
    </ul>
  </li>
  <li><a href="news.html">News</a></li>
  <li><a href="about.html">About</a></li>
</ul>

```

```css
/* 关键点
.nav: 去浮动
.nav>li: float:left
.nav a: display:block
.nav ul: position:absolute;display:none;
.nav>li:hover>ul: display:block;
*/
```

## 表单

通常采用表格布局

```html
<form class="display-table">
  <div class="display-table-row">
    <p class="display-table-cell">lable</p>
    <p class="display-table-cell">control</p>
  </div>
</form>
```

## 布局

### 固定宽度布局

尺寸采用固定宽度

```css
.container{
  width:920px;
  margin:0 auto;
}
```

### 流式布局

尺寸采用百分数

```css
.container{
  width:80%;
  margin:0 auto;
  max-width:125em;
  min-width:62em;
}
```

### 弹性布局

尺寸采用字号

```css
.container{
  width:92em;
  max-width:95%;
  margin:0 auto;
}
```

## 居中

### 水平居中

行内元素

```css
.text-center{
  text-align:center;
}
```

定宽块元素

```css
.container{
  width:1000px;
  margin-left:auto;
  margin-right:auto;
}
```

不定宽块元素

```css
.center{
  position:absolute;
  left:50%;
  transform:translateX(-50%);
}
```

## 垂直居中

一行文本

```css
.middle{
  height:30px;
  line-height;30px;
}
```

内联元素

```css
.middle{
  padding:20px 0;
}
```

定高块元素

```css
.middle{
  position:absolute;
  top:50%;
  height:200px;
  margin-top:-100px;
}
```

不定高块元素

```css
.middle{
  position:absolute;
  top:50%;
  transform:translateY(-50%);
}
```