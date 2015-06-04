title: css3学习笔记
date: 2015-6-2 
categories: 前端开发
tags: [CSS3]

---
```
写作目的：css3是最新版本的css,除了完全向后兼容，css3的新特性极大推动了css在开发中的作用。
本文总结了css3新特性的一些主要内容。包括：
1. 选择器
2. 边框相关
3. 颜色
4. text
5. 背景相关
6. transformation（变换）
7. animation
8. 多列布局
9. 用户接口（resize和offeset）
10. 媒体查询和响应式
11. 盒模型
```
<!-- more -->

**css3向前兼容需要浏览器前缀**       
 
 前缀           | 浏览器
:-----------    | -----------:
 -webkit        |           chrome safari
 -moz           |   firefox
 -ms            |   IE
 -o             |   opera
---
##选择器
- 属性选择器（在css2的基础上增加了三个属性选择器）
  - E[ att^ = 'val' ] :选择匹配元素E，且E元素定义了属性att，且属性值以val开头的任何字符串
  - E[ att$ = 'val' ] :选择匹配元素E，且E元素定义了属性att，且属性值以val结尾的任何字符串
  - E[ att* = 'val' ] :选择匹配元素E，且E元素定义了属性att，且属性值任意位置包含了val
- 伪类选择器
  - ：root :匹配根元素（在HTML中即为<html>）
  - ：not :否定选择器
  - ：empty： 选择没有任何内容的元素
  - ：target：目标选择器‘
  - ：first-child   ：last-child
  - ：nth-child(n)
  - ：nth-of-type(n) :某种类型子元素（在父元素的孩子有很多类型时使用）
  - ：first-of-type  ：last-of-type
  - : only-child :父元素只有一个子元素的元素
  - ：only-of-type: 一个元素的唯一类型的子元素
  - ：enabled ：disabled 表单中可用和禁用的元素
  - ：checked：表单中被选中的元素
  - ：read-only
  - ：read-write
- 伪元素选择器
  - ：：selection：鼠标选中的文本
  - ：：before和：：after：给元素的前后插入内容，与content一起使用

---
##边框相关
- border-radius
```
<!doctype html>
<html>
<head>
<meta charset="utf-8">
<title>border-radius</title>
<style type="text/css">
div.circle{
    height:100px;/*与width设置一致 实心圆*/
    width:100px;
    background:#9da;
    border-radius:50%;/*四个圆角值都设置为宽度或高度值的一半*/
    } 
div.semi-circle{ 
    height:100px; //左半圆
    width:50px;
    background:#9da;
    border-radius:50px 0px 0px 50px;
    }
div.test {
    height: 50px; //下半圆
    width: 100px;
    background:#9da;
    border-radius: 0px 0px 50px 50px;
}
</style>
</head>
<body>
<div class="circle">
</div>
<br/>
<!--任务部分-->
<div class="semi-circle">
</div>
<div class="test"></div>

</body>
</html>
```
- border-image
三个参数，url:图片路径 切割图片的宽度 图片延伸方式（round:平铺 repeat:重复 stretch:拉伸）
例子：我们有一张特殊图片
![Alt text](/img/52e21fea000127e802100210.jpg)
```
#border-image{
   background:#F4FFFA;
   width:210px; height:210px; border:70px solid #ddd;
   border-image:url(borderimg.png) 70 repeat  
}
```
效果如下：
![Alt text](/img/52e220780001091a03530354.jpg)
效果图中没有五，因为是从中心向四周切割的，所以5显示不出来
```
#border-image {
	width:170px;
	height:170px;
	border:70px solid;
	border-image:url(borderimg.png) 70 round；
 }
```
效果如下：
![Alt text](/img/52e2216700014c4103190312.jpg)
```
#border-image{
   background:#F4FFFA;
   width:210px; height:210px; border:70px solid #ddd;
   border-image:url(borderimg.png) 70 stretch  
}
```
效果如下：
![Alt text](/img/52e2218d0001d45403530366.jpg)

- box-shadow
box-shadow: X轴偏移量 Y轴偏移量 [阴影模糊半径] [阴影扩展半径] [阴影颜色] [投影方式]
其中，x,y为必选参数，投影方式省略为外阴影，inset为内阴影
可以为一个元素添加多个阴影，用逗号隔开

---
##颜色
- 新增颜色方式
	- rgba(255,255,255,0.5)
	- HSL(0,100% ,30%) :色调 饱和度 亮度 (0RED 120GREEN 240BLUE)
	- HSLA(0,100%,30%,0.3)
	- opacity：透明度
- gradient
Linear Gradients (goes down/up/left/right/diagonally)
Radial Gradients (defined by their center)
参数： 渐变方向，颜色的起点和终点（可以有多个）
```
background-image:linear-gradient(to left, red, orange,yellow,green,blue,indigo,violet);
```
![Alt text](/img/54b72c080001611c04230192.jpg)

##文字
- text-overflow:clip | ellipsis  ：用来设置是否使用一个省略标记标示元素内文本的溢出
```
text-overflow:ellipsis; 
overflow:hidden; 
white-space:nowrap; 
```
- word-wrap: normal | break-word
前者浏览器默认值，表示在控制连续文本换行 后者表示内容将在边界内换行

- 嵌入字体@font-face
可以加载服务器端的字体文件
用法：
```
@font-face {
    font-family : 字体名称;
    src : 字体文件在服务器上的相对或绝对路径;
} 
p {
    font-size :12px;
    font-family : "My Font";
    /*必须项，设置@font-face中font-family同样的值*/
}
```
- text-shadow
text-shadow: X-Offset Y-Offset blur color;
  - X-Offset：表示阴影的水平偏移距离，其值为正值时阴影向右偏移，反之向左偏移；      
  - Y-Offset：是指阴影的垂直偏移距离，如果其值是正值时，阴影向下偏移，反之向上偏移；
  - Blur：是指阴影的模糊程度，其值不能是负值，如果值越大，阴影越模糊，反之阴影越清晰，如果不需要阴影模糊可以将Blur值设置为0；
  - Color：是指阴影的颜色，其可以使用rgba色。

---
##背景相关
- background-origin ：设置图片的原始起始位置（背景必须是no-repeat,否则此属性无效）
background-origin ： border-box | padding-box | content-box;
 ![Alt text](/img/531003de0001166903660166.jpg)
- background-clip: 从何处裁剪图片
background-clip ： border-box | padding-box | content-box | no-clip
![Alt text](/img/5310065d0001c95103660166.jpg)
- background-size: 设置背景图片的大小
background-size: auto | <长度值> | <百分比> | cover | contain
  - cover：顾名思义为覆盖，即将背景图片等比缩放以填满整个容器；
  - contain：容纳，即将背景图片等比缩放至某一边紧贴容器边缘为止。

---
##transformation
让元素改变形状、大小、位置的效果
css3支持2D和3D变换
transform属性提供了五种函数来满足我们的需求

- rotate(n) :旋转函数，参数为正负180deg之间,二维
```
div {
    -ms-transform: rotate(20deg); /* IE 9 */
    -webkit-transform: rotate(20deg); /* Safari */
    transform: rotate(20deg);
}
```
![Alt text](/img/transform_rotate.gif)
 
 - translate(x,y) |translateX(x) | translateY(y):位移函数，x轴向右为正，y轴向下为正
```
div {
    -ms-transform: translate(50px,100px); /* IE 9 */
   	-webkit-transform: translate(50px,100px); /* Safari */
    transform: translate(50px,100px);
}
```
![Alt text](/img/transform_translate.gif)

- scale(x,y) | sacleX(x) | scaleY(y) :缩放函数，参数为倍数
```
div {
    -ms-transform: scale(2,3); /* IE 9 */
    -webkit-transform: scale(2,3); /* Safari */
    transform: scale(2,3);
}
```
![Alt text](/img/transform_scale.gif)

- skew(m,n) | skewX(m) | skewY(n) :扭曲函数，参数为角度。将一个对象以其中心位置围绕着x轴和y轴按照一定角度倾斜
```
div{
-webkit-transform: skew(45deg);
  -moz-transform:skew(45deg) 
  transform:skew(45deg);
}
```
 ![Alt text](/img/5339140b0001259804140145.jpg)
- matrix(a,b,c,d,e,f) : 矩阵变换（包含了上述几种效果）
```
div {
    -ms-transform: matrix(1, -0.3, 0, 1, 0, 0); /* IE 9 */
    -webkit-transform: matrix(1, -0.3, 0, 1, 0, 0); /* Safari */
    transform: matrix(1, -0.3, 0, 1, 0, 0);
}
```
![Alt text](/img/transform_rotate.gif)

以上这些方法讲的都是2D变换，他们还有对应的3D变换。
参见 [css3transform3D变换](http://www.w3schools.com/css/css3_3dtransforms.asp)

- transform-origin 
任何一个元素都有默认中心点，位于元素中心，可使用此属性改变。那么以上操作都会以新的中心点来变换
```
.transform-origin div {
  -webkit-transform-origin: left top;
  transform-origin: left top;
}
```

---
##transition
平滑的动画效果
- transition-property:指定过渡或动态模拟的CSS属性
- transition-duration:指定完成过渡所需的时间
- transition-timing-function:指定过渡函数
  - ease :由快到慢，逐渐变慢
  - liner ：恒速过度
  - ease-in：加速过度
  - ease-out：减速过渡
  - ease-in-out：先加速再减速
- transition-delay:指定开始出现的延迟时间
```
div {
    transition: width 2s linear 1s;
}
div:hover {
    width: 300px;
}
```

---
##animation
不断改变元素样式的复杂动画
- animation-delay：动画开始播放的时间
- animation-direction	：播放方向 （normal alternate：偶数向前播放，奇数向后播放）
- animation-duration：动画播放持续时间
- animation-fill-mode	：动画开始之前和结束之后发生的操作
  - none:默认值，表示动画将按预期进行和结束，在动画完成其最后一帧时，动画会反转到初始帧处
  - forwards:表示动画在结束后继续应用最后的关键帧的位置
  - backwards:会在向元素应用动画样式时迅速应用动画的初始帧
  - both:元素动画同时具有forwards和backwards效果
- animation-iteration-count	 :动画播放次数（1|整数|infinite）
- animation-name :执行由 @keyframes函数定义的动画行为
  - Keyframes被称为关键帧，其类似于Flash中的关键帧。在CSS3中其主要以“@keyframes”开头，后面紧跟着是动画名称加上一对花括号“{…}”，括号中就是一些不同时间段样式规则。
```
@keyframes wobble {
  0% {
    margin-left: 100px;
    background:green;
  }
  40% {
    margin-left:150px;
    background:orange;
  }
  60% {
    margin-left: 75px;
    background: blue;
  }
  100% {
    margin-left: 100px;
    background: red;
  }
}
``` 
- animation-play-state	: 播放状态（running|paused）
- animation-timing-function：播放函数（同transition中的函数）

```
div {
    width: 100px;
    height: 100px;
    position: relative;
    background-color: red;
    animation-name: wobble;
    animation-duration: 4s;
}
```
##多列布局
columns:轻松实现报纸多列排版
```
.columns {
  width: 500px;
  padding: 5px;
  border: 1px solid green;
  margin: 20px auto; 
  -webkit-columns: 150px 3;
  -moz-columns: 150px 3;
  -o-columns:150px 3;
  -ms-columns: 150px 3;
  columns: 150px 3;
}
```
![Alt text](/img/5360c4c70001336f04870257.jpg)
- column属性
  - width：列宽
  - count：列数
  - gap：列间距
  - rule：列与列的边框宽度
  - span：跨列显示（all | none）

---
##用户接口
- resize ：规定元素是否能被用户拖动大小，增强用户体验
  - none: 不能拖动
  - both：拖动元素在水平和垂直方向同时变化
  - vertical： 仅垂直方向
  - horizontal：仅水平方向
```
textarea {
  -webkit-resize: horizontal;
  -moz-resize: horizontal;
  -o-resize: horizontal;
  -ms-resize: horizontal;
  resize: horizontal;
}
```
- outline :外轮廓outline在页面中呈现的效果和边框border呈现的效果极其相似，但和元素边框border完全不同，外轮廓线不占用网页布局空间，不一定是矩形，外轮廓是属于一种动态样式，只有元素获取到焦点或者被激活时呈现。
outline: ［outline-color］ || [outline-style] || [outline-width] || [outline-offset] || inherit

---
##盒模型
- box-sizing: content-box | border-box | inherit
![Alt text](/img/5365d98000018fa606460416.jpg)
- 弹性盒模型 flex

##媒体查询和响应式设计
- 媒体查询：通过css3来查询媒体，然后调用对应的样式

  - 引入方式：
```
1. link方法
link方法引入媒体类型其实就是在<link>标签引用样式的时候，通过link标签中的media属性来指定不同的媒体类型。如下所示。
<link rel="stylesheet" type="text/css" href="style.css" media="screen" />
<link rel="stylesheet" type="text/css" href="print.css" media="print" />

2. @import方法
@import可以引用样式文件，同样也可以用来引用媒体类型。

@importurl(reset.css) screen;   
@importurl(print.css) print;

3. @media方法
@media是CSS3中新引进的一个特性，被称为媒体查询。在页面中也可以通过这个属性来引入媒体类型。@media引入媒体类型和@import有点类似也具有两方式。
（1）在样式文件中引用媒体类型：
@media screen {
   选择器{/*你的样式代码写在这里…*/}
}
</style>
</head>
```
  - @media 媒体类型   and （媒体特性）{你的样式}
```
@media screen and (min-width:900px){
.wrapper{width: 980px;}
}
```

- 响应式设计RWD
是提供各种设备都能浏览网页的一种设计方法，RWD能让你的网页在不同的设备中展现不同的设计风格。
  - 设置viewport
  ```
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  ```
  ![Alt text](/img/53660f2c0001190005270386.jpg)

  - 弹性图片 img {max-width:100%;}
  - 设置断点：设备宽度的临界点。在Media Queries中，其中媒体特性“min-width”和“max-width”对应的属性值就是响应式设计中的断点值
```
/* For mobile phones: */
[class*="col-"] {
    width: 100%;
}
@media only screen and (min-width: 768px) {
    /* For desktop: */
    .col-1 {width: 8.33%;}
    .col-2 {width: 16.66%;}
    .col-3 {width: 25%;}
    .col-4 {width: 33.33%;}
    .col-5 {width: 41.66%;}
    .col-6 {width: 50%;}
    .col-7 {width: 58.33%;}
    .col-8 {width: 66.66%;}
    .col-9 {width: 75%;}
    .col-10 {width: 83.33%;}
    .col-11 {width: 91.66%;}
    .col-12 {width: 100%;}
}
```
- 屏幕分辨率
```
1.1024px显屏
@media screen and (max-width : 1024px) {                    
/* 样式写在这里 */          
}     
2.800px显屏
@media screen and (max-width : 800px) {              
/* 样式写在这里 */          
}     
3.640px显屏
@media screen and (max-width : 640px) {              
/* 样式写在这*/            
}     
4.iPad横板显屏
@media screen and (max-device-width: 1024px) and (orientation: landscape) {              
/* 样式写在这 */            
}     
5.iPad竖板显屏
@media screen and (max-device-width: 768px) and (orientation: portrait) {         
/* 样式写在这 */            
}     
6.iPhone 和 Smartphones
@media screen and (min-device-width: 320px) and (min-device-width: 480px) {              
/* 样式写在这 */            
}     
```

