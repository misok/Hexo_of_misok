title: JavaScript学习笔记(基础篇)
date: 2014-12-05
categories: 前端开发
tags: [JavaScript, JS, 笔记]

---
让网页呈现各种动态效果
需要文本编辑器


---
<!-- more -->
##如何插入script

1. 插入script标签
```
<script type="text/javascript">
</script>
```
2. 引用外部JS文件
```
<script src="script.js"></script>
```
---

##JS在页面中的位置
 
- javascript作为一种脚本语言可以放在html页面中任何位置，但是浏览器解释html时是按先后顺序的，所以前面的script就先被执行。比如进行页面显示初始化的js必须放在head里面，因为初始化都要求提前进行（如给页面body设置css等）；而如果是通过事件调用执行的function那么对位置没什么要求的。

---

##JS语法元素
###变量
- 定义变量：  var 变量名
- 变量名
  - 变量名必须使用字母或者下划线(_)开始
  - 变量名必须使用英文字母、数字、下划线(_)组成
  - 变量名不能使用JavaScript关键词与JavaScript保留字
 
- 先声明再赋值，变量可以重复赋值
- JS中变量名区分大小写
```
var mychar;
mychar="javascript";
mychar="hello";
```

###判断语句
```
<script type="text/javascript">
	var score =80; //score变量存储成绩，初值为80
	  
	{
     document.write("很棒，成绩及格了。");
	}
  
	{
	 document.write("加油，成绩不及格。");
	}
  </script>
```
 
###函数
- 函数定义
```
function add2(){
   var sum = 3 + 2;
   alert(sum);
}
```
- 函数调用
```
<title>函数调用</title>
   <script type="text/javascript">
    function contxt() //定义函数
      {
         alert("哈哈，调用函数了!");
      }
   </script>
</head>
<body>
   <form>
      <input type="button"  value="点击我" onclick="contxt()"/>  
   </form>
```

---
##交互

###输出（document.write)
1. 输出字符串
2. 通过变量输入
3. 输出标签使起作用（比如换行br）
4. 输出多个内容中间用+连接
 ```
<title>document.write</title>
  <script type="text/javascript">
    var mystr="我是";
    var mychar="JavaScript";
    document.write(mychar+"<br/>");
    document.write(mystr+mychar+"的忠实粉丝");

  </script>
  ```
  
###警告（alert）

我们在访问网站的时候，有时会突然弹出一个小窗口，上面写着一段提示信息文字。如果你不点击“确定”，就不能对网页做任何操作，这个小窗口就是使用alert实现的

- 在点击对话框"确定"按钮前，不能进行任何其它操作
-  消息对话框通常可以用于调试程序
-   alert输出内容，可以是字符串或变量，与document.write 相似
```
<script type="text/javascript">
   var mynum = 30;
   alert("hello!");
   alert(mynum);
</script>
```

###确认消息对话框
- 语法：var str=confirm("提示消息");
- 返回值是一个布尔类型，按确认返回真，取消返回假
```
<script type="text/javascript">
    var mymessage=confirm("你喜欢JavaScript吗?");
    if(mymessage==true)
    {   document.write("很好,加油!");   }
    else
    {  document.write("JS功能强大，要学习噢!");   }
</script>
```

###prompt消息对话框
prompt弹出消息对话框,通常用于询问一些需要与用户交互的信息。弹出消息对话框（包含一个确定按钮、取消按钮与一个文本输入框）。

- 语法：prompt(str1, str2);
- str1: 要显示在消息对话框中的文本，不可修改
  str2：文本框中的内容，可以修改
-  点击确定按钮，文本框中的内容将作为函数返回值
   点击取消按钮，将返回null
```
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>prompt</title>
  <script type="text/javascript">
  function rec(){
	var score; //score变量，用来存储用户输入的成绩值。
	score =prompt("请输入你的成绩");
	if(score>=90)
	{
	   document.write("你很棒!");
	}
	else if(score>=75)
    {
	   document.write("不错吆!");
	}
	else if(score>=60)
    {
	   document.write("要加油!");
    }
    else
	{
       document.write("要努力了!");
	}
  }
  </script>
</head>
<body>
    <input name="button" type="button" onClick="rec()" value="点击我，对成绩做评价!" />
</body>
```

###打开新窗口
打开一个新窗口

- 语法：window.open(<URL>, <窗口名称>, <参数字符串>)
- URL：打开窗口的网址或路径。
- 窗口名称：被打开窗口的名称。可以是"_top"、"_blank"、"_selft"等。
- 参数字符串：设置窗口参数，各参数用逗号隔开。
```
//打开http://www.imooc.com网站，大小为300px * 200px，无菜//单，无工具栏，无状态栏，有滚动条窗口：
<script type="text/javascript"> 
window.open('http://www.imooc.com','_blank','width=300,height=200,menubar=no,toolbar=no,status=no,scrollbars=yes')
</script>
```
**参数之间逗号及等号前后有空格，该字符串无效，只有删除空格才能正常运行**

###关闭窗口
```
<script type="text/javascript">
   var mywin=window.open('http://www.imooc.com'); //将新打的窗口对象，存储在变量mywin中
   mywin.close();
</script>
```
 
###阶段练习
```
/*1、新窗口打开时弹出确认框，是否打开

提示: 使用 if 判断确认框是否点击了确定，如点击弹出输入对话框，否则没有任何操作。
2、通过输入对话框，确定打开的网址，默认为 http：//www.imooc.com/

3、打开的窗口要求，宽400像素，高500像素，无菜单栏、无工具栏。*/
<head>
  <title> new document </title>  
  <meta http-equiv="Content-Type" content="text/html; charset=gbk"/>   
  <script type="text/javascript">
    function openWindow(){
        var ifopen=confirm("是否打开窗口");
        if(ifopen==true){
            var httpaddress=prompt("请输入需要打开的网址","http://imooc.com");
            }
            
        window.open('httpaddress','_blank','width=400,height=500,menubar=no,toolbar=no')
        
        } 
  </script> 
 </head> 
 <body> 
	  <input type="button" value="新窗口打开网站" onclick="openWindow()" /> 
 </body>
```

---
 
##认识DOM
- 文档对象模型DOM（Document Object Model）定义访问和处理HTML文档的标准方法。DOM 将HTML文档呈现为带有元素、属性和文本的树结构（节点树）

###结构
- 元素节点：html、body、p等等，即标签
- 文本节点：向用户展示的内容
- 属性节点：元素的属性

###通过ID获取元素
- 学过HTML/CSS样式，都知道，网页由标签将信息组织起来，而标签的id属性值是唯一的，就像是每人有一个身份证号一样，只要通过身份证号就可以找到相对应的人。那么在网页中，我们通过id先找到标签，然后进行操作
- 语法： document.getElementById(“id”) 
```
<body>
<p id="con">JavaScript</p>
<script type="text/javascript">
  var mychar=document.getElementById("con");
  document.write("结果:"+mychar); //输出获取的P标签
</script>
</body>
```

###innerHTML属性
- 用于获取或替换 HTML 元素的内容
- 语法：Object.innerHTML
- Object是获取的元素对象，如通过document.getElementById("ID")获取的元素
```
<body>
<h2 id="con">javascript</H2>
<p> JavaScript是一种基于对象、事件驱动的简单脚本语言，嵌入在HTML文档中，由浏览器负责解释和执行，在网页上产生动态的显示效果并实现与用户交互功能。</p>
<script type="text/javascript">
  var mychar=document.getElementById("con");           ;
  document.write("原标题:"+mychar.innerHTML+"<br>"); //输出原h2标签内容
  mychar.innerHTML="Hello World";
  document.write("修改后的标题:"+mychar.innerHTML); //输出修改后h2标签内容
</script>
</body>
```

###改变HTML样式
- 语法：Object.style.property=new style;
```
<h2 id="con">I love JavaScript</H2>
  <p id="p1"> JavaScript使网页显示动态效果并实现与用户交互功能。</p>
  <script type="text/javascript">
    var mychar= document.getElementById("con");
    mychar.style.color="red";
    mychar.style.backgroundColor="#ccc";
    mychar.style.width="300px"; 
    var str=document.getElementById("p1");
    str.style.color="blue";
    str.style.backgroundColor="#000";
    </script>
```

###显示和隐藏（display属性）
- 网页中经常会看到显示和隐藏的效果，可通过display属性来设置。
- 语法：Object.style.display = value
- value取值为none：隐藏  block:显示为块
```
<title>display</title>
    <script type="text/javascript"> 
        function hidetext()  
		{  
		var mychar = document.getElementById("con");
        mychar.style.display="none";
		}  
		function showtext()  
		{  
		var mychar = document.getElementById("con");
        mychar.style.display="block";
		}
    </script> 
</head> 
<body>  
    <h1>JavaScript</h1>  
    <p id="con">做为一个Web开发师来说，如果你想提供漂亮的网页、令用户满意的上网体验，JavaScript是必不可少的工具。</p> 
    <form>
       <input type="button" onclick="hidetext()" value="隐藏内容" /> 
       <input type="button" onclick="showtext()" value="显示内容" /> 
    </form>
</body> 
```

###className控制类名属性
- className 属性设置或返回元素的class 属性。
- 语法：object.className = classname
```
<title>className属性</title>
<style>
    body{ font-size:16px;}
    .one{
		border:1px solid #eee;
		width:230px;
		height:50px;
		background:#ccc;
		color:red;
    }
	.two{
		border:1px solid #ccc;
		width:230px;
		height:50px;
		background:#9CF;
		color:blue;
	}
	</style>
</head>
<body>
    <p id="p1" > JavaScript使网页显示动态效果并实现与用户交互功能。</p>
    <input type="button" value="添加样式" onclick="add()"/>
	<p id="p2" class="one">JavaScript使网页显示动态效果并实现与用户交互功能。</p>
    <input type="button" value="更改外观" onclick="modify()"/>

	<script type="text/javascript">
	   function add(){
	      var p1 = document.getElementById("p1");
	      p1.className="one";
	   }
	   function modify(){
	      var p2 = document.getElementById("p2");
	      p2.className="two";
	   }
	</script>
</body>
```
 
###编程练习
，请编写"改变颜色"、"改变宽高"、"隐藏内容"、"显示内容"、"取消设置"的函数，点击相应按钮执行相应操作，点击"取消设置"按钮后，提示是否取消设置，如是执行操作，否则不做操作。


  
```
<head>
    <meta http-equiv="Content-Type" Content="text/html; charset=utf-8" />
    <title>javascript</title>
    <style type="text/css">
        body{font-size:12px;}
        #txt{
            height:400px;
            width:600px;
            border:#333 solid 1px;
            padding:5px;}
        p{
            line-height:18px;
            text-indent:2em;}
    </style>
</head>
<body>
    <h2 id="con">JavaScript课程</H2>
    <div id="txt">
        <h5>JavaScript为网页添加动态效果并实现与用户交互的功能。</h5>
        <p>1. JavaScript入门篇，让不懂JS的你，快速了解JS。</p>
        <p>2. JavaScript进阶篇，让你掌握JS的基础语法、函数、数组、事件、内置对象、BOM浏览器、DOM操作。</p>
        <p>3. 学完以上两门基础课后，在深入学习JavaScript的变量作用域、事件、对象、运动、cookie、正则表达式、ajax等课程。</p>
    </div>

    <form>

        <input type="button" value="改变颜色" onClick="changecolor()" >
        <input type="button" value="改变宽高" onClick="changesize()" >
        <input type="button" value="隐藏内容" onClick="hind()" >
        <input type="button" value="显示内容" onClick="perform()" >
        <input type="button" value="取消设置" onClick="quxiao()" >
    </form>
    <script type="text/javascript">
    //定义"改变颜色"的函数
        function changecolor(){
            var mystr=document.getElementById("con");
            var str=document.getElementById("txt");
            mystr.style.color="red";
            mystr.style.backgroundColor="#333";
            str.style.color="blue";
            str.style.backgroundColor="#ccc";
        }


    //定义"改变宽高"的函数
        function changesize(){
            document.getElementById("con").style.width="600px";
            document.getElementById("txt").style.width="600px";
            document.getElementById("con").style.height="200px";
            document.getElementById("txt").style.height="800px";

        }


    //定义"隐藏内容"的函数
        function hind(){
            document.getElementById("con").style.display="none";
            var mychar = document.getElementById("txt");
            mychar.style.display="none";

        }

    //定义"显示内容"的函数
        function perform(){
            document.getElementById("con").style.display="block";
            var mychar = document.getElementById("txt");
            mychar.style.display="block";
        }

    //定义"取消设置"的函数
        function quxiao(){
            var char=confirm("是否取消设置");
            if(char==true){
                document.getElementById("con").setAttribute('style','');
                document.getElementById("txt").setAttribute('style','');

        }
    }


</script>
</body>

```

 







