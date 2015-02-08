title: 浅谈CSS/jQuery/JS选择器（二）
date: 2015-2-7
categories: 前端开发
tags: [CSS, JS, jQuery]

---
写作目的：
```
想要操作DOM中的元素，最基本的是把他们准确的选择出来。
而选择的办法有很多种，要为元素设置样式，可以通过css选择器来选择。
要实现程序逻辑，可以用JS把元素选择出来，也可以用更强大的jQuery选择器。
上一节我们介绍了CSS选择器，这一节我们来看jQuery选择器。
jquery使用的就是CSS选择器，不过在CSS的基础上做了一些小小的扩展。
```
<!-- more -->

##jQuery选择器

![Alt text](/img/selector_jquery1.png)
![Alt text](/img/selector_jquery2.png)

其中，[attribute!=value],  :checkbox ,  :button，  :contains(text)等为jQuery的扩展。要看详细信息，请查阅犀牛书第六版p567.

---
###详解
还是来看一下具体用法
```
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title>用来测试各种写法的选择器</title>
    <link href="selector.css" type="text/css" rel="stylesheet">
    <script src="jquery.min.js"></script>
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
<script src="selector.js"></script>
</body>
</html>
```
要使用jquery库，我们要引库。以下为css代码。为了方便和css选择器比较，我们还是使用上一篇文章的样式。
```
* :not(body) {
    margin: 3px;
    padding: 10px;
    border: solid 2px black;
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
下面是jQuery代码
```
$("div p").text("我被Jquery选中了");
$("div>p").css("color","red");
$("div+p").css("border","dotted 3px red")
```
最后，让我们来对比下结果：

![Alt text](/img/result.png)

div p的CSS样式为红色边框，而jquery让现实文字为“我被jquery选中了”，完全吻合。
div>p的CSS样式为天蓝色背景，jquery让显示文字变为红色，完全吻合。
div+p的CSS样式为亮绿色背景，jquery给边框加了圆角。完全吻合。

这里不再演示其它选择器，用法都差不多，理解了这些，能准确高效的选出元素，我们才能顺利的往下。


