title: CSS布局(一)
date: 2015-3-25
categories: 前端开发
tags: [CSS，HTML ]

---
```
写作目的：
接上一篇HeadFirst HTML与CSS读书笔记
这一篇重点说说最近理解的CSS布局
包括：
1.侧边栏浮动布局
2.右紧左松布局
3.冻结布局
4.凝胶布局
```

<!--more-->
要说清楚布局，我们这里借用书上的例子来说。
首先，这是一个咖啡店的主页，这是没有布局之前的正常流网页。
![原始网页](/img/origin.png)
先附上源码：
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

可以看出，这是一个典型的具有header，footer,content以及sidebar的布局。那么我们用css怎么来实现呢。

在这之前，先说说如何浮动元素
1. 给要浮动的元素指定一个id
2. 指定宽度（对于浮动元素必须有宽度）
3. 让它浮动（float：left/right;）

---
方法一：让sidebar浮动，main部分可以随浏览器自由伸缩。
- 要让sidebar浮动在main的右边，我们要先考虑下这几部分之间的顺序。
- 浮动是什么意思呢，浮动是把元素从正常文档流中拿出，让他尽可能向一个方向偏离。他前面和后面的块元素会当他不存在一样，继续按顺序在正常流中摆放，而块元素中的内联元素会留意浮动元素的边界。
- 所以让我们来想想，假如按照现在HTML文档中的顺序，浏览器先摆放header，因为是div元素，占满一行，再换行摆放main,main也一样是div元素，占满一行，那么到sidebar的时候浏览器发现他是个向右浮动元素，那么浏览器会在main下面把sidebar浮动在右边，而footer继续正常摆放，那看上去就像这样：
![错误浮动](/img/float-wrong1.png)
这显然不是我们想要的效果，所以聪明的你肯定也想到了，我们想让sidebar在header下面浮动，就要把它紧跟header放置。改动我们的代码，调整位置，并在#sidebar中添加：
```
#sidebar{
	float：right;
	width:280px;
	}
```
现在我们看到的网页就像这样：
![正确浮动](/img/float-ok.png)
调整浏览器窗口大小，让它最大化，情况就变成了这样：
![新问题](/img/footer-wrong.png)
上面的网页现在有两个问题：
1. main部分还是平铺的，main里面的内容（内联元素）是围绕在sidebar周围的，实际上这时候main整个部分是在sidebar下面的，我们怎么让它们看上去是显示在一排的呢，很简单，给main加上右侧外边距，让它的大小至少等于sidebar的宽度。
2. 页脚在全屏的时候上移，这也不是我们想要的效果，这里我们要用到一个新属性，clear（清除浮动）。clear的意思就是：当元素流入页面时，在这个元素的左边或者右边或者两侧不允许有浮动内容。如果有，则会把元素下移，直到没有浮动的地方。
所以，上面两个问题我们再加两个样式就搞定：
```
#main{
	margin-right:330px;
}
#footer{
	clear:right;
}
```
最后完成的网页如图所示：
![完成1](/img/float-finish.png)

虽然看上去还不错，但这种方法有两个缺点：
1. 随着浏览器大小的变化，main部分和sidebar不一样高，所以会有留白
2. 如果在小屏或者手机或者其他浏览器宽度小于一定值时浏览，sidebar部分会在main的上面，这可能对用户来说并不是一件好事，我们应该首先显示重要信息。

---
方法2：右紧左松记忆法，即让main部分浮动，sidebar随浏览器调整大小（可以解决上面第二个问题）

- 调整HTML为最初的顺序
- 添加如下代码：
```
#main{
	width:420px;
	float:left;
}
#sidebar{
	margin-left:470px;
}
#footer{
	clear:left;
}
```
效果如下：
![方法2](/img/float-main.png)

可以看出，上面方法还是有两个问题：
1. main部分和sidebar不一样高
2. sidebar在浏览器足够宽的时候会显得过于扩展。

---
方法3：在上面这个例子中，布局自动扩展给我带了了一些小问题，这个时候我们可能希望锁定布局，当用户调整屏幕大小时，让设计保持原样，这称为冻结布局。

- 首先，给HTML中的四部分最外层加上一个新的div,即用一个div把header，main,sidebar,footer包裹起来，id为allcontent
- 给allcontent添加样式
```
#allcontent{
	width: 800px;
	padding-top:10px;
	padding-bottom:10px;
	background-color:#675c47;
}
```
注意：此处添加的两项是在之前方法二的基础上添加
现在网页是下面这样：
![冻结布局](/img/frozen.png)

可以看出：main和sidebar两部分的相对大小不再随浏览器变化，但是右边有大量留白。

---
方法4：解决上述留白问题，我们使用凝胶布局。这种布局会锁定页面中内容区的宽度，但会将内容在浏览器居中。

- 我们只需要在方法三的基础上添加如下样式：
```
#allcontent{
	margin-left:auto;
	margin-right:auto;
}
```
现在网页是这样：
![凝胶布局](/img/jello.png)

可以看出，已经比以前好多了。但是还是没有解决sidebar和main没对齐的问题。

---
待续。。。