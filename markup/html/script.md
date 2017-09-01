# 脚本标签

可放置在`head`和`body`中

```html
<script type="text/javascript">
  console.log('javascript');
</script>

<script src="myscript"></script>

<noscript>不支持脚本时显示</noscript>
```

* `type`: 脚本的`MIME`类型, 默认为`text/javascript`
* `src`: 脚本文件地址
* `async`: 异步加载脚本文件
* `defer`: 延长执行脚本文件，在文档`DOMContentLoaded`事件前执行
