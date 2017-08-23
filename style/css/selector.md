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