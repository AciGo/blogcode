---
title: Js 笔试真题
---

### 前言

以下一些题,均来各大小公司现场的真实笔试题

### 第 1 题. 变量声明不会提升

直接写出下边程序的输出结果

```
console.log(foo);
var foo = "test"
```

::: details 点击即可查看
答案: undefined

解析: 变量`foo`,相当于只有`var foo`;但是却没有赋值,所以值是`undefined`,并且变量的声明并不会提升,只有函数声明会提升
:::

### 第 2 题 词法作用域

写出下面一段代码输出结果

```
var temp = 123;
function f() {
  console.log(temp);
  if(false) {
    var temp = 456
  }
}
f();
```

::: details 点击即可查看
答案: `undefined`

解析: 在没有调用 f 函数时,`temp`的值是`123`,在查找变量时,它先会从函数内沿着作用域链逐级向外进行查找,若有则会返回,若无,则会返回`undefined`,

使用`var`声明的变量并不会有块级作用域,在`if`语句块声明赋值的变量,相当于是裸露的,因为在 f 函数内,变量先使用,但是未赋值,所以是`undeifined`

:::

### 第 3 题 块级作用域

写出下面一段代码输出的结果

```
var temp = 123;
function f() {
  console.log(temp);
  if(true) {
     console.log(temp);
     let temp = 456;
  }
}
f();
```

::: details 点击即可查看详情
答案: 123,然后报错`ReferenceError: Cannot access 'temp' before initialization`,无法在初始化之前访问变量

解析: `let`声明的变量是有块级作用域的,不能重复声明定义
:::

### 第 4 题-Promise 执行问题

写出下面一段程序的输出的结果

```
new Promise(resolve => {
    console.log(1);
    setTimeout(() => console.log(2),0)
    Promise.resolve().then(() => console.log(3))
    resolve();
}).then(() => console.log(4))
console.log(5)
```

::: details 点击可查看详情
答案: 1 5 3 4 2

解析:
:::

### 第 5 题-"123456789".match(/\d{3,5}?/g)的结果是什么?

### 第 6 题-编程将字符串"2018-11-03"转换成"11/03/2018"

### 第 7 题-如果浏览器不支持 bind 函数,实现一个函数让其兼容

### 第 8 题-简单实现一下对象的深拷贝

### 第 9 题-实现一个数组的快速排序
