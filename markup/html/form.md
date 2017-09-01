# 表单标签

## form

```html
<form action="form_action.asp" method="get">
  <p>First name: <input type="text" name="fname" /></p>
  <p>Last name: <input type="text" name="lname" /></p>
  <input type="submit" value="Submit" />
</form>
```

属性

* `name`: 表单名称
* `action`: 表单提交到哪
* `method`: 表单提交的`HTTP`方法，默认`GET`
* `target`: 表单提交的目标，默认`_self`
* `accept-charset`: 表单数据的编码方式，默认为页面编码
* `enctype`: 表单数据的类型，默认`application/x-www-form-urlencoded`
* `novalidate`: 禁止默认验证

## fieldset

分组

```html
<fieldset>
  <legend>Personal information:</legend>
  First name:<br>
  <input type="text" name="firstname" value="Mickey">
  <br> Last name:<br>
  <input type="text" name="lastname" value="Mouse">
  <br><br>
  <input type="submit" value="Submit">
</fieldset>
```

属性

* `name`: 名称

## label

```html
<label for="male">Male</label>
<input type="radio" name="sex" id="male" />

<label><input type="radio" name="sex" /></label>
```

属性

* `for`: 将`label`绑定到哪个表单元素

## input

属性

* `type`: 类型
* `name`: 名称
* `value`: 初始值
* `autofocus`: 自动获取焦点
* `placeholder`: 输入提示
* `readonly`: 只读
* `disabled`: 禁用
* `checked`: 选中
* `required`: 必填
* `min`: 最小值
* `max`: 最大值
* `maxlength`: 允许输入的最大长度
* `minlength`: 允许输入的最小长度

### 输入框

```html
<input type="text" name="text" />
```

### 密码框

```html
<input type="password" name="password" />
```

### 单选框

```html
<input type="radio" name="sex" value="male" checked>Male
<br>
<input type="radio" name="sex" value="female">Female
```

### 复选框

```html
<input type="checkbox" name="vehicle" value="Bike" checked>I have a bike
<br>
<input type="checkbox" name="vehicle" value="Car">I have a car
```

### 文件框

```html
<input type="file" name="file">
```

### 隐藏框

```html
<input type="hidden" name="hidden">
```

## select

```html
<select name="cars">
  <option value="volvo">Volvo</option>
  <option value="saab" selected>Saab</option>
  <option value="fiat">Fiat</option>
  <option value="audi">Audi</option>
</select>
```

select属性

* `name`: 名称
* `autofocus`: 自动获取焦点
* `disabled`: 禁用
* `required`: 必选
* `multiple`: 多选
* `size`: 可见的选项数目

option属性

* `value`: 选项值
* `selected`: 选中

## textarea

```html
<textarea name="message" rows="10" cols="30">
The cat was playing in the garden.
</textarea>
```

属性

* `name`: 名称
* `autofocus`: 自动获取焦点
* `placeholder`: 输入提示
* `readonly`: 只读
* `disabled`: 禁用
* `required`: 必填
* `maxlength`: 最大字符数
* `rows`: 可见行
* `cols`: 可见列

## button

```html
<button type="button">普通按钮</button>
<button type="submit">提交按钮</button>
<button type="reset" disabled>重置按钮</button>

<!--input-->
<input type="button" value="普通按钮"/>
<input type="submit" value="提交按钮"/>
<input type="reset" value="重置按钮" disabled/>
```

属性

* `type`: 按钮类型，默认为`button`
  * `button`: 普通按钮
  * `submit`: 提交按钮
  * `reset`: 重置按钮
* `disabled`: 禁用