# 结构

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Document</title>
</head>
<body>

</body>
</html>
```

## 注释

```html
<!--注释-->
```

## DOCTYPE或doctype

文档类型声明，指定`html`版本

### HTML5

```html
<!DOCTYPE html>
```

### HTML 4.01 Strict

不包括展示性的和弃用的元素，不允许框架集

```html
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
```

### HTML 4.01 Transitional

包括展示性的和弃用的元素，不允许框架集

```html
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
```

### HTML 4.01 Frameset

包括展示性的和弃用的元素，允许框架集

```html
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Frameset//EN" "http://www.w3.org/TR/html4/frameset.dtd">
```

### XHTML 1.0 Strict

不包括展示性的和弃用的元素，不允许框架集，以格式正确的`XML`来编写标记

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
```

### XHTML 1.0 Transitional

包括展示性的和弃用的元素，不允许框架集，以格式正确的`XML`来编写标记

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
```

### XHTML 1.0 Frameset

包括展示性的和弃用的元素，允许框架集，以格式正确的`XML`来编写标记

## html

文档的根元素，指定文档为`HTML`

* `xmlns`: 指定文档的命名空间，默认`http://www.w3.org/1999/xhtml`

## head

文档头部，描述文档的信息

### title

页面标题

```html
<title>页面标题</title>
```

### meta

指定页面的描述、关键词、作者、最后修改时间以及其他元数据

```html
<meta name="author" content="Lxxyx,841380530@qq.com">
<meta name="description" content="Free Web tutorials on HTML, CSS, XML" />
<meta name="keywords" content="HTML, CSS, XML" />
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="robots" content="none">
<meta name="generator" content="Sublime Text3">
<meta http-equiv="content-Type" content="text/html;charset=utf-8">  <!--旧的HTML，不推荐-->
<meta charset="utf-8"> <!--HTML5设定网页字符集的方式，推荐使用UTF-8-->
<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1"/>
<meta http-equiv="cache-control" content="no-cache">
<meta http-equiv="expires" content="31 Dec 2008">
<meta http-equiv="refresh" content="2;URL=http://www.lxxyx.win/">
<meta http-equiv="Set-Cookie" content="User=Lxxyx; path=/; expires=Sunday, 10-Jan-16 10:00:00 GMT">
```

属性

* `content`: 定义与`http-equiv`或`name`属性相关的元信息
* `name`: 把`content`属性关联到一个名称
  * `author`: 作者
  * `description`: 描述
  * `keywords`: 关键字
  * `viewport`: 窗口
  * `robots`: 搜索引擎爬虫的索引方式
  * `generator`: 网页制作软件
* `http-equiv`: 把`content`属性关联到`HTTP`头部
  * `content-Type`: 内容类型
  * `X-UA-Compatible`: 采取何种版本渲染当前页面
  * `cache-control`: 缓存方式
  * `expires`: 网页到期时间
  * `refresh`: 自动刷新并指向某页面
  * `Set-Cookie`: cookie设定

### base

页面链接的相对地址和默认目标

```html
<base href="http://www.w3school.com.cn/images/" />
<base target="_blank" />
```

### link

外部资源

```html
<link rel="stylesheet" type="text/css" href="mystyle.css" />
<link rel="icon" type="image/x-icon" href="favicon.ico">
```

属性

* `rel`: 当前文档与外部资源的关系
  * `stylesheet`: 样式表
  * `alternate stylesheet`: 候选样式表，供用户选择
  * `icon`: 图标
* `type`: 外部资源的`MIME`类型
* `href`: 外部资源的地址
* `media`: 媒体类型

### style

页面样式

```html
<style type="text/css">
  body {background-color:yellow}
  p {color:blue}
</style>
```

属性

* `type`: 样式表的MIME类型，默认`text/css`

## body

文档主体，包含文档的所有内容

### 常见内容

* 文本
* 超链接
* 图片
* 列表
* 表格
* 表单
