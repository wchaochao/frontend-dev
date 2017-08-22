# CSS

定义如何显示`HTML`元素

## 目录

## 推荐资料

* [w3school-css](http://www.w3school.com.cn/css/index.asp)
* [codecademy-html-css](https://www.codecademy.com/learn/learn-html-css)
* 《Head First HTML and CSS》
* 《精通css:高级web标准解决方案》
* 《CSS权威指南》


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

# 文档结构

* 一般性样式
  * reset样式
  * 主体样式
  * 链接
  * 标题
  * 其他元素
* 辅助样式
  * 距离
  * 颜色
  * 背景颜色
  * 其他辅助样式
* 页面结构
  * 页头、页脚、导航
  * 布局
  * 其他页面结构元素
* 页面组件
* 具体页面


# 选择器

## 通配符选择器

* `*`: 所有元素

```css
/* reset */
*{
  padding:0;
  margin:0;
}
```

## 元素选择器

* `element`: 某类元素

## id选择器

* `#id`: 拥有指定`id`的元素
* `selector#id`: 拥有指定`id`的某个选择器

## 类选择器

* `.class`: 拥有指定类的元素
* `selector.class`: 拥有指定类的某个选择器

## 属性选择器

* `[attribute]`: 拥有指定属性的元素
* `[attribute=value]`: 指定属性的属性值为指定值的元素
* `[attribute~=value]`: 指定属性的属性值可包含多个词且指定值是其中之一的元素
* `[attribute|=value]`: 指定属性的属性值以指定值或指定值-开头的元素
* `[attribute^=value]`: 指定属性的属性值以指定值开头的元素
* `[attribute$=value]`: 指定属性的属性值以指定值结尾的元素
* `[attribute*=value]`: 指定属性的属性值包含指定值的元素
* `selector[attribute]`: 拥有指定属性的某个选择器

## 分组选择器

* `selector1,selector2...`: 多个选择器应用同一套规则

## 后代选择器

* `ancestor descendant`: 某个选择器的后代选择器

## 子代选择器

* `parent>child`: 某个选择器的子代选择器

## 兄弟选择器

* `prev ~ siblings`: 某个选择器后面的所有兄弟选择器

## 相邻兄弟选择器

* `prev + next`: 某个选择器的下一个兄弟选择器

## 伪类选择器

将某种幻象类关联到元素上

### 效果伪类

* `:link`: 未访问的链接
* `:visited`: 已访问的链接
* `:hover`: 鼠标悬停
* `:focus`: 获取焦点
* `:active`: 激活
* `:target`: 目标
* `:enabled`: 启用
* `:disabled`: 禁用
* `:checked`: 选中

### 角色伪类

* `:first-child`: 作为第一个子元素
* `:last-child`: 作为最后一个子元素
* `:only-child`: 作为唯一一个子元素
* `:nth-child(n)`: 作为第n个子元素, 子元素从`1`开始
  * `:nth-child(an+b)`: 作为第`an+b`个子元素, `n`从0开始
  * `:nth-child(odd)`: 作为第`2n-1`个子元素
  * `:nth-child(even)`: 作为第`2n`个子元素
* `:nth-last-child(n)`: 作为倒数第`n`个子元素
* `:first-of-type`: 在子元素中第一个出现的某类元素
* `:last-of-type`: 在子元素中最后一个出现的某类元素
* `:only-of-type`: 在子元素中唯一出现的某类元素
* `:nth-of-type(n)`: 在子元素中第`n`个出现的某类元素
* `:nth-last-of-type(n)`: 在子元素中倒数第`n`个出现的某类元素
* `:empty`: 没有子元素
* `:root`: 作为根元素

### 筛选伪类

* `:lang(value)`: 相当于`[lang|="value"]`
* `:not(selector)`: 排除某些选择器


## 伪元素

插入假想的元素

* `:first-letter`: 首字母
* `:first-line`: 首行
* `:before`: 内容之前
* `:after`: 内容之后
* `::selection`: 选中部分

**限制**：只能放在选择器的最后面，且只能应用某些CSS样式


# 优先级

## 样式表优先级

浏览器默认样式<读者样式<创作者样式

## 选择器优先级

分为a,b,c,d四个等级, 依次比较a,b,c,d

* `a`: 行内样式为1
* `b`: `id`选择器的数目
* `c`: 类选择器、伪类选择器、属性选择器的数目
* `d`: 元素选择器、伪元素选择器的数目

## 样式优先级

普通样式<`!important`样式

## 应用样式

1. 收集元素的样式，将样式按以下三类划分
* 创作者普通样式、读者普通样式、浏览器默认样式
* 创作者重要样式
* 读者重要样式
2. 每类按选择器优先级排序
3. 同选择器优先级的按样式表优先级排序
4. 同样式表优先级的按出现顺序排序
5. 排序完后按排序的顺序依次应用样式，样式冲突时后面的样式会覆盖前面的样式和继承的样式


# 样式值

## 字体

### 通用字体系列

拥有相似外观的字体组合

* `Serif`：有衬线，多用于新闻报纸的文字排版
* `Sans-serif`：无衬线，多用于计算机屏幕
* `Monospace`：等宽字体，多用于软件代码示例
* `Cursive`： 手写体
* `Fantasy`：幻想体

### 特定字体系列

具体的字体系列

* `Times`
* `Courier`

### web字体

托管在服务器上的字体

* `.ttf`: `TureType`字体格式
* `.otf`: `OpenType`字体格式
* `.eot`: `Embedded OpenType`字体格式
* `.svg`: `SVG`字体格式
* `.woff`: `Web`开放字体格式

使用`web`字体

```css
@font-face{
  font-family:<font-family>;
  src:url("<url>"),...
}
```

## 长度

### 绝对长度

* `cm`: 厘米
* `mm`: 毫米
* `in`: 英寸，`2.54cm`
* `pt`: 点，印刷单位，`1/72in`
* `pc`: 派卡，印刷单位，`12pt`

### 相对长度

* `px`: 像素
* `em`: 字体大小
* `ex`: 小写`x`的高度
* `%`: 百分比

## 颜色

* 颜色名：`aqua, black, blue, fuchsia, gray, green, lime, maroon, navy, olive, orange, purple, red, silver, teal, white, yellow`等147种颜色
* 十六进制颜色：`#RRGGBB`, RR(红色)、GG(绿色)、BB(蓝色), 值`00~FF`之间，`#rrggbb`形式的十六进制颜色可简写为`#rgb`
* RGB颜色: `rgb(red, green, blue)`，值`0~255`或`0% ~100%`之间
* RGBA颜色: `rgba(red, green, blue, alpha)`, `alpha`为不透明度，值`0~1`之间
* HSL颜色：`hsl(hue, saturation, lightness)`, hue(色调)(0~360)(红-绿-蓝), saturation(饱和度)(0%~100%)(灰-全彩), lightness(亮度)(0%~100%)(黑-白)
* HSLA 颜色: hsla(hue, saturation, lightness, alpha)

## URL

* 绝对URL：`<protocol>://<user>:<password>@<host>:<port>/<path>?<query>#<hash>`
* 相对URL：`<path>?<query>#<hash>`

## 关键字

* `inherit`: 继承父元素的样式


# 文本样式

## 注释

```css
/* comment */
```

## 字体

* `font-family`: 文本的字体
  * `字体`: 可定义多个字体作为备用，字体间用`,`隔开，最后一个通常为字体系列，字体名有空格或`#`,`$`时需要用引号
* `font-style`: 字体风格，默认为`normal`
  * `normal`: 正常显示
  * `italic`: 斜体显示
  * `oblique`: 倾斜显示
* `font-variant`: 字体变形，默认为`normal`
  * `normal`: 正常
  * `small-caps`: 小型大写字母
* `font-weight`: 字体加粗，默认为`normal`
  * `normal`: 正常
  * `bold`: 粗体
  * `bolder`: 更粗
  * `lighter`: 更细
  * `<100|200...|900>`: 400相当于`normal`，700相当于`bold`
* `font-size`: 字体大小, 默认为`medium`
  * `length`: 具体长度
  * `em|percentage`: 相对于父字体大小
  * `关键字`：`xx-small, x-small, small, medium, large, x-large, xx-large, smaller, larger`
* `font:[font-style] [font-variant] [font-weight] <font-size[/line-height]> <font-family>`: 字体

![font-family](images/font-family.png)

![font-style](images/font-style.png)

![font-variant](images/font-variant.png)

![font-weight](images/font-weight.png)

![font-size](images/font-size.png)

![font](images/font.png)

## 文本

* `color`: 文本颜色
* `text-indent`: 缩进
  * `length`: 具体长度
  * `em`: 相对于自身字体大小
  * `percentage`: 相对于父元素的宽度
* `text-align`: 水平对齐
  * `left`: 左对齐
  * `center`: 居中对齐
  * `right`: 右对齐
  * `justify`: 两端对齐
* `line-height`: 行高，默认为`normal`
  * `normal`: 正常，通常为`1.2em`
  * `length`：具体长度
  * `em|percentage`: 相对于自身字体大小
  * `number`: 缩放因子，相对于自身字体大小
* `vertical-align`: 垂直对齐, 默认为`baseline`
  * `baseline`: 行内框的基线与行框的基线对齐
  * `sub`: 行内框的基线与行框的下标基线低
  * `super`: 行内框的基线与行框的上标基线高
  * `top`: 行内框的顶端与行框的顶端对齐
  * `text-top`: 行内框的顶端与行框字体的顶端对齐
  * `middle`: 行内框的中线与行框基线上方的`0.5ex`处对齐
  * `bottom`: 行内框的底端与行框的底端对齐
  * `text-bottom`: 行内框的底端与行框字体的底端对齐
  * `length`: 相对于行框的基线升高或降低
  * `percentage`: 相对于`line-height`而言
* `word-spacing`: 字间隔，默认为`normal`
  * `normal`: 正常间隔，相当于`0`
  * `length`：具体长度
* `letter-spacing`: 字母间隔，默认为`normal`
  * `normal`: 正常间隔，相当于`0`
  * `length`：具体长度
* `text-transform`: 文本转换，默认为`none`
  * `none`: 不处理
  * `uppercase`: 全大写
  * `lowercase`: 全小写
  * `capitalize`: 首字母大写
* `text-decoration`: 文本装饰，默认为`none`，可指定多个，颜色为文本颜色
  * `none`: 无装饰
  * `underline`: 下划线
  * `overline`: 上划线
  * `line-through`: 删除线
  * `blink`: 闪烁
* `text-shadow: [h-shadow] [v-shadow] [blur] [color]`: 文本阴影，可指定多个
  * `h-shadow`: 阴影的水平偏移
  * `v-shadow`：阴影的垂直偏移
  * `blur`: 模糊距离
  * `color`: 阴影颜色
* `white-space`: 空白符处理，默认为`normal`
  * `normal`: 合并空白符，忽略换行符，允许自动换行
  * `nowrap`: 合并空白符，忽略换行符，不允许自动换行
  * `pre`: 保留空白符，保留换行符，不允许自动换行
  * `pre-wrap`: 保留空白符，保留换行符，允许自动换行
  * `pre-line`: 合并空白符，保留换行符，允许自动换行
* `word-break`: 自动换行方式, 默认为`normal`
  * `normal`: 默认换行规则
  * `break-all`: 允许单词内换行
  * `keep-all`: 只能在半角空格或连字符处换行
* `word-wrap`: 长单词换行处理，默认为`normal`
  * `normal`: 长单词不自动换行
  * `break-word`: 长单词自动换行
* `text-overflow`: 文本溢出处理，要与`overflow:hidden`配合
  * `clip`: 修剪文本
  * `ellipsis`: 使用省略号代表修剪的文本
  * `string`: 使用指定字符串代表修剪的文本
* `cursor`: 光标，默认`default`
  * `url("<url>")`: 自定义光标
  * `default`: 箭头
  * `pointer`: 手型
  * `crosshair`: 十字线
  * `move`: 移动
  * `text`: 文本
  * `wait`: 忙碌
  * `help`: 帮助
* `direction`: 文本方向
  * `ltr`: 从左到右
  * `rtl`: 从右到左

![color](images/color.png)

![text-indent](images/text-indent.png)

![text-align](images/text-align.png)

![line-height](images/line-height.png)

![vertical-align](images/vertical-align.png)

![word-spacing](images/word-spacing.png)

![letter-spacing](images/letter-spacing.png)

![text-transform](images/text-transform.png)

![text-decoration](images/text-decoration.png)

![text-shadow](images/text-shadow.png)

![white-space](images/white-space.png)

![direction](images/direction.png)



# 盒模型

![盒模型](images/ct_boxmodel.gif)

![盒模型](images/boxmodel.png)

四边尺寸处理

* `一个尺寸`: 上/下/左/右
* `两个尺寸`: 上/下 左/右
* `三个尺寸`：上 左/右 下
* `四个尺寸`：上 右 下 左(顺时针方向)

## width/height

行内非替换元素不能设置宽高

* `width`: 元素的宽，默认为`auto`
  * `auto`: 自动计算，块元素由盒模型决定，行内元素由内容决定
  * `length`: 宽
  * `percentage`: 相对于父元素的宽而言
* `min-width`: 元素的最小宽度
* `max-width`: 元素的最大宽度
* `height`: 元素的高，默认为`auto`
  * `auto`: 自动计算, 由内容决定
  * `length`: 高
  * `percentage`: 相对于父元素的高而言
* `min-height`: 元素的最小高度
* `max-height`: 元素的最大高度

![width](images/width.png)

![height](images/height.png)

![min-length](images/min-length.png)

![max-length](images/max-length.png)

## padding

尺寸不能为负，百分比相对于父元素的宽度而言

* `padding-top`: 上内边距
* `padding-bottom`: 下内边距
* `padding-left`: 左内边距
* `padding-right`: 右内边距
* `padding`: 内边距

![padding-4](images/padding-4.png)

![padding](images/padding.png)

## margin

尺寸可以为负，可以为`auto`, 百分比相对于父元素的宽度而言

* `margin-top`: 上外边距
* `margin-bottom`: 下外边距
* `margin-left`: 左外边距
* `margin-right`: 右外边距
* `margin`: 外边距

![margin-4](images/margin-4.png)

![margin](images/margin.png)

## 外边距合并

同一个BFC中的块元素的垂直外边距相遇时，会合并为一个外边距

1. 将相遇的垂直外边距按正负化为两类
2. 正的一类取大的，负的一类取小的
3. 将取得的两个值相加，为合并后的外边距大小

### 兄弟元素

![兄弟元素](images/ct_css_margin_collapsing_example_1.gif)

### 父子元素

![父子元素](images/ct_css_margin_collapsing_example_2.gif)

### 空元素

![空元素](images/ct_css_margin_collapsing_example_3.gif)

## box-sizing

* `box-sizing`: 宽高对应的框，默认为`content-box`
  * `content-box`: 宽高为`content-box`的尺寸
  * `border-box`: 宽高为`border-box`的尺寸

content-box

![content-box](images/htmlcss1-diagram__contentbox.svg)

border-box

![border-box](images/htmlcss1-diagram__borderbox.svg)

## display

浮动或定位时，`display`会重新计算，`inline-table`变为`table`，其他变为`block`

* `display`: 显示方式，默认为`inline`
  * `none`: 不存在，从普通流中删除
  * `block`: 块元素
  * `inline`: 行内元素
  * `inline-block`: 行内块元素
  * `run-in`: 根据上下文作为块级元素或行内元素显示
  * `list-item`: 列表项
  * `table`: 块级表
  * `inline-talbe`: 行内表
  * `table-row`: 行
  * `table-row-group`: 行组
  * `table-header-group`: 表头
  * `table-footer-group`: 表注
  * `table-colume`: 列
  * `table-column-group`: 列组
  * `table-cell`: 单元格
  * `table-caption`: 表标题

![display](images/display.png)

## visibility

* `visibility`: 可见性，默认`visible`
  * `visible`: 可见
  * `hidden`: 隐藏，仍存在
  * `collapse`: 表元素时隐藏一行或一列，其他元素等同于`hidden`

![visibility](images/visibility.png)

## opacity

* `opacity`: 不透明度，`0~1`之间，会被子元素继承

## overflow

* `overflow`: 内容溢出可视区域处理，默认为`visible`
  * `visible`: 显示溢出部分
  * `hidden`: 隐藏溢出部分
  * `scroll`: 显示滚动条
  * `auto`: 自动显示滚动条
* `overflow-x`: 水平方向溢出处理
* `overflow-y`: 垂直方向溢出处理

![overflow](images/overflow.png)

## clip

* `clip`: 裁剪可视区域，默认为`auto`
  * `auto`: 不裁剪
  * `rect(<top>, <right>, <bottom>, <left>)`: 裁剪一个矩形，值为各边距内边距框左上角的距离

![clip](images/clip.png)

## border

* `border-width`: 四条边框宽度，默认为`medium`
  * `length`：具体长度
  * `关键字`：`thin,medium,thick`
* `border-style`: 四条边框样式，默认为`none`
  * `none`: 无边框
  * `solid`: 实线
  * `dashed`: 虚线
  * `dotted`: 点线
  * `double`: 双线
  * `groove`: 3D凹槽
  * `ridge`: 3D凸槽
  * `inset`: 3D凹边
  * `outset`: 3D凸边
* `border-color`: 四条边框颜色, 默认为文本颜色
* `border-top:[border-top-width] [border-top-style] [border-top-color]`: 上边框
* `border-bottom:[border-bottom-width] [border-bottom-style] [border-bottom-color]`: 下边框
* `border-left:[border-left-width] [border-left-style] [border-left-color]`: 左边框
* `border-right:[border-right-width] [border-right-style] [border-right-color]`: 右边框
* `border:[border-width] [border-style] [border-color]`: 四条边框

![border-width-4](images/border-width-4.png)

![border-width](images/border-width.png)

![border-style-4](images/border-style-4.png)

![border-style](images/border-style.png)

![border-color-4](images/border-color-4.png)

![border-color](images/border-color.png)

![border-4](images/border-4.png)

![border](images/border.png)

## border-radius

圆角半径最大为`border-box`宽高较小值的一半，大于这个值时当作这个值处理

* `border-top-left-radius`: 左上角圆角
* `border-top-right-radius`: 右上角圆角
* `border-bottom-left-radius`: 左下角圆角
* `border-bottom-right-radius`: 右下角圆角
* `border-radius`: 四个圆角

## outline

绘制在`border-box`外，不影响页面布局

* `outline-width`: 轮廓宽度
* `outline-style`: 轮廓样式
* `outline-color`: 轮廓颜色，默认为文本颜色
* `outline:[outline-width] [outline-style] [outline-color]`: 轮廓

## background

通常将多个图标放置在一张图片上，以减少请求次数，可提供多个背景

* `background-color`: 背景颜色，默认为`transparent`
* `background-image`: 背景图片，默认为`none`
  * `none`: 无背景图片
  * `url("<url>")`: 背景图片地址
* `background-repeat`: 背景重复，默认为`repeat`
  * `no-repeat`: 不重复
  * `repeat`: x, y方向都平铺
  * `repeat-x`: x方向平铺
  * `repeat-y`: y方向平铺
* `backgound-position`: 背景位置，默认为`0% 0%`
  * `关键字`：`<left|center|right> <top|center|bottom>`，一个关键字时，另一个默认为`center`
  * `percentage`：`x% y%`，一个百分比时，另一个默认为`50%`
  * `length`：`x y`, 相对于左上角而言，可以为负
* `background-origin`: `background-position`相对什么定位，默认为`border-box`
  * `content-box`: 内容框
  * `padding-box`: 内边距框
  * `border-box`: 边框
* `background-clip`: 背景的绘制区域, 默认为`border-box`
  * `content-box`: 内容框
  * `padding-box`: 内边距框
  * `border-box`: 边框
* `background-size`: 背景图片大小
  * `length`: 第一个值为宽度，第二个值为高度(默认为`auto`)
  * `percentage`: 相对于父元素的`width`而言
  * `contain`: 覆盖内容区域
  * `cover`: 覆盖背景区域
* `background-attachment`: 背景关联，默认为`scroll`
  * `scroll`: 随页面滚动
  * `fixed`: 固定，不随页面滚动，背景位置相对于浏览器窗口而言
* `background:[background-color] [background-image] [background-repeat] [background-attachment] [background-position]`: 背景样式

![background-color](images/background-color.png)

![background-image](images/background-image.png)

![background-repeat](images/background-repeat.png)

![background-position](images/background-position.png)

![background-position-percentage](images/background-position-percentage.png)

![background-attachment](images/background-attachment.png)

![background](images/background.png)

## box-shadow

* `box-shadow: [h-shadow] [v-shadow] [blur] [spread] [color] [inset]`: 阴影，可添加多个
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
* 块级框从上到下一个接一个排列，框的水平部分总和等于父元素的宽，框之间的垂直距离由框的垂直外边距合并而成
* 行内框在一行中水平排列，内边距、边框、外边距对非替换元素无垂直效果，对替换元素（如图片、文本框）有垂直效果，`vertical-align`影响垂直分布

## 浮动

浮动的框可以向左或向右移动，直到它的外边缘碰到父元素框或另一个浮动框为止

* `float`: 浮动, 默认为`none`
  * `none`: 不浮动
  * `left`: 向左浮动，自动变成块级框，原来所占的位置删除，周围内容环绕浮动元素
  * `right`: 向右浮动，自动变成块级框，原来所占的位置删除，周围内容环绕浮动元素

![浮动](images/ct_css_positioning_floating_linebox.gif)

![float](images/float.png)

尺寸不够时往下排列

![float-down](images/float-down.png)

与内容重叠时

* 与行内框重叠，行内框的边框、背景、内容在浮动元素之上显示
* 与块框重叠，边框、背景在浮动元素之下，内容在浮动元素之上

清除浮动

* `clear`: 清除浮动，默认为`none`
  * `none`: 不清除浮动
  * `left`: 清除左浮动，元素左边不允许有浮动内容
  * `right`: 清除右浮动，元素右边不允许有浮动内容
  * `both`: 清除左右浮动，元素左右两边不允许有浮动内容

![清除浮动](images/ct_css_positioning_floating_clear_div.gif)

![clear](images/clear.png)

```css
/*清除浮动*/

.clearfix:before,
.clearfix:after{
  content:" ";
  display:table;
}

.clearfix:after{
  clear:both
}

/* or */
parent{
  overflow:hidden;
}

/* or */
parent{
  float:left;
}
```


## 定位

以外边距框来完成偏移

* `position`: 定位，默认为`static`
  * `static`: 静态定位，元素框正常生成，块级元素生成块框，行内元素生成行内框
  * `relative`: 相对定位，元素框可以相对于原来的位置偏移，原来所占的位置仍保留
  * `absolute`: 绝对定位，元素框可以相对于最近的已定位的祖先元素的内边距框偏移(没有时相对于`body`元素)，自动变成块级框，原来所占的位置删除
  * `fixed`: 固定定位，元素框可以相对于浏览器窗口位置偏移，自动变成块级框，原来所占的位置删除，页面滚动时仍不动
* `top`: 盒模型的上偏移，正数对应下移，默认为`auto`
* `bottom`: 盒模型的下偏移，正数对应上移，默认为`auto`
* `left`: 盒模型的左偏移，正数对应右移，默认为`auto`
* `right`: 盒模型的右偏移，正数对应左移，默认为`auto`
* `z-index`: 堆叠顺序，默认为`auto`
  * `auto`: 与父元素堆叠顺序相同
  * `number`: 相对于父元素的堆叠顺序

![relative](images/relative.png)

![absolute](images/absolute.png)

![position](images/position.png)

![offset](images/offset.png)

![z-index](images/z-index.png)


# 布局原理

## visual formatting model

视觉格式化模型，规定浏览器如何在屏幕上绘制元素，每个元素根据盒模型创建零个或者多个盒子，盒子的布局由以下因素决定：

* 盒子的尺寸和类型
* 定位机制(`normal flow`, `float`, `absolute positioning`)
* 元素在文档树中的关系
* 其它因素(viewport size, 图片的本身的尺寸等)

## container block

很多盒子的位置和大小，是根据一个与之相关的矩形来计算的，称为包含块

## box

渲染的基本单位，`box`的类型由元素的类型和`display`属性决定，不同类型的`box`参与不同类型的`formatting context`布局。

### block

* `block-level-element`: `display: block / list-item / table;`的元素
* `block-level box`: `block-level-element`会创建一个`block-level box`，受控于`block formatting context`
* `block container box`: 包含`block-level box`或创建一个`inline formatting context`，用于包含`inline-level box`
  * 除了`display: table;`之外的`block-level box`
  * 行内块级元素，单元格元素
* `block box`: 既是`block-level box`，又是`block container box`

### inline

* `inline-level element`: `display: inline / inline-table / inline-block;`的元素
* `inline-level box`: `inline-level element`会创建`inline-level box`，受控于`inline formatting context`
* `inline box`: 既是`inline-level box`, 而且其内容受控于`inline formatting context`
  * 不可替换的行内元素
* `atomic inline-level box`: 既是`inline-level box`, 而且其作为一个整体受控于`inline formatting context`
  * 可替换的行内元素，行内块级元素，`inline-table`元素

## Formatting Contexts

格式化上下文，页面中的一块渲染区域，并且有一套渲染规则，它决定了其子元素将如何定位，以及和其他元素的关系和相互作用

### BFC

块级格式化上下文(`Block Formatting Contexts`)

#### 创建

* 根元素或其它包含它的元素
* 浮动元素 (元素的`float`不为`none`)
* 绝对定位元素(元素的`position`为`absolute`或`fixed`)
* 行内块元素(元素的`display`为`inline-block`)
* 表格单元格(元素的`display`为`table-cell`)
* 表格标题(元素的`display`为`table-caption`)
* `overflow`的值不为`visible`的元素

#### 特性

* `box`从`containing block`的顶部开始，在垂直方向上，一个接一个的排列
* 两个相邻的`box`间的垂直间距，由它们的`margin`属性决定，并且，会发生`margin collapse`
* 每一个box的左边缘紧贴`containing block`的左边缘，即使设置了浮动，也是如此
* 不会与`float box`重叠，常用来清除浮动和布局
* 计算高度时，浮动元素也参与计算

#### 作用

* `margin collapse`
* `contain float`

### IFC

行内格式化上下文(`Inline Formatting Contexts`)

#### 生成

块级元素中仅包含内联级别元素时

#### 规则

* `box`会从`container block`的顶部开始，在水平方向上，一个接一个的排列
* 水平`margin`，`border`，`padding`，会作用到这些`box`上
* 垂直方向上按照`vertical-align`来对齐
* 每一行的多个`box`，会包含在一个矩形区域中，这个矩形区域，称为`line box`
* 行框的宽度是由包含块和存在的浮动来决定
* 行框的高是最顶端框的顶边到最底端框的底边的距离
* 计算行框里的各行内级框的高度时，对于可替换元素、行内块元素、行内表格元素来说，是外边距框的高度，对于行内框来说，是其`line-height`
* 当一个`inline box`超过`line box`的宽度时，它会被分割成多个`boxes`，这些`boxes`被分布在多个`line box`里

#### 实用

* 水平居中
* 垂直居中

### GFC

栅格格式化上下文(`Grid Formatting Contexts`)

### FFC

Flex格式化上下文(`Flex Formatting Contexts`)


# 表布局

CSS中的表布局

## 表元素

根据`display`属性的值判断

* `table`: 块级表
* `inline-talbe`: 行内表
* `table-row`: 行
* `table-row-group`: 行组
* `table-header-group`: 表头
* `table-footer-group`: 表注
* `table-colume`: 列
* `table-column-group`: 列组
* `table-cell`: 单元格
* `table-caption`: 表标题

![表元素](images/table-element.png)

## 表编排

* 行框包含一行表格单元，所有行框按其出现的顺序从上到下地填充表
* 行组包括多个行框
* 列框包含一列或多列表格单元，所有列框按其出现的顺序依次相邻放置
* 列组包含多个列框
* 单元格可能跨多行或多列
* 单元格不能超出表或行组的最后一个行框
* 单元格有内容、内边距、边框，无外边框，设置外边框样式时会被忽略
* 行框的表格单元的高度相等，列框的表格单元的宽度相等
* 以行为主，列从行中推导出来
* 最少需要表、行、单元格三个元素才能组成表，缺少时插入匿名表对象

## 表层

![表层](images/table-layer.png)

## 列

列和列组只能接受四种样式

* `border`: 分隔边框模型时才能设置边框
* `background`: 根据表层确认是否会被覆盖
* `width`: 列或列祖的最小宽度
* `visibility`: 只有`collapse`才有用，其它忽略

## 表标题

一小段文本，描述表内容的本质

* `caption-side`: 标题位置，默认`top`
  * `top`: 表格之上
  * `bottom`: 表格之下

![caption-side](images/caption-side.png)

## 边框模型

* `border-collapse`: 边框模型，默认`separate`
  * `separate`: 分隔边框模型
  * `collapse`: 合并边框模型

![border-collapse](images/border-collapse.png)

### 分隔边框模型

边框间隔

* `border-spacing`: 单元格边框间隔
  * `x`: 水平与垂直间隔
  * `x y`: 水平间隔、垂直间隔

![border-spacing](images/border-spacing.png)

空单元格处理

* `empty-cells`: 空单元格处理
  * `show`: 显示空单元格的边框和背景
  * `hide`: 不显示空单元格的边框和背景

![empty-cells](images/empty-cells.png)

### 合并单元格模型

![collapse](images/collapse.png)

合并规则

* 表忽略内边距，单元格忽略间隔
* 多个边框相邻时，相互合并，取优先级最大的哪一个边框
  * 边框样式为`hidden`，优先级最高
  * 边框样式为`none`，优先级最低
  * 边框宽度不同，宽度大的优先级高
  * 边框宽度相同，比较边框样式，优先级从高到低`double, solid, dashed, dotted, ridge, outset, groove, inset`
  * 边框宽度、样式相同时，比较边框颜色，优先级从高到低`cell, row, row group, column, column group, table`

## 布局方式

* `table-layout`: 表格布局方式，默认为`auto`
  * `auto`: 自动布局
  * `fixed`：固定布局

![table-layout](images/table-layout)

### 固定布局

* 查找列宽度
* 列宽度为`auto`, 查找首行单元格的宽度
* 首行单元格宽度仍为`auto`, 则自动计算
* 列宽度之和大于表宽度，则表宽度为列宽度之和
* 列宽度之和小于表宽度，则将多余的宽度平均加到每一列上

### 自动布局

* 对于一列中的各个单元格，计算最小和最大单元格宽度
* 对于各列，计算最小和最大单元格宽度
* 表宽度为`auto`，列宽之和为表宽度
* 表宽度不为`auto`，比较列宽之和和表宽度，大的为表宽度

## 对齐

* 水平对齐：`text-align`
* 垂直对齐：`vertical-align`，通过调整单元格的上下内边距来垂直对齐
  * 只有`top, bottom, middle, baseline`四个值，其他值忽略


# 列表与生成内容

## 列表项标志

标志类型

* `list-style-type`: 列表项标志类型，默认为`disc`
  * `none`: 无标志
  * `disc`: 实心圆，无序列表默认类型
  * `circle`: 空心圆
  * `square`: 实心方块
  * `decimal`: 数字，有序列表默认类型
  * `lower-roman`: 小写罗马数字
  * `upper-roman`: 大写罗马数字
  * `lower-alpha`: 小写英文字母
  * `upper-alpha`: 大写英文字母
  * `lower-greek`: 小写希腊字母

![list-style-type](images/list-style-type.png)

图像标志

* `list-style-image`: 列表项图像标志，默认为`none`
  * `none`: 无
  * `url("<url>")`: 图像路径

![list-style-image](images/list-style-image.png)

标志位置

* `list-style-position`: 列表项标志位置，相对于列表项的内容定位，默认为`outside`
  * `outside`: 列表项外
  * `inside`: 列表项内

![list-style-position](images/list-style-position.png)

简写

* `list-style:[list-style-type] [list-style-position] [list-style-image]`: 列表项标志样式

![list-style](images/list-style.png)

## 生成内容

使用`:before`和`:after`伪元素来插入生成内容

### 限制

* 禁止浮动和定位
* 禁止列表样式和表样式
* `display`处理
  * 选择器为块元素，`display`只能为`none, inline, block, marker`, 其它的作为`block`处理
  * 选择器为行内元素，`display`只能为`none, inline`，其它的作为`inline`处理

### 指定内容

* `content`: 生成内容，默认为`normal`，可多种内容拼接
  * `normal`: 正常
  * `<string>`: 文本
  * `url("<url>")`: 外部资源
  * `attr(<identifier>)`: 属性值
  * `open-quote`: `quotes`属性值的开始引号
  * `close-quote`: `quotes`属性值的结束引号
  * `no-open-quote`: 无开始引号
  * `no-close-quote`: 无结束引号

![content](images/content.png)

### 指定引号

* `quotes`: 指定引号对
  * `none`: 无引号对
  * `<string> <string>...`: 一个或多个引号对，后面的为更深层次的引号对

![quotes](images/quotes.png)


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

