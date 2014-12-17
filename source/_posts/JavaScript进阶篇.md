title: JavaScript进阶篇
date: 2014-12-17
categories: 前端开发
tags: [JavaScript, JS, 笔记]

---
也许你已经了解HTML标记(也称为结构)，知道了CSS样式(也称为表示)，会使用HTML+CSS创建一个漂亮的页面，但这还不够，它只是静态页面而已。我们还需使用JavaScript增加行为，为网页添加动态效果。准备好，让JavaScript带你进入新境界吧!
<!-- more -->
---

##JS能做什么？
- 增强页面动态效果（图片轮播、信息滚动）
- 实现页面与用户之间的实时、动态交互（用户注册、登录验证）

---
##JS基础语法
---
###变量
- 定义
- 命名规则
- 声明变量
```
var num1,num2;
```
- 变量赋值
- 变量内容

说明：所以，这样来比喻变量，就像装东西的盒子，首先盒子得有一个合法且有意义的名字。然后盒子可以装东西，把东西放进盒子的过程就是变量赋值。最后，盒子可以装各种东西，可以是水果、衣服等等，也就是变量的内容可以是字符串、数值、布尔等。

**老早就发现，跟其他编程语言不同的是，这里变量不分类型，没有所谓Int,char这些类型，倒是简化了工作**

---

###表达式
表达式是指具有一定的值、用操作符把常数和变量连接起来的代数式。一个表达式可以包含常数或变量

---

- 操作符 + 变量
  - 操作符：操作符是用于在JavaScript中指定一定动作的符号
    - 算术操作符(+、-、*、/)
    - 比较操作符(<、>、>=、<=等)
    - 逻辑操作符(&&、||、！)
    - + 还可以表示连接字符串
    - 自加和自减
    - 操作符优先级
      - 算术操作符 > 比较操作符 > 逻辑操作符 >"="赋值符号
      - 如果同级的运算是按从左到右次序进行,多层括号由里向外
    
```
<script type="text/javascript">
  var a,b,sum;
  var  a  = 5;
  var  b  = 100%7;  
  sum = a > b && a*b > 0 ;
  document.write( "我认为 a 的值是:" + 5  + " b的值是:" + 2 + "sum 的值是:" +　true +"<br/>");
  document.write( "答案是,第一轮计算后，a 为："+ a +";b为："+b +";第一次计算sum为："+ sum +"<br/>");

  sum = ( (++a) + 3 ) / (2 - (--b) ) * 3;  
  document.write( "再一次计算后，我认为 a 的值是:" +  6  + " b的值是:" +  1 + "sum 的值是:" +  27 +"<br/>"); 
  document.write( "答案是，第二轮计算后，a 为：" + a + ";b为：" + b +";第二次计算sum为："+ sum +",sum的类型也发生变化了。");

</script>

 ```
--- 
###数组
---
####一维数组
一维数组就是一组可以放东西的盒子

---
- 创建数组：var myarray=new Array();
- 如果输出空数组则显示undefined
- 创建时可以再括号中制定数组长度
- 虽然创建数组时，指定了长度，但实际上数组都是变长的，也就是说即使指定了长度为8，仍然可以将元素存储在规定长度以外（跟其他语言不同，个人感觉这样灵活点啊）
- 数组赋值（除了一般方法外，还有以下方法）
  - var myarray = new Array(66,80,90,77,59);//创建数组同时赋值
  - var myarray = [66,80,90,77,59];//直接输入一个数组（称 “字面量数组”）
- 添加新元素，只需按序号一直往后存储即可（所以这玩意的空间是动态增长的？nice）
- 数组的长度
  - 用arr.length 访问（看来HTML借鉴的是面向对象的思想）
  - 而且!数组的length可以显示改变，调用上面语句给他赋值就好了
  ```
<script language="javascript">
 var mynum=new Array(65,90,88,98);
 document.write("数组的长度是:"+  mynum.length+"<br/>");
 mynum.length = 2;
 document.write(mynum[3] + "<br/>" +mynum[1]);
</script>
猜猜上面的输出是什么：没错，就是这样，跟我想的一样
数组的长度是:4
undefined
90
  ```
---

####二维数组

这个比喻很恰当，一维的我们看成一组盒子，二维我们就看成一组可以放盒子的盒子。

---
- 定义方法
  - 用For循环，先声明一维（相当于行，再声明二维，相当于列）
  ```
var myarr=new Array();  //先声明一维 
for(var i=0;i<2;i++){   //一维长度为2
   myarr[i]=new Array();  //再声明二维 
   for(var j=0;j<3;j++){   //二维长度为3
   myarr[i][j]=i+j;   // 赋值，每个数组元素的值为i+j
   }}
```
  - var Myarr = [[0 , 1 , 2 ],[1 , 2 , 3, ]]
---

###流程控制语句

---
####if语句
其实这边真没什么可说（恩，如果学过编程语言的话），就是二选一，要么多重判断，注意条件的覆盖性就好了

####Switch语句
记得写上break,不然会执行所有语句
它跟if的区别是只要条件满足就跳到switch块之后继续执行，但是if会判断完所有分支，这点switch效率高一点

####For循环
####while循环
- 与for相比的话，还是更喜欢for,一目了然，我记得我以前写while老是忘记写更新条件
####do...while循环
- 它是先执行再判断，至少保证循环体被执行一次

#####对于以上循环语句，可以使用break中断退出循环
#####使用continue跳过本次循环，但不退出循环体

---
###函数
---
####函数声明
function 函数名(){do something}

####函数调用
- script标签内调用(直接写函数名调用)
- 在HTML文件中调用，如通过点击按钮后调用定义好的函数
```
<input type="button" value="click it" onclick="add2()"> 
```

####带参数的函数
function 函数名(x,y,);{do something}


####返回值函数
- 就是对函数执行的结果进行处理嘛
- 返回类型任意（但是不用显示指定类型，你懂得，貌似JS里面没有这个）

---
##事件响应-让网页交互
finally,要来点新知识了，let's go!

---
###什么是事件
- 事件是可以被 JavaScript 侦测到的行为，网页中的每个元素都可以产生某些可以触发 JavaScript 函数或程序的事件
- 主要事件
  - 鼠标点击：onClick
  - 鼠标经过：onmouseover
  - 鼠标移开:onmouseout
  - 文本框内容改变:onchange
  - 文本框内容被选中:onselect
  - 光标聚集:onfocus
  - 光标离开:onblur
  - 网页导入:onload
  - 关闭网页:onunload
- 在网页中，如使用事件，就在该元素中设置事件属性。
```
<form>
  <a href="http://www.imooc.com" onmouseout="message()">点击我</a>
</form>
//下拉列表获得焦点
<form>
    <select name="career" onfocus="message()"> 
      <option>学生</option> 
      <option>教师</option> 
      <option>工程师</option> 
      <option>演员</option> 
      <option>会计</option> 
    </select> 
//密码框失去焦点
密码:<input name="password" type="text" value="请输入密码！" onblur="message()" >
//文本框内容被选中
<form>
  个人简介：<br>
   <textarea name="summary" cols="60" rows="5"   onselect="message()">请写入个人简介，不少于200字！</textarea>
  </form>
//加载事件：加载页面时触发，一般写在body内
<body onload="message()">
  欢迎学习JavaScript。
</body>
//卸载事件：不同浏览器对此事件支持不同
<script type="text/javascript">   
     window.onunload = onunload_message;   
     function onunload_message(){   
        alert("您确定离开该网页吗？");   
    }   
</script>
```
###编程练习
```
<head>
  <title> 事件</title>  
  <script type="text/javascript">
   function count(){
    var a=document.getElementById("txt1").value;
    var b=document.getElementById("txt2").value;
    
    //获取第一个输入框的值
	//获取第二个输入框的值
	//获取选择框的值
    var char=document.getElementById("select").value;
	//获取通过下拉框来选择的值来改变加减乘除的运算法则
    switch(char){
        case "+":
            var c=parseInt(a)+parseInt(b);
            break;
        case "-":
            var c=parseInt(a)-parseInt(b);
            break;
        case "*":
            var c=parseInt(a)*parseInt(b);
            break;
        case "/":
            var c=parseInt(a)/parseInt(b);
            break;
    }
    //设置结果输入框的值 
    document.getElementById("fruit").value=c;
   }
  </script> 
 </head> 
 <body>
   <input type='text' id='txt1' /> 
   <select id='select'>
		<option value='+'>+</option>
		<option value="-">-</option>
		<option value="*">*</option>
		<option value="/">/</option>
   </select>
   <input type='text' id='txt2' /> 
   <input type='button' value=' = ' onclick="count()" /> <!--通过 = 按钮来调用创建的函数，得到结果--> 
   <input type='text' id='fruit' />   
 </body>
 ```

---
##JS内置对象
JavaScript 中的所有事物都是对象，如:字符串、数值、数组、函数等，每个对象带有属性和方法
- 对象的属性：反映该对象某些特定的性质的，如：字符串的长度、图像的长宽等
- 对象的方法：能够在对象上执行的动作。例如，表单的“提交”(Submit)，时间的“获取”(getYear)等
- 使用对象
  - 先定义对象：var objectName =new Array();//使用new关键字定义对象 或者var objectName =[];
  - 访问对象是属性objectName.propertyName
  - 访问对象的方法：objectName.methodName()
---

###Date日期对象
- 日期对象可以储存任意一个日期，并且可以精确到毫秒数（1/1000 秒）
- 初始值：当前时间(当前电脑系统时间)
- Date的方法
  - set/getFullYear()
  - getDay():返回星期（返回的是0-6,0代表星期天，如果要返回星期数可实现如下：
  ```
<script type="text/javascript">
  var mydate=new Date();//定义日期对象
  var weekday=["星期日","星期一","星期二","星期三","星期四","星期五","星期六"];
//定义数组对象,给每个数组项赋值
  var mynum=mydate.getDay();//返回值存储在变量mynum中
  document.write(mydate.getDay());//输出getDay()获取值
  document.write("今天是："+ weekday[mynum]);//输出星期几
</script>
```

  - get/setTime():返回/设置时间，单位毫秒数，计算从 1970 年 1 月 1 日零时到日期对象所指的日期的毫秒数
  ```
<script type="text/javascript">
  var mydate=new Date();
  document.write("当前时间："+mydate+"<br>");
  mydate.setTime(mydate.getTime() + 60 * 60 * 1000);
  document.write("推迟一小时时间：" + mydate);
</script>
```
**注意:1. 一小时 60 分，一分 60 秒，一秒 1000 毫秒**
---

###字符串对象
- 属性：length
- 方法
  - 返回指定位置的字符：charAt(index)
  **字符串第一个字符的下标为0**
  - 返回指定的字符串首次出现的位置
    - stringObject.indexOf(substring, startpos)
    - substring:必需参数，需要检索的字符串
    - startpos:非必需，检索的起始位置，确实默认从头开始
    ```
<script type="text/javascript">
  var str="I love JavaScript!"
  document.write(str.indexOf("I") + "<br />");
  document.write(str.indexOf("v") + "<br />");
  document.write(str.indexOf("v",8));
</script>
```
    **indexOf() 方法区分大小写**
    **如果要检索的字符串值没有出现，则该方法返回 -1**
  - 字符串分割split()
    - stringObject.split(separator,limit)
    - 第一个参数必需，指定开始分割的地方
    - 可选，分割的次数，默认不限次数
    ```
<script type="text/javascript">
var mystr="86-010-85468578";
document.write(mystr.split("-")+ "<br />");
document.write(mystr.split("")+ "<br />");
document.write(mystr.split("",3));
</script>
```
    **如果把空字符串 ("") 用作 separator，那么 stringObject 中的每个字符之间都会被分割**
  - 提取字符串substring()
    - stringObject.substring(starPos,stopPos)
    - 第一个参数，必需，开始位置
    - 可选，结束位置，省略则默认到结尾
    - 返回的内容是从 start开始(包含start位置的字符)到 stop-1 处的所有字符，其长度为 stop 减start
    - 如果参数 start 与 stop 相等，那么该方法返回的就是一个空串（即长度为 0 的字符串）
    ```
<script type="text/javascript">
  var mystr="I love JavaScript";
  document.write(mystr.substring(7));
  document.write(mystr.substring(2,6));
</script>
运行结果:
JavaScript
love
```
    ** 如果 start 比 stop 大，那么该方法在提取子串之前会先交换这两个参数**
  - 提取指定数目的字符substr()
    - stringObject.substr(startPos,length)
    - 第一个参数必需，子串起始位置
    - 第二个参数可选，提取长度。省略默认到结尾
    - 如果参数startPos是负数，从字符串的尾部开始算起的位置。也就是说，-1 指字符串中最后一个字符，-2 指倒数第二个字符，以此类推
---   

###Math对象
提供对数据的数学计算

---
- 属性
  - E,LN2,LN10,LOG2E,LOG10E,PI,SQRT2,SQRT1_2
- 方法
  - abs(): 绝对值
  - pow(x,y)：返回x的y次幂
  - random()：返回0-1之间随机数,返回一个大于或等于 0 但小于 1 的符号为正的数字值。
  ```
<script type="text/javascript">
document.write(Math.round((Math.random())*10));
</script>
```
  - toSource()返回该对象的源代码
  - valueOf()：返回该对象的原始值
  - ceil():向上取整，它返回的是大于或等于x，并且与x最接近的整数
  - floor(): 向下取整，返回的是小于或等于x，并且与x最接近的整数
  - round(x) 方法可把一个数字四舍五入为最接近的整数
    - 对于 0.5，该方法将进行上舍入。(5.5 将舍入为 6)
    -  如果 x 与两侧整数同等接近，则结果接近 +∞方向的数字值 。(如 -5.5 将舍入为 -5; -5.52 将舍入为 -6
**Math 对象是一个固有的对象，无需创建它，直接把 Math 作为对象使用就可以调用其所有属性和方法。这是它与Date,String对象的区别**
```
<script type="text/javascript">
  var mypi=Math.PI; 
  var myabs=Math.abs(-15);
  document.write(mypi);
  document.write(myabs);
</script>
```
 - 还有一些其它方法。。。
---

###Array 数组对象
数组对象是一个对象的集合，里边的对象可以是不同类型的。数组的每一个成员对象都有一个“下标”，用来表示它在数组中的位置，是从零开始的

---
- 数组定义的方法
  - 定义了一个空数组:var  数组名= new Array();
  - 定义时指定有n个空元素的数组：var 数组名 =new Array(n);
  - 定义数组的时候，直接初始化数据var myArray = [2, 8, 6]; 
- 属性：length
- 方法:
  - concat() 
    - 用于连接两个或多个数组。此方法返回一个新数组，不改变原来的数组。
    - arrayObject.concat(array1,array2,...,arrayN)
    - 该方法不会改变现有的数组，而仅仅会返回被连接数组的一个副本
    ```
<script type="text/javascript">
  var mya1= new Array("hello!")
  var mya2= new Array("I","love");
  var mya3= new Array("JavaScript","!");
  var mya4=mya1.concat(mya2,mya3);
  document.write(mya4);
</script>
```
  - 指定分隔符连接数组元素join()
    - join()方法用于把数组中的所有元素放入一个字符串。元素是通过指定的分隔符进行分隔的
    - arrayObject.join(分隔符)
    - 参数可选，若省略，则默认用逗号分隔
    - 返回一个字符串，该字符串把数组中的各个元素串起来，用<分隔符>置于元素与元素之间。这个方法不影响数组原本的内容。
  - 颠倒数组元素顺序reverse()
    - arrayObject.reverse()
    - 该方法会改变原来的数组，而不会创建新的数组
  - 选定元素slice()
    - slice() 方法可从已有的数组中返回选定的元素
    - arrayObject.slice(start,end)
    - 返回一个新的数组，包含从 start 到 end （不包括该元素）的 arrayObject 中的元素
    - 该方法并不会修改数组，而是返回一个子数组
    - 可使用负值从数组的尾部选取元素
    - 如果 end 未被规定，那么 slice() 方法会选取从 start 到数组结尾的所有元素
  - 数组排序sort()
    - arrayObject.sort(方法函数)
    - 如果不指定<方法函数>，则按unicode码顺序排列
    - 如果指定<方法函数>，则按<方法函数>所指定的排序方法排序
    ```
降序排列
<script type="text/javascript">
   function sortNum(a,b) {
    return b-a;
   }
var myarr = new Array("80","16","50","6","100","1");
document.write(myarr.sort(sortNum));
</script>
```
---

###编程练习
 ```
<script type="text/javascript">
//通过javascript的日期对象来得到当前的日期，并输出。
  var weekday=["星期日","星期一","星期二","星期三","星期四","星期五","星期六"];
  var mydate=new Date();
  document.write(mydate.getFullYear()+"年"+(mydate.getMonth()+1)+"月"+mydate.getDate()+"日"+" "+weekday[mydate.getDay()]);
//成绩是一长窜的字符串不好处理，找规律后分割放到数组里更好操作哦
  var scoreStr = "小明:87;小花:81;小红:97;小天:76;小张:74;小小:94;小西:90;小伍:76;小迪:64;小曼:76";
  var myarr=scoreStr.split(";");
  var sum=0;
  for(var i=0;i<myarr.length;i++){
    sum += parseInt(myarr[i].substr(myarr[i].indexOf(":")+1));
  }
document.write("--班级总分为:"+sum+"<br/>");
//从数组中将成绩撮出来，然后求和取整，并输出。
document.write(Math.round(sum/myarr.length));
</script>
 ```

---
接下来就是JavaScript的核心了。好激动。终于要学新知识了。晚上继续写。

---
##window对象
window对象是BOM的核心，window对象指当前的浏览器窗口

---
###JavaScript 计时器
- 在JavaScript中，我们可以在设定的时间间隔之后来执行代码，而不是在函数被调用后立即执行
- 计时器分为一次性计时器：仅在指定的延迟时间之后触发一次。间隔性触发计时器：每隔一定的时间间隔就触发一次
- setTimeout()
- clearTimeout()
- setinterval()
- Clearinterval()

---
####计时器setInterval()
- setInterval(代码,交互时间);
  - 代码：要调用的函数或要执行的代码串
  -  交互时间：周期性执行或调用表达式之间的时间间隔，以毫秒计（1s=1000ms）
- 一个可以传递给 clearInterval() 从而取消对"代码"的周期性执行的值
- setInterval("clock()",1000)或setInterval(clock,1000)
```
<title>定时器</title>
<script type="text/javascript">
  var attime;
  //var rec=setInterval(clock,60*1000);
  function clock(){
    var time=new Date();          
    attime = time.getHours() + ":" + time.getMinutes() + ":" + time.getSeconds();
    document.getElementById("clock").value = attime;
  }
  var rec=setInterval("clock()",3000);
</script>
</head>
<body>
<form>
<input type="text" id="clock" size="50"  />
</form>
</body>
```

####取消计时器clearInterval()
- clearInterval() 方法可取消由 setInterval() 设置的交互时间
- clearInterval(id_of_setInterval)
- id_of_setInterval：由 setInterval() 返回的 ID 值
- 自己试了一下，这个作用不可逆
```
<title>计时器</title>
<script type="text/javascript">
   function clock(){
      var time=new Date();               	  
      document.getElementById("clock").value = time;
   }
    var rec = setInterval(clock,1000); //每隔一秒显示时间
</script>
</head>
<body>
  <form>
    <input type="text" id="clock" size="50"  />
    <input type="button" value="Stop" onClick="clearInterval(rec)" />//通过返回值rec使按下按钮时停止显示
  </form>
</body>
```

####计时器setTimeout()
- setTimeout()计时器，在载入后延迟指定时间后,去执行一次表达式,仅执行一次
- setTimeout(代码,延迟时间);
```
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<title>计时器</title>
</head>
<script type="text/javascript">
  var num=0;
  function startCount() {
    document.getElementById('count').value=num;
    num=num+1;
    setTimeout("startCount()",1000); 
  }
setTimeout("startCount()",1000);//调用函数自己实现计数器
function info(){
    setTimeout("alert('hello!')",5000);//单击按钮5s后出现警告窗口
}
setTimeout("alert('hello')",3000);//打开页面3秒后弹窗
</script>
</head>
<body>
<form>
<input type="text" id="count" />
<input type="button" value="start" onClick="info()" />
</form>
</body>
</html>
```

####取消计时器clearTimeout()
- setTimeout()和clearTimeout()一起使用，停止计时器
- clearTimeout(id_of_setTimeout)
- id_of_setTimeout：由 setTimeout() 返回的 ID 值。该值标识要取消的延迟执行代码块
```
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<title>计时器</title>
</head>
<script type="text/javascript">
  var num=0;
  var i;
  function startCount(){
    document.getElementById('count').value=num;
    num=num+1;
    i=setTimeout("startCount()",1000);
  }
  function stopCount(){
    clearTimeout(i);
  }
</script>
</head>
<body>
  <form>
    <input type="text" id="count" />
    <input type="button" value="Start" onClick="startCount()" />
    <input type="button" value="Stop"  onClick="stopCount()" />
  </form>
</body>
</html>
```
---

###History 对象
- history对象记录了用户曾经浏览过的页面(URL)，并可以实现浏览器前进与后退相似导航的功能
- 从窗口被打开的那一刻开始记录，每个浏览器窗口、每个标签页乃至每个框架，都有自己的history对象与特定的window对象关联- window.history.[属性|方法],其中window可以省略
- 属性：length
- 方法
  - back()
  - forward()
  - go()
---

####返回前一个浏览的页面
- back()方法，加载 history 列表中的前一个 URL
- window.history.back();
- 等同于点击浏览器的倒退按钮;等同于window.history.go(-1);
```
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<title>无标题文档</title>
</head>
 <script type="text/javascript">
        function GoBack() {
            window.history.back();    
        }
       
    </script>
</head>
<body>
点击下面的锚点链接，添加历史列表项:
    
    <br />
    <a href="#target1">第一个锚点</a>
    <a name="target1"></a>
    <br />
    <a href="#target2">第二个锚点</a>
    <a name="target2"></a>
    <br /><br />
    使用下面按钮，实现返回前一个页面:
    <form>
       <input type="button"  value="返回前一个页面" onclick="GoBack();" />        
    </form>
</body>
</html>
```
结束

####返回下一个浏览的页面
- forward()方法，加载 history 列表中的下一个 URL。如果倒退之后，再想回到倒退之前浏览的页面，则可以使用forward()方法
- window.history.forward();
- 相当于window.history.go(1);

####返回浏览历史中的其他页面
- go()方法，根据当前所处的页面，加载 history 列表中的某个具体的页面
- window.history.go(number);
```
浏览器中，返回当前页面之前浏览过的第二个历史页面，代码如下：window.history.go(-2);和在浏览器中单击两次后退按钮操作一样。
返回当前页面之后浏览过的第三个历史页面，代码如下：window.history.go(3);
```
---

###location对象
- location用于获取或设置窗体的URL，并且可以用于解析URL
- location.[属性|方法]
- window.location.href="http://misok.github.io"//设置窗体的URL
---

###Navigator对象
- Navigator 对象包含有关浏览器的信息，通常用于检测浏览器与操作系统的版本
```
<script type="text/javascript">
 document.write(navigator.appName+"<br/>");
 document.write(navigator.appVersion+"<br/>");
 document.write(navigator.platform+"<br/>")
 document.write(navigator.appCodeName+"<br/>")
 document.write(navigator.userAgent);
</script>
显示结果：
Netscape
5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/39.0.2171.71 Safari/537.36
Win32
Mozilla
Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/39.0.2171.71 Safari/537.36
```
- userAgent:返回用户代理头的字符串表示(就是包括浏览器版本信息等的字符串)
```
<script type="text/javascript">
  function validB(){ 
    var u_agent =navigator.userAgent; 
    var B_name="不是想用的主流浏览器!"; 
    if(u_agent.indexOf("Firefox")>-1){ 
        B_name="Firefox"; 
    }else if(u_agent.indexOf("Chrome")>-1){ 
        B_name="Chrome"; 
    }else if(u_agent.indexOf("MSIE")>-1&&u_agent.indexOf("Trident")>-1){ 
        B_name="IE(8-10)";  
    }
        document.write("浏览器:"+B_name+"<br>");
        document.write("u_agent:"+u_agent+"<br>"); 
  } 
</script>
</head>
<body>
  <form>
     <input type="button" value="查看浏览器" onClick="validB()"  >
  </form>
</body>
```
以上代码用于测试浏览器版本信息
---

###screen对象
- screen对象用于获取用户的屏幕信息
- window.screen.属性

---

####屏幕分辨率的高和宽
- screen.height 返回屏幕分辨率的高
- screen.width 返回屏幕分辨率的宽
- 单位以像素计
- window.screen 对象在编写时可以不使用 window 这个前缀
```
<script type="text/javascript">
document.write( "屏幕宽度："+window.screen.width);
document.write( "屏幕高度："+window.screen.height);  </script>
```

####屏幕可用高和宽度
- screen.availWidth 属性返回访问者屏幕的宽度，以像素计，减去界面特性，比如任务栏
-  screen.availHeight 属性返回访问者屏幕的高度，以像素计，减去界面特性，比如任务栏
-  不同系统的任务栏默认高度不一样，及任务栏的位置可在屏幕上下左右任何位置，所以有可能可用宽度和高度不一样。
```
<script type="text/javascript">
document.write("可用宽度：" +window.screen.availWidth );
document.write("可用高度：" +window.screen.availHeight );     
</script>
```
---

###编程练习
要求：
1. 如果打开该页面后，如果不做任何操作则5秒后自动跳转到一个新的地址，如慕课网主页。

2. 如果点击“返回”按钮则返回前一个页面
```
<!DOCTYPE html>
<html>
 <head>
  <title>浏览器对象</title>  
  <meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>   
 </head>
 <body>
  <!--先编写好网页布局-->
  <h1>操作成功</h1>
  <span id="second">5</span>秒后回到主页<a href="javascript:backwin()" >返回</a>
<script type="text/javascript">  
//获取显示秒数的元素，通过定时器来更改秒数。
    var n=document.getElementById("second");
    var i=5;
    function openwin(){
        i--;
        n.innerHTML=i;
        if(i==1){
            window.location.href="http://www.imooc.com";
        }
    }
    setInterval(openwin,1000);
    //通过window的location和history对象来控制网页的跳转    function backwin(){
       window.history.go(-1);
   }
</script> 
</body>
</html>
```
---
##DOM对象
简介在基础篇已经说过了，现在来看点具体的。
- 节点属性
  - nodeName:返回一个字符串，其内容是给定节点的名字
  - nodeType:返回一个整数，代表给定节点的类型
  - nodeValue:返回给定节点的当前值
- 节点方法
  - childNodes:返回一个数组，这个数组由给定元素节点的子节点构成
  - firstChild:返回第一个子节点
  - lastChird:返回最后一个子节点
  - parentNode:返回一个给定节点的父节点
  - nextSibling：返回给定节点的下一个子节点
  - previousSibling:返回给定节点的上一个子节点
---

###getElementsByName()方法
- 返回带有指定名称的节点对象的集合
- document.getElementsByName(name)
- 因为文档中的 name 属性可能不唯一，所有 getElementsByName() 方法返回的是元素的数组，而不是一个元素
- 和数组类似也有length属性，可以和访问数组一样的方法来访问，从0开始
```
<script type="text/javascript">
function getnum(){
  var mynode=document.getElementsByName("myt");  
  alert(mynode.length);
}
</script>
</head>
<body>
<input name="myt" type="text" value="1">
<input name="myt" type="text" value="2">
<input name="myt" type="text" value="3">
<input name="myt" type="text" value="4">
<input name="myt" type="text" value="5">
<input name="myt" type="text" value="6">
<br />
<input type="button" onclick="getnum()" value="看看有几项？" />
</body>
```

###getElementsByTagName()方法
- getElementsByTagName(Tagname)
- Tagname是标签的名称，如p、a、img等标签名

###三种获取元素的方法比较
以人来举例说明，人有能标识身份的身份证，有姓名，有类别(大人、小孩、老人)等
- ID 是一个人的身份证号码，是唯一的。所以通过getElementById获取的是指定的一个人
- Name 是他的名字，可以重复。所以通过getElementsByName获取名字相同的人集合
- TagName可看似某类，getElementsByTagName获取相同类的人集合。如获取小孩这类人，getElementsByTagName("小孩")
```
<body>
        <form>
          请选择你爱好:<br>
          <input type="checkbox" name="hobby" id="hobby1" >  音乐
          <input type="checkbox" name="hobby" id="hobby2">  登山
          <input type="checkbox" name="hobby" id="hobby3">  游泳
          <input type="checkbox" name="hobby" id="hobby4">  阅读
          <input type="checkbox" name="hobby" id="hobby5">  打球
          <input type="checkbox" name="hobby" id="hobby6">  跑步 <br>
          <input type="button" value = "全选" onclick = "checkall()">
          <input type="button" value = "全不选" onclick = "clearall()">
          <p>请输入您要选择爱好的序号，序号为1-6:</p>
          <input id="wb" name="wb" type="text" >
          <input name="ok" type="button" value="确定" onclick = "checkone()">
        </form>
        <script type="text/javascript">
        function checkall(){
            var hobby = document.getElementsByTagName("input");
           
          // 任务1 
          for(var i=0;i<hobby.length;i++){
              if(hobby[i].type=="checkbox")
              {
                  hobby[i].checked=true;
              }
          }
        }
        function clearall(){
            var hobby = document.getElementsByName("hobby");
            
         // 任务2    
           for(var i=0;i<hobby.length;i++){
              if(hobby[i].type=="checkbox")
              {
                  hobby[i].checked=false;
              }
          } 
        }
        
        function checkone(){
            var j=document.getElementById("wb").value;
        
         // 任务3
        var hobby = document.getElementsByName("hobby");
       
        hobby[parseInt(j)-1].checked=true;
              
        }
        
        </script>
    </body>
</html>
```

###getAttribute()方法
- 通过元素节点的属性名称获取属性的值
- elementNode：使用getElementById()、getElementsByTagName()等方法，获取到的元素节点
-  name：要想查询的元素节点的属性名字
```
<body>   
<p id="intro">课程列表</p>  
    <ul>  
        <li title="第1个li">HTML</li>  
        <li>CSS</li>  
        <li title="第3个li">JavaScript</li>  
        <li title="第4个li">Jquery</li>  
        <li>Html5</li>  
    </ul>  
<p>以下为获取的不为空的li标签title值:</p>
<script type="text/javascript">
    var con=document.getElementsByTagName("li");
    for (var i=0; i< con.length;i++){
      var text=con[i].getAttribute("title");
      if(text!=null)
      {
        document.write(text+"<br>");
      }
    } 
 </script> 
</body>
```

###setAttribute()方法
- setAttribute() 方法增加一个指定名称和值的新属性，或者把一个现有的属性设定为指定的值
- elementNode.setAttribute(name,value)
- name: 要设置的属性名
- value: 要设置的属性值
- 把指定的属性设置为指定的值。如果不存在具有指定名称的属性，该方法将创建一个新属性
- 类似于getAttribute()方法，setAttribute()方法只能通过元素节点对象调用的函数
```
<body>
  <p id="intro">我的课程</p>  
  <ul>  
    <li title="JS">JavaScript</li>  
    <li title="JQ">JQuery</li>  
    <li title="">HTML/CSS</li>  
    <li title="JAVA">JAVA</li>  
    <li title="">PHP</li>  
  </ul>  
  <h1>以下为li列表title的值,当title为空时，新设置值为"WEB前端技术":</h1>
<script type="text/javascript">
  var Lists=document.getElementsByTagName("li");
  for (var i=0; i<Lists.length;i++)
  {
    var text=Lists[i].getAttribute("title");
    document.write(text +"<br>");
    if(text=="")
    {
    Lists[i].setAttribute("title","WEB前端技术");
    document.write(Lists[i].getAttribute("title")+"<br>");
    }
  }
</script>
</body>
```
参见前面取消设置的例子，再加深理解setAttribute的功能
---

###节点属性
在文档对象模型 (DOM) 中，每个节点都是一个对象。DOM 节点有三个重要的属性
-  nodeName : 节点的名称，是只读的
  - 元素节点的nodeName 与标签名相同
  - 属性节点的 nodeName 是属性的名称
  - 文本节点的 nodeName 永远是 #text
  - 文档节点的 nodeName 永远是 #document
- nodeValue 属性：节点的值
  - 元素节点的 nodeValue 是 undefined 或 null
  - 文本节点的 nodeValue 是文本自身
  - 属性节点的 nodeValue 是属性的值
- nodeType 属性: 节点的类型，是只读的。以下常用的几种结点类型

| 元素类型 |节点类型 |
| :------- | :-------: |
| 元素 | 1 |
| 属性 | 2 |
| 文本 | 3 |
| 注释 | 8 |
| 文档 | 9 |
 ```
<title>节点属性</title>
</head>
<body>
  <ul>
     <li>javascript</li>
     <li>HTML/CSS</li>
     <li>jQuery</li>     
  </ul>
  <script type="text/javascript">
   var item=document.getElementsByTagName("li");
   for(var i=0;i<item.length;i++){
       document.write(item[i].nodeName+"<br/>");
       document.write(item[i].nodeValue+"<br/>");
       document.write(item[i].nodeType+"<br/>");
       
    }
</script>
 ```
###访问子结点childNodes
访问选定元素节点下的所有子节点的列表，返回的值可以看作是一个数组，他具有length属性
- elementNode.childNodes
- 如果选定的节点没有子节点，则该属性返回不包含节点的 NodeList
```
<title>无标题文档</title>
</head>
<body>
<div>
  javascript  
  <p>javascript</p>
  <div>jQuery</div>
  <h5>PHP</h5>
</div>
<script type="text/javascript">
 var item=document.getElementsByTagName("div")[0].childNodes;
 for(var i=0;i<item.length;i++){
     document.write(item[i].nodeType+item[i].nodeName+item[i].nodeValue+"<br/>");
 }
</script>
```
这里存在一个浏览器兼容性的问题，看上面代码，如果是IE，则正常输出,其他浏览器的输出像这样：
```
3#text javascript 
1Pnull
3#text 
1DIVnull
3#text 
1H5null
3#text 
```
**因为其他浏览器中，元素之间的空白符是算成文本节点的**

###访问子结点的第一和最后项
- firstChild 属性返回‘childNodes’数组的第一个子节点。如果选定的节点没有子节点，则该属性返回 NULL。
- node.firstChild
- 与elementNode.childNodes[0]是同样的效果
-  lastChild 属性返回‘childNodes’数组的最后一个子节点。如果选定的节点没有子节点，则该属性返回 NULL
-  node.lastChild
-  与elementNode.childNodes[elementNode.childNodes.length-1]是同样的效果
```
<title>无标题文档</title>
</head>
<body>
<div id="con"><p>javascript</p><div>jQuery</div><h5>PHP</h5></div>
<script type="text/javascript">
  var x=document.getElementById("con");
  document.write(x.firstChild.nodeName+"<br/>");
  document.write(x.lastChild.nodeName);
 </script>
```
上一节所说浏览器兼容问题，如果代码写成如上样子，则每个浏览器输出结果相同

###访问父节点parentNode
- elementNode.parentNode
- 访问祖节点:elementNode.parentNode.parentNode
```
//试一试，通过获取的mylist节点，使用访问父节点parentNode，将"HTML/CSS"课程内容输出
<body>
<ul id="con">
<li id="lesson1">javascript
  <ul> 
      <li id="tcon"> 基础语法</li>
      <li>流程控制语句</li>
      <li>函数</li>
      <li>事件</li>
      <li>DOM</li>
  </ul>
</li>
<li id="lesson2">das</li>
<li id="lesson3">dadf</li>
<li id="lesson4">HTML/CSS 
  <ul>
    <li>文字</li>
    <li>段落</li>
    <li>表单</li>
    <li>表格</li>  
  </ul> 
</li></ul>  
<script  type="text/javascript">    
   var mylist = document.getElementById("tcon"); 
   document.write(mylist.parentNode.parentNode.parentNode.lastChild.innerHTML);
</script> 
</body>
```

###访问兄弟节点
nextSibling 属性可返回某个节点之后紧跟的节点（处于同一树层级中）
- nodeObject.nextSibling
- 如果无此节点，则该属性返回 null

previousSibling 属性可返回某个节点之前紧跟的节点（处于同一树层级中）
- nodeObject.previousSibling 
- 如果无此节点，则该属性返回 null

**两个属性获取的是节点。Internet Explorer 会忽略节点间生成的空白文本节点（例如，换行符号），而其它浏览器不会忽略**
 ```
<body>
<ul id="u1">   
            <li id="a">javascript</li>   
            <li id="b">jquery</li>   
            <li id="c">html</li>   
        </ul>   
        <ul id="u2">   
            <li id="d">css3</li>   
            <li id="e">php</li>   
            <li id="f">java</li>   
        </ul>   
<script type="text/javascript">
    function get_nextSibling(n){
        var x=n.nextSibling;
        //过滤子节点，因为浏览器兼容性问题产生的空白元素
        while (x && x.nodeType!=1){
            x=x.nextSibling;
        }
        return x;
    }
    var x=document.getElementsByTagName("li")[0];
    document.write(x.nodeName);
    document.write(" = ");
    document.write(x.innerHTML);
    var y=get_nextSibling(x);
    if(y!=null){
        document.write("<br />nextsibling: ");
        document.write(y.nodeName);
        document.write(" = ");
        document.write(y.innerHTML);
    }else{
      document.write("<br>已经是最后一个节点");      
    }
</script>
</body>
 ```

###插入节点appendChild()
- 在指定节点的最后一个子节点列表之后添加一个新的子节点
- appendChild(newnode)
- newnode：指定追加的节点。
```
<body>
<ul id="test">
  <li>JavaScript</li>
  <li>HTML</li>
</ul> 
<script type="text/javascript">
  var otest = document.getElementById("test");  
  var newnode=document.createElement("li");
  newnode.innerHTML="PHP";
  otest.appendChild(newnode);
</script> 
</body>
```

###插入节点insertBefore()
- insertBefore() 方法可在已有的子节点前插入一个新的子节点
- insertBefore(newnode,node);
- newnode: 要插入的新节点
- node: 指定此节点前插入节点
```
<body>
<ul id="test"><li>JavaScript</li><li>HTML</li></ul> 
 <script type="text/javascript">
  var otest = document.getElementById("test");  
  var newnode = document.createElement("li");
  newnode.innerHTML = "PHP";
  otest.insertBefore(newnode,otest.childNodes[0]);
</script> 
</body>
```

###删除节点removeChild()
- removeChild() 方法从子节点列表中删除某个节点。如删除成功，此方法可返回被删除的节点，如失败，则返回 NULL
- nodeObject.removeChild(node)
- 删除的子节点不在DOM树中，但是还存在内存中，可通过返回值操作，如果要完全删除对象，返它null 值
```
<body>
<div id="content">
  <h1>html</h1>
  <h1>php</h1>
  <h1>javascript</h1>
  <h1>jquery</h1>
  <h1>java</h1>
</div>
<script type="text/javascript">
function clearText() {
  var content=document.getElementById("content");
  // 在此完成该函数
   for(var i=content.childNodes.length-1;i>=0;i--){
     var childNode = content.childNodes[i];
     content.removeChild(childNode);
  }
}
</script>
<button onclick="clearText()">清除节点内容</button>
</body>
```

###替换元素节点replaceChild()
- replaceChild 实现子节点(对象)的替换。返回被替换对象的引用
- node.replaceChild (newnode,oldnew ) 
- 当 oldnode 被替换时，所有与之相关的属性内容都将被移除
```
<body>
<div><b id="oldnode">JavaScript</b>是一个很常用的技术，为网页添加动态效果。</div>
  <a href="javascript:replaceMessage()"> 将加粗改为斜体</a>
 <script type="text/javascript">
      function replaceMessage(){
         var oldnode=document.getElementById("oldnode");
           var oldHTML= oldnode.innerHTML;           
           var newnode=document.createElement("i");         
           oldnode.parentNode.replaceChild(newnode,oldnode);
           newnode.innerHTML=oldHTML;}
  </script>
```

###创建元素节点createElement
- createElement()方法可创建元素节点。此方法可返回一个 Element 对象
- document.createElement(tagName)
- tagName：字符串值，这个字符串用来指明创建元素的类型
- 要与appendChild() 或 insertBefore()方法联合使用，将元素显示在页面中
```
<script type="text/javascript">
var main = document.body;
//创建链接
var body=document.body;
function createa(url,text)
{
    var a=document.createElement("a");
    a.href=url;
    a.innerHTML=text;
    a.style.color="red";
    body.appendChild(a);
}
// 调用函数创建链接
createa("http://misok.github.io","我的博客");
</script> 
```

###创建文本节点createTextNode
- createTextNode() 方法创建新的文本节点，返回新创建的 Text 节点
- document.createTextNode(data)
- data : 字符串值，可规定此节点的文本
```
<title>无标题文档</title>
<style type="text/css">
.message{    
	width:200px;
	height:100px;
	background-color:#CCC;}
</style>
</head>
<body>
<script type="text/javascript">
var p =document.createElement("p");
p.className="message";
var textnode=document.createTextNode("I love javascript");
p.appendChild(textnode);
document.body.appendChild(p);
</script> 
```

###浏览器窗口可视区域大小
获得浏览器窗口的尺寸（浏览器的视口，不包括工具栏和滚动条）的方法
- 对于IE9+、Chrome、Firefox、Opera 以及 Safari
  -  window.innerHeight - 浏览器窗口的内部高度
  -  window.innerWidth - 浏览器窗口的内部宽度
- 对于 Internet Explorer 8、7、6、5
  - document.documentElement.clientHeight表示HTML文档所在窗口的当前高度
  - document.documentElement.clientWidth表示HTML文档所在窗口的当前宽度
- Document对象的body属性对应HTML文档的<body>标签
  - document.body.clientHeight
  - document.body.clientWidth
- 在不同浏览器都实用的 JavaScript 方案:
  - var w= document.documentElement.clientWidth|| document.body.clientWidth;
  - var h= document.documentElement.clientHeight|| document.body.clientHeight;

###网页尺寸scrollHeight
- scrollHeight和scrollWidth，获取网页内容高度和宽度(不包括滚动条)
- 针对IE、Opera:scrollHeight 是网页内容实际高度，可以小于 clientHeight。
- 针对NS、FF:scrollHeight 是网页内容高度，不过最小值是 clientHeight。也就是说网页内容实际高度小于 clientHeight 时，scrollHeight 返回 clientHeight
- 兼容写法：
  - var w=document.documentElement.scrollWidth|| document.body.scrollWidth;
  - var h=document.documentElement.scrollHeight|| document.body.scrollHeight;
  - scrollHeight和scrollWidth还可获取Dom元素中内容实际占用的高度和宽度
 

###网页尺寸offsetHeight
- offsetHeight和offsetWidth，获取网页内容高度和宽度(包括滚动条等边线，会随窗口的显示大小改变)
- offsetHeight = clientHeight + 滚动条 + 边框。
- 浏览器兼容性
  - var w= document.documentElement.offsetWidth|| document.body.offsetWidth;
  - var h= document.documentElement.offsetHeight|| document.body.offsetHeight;
  

###网页卷去的距离与偏移量
![Alt text](./1.jpg)

- scrollLeft:设置或获取位于给定对象左边界与窗口中目前可见内容的最左端之间的距离 ，即左边灰色的内容
- scrollTop:设置或获取位于对象最顶端与窗口中可见内容的最顶端之间的距离 ，即上边灰色的内容
- offsetLeft:获取指定对象相对于版面或由 offsetParent 属性指定的父坐标的计算左侧位置
- offsetTop:获取指定对象相对于版面或由 offsetParent 属性指定的父坐标的计算顶端位置 
- 区分大小写
- offsetParent：布局中设置postion属性(Relative、Absolute、fixed)的父容器，从最近的父节点开始，一层层向上找，直到HTML的body
```
<!DOCTYPE HTML>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<script type="text/javascript">
    function req(){
          var div = document.getElementById("div1");
          document.getElementById("li1").innerHTML = (div.offsetTop)+"px";//div1距离屏幕顶部的距离
          document.getElementById("li2").innerHTML = (div.offsetLeft)+"px";//div1距离屏幕左部的距离
          document.getElementById("li3").innerHTML = (div.scrollTop)+"px";//div1纵向滚动条滚动的距离
          document.getElementById("li4").innerHTML = (div.scrollLeft)+"px";//div1横向滚动条滚动的距离
     }
</script>
</head>
<body style="border:10px solid #ccc;padding:0px 0px;margin:5px 10px">
    <div style="width:60%;border-right:1px dashed red;float:left;">
        <div style="float:left;">
            <div id="div1" style="border:5px red solid;height:300px;width:200px;overflow:auto">
                <div style="height:500px;width:400px">请调整横竖滚动条后，点击按钮后查看offsetTop、offsetLeft、scrollTop、scrollLeft值。</div>
            </div>
            <input type="button" value="点击我!" onclick="req()" style="border: 1px solid purple;height: 25px;"/>
        </div>
        
    </div>
    <div style="width:30%;float:left;">
        <ul style="list-style-type: none; line-height:30px;">结果：
            <li>offsetTop : <span id="li1"></span></li>
            <li>offsetLeft : <span id="li2"></span></li>
            <li> scrollTop : <span id="li3"></span></li>
            <li>scrollLeft : <span id="li4"></span></li>
        </ul>
        
    </div>
    <div style="clear:both;"></div>    
</body>
</html>
```

###编程练习
 ```
<!DOCTYPE html>
<html>
 <head>
  <title> new document </title>  
  <meta http-equiv="Content-Type" content="text/html; charset=gbk"/>   
  <script type="text/javascript"> 
  window.onload = function(){
// 鼠标移动改变背景,可以通过给每行绑定鼠标移上事件和鼠标移除事件来改变所在行背景色。
    var item = document.getElementsByTagName("tr");
    for(var i=0;i<item.length;i++){
        item[i].onmouseover=function(){
            this.style.backgroundColor="#f2f2f2";
        }  
        item[i].onmouseout=function(){
            this.style.backgroundColor="#fff";
        }
    }
}
// 编写一个函数，供添加按钮调用，动态在表格的最后一行添加子节点；
    function addline(obj){
        var tbody = document.getElementById("table").lastChild;
        var tr=document.createElement("tr");
        var td1=document.createElement("td");
        td1.innerHTML="<input type='text' />";
        tr.appendChild(td1);
        var td2=document.createElement("td");
        td2.innerHTML="<input type='text ' />";
        tr.appendChild(td2);
        var td3=document.createElement("td");
        td3.innerHTML="<a href='javascript:;' onclick='removeline(this)'>删除</a>"
        tr.appendChild(td3);
        tbody.appendChild(tr);
    } 
 // 创建删除函数
    function removeline(obj){
        var tbody = document.getElementById('table').lastChild;  
    	var tr = obj.parentNode.parentNode;
		 tbody.removeChild(tr);
    } 
</script> 
 </head> 
 <body> 
	   <table border="1" width="50%" id="table">
	   <tr>
		<th>学号</th>
		<th>姓名</th>
		<th>操作</th>
	   </tr> 
	   <tr>
		<td>xh001</td>
		<td>王小明</td>
		<td><a href="javascript:;" onclick="removeline(this)" >删除</a></td>   <!--在删除按钮上添加点击事件  -->
	   </tr>

	   <tr>
		<td>xh002</td>
		<td>刘小芳</td>
		<td><a href="javascript:;" onclick="removeline(this)" >删除</a></td>   <!--在删除按钮上添加点击事件  -->
	   </tr>  
	   </table>
	   <input type="button" value="添加一行" onClick="addline()" />   <!--在添加按钮上添加点击事件  -->
 </body>
</html>
 ```
 




