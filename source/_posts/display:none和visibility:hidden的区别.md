title: CSS伪类、优先级、属性的继承性等问题
date: 2015-3-10
categories: 前端开发
tags: [CSS]

---
```
写作目的：CSS中有一些需要掌握的知识。贴在这里。主要内容包括：
1.display:none和visibility:hidden的区别
2.CSS选择符、属性的继承性、优先级
3.：before和：after伪类
另外还有position属性的解读和float属性。这是关于布局的另一个故事了，请期待下一篇。
```
###display:none和visibility:hidden的区别
- 首先，两者都是隐藏对应的元素
- display：none 隐藏对应元素后文档布局不再为其分配空间，它周围的元素会合拢
- visibility：hidden隐藏对应元素但在文档布局中依然保留其空间

###CSS选择符、属性的继承性、优先级
- 选择符
  - id选择器
  - 类选择器
  - 标签选择器
  - 子选择器
  - 后代选择器
  - 相邻选择器
  - 属性选择器
  - 伪类选择器
  - 通配符选择器
  
- 属性的继承性

  所谓CSS的继承是指被包在内部的标签将拥有外部标签的样式性质，它是依赖于祖先-后代的关系的。继承特性最典型的应用通常发挥在整个网页的样式预设。
  
  - 可继承的样式
    - 字体：font、color、font-family、font-size（继承计算后的值）、font-size-adjust、font-stretch 、font-style 、font-style 、text-underline-position 、font-variant 、 text-transform line-height、letter-spacing 、word-spacing 
    - 文本：text-indent 、text-align 、layout-flow 、writing-mode 、white-space 、word-wrap 、text-kashida-space 、layout-grid 、layout-grid-char 、layout-grid-char-spacing 、layout-grid-line 、layout-grid-mode 、layout-grid-type
    - 列表：list-style     、list-style-image 、list-style-position 、list-style-type
    - 表格：border-collapse 、border-spacing 、caption-side 、empty-cells 、table-layout 、speak-header
  - 不可继承的样式
    - 字体：text-decoration 、text-shadow
    - 文本：text-overflow 、vertical-align 、direction、unicode-bidi 、word-break 、line-break 、text-autospace、text-justify 、ruby-align 、ruby-overhang 、ruby-position 、ime-mode
    - 背景：background、background-origin 、background-clip 、background-size 、background-attachment 、background-color、background-image 、background-position 、background-positionX 、background-positionY 、background-repeat 、layer-background-color 、layer-background-image 
    - 定位：position 、z-index 、top、right 、bottom 、left
    - 尺寸：height 、max-height 、min-height 、width、max-width 、min-width
    - 布局：clear 、float、clip 、overflow、overflow-x、overflow-y、display、visibility
    - 外补丁：margin 、margin-top 、margin-right 、margin-bottom 、margin-left
    - 内补丁：padding 、padding-top 、padding-right 、padding-bottom 、padding-left
    - 轮廓：outline、outline-color 、outline-style 、outline-style 、outline-width
    - 边框：border、border-color 、border-style 、border-image 、border-radius 、box-shadow、border-width 、border-top 、border-top-color 、border-top-style 、border-top-width 、border-right 、border-right-color 、border-right-style 、border-right-width 、border-bottom 、border-bottom-color 、border-bottom-style 、border-bottom-width 、border-left 、border-left-style 、border-left-width
    - 列表：marker-offset
    - 其他：cursor、zoom
    
###优先级
css优先级用来决定同一个元素样式设置冲突的时候采用哪个样式。

首先整体优先级原则是：
- 优先级就近原则： 同权重情况下以最靠近的元素的样式为准
- 载入样式以最后载入的定位为准

具体有以下规则：

- 内联样式>内部样式>外部样式
  - 注意：若外部样式放在内部样式之后，则会覆盖内部样式
- 选择器优先权
  - 内联样式表：1000（权值）
  - id选择器：100
  - class选择器：10
  - 标签选择器：1
  
  在样式表内，计算选择器的权值，权值越大优先级越高
- 网页编写者的CSS优先于浏览器默认样式
- 继承的样式低于后来新设置的样式
- 同一组属性设置中标有！important规则的优先级最高
  - ！important > id > class > tag
  
###：before和：after伪类
：before和：after伪类的作用就是在指定的元素内容（而不是元素本身）之前或者之后插入一个包含content属性指定内容的行内元素
如果没有content属性，伪类元素就没有作用。插入的内容默认是一个行内元素，且在HTML源代码中无法看到，也无法通过DOM操作。

但伪类可用于清除浮动：

```

.clearfix:after{
	content: "";
	display: inline-block;
	clear: both;
	visibility: hidden;
	height: 0;
	

```
