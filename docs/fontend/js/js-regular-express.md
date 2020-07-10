---
title: Js正则表达式
---

## 快速导航

<TOC />

## 验证 HTTP-URL 的正确性

校验一用户输入 url 的正确性

<regular-regExpress :label="`输入链接网址`"  :input="`https://coder.itclan.cn`" :btntext="`立即校验`" :type="`url`"/>

::: details 点击即可查核心代码

```js{1}
let regUrl = /^(?:http(s)?:\/\/)?[\w.-]+(?:\.[\w\.-]+)+[\w\-\._~:/?#[\]@!\$&'\*\+,;=.]+$/;

let testUrl = 'https://coder.itclan.cn/';
function checkUrl(str) {
  if (regUrl.test(str)) {
    // url正确
  } else {
    // url不正确
  }
}

console.log(checkUrl(testUrl)); // https://coder.itclan.cn/
```

:::

## 校验手机号码的正确性

校验用户输入手机号码的正确性

<regular-regExpress :label="`输入手机号`" :type="`phone`" :input="13801134168" :btntext="`立即校验`" />

- **正则中的小/圆`()`括号**

::: details 点击即可查看手机号码核心代码

```js {2}
function checkPhone(str) {
  if (!/^1(3|4|5|6|7|8|9)\d{9}$/.test(str)) {
    // 手机号码11位,第一位开头是1，,第二位可能是3/4/5/7/8等的任意一个,\d表示数字[0-9]的9位，总共加起来11位结束
    alert('您输入的手机号码有误,请重新输入');
    return false;
  } else {
    // 输入的手机手机号码正确
    console.log(str);
  }
}
let testPhone = 13801134168;
checkPhone(testPhone); // 13801134168
```

:::

- **正则中的中括号**

这是另外一种正则写法

::: details 点击即可查看手机号码核心代码

```js
function checkPhone(str) {
  if (!/^1[3456789]\d{9}$/.test(str)) {
    alert('您输入的手机号码有误,请重新输入');
    return false;
  } else {
    // 输入的手机手机号码正确
    console.log(str);
  }
}
let testPhone = 13801134168;
checkPhone(testPhone); // 13801134168
```

:::
上面两种写法都可以实现手机号码的校验,其中小括号`()`就是括号内`(3|4|5|6|7|8|9)`看成一个整体 ,中括号`[3456789]`就是匹配括号内的其中一个”

在正则里面的中括号`[]`只能匹配其中一个，如果要匹配特定几组字符串的话，那就必须使用小括号`()`加或`|`

符号`|`在中括号里面也是一个字符，并不代表或

`[3456789]`匹配`3`或者`4`或者`5`或`6`者`7`或`8`或`9`，而`(3456789)`只匹配`3456789`整个，若要跟前面一样可以加或`(3|4|5|7|8|9)`。表示匹配`3`或`|`或者`4`或者`|`或者`5`或`|`者`7`,或`8`或`|`或`9`

而`(34|56|789)`能匹配`34`或者`56`或`789`

在如今的手机号中,第 1 位是数字 1,第 2 位则有`[3,4,5,7,8]`之间的任意一数,第三位则是`[0-9]`之间的数,但是这个第 2 位代码可能随时增加一个,比如以`16`开头呢？`19`开头呢？

在上面的示例代码中,已经把`16`,`19`考虑进去了的,所以大胆放心的用吧,如果不考虑`16`,或者`19`

::: details 点击即可查看,不考虑 16,19

```
var regPhone = /^1[3|4|5|7|8][0-9]{9}$/; //验证规则,总共是11位

var phoneNum = '13801134168'; //手机号码

var flag = regPhone.test(phoneNum); //true
```

如果嫌验证麻烦,还可以不验证第二位规则
::: details 忽略手机号第 2 位数的限制

```
var regPhone = /^1[0-9]{10}$/;
```

:::

## 校验座机号码的正确性

校验座机号码的正确性,虽然座机现在验证的情况比较少,更多的是移动端手机号,用于接收短信接收验证码之类的

::: details 点击即可查看座机号码正则

```js
function checkTel(str) {
  if (!/^(\(\d{3,4}\)|\d{3,4}-|\s)?\d{7,14}$/.test(str)) {
    alert('固定电话有误，请重填');
    return false;
  } else {
    // 固定电话正确
    console.log(str);
  }
}

let tel = `010-60440426`;
console.log(checkTel(tel)); // 010-60440426
```

:::

<footer-FooterLink :isShareLink="true" :isDaShang="true" />
