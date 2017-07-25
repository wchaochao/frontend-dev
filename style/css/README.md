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

# 语法

## selector

选择器，需要设置样式的某个或某类`HTML`元素

## declaration

声明，要设置的样式，由属性和属性值组成

## rule

规则，对某个或某类`HTML`元素设置样式，由选择器和声明组成

```css
selector {
  property1:value1;
  ...
}
```

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

媒介类型，在某种媒介上应用样式, 默认为`all`

* `all`: 所有媒介设备
* `screen`: 显示器
* `print`: 打印机

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

## 兄弟选择器

* `prevSelector+selector`: 某个选择器后面的所有兄弟选择器

## 相邻兄弟选择器

* `prevSelector~selector`: 某个选择器的下一个兄弟选择器

## 伪类选择器

### 效果伪类

* `:link`: 未访问的链接
* `:visited`: 已访问的链接
* `:hover`: 鼠标悬停
* `:focus`: 获取焦点
* `:active`: 点中的链接
* `:target`: 跳转到的锚点
* `:enabled`: 启用
* `:disabled`: 禁用
* `:checked`: 选中

### 角色伪类

* `:first-child`: 作为第一个子元素
* `:last-child`: 作为最后一个子元素
* `:only-child`: 作为唯一一个子元素
* `:nth-child(n)`: 作为第n个子元素
* `:nth-last-child(n)`: 作为倒数第n个子元素
* `:first-of-type`: 在子元素中第一个出现的某类元素
* `:last-of-type`: 在子元素中最后一个出现的某类元素
* `:only-of-type`: 在子元素中唯一出现的某类元素
* `:nth-of-type(n)`: 在子元素中第n个出现的某类元素
* `:nth-last-of-type`: 在子元素中倒数第n个出现的某类元素
* `:empty`: 没有子元素
* `:root`: 作为根元素

### 筛选伪类

* `:lang(value)`: `lang`属性的属性值以指定值开头
* `:not(selector)`: 排除某些选择器


## 伪元素

元素的某一部分

* `:first-letter`: 首字母
* `:first-line`: 首行
* `:before`: 内容之前
* `:after`: 内容之后
* `::selection`: 选中部分

# 优先级

## 样式表优先级

越晚应用优先级越高

浏览器缺省设置<外部样式表<内部样式表<内联样式

## 选择器优先级

描述的越精确优先级越高

* 普通选择器：所有元素选择器<元素选择器<类选择器<`id`选择器
* 其他选择器：计算`id`选择器、类选择器、元素选择器的个数，并依次比较

## 样式优先级

普通样式<`!important`样式


# 样式值

## 字体

### 通用字体系列

拥有相似外观的字体系统组合

* `Serif`
* `Sans-serif`
* `Monospace`
* `Cursive`
* `Fantasy`

### 特定字体系列

具体的字体系列

* `Times`
* `Courier`


## 尺寸

`CSS`用以下方式表示尺寸

* `%`: 百分比
* `px`: 像素
* `em`: 字体尺寸

## 颜色

`CSS`用以下方式表示颜色

* 颜色名：`transparent, aqua, black, blue, fuchsia, gray, green, lime, maroon, navy, olive, orange, purple, red, silver, teal, white, yellow`
* 十六进制颜色：`#RRGGBB`, RR(红色)、GG(绿色)、BB(蓝色), 值`00~FF`之间
* RGB颜色: `rgb(red, green, blue)`，值`0~256`或`0% ~100%`之间
* RGBA颜色: `rgba(red, green, blue, alpha)`, `alpha`为不透明度，值`0~1`之间
* HSL颜色：`hsl(hue, saturation, lightness)`, hue(色调)(0~360)(红-绿-蓝), saturation(饱和度)(0%~100%)(灰-全彩), lightness(亮度)(0%~100%)(黑-白)
* HSLA 颜色: hsla(hue, saturation, lightness, alpha) 


# 文本样式

## 字体

* `font-family`: 文本的字体
  * `字体`: 可定义多个字体作为备用，字体名有空格时需要用引号
* `font-style`: 字体风格，默认为`normal`
  * `normal`: 正常显示
  * `italic`: 斜体显示
  * `oblique`: 倾斜显示
* `font-variant`: 字体变形
  * `normal`: 正常
  * `small-caps`: 小型大写字母
* `font-weight`: 字体加粗，默认为`normal`
  * `normal`: 正常
  * `bold`: 粗体
  * `bolder`: 更粗
  * `lighter`: 更细
  * `<100|200...|900>`: 400相当于`normal`，700相当于'bold'
* `font-size`: 字体大小
  * `length`: 固定尺寸
  * `percentage`: 相对于父字体大小而言
  * `em`: 相对于父字体大小而言

## 文本

* `color`: 文本颜色
* `direction`: 文本方向
  * `ltr`: 从左到右
  * `rtl`: 从右到左
* `line-height`: 行高
* `text-indent`: 缩进，一般设置`2em`
* `text-align`: 水平对齐，默认为`left`
  * `left`: 左对齐
  * `center`: 居中对齐
  * `right`: 右对齐
  * `justify`: 两端对齐
* `vertical-align`: 垂直对齐, 默认为`baseline`
  * `baseline`: 基线对齐
  * `top`: 顶端对齐
  * `middle`: 中间对齐
  * `bottom`: 底端对齐
  * `length`: 允许负数
  * `percentage`: 相对于`line-height`而言
* `text-transform`: 大小写处理，默认为`none`
  * `none`: 不处理
  * `uppercase`: 大写
  * `lowercase`: 小写
  * `capitalize`: 首字母大写
* `text-decoration`: 文本装饰，默认为`none`
  * `none`: 无装饰
  * `underline`: 下划线
  * `overline`: 上划线
  * `line-through`: 删除线
  * `blink`: 闪烁
* `word-spacing`: 字/单词的间隔，默认为`normal`
  * `normal`: 正常间隔
  * `尺寸`：间隔多少
* `letter-spacing`: 字符的间隔，默认为`normal`
  * `normal`: 正常间隔
  * `尺寸`：间隔多少
* `white-space`: 空白符处理，默认为`normal`
  * `normal`: 合并空白符，忽略换行符，允许自动换行
  * `nowrap`: 合并空白符，忽略换行符，不允许自动换行
  * `pre`: 保留空白符，保留换行符，不允许自动换行
  * `pre-wrap`: 保留空白符，保留换行符，允许自动换行
  * `pre-line`: 合并空白符，保留换行符，允许自动换行
* `text-shadow: h-shadow v-shadow blur color`: 文本阴影
  * `h-shadow`: 阴影的水平偏移
  * `v-shadow`：阴影的垂直偏移
  * `blur`: 模糊的距离
  * `color`: 阴影颜色
* `word-break`: 自动换行方式, 默认为`normal`
  * `normal`: 默认换行规则
  * `break-all`: 允许单词内换行
  * `keep-all`: 只能在半角空格或连字符处换行
* `word-wrap`: 长单词换行处理，默认为`normal`
  * `normal`: 长单词不自动换行
  * `break-word`: 长单词自动换行
* `text-overflow`: 文本溢出处理，要与'overflow:hidden'配合
  * `clip`: 修剪文本
  * `ellipsis`: 使用省略号代表修剪的文本
  * `string`: 使用指定字符串代表修剪的文本
* `cursor`: 光标，默认`default`
  * `url(<url>)`: 自定义光标
  * `default`: 箭头
  * `pointer`: 手型
  * `crosshair`: 十字线
  * `move`: 移动
  * `text`: 文本
  * `wait`: 忙碌
  * `help`: 帮助


# 盒模型

![盒模型](images/ct_boxmodel.gif)

尺寸

* `一个尺寸`: 上/下/左/右
* `两个尺寸`: 上/下 左/右
* `三个尺寸`：上 左/右 下
* `四个尺寸`：上 右 下 左

## display

* `display`: 框类型
  * `none`: 不显示
  * `block`: 块元素
  * `inline`: 内联元素
  * `inline-block`: 行内块元素
  * `table`: 表格元素

## 可见性

* `opacity`: 不透明度，`0~1`之间，IE8及以下使用`filter:alpha(opacity=x)`兼容
* `visibility`: 是否可见，默认`visible`
  * `visible`: 可见
  * `hidden`: 不可见

## width/height

行内框不能设置尺寸

* `width`: 元素的宽，默认为`auto`
  * `auto`: 自动计算
  * `length`: 宽
  * `percentage`: 相对于父元素的`width`而言
* `min-width`: 元素的最小宽度
* `max-width`: 元素的最大宽度
* `height`: 元素的高，默认为`auto`
* `min-height`: 元素的最小高度
* `max-height`: 元素的最大高度

## overflow

* `overflow`: 框溢出处理，默认为`visible`
  * `visible`: 不裁剪，直接显示
  * `hidden`: 裁剪
  * `scroll`: 显示滚动条
  * `auto`: 自动显示滚动条
* `overflow-x`: 水平方向溢出处理
* `overflow-y`: 垂直方向溢出处理

## padding

尺寸不能为负，百分比相对于父元素的宽度而言

* `padding-top`: 上内边距
* `padding-bottom`: 下内边距
* `padding-left`: 左内边距
* `padding-right`: 右内边距
* `padding`: 内边距

## margin

尺寸可以为负，可以为`auto`, 百分比相对于父元素的宽度而言

* `margin-top`: 上外边距
* `margin-bottom`: 下外边距
* `margin-left`: 左外边距
* `margin-right`: 右外边距
* `margin`: 外边距
* `margin:0 auto`: 块元素水平居中

## 外边距合并

普通文档流中块元素的垂直边距相遇时，会合并为一个外边距，高度为大的外边距

### 兄弟元素

![兄弟元素](images/ct_css_margin_collapsing_example_1.gif)

### 父子元素

![父子元素](images/ct_css_margin_collapsing_example_2.gif)

### 空元素

![空元素](images/ct_css_margin_collapsing_example_3.gif)

## border

* `border-width`: 四条边框宽度
* `border-style`: 四条边框样式
  * `none`: 无边框
  * `solid`: 实线
  * `dashed`: 虚线
  * `dotted`: 点线
  * `double`: 双线
  * `groove`: 3D凹槽
  * `ridge`: 3D凸槽
  * `inset`: 3D凹边
  * `outset`: 3D凸边
* `border-color`: 四条边框颜色
* `border:[border-width] [border-style] [border-color]`: 四条边框
* `border-top:[border-top-width] [border-top-style] [border-top-color]`: 上边框
* `border-bottom:[border-bottom-width] [border-bottom-style] [border-bottom-color]`: 下边框
* `border-left:[border-left-width] [border-left-style] [border-left-color]`: 左边框
* `border-right:[border-right-width] [border-right-style] [border-right-color]`: 右边框

## outline

* `outline-width`: 轮廓宽度
* `outline-style`: 轮廓样式
  * `none`: 无轮廓
  * `solid`: 实线
  * `dashed`: 虚线
  * `dotted`: 点线
  * `double`: 双线
  * `groove`: 3D凹槽
  * `ridge`: 3D凸槽
  * `inset`: 3D凹边
  * `outset`: 3D凸边
* `outline-color`: 轮廓颜色
* `outline:[outline-width] [outline-style] [outline-color]`: 轮廓

## border-radius

* `border-top-left-radius`: 左上角圆角
* `border-top-right-radius`: 右上角圆角
* `border-bottom-left-radius`: 左下角圆角
* `border-bottom-right-radius`: 右下角圆角
* `border-radius`: 四个圆角

## background

* `background-color`: 背景颜色，默认为`transparent`
* `background-image`: 背景图片，默认为`none`
  * `url(<url>)`: 背景图片地址
* `background-repeat`: 背景重复，默认为`repeat`
  * `no-repeat`: 不重复
  * `repeat`: x, y方向都平铺
  * `repeat-x`: x方向平铺
  * `repeat-y`: y方向平铺
* `backgound-position`: 背景位置，默认为左上角
  * `关键字`：`<left|center|right> <top|center|bottom>`
  * `百分比`：`x% y%`，相对于当前盒模型的`width`, `height`而言
  * `尺寸`：`x y`, 相对于左上角而言，可以为负
* `background-origin`: `background-position`相对什么定位
  * `content-box`: 内容框
  * `padding-box`: 内边距框
  * `border-box`: 边框
* `background-clip`: 背景的绘制区域
  * `content-box`: 内容框
  * `padding-box`: 内边距框
  * `border-box`: 边框
* `background-size`: 背景图片大小
  * `length`: 第一个值为宽度，第二个值为高度(默认为auto)
  * `percentage`: 相对于父元素的`width`而言
  * `contain`: 覆盖内容区域
  * `cover`: 覆盖背景区域
* `background-attachment`: 背景关联，默认随页面滚动
  * `scroll`: 随页面滚动
  * `fixed`: 固定，不随页面滚动
* `background:[background-color] [background-image] [background-repeat] [background-position]`: 背景样式

## box-shadow

* `box-shadow: h-shadow v-shadow blur spread color inset,...`: 添加一个或多个阴影
  * `h-shadow`: 阴影的水平偏移
  * `v-shadow`: 阴影的垂直偏移
  * `blur`: 模糊距离
  * `spread`: 阴影尺寸
  * `color`: 阴影颜色
  * `inset`: 将外部阴影`outset`改为内部阴影


# 定位机制

* 普通流
* 浮动
* 定位

## 普通流

* 元素的位置由元素在`HTML`中的位置决定
* 块级框从上到下一个接一个排列，框之间的垂直距离由框的垂直外边距合并而成
* 行内框在一行中水平布置，可以使用内边距、边框、水平外边距影响行内框的排布，垂直外边距不影响行内框的排布

## 浮动

浮动的框可以向左或向右移动，直到它的外边缘碰到父元素框或另一个浮动框为止

* `float`: 浮动, 默认为`none`
  * `none`: 不浮动
  * `left`: 向左浮动，自动变成块级框，原来所占的位置删除，占用覆盖位置
  * `right`: 向右浮动，自动变成块级框，原来所占的位置删除，占用覆盖位置

![浮动](images/ct_css_positioning_floating_linebox.gif)

* `clear`: 清除浮动，默认为`none`
  * `none`: 不清除浮动
  * `left`: 清除左浮动，父元素包围左浮动元素
  * `right`: 清除右浮动，父元素包围右浮动元素
  * `both`: 清除左右浮动，父元素包围左右浮动元素

![清除浮动](images/ct_css_positioning_floating_clear_div.gif)

```css
/*清除浮动*/

.clearfix:before,
.clearfix:after{
  content:" ";
  display:block;
}

.clearfix:after{
  clear:both
}
```

## 定位

* `position`: 定位，默认为`static`
  * `static`: 不定位，元素框正常生成
  * `relative`: 相对定位，元素框可以相对于原来的位置偏移，原来所占的位置仍保留
  * `absolute`: 绝对定位，元素框可以相对于最近的已定位的祖先元素偏移，自动变成块级框，原来所占的位置删除
  * `fixed`: 固定定位，元素框可以相对于屏幕位置偏移，自动变成块级框，原来所占的位置删除
* `top`: 盒模型的上偏移
* `bottom`: 盒模型的下偏移
* `left`: 盒模型的左偏移
* `right`: 盒模型的右偏移
* `z-index`: 堆叠顺序，默认为`auto`
  * `auto`: 与父元素相同
  * `number`: 设置堆叠顺序

# 标签样式

## 链接

* `a:link`: 未访问的链接
* `a:visited`: 访问了的链接
* `a:hover`: 鼠标移上去的链接，得放在`a:link`, `a:visited`后面
* `a:focus`: 获取焦点的链接，得放在`a:link`, `a:visited`后面
* `a:active`: 点中的链接，，得放在`a:hover`

## 列表

* `list-style-type`: 列表项标记类型
  * `none`: 无标记
  * `disc`: 实心圆，无序列表默认类型
  * `circle`: 空心圆
  * `square`: 实心方块
  * `decimal`: 数字，有序列表默认类型
  * `lower-roman`: 小写罗马数字
  * `upper-roman`: 大写罗马数字
  * `lower-alpha`: 小写英文字母
  * `upper-alpha`: 大写英文字母
  * `lower-greek`: 小写希腊字母
* `list-style-position`: 列表项标记位置，默认`outside`
  * `outside`: 文本外
  * `inside`: 文本内
* `list-style-image`: 列表项图片，默认为`none`
  * `none`: 无
  * `url(<url>)`: 图片路径
* `list-style:[list-style-type] [list-style-position] [list-style-image]`: 列表项样式

## 表格

* `border-collapse`: 合并边框，默认`separate`
  * `separate`: 不合并
  * `collapse`: 合并边框
* `border-spacing`: 单元格外边距
  * `x y`: 水平间距、垂直间距
* `caption-side`: 标题位置，默认`top`
  * `top`: 表格之上
  * `bottom`: 表格之下
* `table-layout`: 表格布局
  * `automatic`: 自动布局
  * `fixed`：固定布局

# 居中

## 水平居中

### 行内元素

```css
.text-center{
  text-align:center;
}
```

### 定宽块元素

```css
.container{
  width:1000px;
  margin-left:auto;
  margin-right:auto;
}
```

## 垂直居中

### 一行文本

```css
.middle{
  height:30px;
  line-height;30px;
}
```

### 内联元素

```css
.middle{
  padding:20px 0;
}
```

### 定高块元素

```css
.middle{
  position:absolute;
  top:50%;
  height:200px;
  margin-top:-100px;
}
```

### 不定高块元素

```css
.middle{
  position:absolute;
  top:50%;
  transform:translateY(-50%);
}
```