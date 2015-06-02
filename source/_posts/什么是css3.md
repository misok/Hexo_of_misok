title: css3学习笔记（一）
date: 2015-6-2 
categories: 前端开发
tags: [CSS3]

---
###什么是css3
- css的最新版本
- 完全向后兼容
- 向前兼容需要浏览器前缀
| 前缀 | 浏览器|
| :--- | ---- |
| -webkit | chrome和safari |
| -moz | firefox |
 | -ms | IE |
 | -o | opera |
 

###新特性
- 选择器
- 边框相关
- 颜色
- text
- 背景相关
- transformation（变换）
- animation
- 多列布局
- 用户接口（resize和offeset）
- 媒体查询和响应式
- 盒模型

####选择器
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

####边框相关
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
![Alt text](./52e21fea000127e802100210.jpg)
```
#border-image{
   background:#F4FFFA;
   width:210px; height:210px; border:70px solid #ddd;
   border-image:url(borderimg.png) 70 repeat  
}
```
效果如下：
![Alt text](./52e220780001091a03530354.jpg)
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
![Alt text](./52e2216700014c4103190312.jpg)
```
#border-image{
   background:#F4FFFA;
   width:210px; height:210px; border:70px solid #ddd;
   border-image:url(borderimg.png) 70 stretch  
}
```
效果如下：
![Alt text](./52e2218d0001d45403530366.jpg)

- box-shadow
box-shadow: X轴偏移量 Y轴偏移量 [阴影模糊半径] [阴影扩展半径] [阴影颜色] [投影方式]
其中，x,y为必选参数，投影方式省略为外阴影，inset为内阴影
可以为一个元素添加多个阴影，用逗号隔开

####颜色
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
![Alt text](./54b72c080001611c04230192.jpg)

####文字
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

####背景相关
- background-origin ：设置图品的原始起始位置（背景必须是no-repeat,否则此属性无效）
background-origin ： border-box | padding-box | content-box;
 ![Alt text](./531003de0001166903660166.jpg)
- background-clip: 从何处裁剪图片
background-clip ： border-box | padding-box | content-box | no-clip
![Alt text](./5310065d0001c95103660166.jpg)
- background-size: 设置背景图片的大小
background-size: auto | <长度值> | <百分比> | cover | contain
  - cover：顾名思义为覆盖，即将背景图片等比缩放以填满整个容器；
  - contain：容纳，即将背景图片等比缩放至某一边紧贴容器边缘为止。
- 
 