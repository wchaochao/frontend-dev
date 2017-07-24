# 表格标签

```html
<table>
  <caption>表格标题</caption>
  <thead>
    <tr>
      <th>列1</th>
      <th>列2</th>
      <th>列3</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>单元格1</td>
      <td>单元格2</td>
      <td>单元格3</td>
    </tr>

    <tr>
      <td>单元格4</td>
      <td>单元格5</td>
      <td>单元格6</td>
    </tr>
  </tbody>

  <tfoot>
    <tr>
      <th>列1</th>
      <th>列2</th>
      <th>列3</th>
    </tr>
  </tfoot>
</table>
```

* `table`: 表格
  * `width`: 宽度
  * `border`: 边框
  * `cellpadding`: 单元格内间距
  * `cellspacing`: 单元格外间距
* `caption`: 表格标题
* `thead`: 表头
* `tbody`: 表格主体，可多个
* `tfoot`: 表注
* `tr`: 行
* `td/th`: 单元格/表头单元格
  * `colspan`: 跨列
  * `rowspan`: 跨行