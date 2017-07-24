# 框架标签

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