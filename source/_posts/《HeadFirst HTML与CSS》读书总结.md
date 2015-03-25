title: 《HeadFirst HTML与CSS》读书总结
date: 2015-3-25
categories: 前端开发
tags: [CSS，HTML ]

---
```
写作目的：
看来阿里那个学长说的不错，每读完一本书都会有新的收获。
之前HTML与CSS都是跟着网站视频学的，没有系统的去看这方面的书。
后来选了HeadFirst HTML与CSS，读完对标签的正确使用，页面布局的选择等都有了一个全新的认识。
这里写下这本书中一些我认为重要的地方。
```

<!--more-->
##HTML部分
HTML:（HyperText Markup Language超文本标记语言)
其中，标记语言就是来告诉浏览器文本的结构是怎样的。而超文本是因为一个HTML页面可能会连接到WEB的其他资源和页面。

###q和blockquote
（这里所有标记都不加尖括号，因为Markdown会自动识别语义）
  - 如果想在段落中，即把一个引用放在现有的文字中，使用q，如果想引用一段或者多段文字或者希望引用在页面上自成一段使用blockquote。
  - 一般q会表现为一个内联元素，浏览器会为q中的内容加上引号。
  - blockquote表现为一个块元素，浏览器会让他缩进成块显示
  - 但是注意，有时候不同浏览器对他们的细节处理不同。我们使用这些具有语义的元素，他们的外部表现并不重要，毕竟外部表现可以用css去改变去设置，但是我们在html中使用，是为了告诉浏览器文本的结构，我是一个引用。

通过这个例子，还有一点需要补充，一个元素的语义其实很重要，我们不能为了得到一个斜体就去使用em,如果是结构需要，我们才使用em,毕竟em的外部表现是可以设置的。所以，好的设计是结构与表现分离，让html去专注结构，表现交给css。
###特殊的img
- 是一个void元素，是一个内联元素
- 可以设置width/height;
-  默认的，img元素在屏幕占据的空间与其图片的实际像素一致，除非CSS有设置或者自身的width/height HTML 属性有设置
- 如果img标签的包裹元素为也为inline元素，则img的边界可以超出其直接父元素的边界，直到自己的宽、高达到最大或者设定值为止，而且文档流中img的兄弟元素也不能遮盖住img。最常见的就是a里面包含的img
- 所以从行为上看,img元素作为替换元素，有着类似于Inline-block的行为，尽管在SPEC里面，他的确是一个inline元素

所谓void元素，就是在两个标签之间没有内容的元素。所以只有一个标记组成，比如br。

- 从上面一条我们得到一个信息，内联元素不能设置宽高（这个博主以前真不知道，还犯过这些错误）

###a元素
- 使用id属性为a创建目标：也就是说，点击a元素后让他跳到拥有此id的位置。这个非常常见的就是浏览网站时的回到顶部。
```html
<a href="index.html#top">回到顶部</a>
```
- a元素的href属性可以使用相对路径或者URL来连接其他WEB页面，对于同一网站中的其他页面，我们最好使用相对链接，对外部链接才使用URL
- a元素中使用title属性提供链接的一个描述，便于访问
- 使用target属性在新的窗口打开链接（但这个属性在不同设备可能会有问题）
   
###img元素
- 使用alt属性为图片提供候选格式（不同浏览器对此属性的表现不同，但是在千奇百怪的web世界，提供一个alt，在图片挂掉的时候让别人知道你这个图片是干嘛的）
- 图片可以设置宽高，也提供宽高属性，但是这个宽高属性我们应该正确来使用，浏览器下载图片之前是不知道图片大小的，除非我们显式告诉它，否则浏览器可能会在下载图片重新调整布局，这时候我们可以使用宽高属性。但是如果是想用合适的大小来显示图片，最好还是使用css(两个都提供时，会以css中的为准)。并且如果我们使用属性来缩放图片时，浏览器在缩放图片使之适应页面大小之前，还是要获取整个大图像。
- 一般来讲，图片是最大宽度应该小于800px.

###W3C有HTML页面和CSS验证工具
- html:http://validator.w3.org/
- css:http://jigsaw.w3.org/css-validator/

---

##CSS部分
- 一般有个原则，不使用a元素的text-decoration属性，而用border-bottom
- HTML5中，link标签的type属性变成可选
- 加载自定义字体的方法：@font-face
```
@font-face{
	font-family:"Emblema One;
	src: url("http://xxxxxxxxxxxxxxxx.woff");
}
body{
	font-family:"Emblrma One", sans-serif;
}
```
以上为使用方法
这种web字体的缺点是，加载慢，移动设备和小型设备不支持

- 上面提到的@技术为内置CSS规则，类似的还有@import和@media
  - @import允许导入其他CSS文件
  - @media允许创建特定于某些媒体类型的CSS规则，比如手机，打印机等等。

-  h1-h6字体大小为默认字体大小的200%，150%，120%，100%，90%，60%。而浏览器默认字体大小一般为16px
- font-style:italic,表示文本风格为斜体
- 颜色中十六进制码中的每一位都相同（例如#111111），则这些颜色全都是灰色，从深灰一直到浅灰
- 内边距是内容周围增加额外空间的，外边距提供元素之间的距离。margin是用来提供更多可见空间，不能对margin设置颜色，也不能增加装饰。
- 类名以字母开头，id可以以一个数字或者字母开头。id和类名都可以包含字母、数字和_字符
- 媒体查询的CSS可以有两种写法。
 - 一种用link引入，link标签中加上media属性，指明是试用那种媒体
 - 另外一种是放在同一个CSS文件中，用@media规则，把不同规则放在对应屏幕@media下面，通用规则放在最后
```
<link type="text/css" rel="stylesheet" href="xxx.css" media="screen and (min-width: 481px)">
<link type="text/css" rel="stylesheet" href="xxxx.css" media="screen and (max-width: 480px)">
<link type="text/css" rel="stylesheet" href="xxx.css" media="print">
@media screen and (min-device-width:481px){
	#guarantee{
			xxxxxxx;
	}
}
@media screen and (max-device-width:480px){
	#guarantee{
			xxxxxxx;
	}
}
```
- div元素内边剧和外边距默认为0
- 一个块元素的默认宽度是auto，则其会延伸占满可用的空间
- text-align属性只能在块元素上设置，对块元素中的所有内联内容对齐，如果在内联元素上使用，则不起作用。
- div p选择器是子孙选择器，注意子孙儿子，即div的所有p子孙，div>p是直接儿子选择器
- line-height（行高）可以使用数字，表示其行高是自己字体大小的几倍
```
#xxx{
line-height:1;
}
```
- 设置a元素行为时，按如下顺序，：link,:visited,:hover,:focus,:activ
- 最后一个重要的问题，css布局，我们放在下一篇吧。