# 链接标签

## 链接

```html
<a href="url">链接</a>
```

属性

* `href`: 链接的地址
  * `<protocol>://<user>:<password>@<host>:<port>/<path>?<query>#<hash>`: 链接到某个地址的某个锚点
  * `mailto:<email>`: 发送邮件
  * `#`: 跳转到页面顶部
  * `javascript:void(0);`: 不跳转
* `target`: 链接文档在何处显示，默认本页面显示
  * `_self`: 本页面显示
  * `_blank`: 新页面显示
  * `_<frame>`: 指定框架显示
  * `_parent`: 父框架显示
  * `_top`: 顶层框架显示

## 锚点

```html
<a name="tip">锚点</a>
<a href="#tip">跳转到tip锚点或id="tip"的地方</a>
```