# 图片标签

## 格式

* `BMP`: 无损的、既支持索引色又支持直接色的点阵图，文件较大
* `GIF`: 无损的、采用索引色的点阵图，文件小，支持动画和透明，只存在256种颜色
* `JPEG`: 有损的、采用直接色的点阵图，色彩丰富，适合存储照片
* `PNG-8`: 无损的、采用索引色的点阵图，GIF格式的替代者，动画效果较差
* `PNG-24`: 无损的、采用直接色的点阵图，支持透明，文件比`JPEG`大
* `SVG`: 无损矢量图，适合Logo、Icon

## 图片

```html
<img src="url" alt="图片加载失败时显示的文字">
```

属性

* `src`: 图片地址
* `alt`: 替换文本
* `width`: 图片宽
* `height`: 图片高
* `usemap`: 图片映射

## 图片映射

```html
<img src="url" alt="替换文本" usemap="#map">

<map name="map" id="map">
  <area shape="形状" coords="坐标" href="url" alt="替换文字">
</map>
```

area属性

* `shape`: 区域形状
  * `rect`: 四边形
  * `circ`: 圆
  * `poly`: 多边形
* `coords`: 区域坐标
* `href`: 链接地址
* `target`: 链接目标
* `alt`: 替换文本