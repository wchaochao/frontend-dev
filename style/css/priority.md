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

* 收集元素的样式，将样式按以下三类划分
  * 创作者普通样式、读者普通样式、浏览器默认样式
  * 创作者重要样式
  * 读者重要样式
* 每类按选择器优先级排序
* 同选择器优先级的按样式表优先级排序
* 同样式表优先级的按出现顺序排序
* 排序完后按排序的顺序依次应用样式，样式冲突时后面的样式会覆盖前面的样式和继承的样式