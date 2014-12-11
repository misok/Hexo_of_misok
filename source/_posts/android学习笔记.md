title: android学习笔记
date: 2014-11-8
categories: Android
tags: [android, 笔记]

---
最近课程需要，大致了解了下android，虽然刚开始被环境搞定有点崩溃，但是几天学完后发现还蛮有意思的。写了点笔记，非常粗略，自用。
<!-- more -->
---
##1.环境搭建

- jdk（6.0以后版本）
- eclipse
- SDK
- ADT(提供模拟器、提供程序界面视图)
---
##2.项目结构介绍
###2.1新建Android工程

###2.2工程目录介绍
![工程目录介绍](/img/目录.png)

- src:存放Java源代码
- gen：存放系统自动生成的配置文件
- andriod4.4.2：包含andriod.jar文件，这是一个Java归档文件，其中包含构建应用程序所需的所有的andriod SDK库和APIs
- assets：存放资源文件，（音频，图片），不会自动生成id且不会自动占用空间
- bin：存放应用编译后生成的可执行文件（.apk），以及应用用到被打包到apk中的资源文件
- libs：第三方架包
- res：存放应用用到 所有资源，如图片布局等等（占用apk的大小）
  1. drawable：存放不同密度的图片资源
  2. layout：存放布局文件
  3. menu：存放菜单布局文件
  4. values：存放字符串、主题、颜色、样式等资源文件
- AndriodManifest.xml：清单文件，配置一些与应用有关的重要信息，包含包名、权限、程序组件等等
---
##3.控件概述

- TextView:显示文本框控件
  - id
  - layout_width
  - 。。。
- EditView：输入文本框
  - 输入类型
	
		姓名：请输入姓名
		
		
- ImageView
     - src：图片内容
     - background：图片背景
     - 手机模拟器的分辨率不一样，调用的图片是对应的分辨率。对应于res-drawable不同文件夹下的不同分辨率图片
    
- 按钮概述
     - Button
           1. 都可以作为按钮产生点击事件
           2. 有text属性
     - ImageButton(图片按钮)
            1. 有src属            性
            2. 都有background属性
            3. 都有明显的点击效果
- 按钮监听事件
     - onClick
  
  
  		    监听事件的几种实现方法
  		        1. 匿名内部类 
  		        2. 独立类监听
  		        3. 接口方式监听
- AutoCompleteTextView（动态匹配输入文本）


		得设置android：completetionThreshold="2"(输入多少字符以后提示)
- MultiAutoCompleteTextView（支持多选）


		不仅要设置上面属性，还要设置分隔符，即用什么分隔选择的多个属性
		  mtxt:setTokenizer....
		  
- ToggleButton:选中和未选中
     - checked
     - textoff
     - texton
- RadioButton
- RadioGroup:提供多选一的机制，一组radioButoon
     - orientation=vertical：垂直排布
     - horizontal：水平排布
 ---   
##4.布局讲解


###1. 线性布局LinearLayout
- 子空间以横向排布或者竖向排布
- orientation决定排布
       1. horizontal：水平排布
       2.vertical：垂直排放
   
- gravity：决定子类控件的x,y坐标为位置
        1. 垂直居中
        2. 水平居中
		3. 底部显示
		4. 靠右
		5. 靠左
	注意：可以多属性连用，用|隔开
- layout_gravity:指本身控件的坐标位置
- layout_weight:控件所占父容器比例
     
     **布局可以嵌套使用**


###2.RelativeLayout：相对布局
- 它包含的子控件将以控件之间的相对位置或者子类控件相对父类容器的位置的方式排列
- 反正就是一堆属性慢慢看

###3.帧布局FrameLayout
- 所有的元素都不能被指定放置的位置，它们统统放在这块区域的左上角，后面的子元素直接覆盖前面的子元素，将前面的子元素部分和全部遮挡

###4绝对布局AbsoluteLayout
- 又可以叫坐标布局，可以直接指定子元素的绝对位置
- 开发中很少用（适配性较差）


###5TableLayout表格布局
- 以行列的形式管理子控件，每一行为一个TableRow的对象，当然也可以是一个View对象
- layout：
---
##4.认识Activity
- 是一个应用程序组件，提供用户与程序交的界面

         安卓四大组件：
        - Activity
        - Service
        - BroadcastReceiver
        - ContenProvider

- 如何创建使用
     - 继承安卓的Activity类
     - 重写Oncreate方法
     - 设置显示布局
     - 在AndroidManifes文件中注册

- Activity生命周期
   
   ![生命周期](/img/生命周期.png)
- Activity的四种状态
     - 活动状态，处于界面最顶端，获取到了焦点
     - 暂停状态：（弹出一个对话框或者半透明activity时）失去焦点，但对用户可见
     - 停止状态：（按下home键或者弹出一个新的activity）完全被遮挡，但保留所有状态和成员信息
     - 非活动状态：被销毁了
---
##5页面跳转

###什么是intent
可以理解为一个信使；由intent来协助完成安卓各组件之间的通信
           
    intent实现页面之间的跳转：
    1.startActivity（intent）：无返回结果
    2.startActivityForResult（intent，requestCode）：有返回结果
       - 通过此方法启动还需要两个方法：onActivityResult（int requestCode，int resultCode，Intent data）
       - setResult（resultCode，data）
    
    例如：现在我想要实现一个无返回结果的跳转，步骤如下：
    1. 创建一个新的类（主Activity），书写Oncreate方法
    2.给这个新的类创建一个对应的xml文件，其中包含一个button
    3.去Manifest文件注册这个类，使它成为主Activity
    4.以同样的以上三步创建待跳转页面的Activity，注意去掉其中的主Activity属性
    5。在主Activity里面注册button的监听器（注意需要button对象和监听器，用内部类方法实现监听动作）
    6.使按下按钮就跳转到另外一个页面（首先需要一个intent（注意intent的参数，第一个为主页面，第二个为目标页面），然后需要用stratActivity（intent）方法启动）
    

---
##app签名打包

###签名的意义：
- 为了保证每个应用程序开发者的合法
- 防止部分人通过使用相同的PackageName来混淆替换已经安装的程序，从而出现一些恶意篡改
- 保证每次发布的版本的一致性

###签名的步骤
- 导出需要签名的工程
- 在Keystore selection界面进行签名
     - location：表示签名文件的存放位置
     - password：签名密码
     - 确认密码
- 下一步
- 填写一些信息（最后一项CN）
- 下一步：生成apk文件的位置（已签名的应用程序）

---
##使用SDK开发文档

SDK开发文档的位置：SDK--》docs--》index.xml--》打开
可以下载中文版
 

	