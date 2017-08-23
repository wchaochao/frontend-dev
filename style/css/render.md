# 渲染

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
  * 行内非替换元素
* `atomic inline-level box`: 既是`inline-level box`, 而且其作为一个整体受控于`inline formatting context`
  * 行内替换元素，行内块级元素，`inline-table`元素

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
* 计算行框里的各行内级框的高度时，对于行内替换元素、行内块元素、行内表格元素来说，是外边距框的高度，对于行内框来说，是其`line-height`
* 当一个`inline box`超过`line box`的宽度时，它会被分割成多个`boxes`，这些`boxes`被分布在多个`line box`里

#### 实用

* 水平居中
* 垂直居中

### GFC

栅格格式化上下文(`Grid Formatting Contexts`)

### FFC

自适应格式化上下文(`Flex Formatting Contexts`)