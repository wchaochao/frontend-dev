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

## 系统字体

* `caption`: 标题控件使用的字体样式，如按钮和下拉控件
* `small-caption`: 标题小控件的标签使用的字体样式
* `icon`: 图标标签使用的字体样式，如文件夹、文件图标
* `menu`: 下拉菜单和菜单列表使用的字体样式
* `message-box`: 对话框使用的字体样式
* `status-bar`: 状态了使用的字体样式

## 长度

### 绝对长度

* `cm`: 厘米
* `mm`: 毫米
* `in`: 英寸，`2.54cm`
* `pt`: 点，印刷单位，`1/72in`
* `pc`: 派卡，印刷单位，`12pt`

### 相对长度

* `px`: 像素
* `em`: 字体大小，相对父元素的字体
* `rem`: 字体大小，相对根元素的字体
* `ex`: 小写`x`的高度
* `%`: 百分比，相对父元素的字体

## 颜色

* `颜色名`：`aqua, black, blue, fuchsia, gray, green, lime, maroon, navy, olive, orange, purple, red, silver, teal, white, yellow`等147种颜色
* `十六进制颜色`：`#RRGGBB`, RR(红色)、GG(绿色)、BB(蓝色), 值`00~FF`之间，`#rrggbb`形式的十六进制颜色可简写为`#rgb`
* `RGB颜色`: `rgb(red, green, blue)`，值`0~255`或`0% ~100%`之间
* `RGBA颜色`: `rgba(red, green, blue, alpha)`, `alpha`为不透明度，值`0~1`之间
* `HSL颜色`：`hsl(hue, saturation, lightness)`, hue(色调)(0~360)(红-绿-蓝), saturation(饱和度)(0%~100%)(灰-全彩), lightness(亮度)(0%~100%)(黑-白)
* `HSLA 颜色`: hsla(hue, saturation, lightness, alpha)
* `currentColor`: 当前文本颜色

## URL

* `绝对URL`：`<protocol>://<user>:<password>@<host>:<port>/<path>?<query>#<hash>`
* `相对URL`：`<path>?<query>#<hash>`

## 关键字

* `inherit`: 继承父元素的样式计算值，伪元素继承宿主元素的样式计算值

## calc()

* `calc(expression)`: 使用`+, -, *, /`计算长度，可各种长度单位混合运算，运算符左右要有空格