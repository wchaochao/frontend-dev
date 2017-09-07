# 语句

## 变量

### 声明

```
语法：var 变量
解释：声明了一个变量
```

### 赋值

```
语法：变量=值
解释：将右边的值赋给左边的变量
```

### 初始化

```
语法：var 变量=值
解释：声明了一个变量并且把值赋给了变量
```

## 条件语句

### if

```
语法：if(condition){
          statement
     }
解释：condition为true，执行statement
```

### if/else

```
语法：if(condition){
          statement1
     }else{
          statement2
     }
解释：值为true，执行statement1
     值为false，执行statement2
```

### switch

```
语法：switch(值){
          case 值1：
               statement1
          case 值2：
               statement2
          ...
          case 值n:
               statementn
          default：
               statement
     }
解释：值===值1，从statement1开始执行
     值===值2，从statement2开始执行
     ...
     值===值n，从statementn开始执行
     值都不完全等，从statement开始执行
     执行过程中遇到break语句跳出switch，没遇到继续执行下一个case/default中的语句
```

## 循环语句

### while

前循环语句

```
语法：while(condition){
          statement
     }
解释：condition为true，执行statement，并再次判断condition
     condition为false，跳出while循环
```

### do/while

后循环语句

```
语法：do{
          statement
     }while(condition);
解释：相当于
     statement
     while(condition){
          statement
     }
```

### for

```
语法：for(init;condition;next){
          statement
     }
解释：相当于
     init
     while(condition){
          statement
          next
     }
```

### for/in

```
语法：for(var key in obj)
解释：遍历对象及对象的原型链上的所有可枚举的属性
```

## 标签语句

```
语法：label:statement
解释：给statement语句添加label标签
```

## 退出语句

### break

```
语法：break;
     break <label>;
解释：跳出循环或switch语句
     跳出label所在的循环
```

### continue

```
语法：continue;
     confinue <label>;
解释：退出本次循环，开始下一次循环
     退出本次循环，开始label所在的下一次循环

for循环中要先执行next再开始下一次循环
```

## 返回语句

```
语法：return;
     return 值;
解释：退出函数并返回undefined
     退出函数并返回值
```

## with语句

```
语法：with(obj){
         statement
     }
解释：将obj临时压入作用域的前端，statement中查找变量时先查找局部变量再首先查找obj

严格模式下使用with语句会抛出SyntaxError
```

## 错误处理语句

### throw

```
语法：throw value;
参数：value，可为任意值
解释：手动停止执行程序并抛出异常

代码运行过程中发生错误时会自动停止执行并抛出异常
```

### try/catch

```
语法：try{
          try_statement
     }catch(e){
          catch_statement
     }
解释：try_statement未抛出异常，跳过catch语句
     try_statemnet抛出异常，catch捕捉异常e并执行catch_statement
```

### try/finally

```
语法：try{
          try_statement
     }finally{
          finally_statement
     }
解释：try_statement未抛出异常，执行finally_statement
     try_statement抛出异常或有return语句时，先执行finally语句再返回抛出异常或执行return语句
```

### try/catch/finally

```
语法：try{
          try_statement
     }catch(e){
          catch_statement
     }finally{
          finally_statement
     }
解释：try_statement未抛出异常，相当于try/finally
     try_statemnet抛出异常，catch捕获异常，catch/finally也相当于try/finally
```