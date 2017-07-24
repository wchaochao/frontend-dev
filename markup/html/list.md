# 列表标签

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
