title: CSS布局(二)
date: 2015-3-26
categories: 前端开发
tags: [CSS，HTML ]

---
```
写作目的：
接上一篇CSS布局（一），内容包括：
1.绝对布局
2.表格布局
```

<!--more-->

绝对布局我们要使用最初的源码，所以还是贴出代码。
```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Starbuzz Coffee</title>
    <link rel="stylesheet" type="text/css" href="starbuzz.css">
  </head> 

  <body>
    <div id="header">
      <img src="images/header.gif" alt="Starbuzz Coffee header image">
    </div>

    <div id="main">
      <h1>QUALITY COFFEE, QUALITY CAFFEINE</h1>
      <p>
        At Starbuzz Coffee, we are dedicated to filling all your  caffeine needs through our 
        quality coffees and teas. Sure, we want you to have a great cup of coffee and a great 
        coffee experience as well, but we're the only company that actively monitors and 
        optimizes caffeine levels. So stop by and fill your cup, or order online with our new Bean 
        Machine online order form, and get that quality Starbuzz coffee that you know will meet 
        your caffeine standards.
      </p>
      <p>
        And, did we mention <em>caffeine</em>? We've just started funding the guys doing all 
        the wonderful research at the <a href="http://buzz.wickedlysmart.com"
        title="Read all about caffeine on the Buzz">Caffeine Buzz</a>.
        If you want the latest on coffee and other caffeine products, 
        stop by and pay them a visit.
      </p>
      <h1>OUR STORY</h1>
      <p>
        "A man, a plan, a coffee bean". Okay, that doesn't make a palindrome, but it resulted
        in a damn good cup of coffee.  Starbuzz's CEO is that man, and you already know his 
        plan: a Starbuzz on every corner.
      </p> 
      <p>In only a few years he's executed that plan and today 
        you can enjoy Starbuzz just about anywhere.  And, of course, the big news this year 
        is that Starbuzz teamed up with Head First readers to create Starbuzz's Web presence,  
        which is growing rapidly and helping to meet the caffeine needs of a whole new set of 
        customers.  
      </p>
      <h1>STARBUZZ COFFEE BEVERAGES</h1>
      <p>
        We've got a variety of caffeinated beverages to choose
        from at Starbuzz, including our 
        <a href="beverages.html#house" title="House Blend">House Blend</a>,
        <a href="beverages.html#mocha" title="Mocha Cafe Latte">Mocha Cafe Latte</a>, 
        <a href="beverages.html#cappuccino" title="Cappuccino">Cappuccino</a>,
        and a favorite of our customers, 
        <a href="beverages.html#chai" title="Chai Tea">Chai Tea</a>.
      </p>
      <p>
        We also offer a variety of coffee beans, whole or ground, for you to
        take home with you.  Order your coffee today using our online
        <a href="form.html">Bean Machine</a>, and take
        the Starbuzz Coffee experience home.
      </p>
    </div>

    <div id="sidebar">
      <p class="beanheading">
        <img src="images/bag.gif" alt="Bean Machine bag">
        <br>
        ORDER ONLINE
        with the 
        <a href="form.html">BEAN MACHINE</a>
        <br>
        <span class="slogan">
            FAST <br>
            FRESH <br>
            TO YOUR DOOR <br>
        </span>
      </p>
      <p>
        Why wait?  You can order all our fine coffees right from the Internet with our new, 
        automated Bean Machine.  How does it work?  Just click on the Bean Machine link, 
        enter your order, and behind the scenes, your coffee is roasted, ground 
        (if you want), packaged, and shipped to your door.
      </p>
    </div>

    <div id="footer">
      &copy; 2012, Starbuzz Coffee
      <br>
      All trademarks and registered trademarks appearing on 
      this site are the property of their respective owners.
    </div>

  </body>
</html>
```
css文件：
```
body { 
  background-color: #b5a789;
  font-family:      Georgia, "Times New Roman", Times, serif;
  font-size:        small;
  margin:           0px;
}
#header {
  background-color: #675c47;
  margin:           10px;
  height:           108px;
}
#sidebar {
  background:       #efe5d0 url(images/background.gif) bottom right;
  font-size:        105%;
  padding:          15px;
  margin:           0px 10px 10px 10px;
}
#main {
  background:       #efe5d0 url(images/background.gif) top left;
  font-size:        105%;
  padding:          15px;
  margin:           0px 10px 10px 10px;
}
#footer {
  background-color: #675c47;
  color:            #efe5d0;
  text-align:       center;
  padding:          15px;
  margin:           10px;
  font-size:        90%;
}
h1 {
  font-size:        120%;
  color:            #954b4b;
}
.slogan { color: #954b4b; }
.beanheading {
  text-align:       center;
  line-height:      1.8em;
}
a:link {
  color:            #b76666;
  text-decoration:  none;
  border-bottom:    thin dotted #b76666;
}
a:visited {
  color:            #675c47;
  text-decoration:  none;
  border-bottom:    thin dotted #675c47;
}
```
---
方法5：实际上在完全解决[CSS布局（一）](http://misok.github.io/2015/03/25/CSS%E5%B8%83%E5%B1%80%EF%BC%88%E4%B8%80%EF%BC%89/#more)提到的问题之前，我们还要介绍一种非浮动技术，那就是绝对定位。利用绝对定位，我们可以指定每个部分的准确位置，从而达到两栏布局。使用绝对定位，要用最初的那个html样式，也就是文章一开始的两个原始代码。

- 添加如下样式：
```
#sidebar{
	position:absolute;
	top:128px;
	right:0px;
	width:280px;
}
#main{
	margin-right:330px;
}
```
结果如下图：
![绝对定位](/img/absolute.png)

如图所示，这样做还是有一些问题：
1. footer部分上移（这个不能用clear解决，因为流元素完全不知道绝对定位元素的存在）

这里要对绝对定位做一些说明：
- 一个元素绝对定位时，浏览器首先要做的是把它从政策流中删除，然后用top left right bottom指定是位置来放置它
- 正常流中的元素不会将其内联元素的内容围绕在绝对定位元素周围
- 绝对位置可以分层放置，用z-index属性
- 绝对定位不一定要指定元素宽度，如果不指定，则默认占满整个宽度。

---
方法6：表格布局

要使用表格布局，就要添加新的元素来提供定位。
修改原始HTML如下：
```
...//这里是header部分
<div id="tablecontainer">
	<div id="tablerow">
		 <div id="main">
		 ...
		 </div>
		 <div id="sidebar">
		 ...
		 </div>
	</div>
</div>
...//这里是footer部分
```
修改css如下：
```
#tablecontainer{
	display:table;
	border-spacing:10px;
}
#tablerow{
	display:table-row;
}
#main{
	display：table-cell;
	删除这里的外边距设置
}
#sidebar{
	display:table-cell;
	删除这里的外边距设置
}
```
以下是最终结果：
![表格布局](/img/table.png)

表格布局终于完美的解决了以上问题，如果觉得main部分还是有点窄，可以给其设置宽度，达到最满意的要求。

但是表格布局也有一些问题，在小屏幕上查看可能体验不是很好。而且有违响应式布局的设计。但是这些我们都能通过别的方法解决。这些需要慢慢去探索。

---
通过以上学习，我们可以很轻松的做出131的布局或者各种别的布局，因为道理都是相通的。
