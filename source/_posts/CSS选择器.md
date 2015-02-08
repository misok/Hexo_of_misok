title: 浅谈CSS/jQuery/JS选择器（一）
date: 2015-2-4
categories: 前端开发
tags: [CSS, JS, jQuery]

---
写作目的：
```
想要操作DOM中的元素，最基本的是把他们准确的选择出来。
而选择的办法有很多种，要为元素设置样式，可以通过css选择器来选择。
要实现程序逻辑，可以用JS把元素选择出来，也可以用更强大的jQuery选择器。
```
<!-- more -->
---
##CSS选择器

---
###概览

![Alt text](/img/css_selector.png)
![Alt text](/img/css_selector2.png)

---
###详解

---
####div p && div>p && div+p

以上是所有css选择器的用法。其中有一些容易混淆，我们来看下面几个例子就会明白其中区别。
```html
<!-- 这是HTML代码 -->
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title>用来测试各种写法的选择器</title>
    <link href="selector.css" type="text/css" rel="stylesheet">
</head>
<body>
    <h1 class="navbar">测试各种选择器 这是HI</h1>
    <p>选择器有很多种P</p>
    <div>DIV
        <p>P</p>
        <div>DIV
            <p>P</p>
            <h2>h2</h2>
        </div>
        <div>DIV</div>
        <p>p</p>
        <p>P</p>
    </div>
    <div>DIV<h1>h1<p>p</p></h1></div>
    <div>DIV<p>P</p></div>
    <p>p</p>
</body>
</html>
```
以上是html代码
```css
/*这是CSS代码*/
* :not(body) {
    margin: 3px;
    padding: 10px;
    border: solid 1px black;
}
div p{
    border-color: red;
}
div > p{
    background-color: aquamarine;/*天蓝色*/
}
div + p {
    background-color: greenyellow;
}
```
以上为CSS样式，为了便于观察，我们给所有除了Body的元素全部加上了边框

---
用div p选择所有div 元素内部的p元素，结果如下图：
![Alt text](/img/div p.png)

这是div > p的结果，我们把它的背景色设置为浅蓝，结果如下：
![Alt text](/img/父元素.png)
最后，我们来看div + p的结果：
![Alt text](/img/紧跟.png)

通过例子，以上三个选择器的区别一目了然。

---
####:first-child && :first-of-type
这两个也是存在细微差别的，看下面例子：
```
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title>用来测试各种写法的选择器</title>
    <link href="selector.css" type="text/css" rel="stylesheet">
</head>
<body>
    <ul>ul
       <li>li
        <ol>ol
            <li>li</li>
            <li>li</li>
            <li>li</li>
        </ol>
    </li>
    <li>li
        <ol>ol
            <li>li</li>
            <li>li</li>
        </ol>
    </li>
    <li>li</li>
    <li>li</li>
   </ul>
   <ul>ul
    <li>li</li>
    <li>li</li>
    <li>li</li>
   </ul>
</body>
</html>
```
css样式如下：
```
* :not(body) {
    margin: 3px;
    padding: 10px;
    border: solid 2px black;
}
ul,ol {
    list-style: none;
}

li:first-child {
    border-color: yellow;
}
li:first-of-type {
    background-color: pink;
}
```
结果如下：
![Alt text](/img/first.png)

**注意：这种选择器前面的元素必须紧跟分号，不然选出来的就不是我们想要的结果。即： li:first-child**

---