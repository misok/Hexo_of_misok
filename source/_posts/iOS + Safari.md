title: 手机端网页调试方案（iOS&android）
date: 2015-7-07
categories: 前端开发
tags: [调试]

---
```
写作目的：
在人人离不开手机的年代，不适配移动端的网页都不好意思混了。
作为一个严谨追求完美的程序员，怎么能不会手机端调试呢。毕竟这里面还是有很多坑的。
有时候觉得生的真好，据说12年以前手机端调试是很麻烦的。现在已经有一些较成熟的方案。
最后，以后博客要改比较活泼的文风。以前有点过于严肃了呢。
厄，还有，这不是一篇整理总结性文章。只是我目前知道的一些方法，欢迎补充。
```
<!-- more -->
## iOS + Safari
---
####1.打开手机web检查器
**设置 >> Safari >> 高级 >> web检查器**
![Alt text](/img/2.pic.jpg)
####2.在手机Safari中打开将要调试的网页
- 如果你的网页是线上能访问到的网址，请直接输入
- 如果是未上线的本地网页，则需要配置
	- 首先你得有Python（没安装的请自行搜素或者brew安装）
	- 在terminal中cd到待调试网页的项目目录下。敲下面命令：
	```
	python -m SimpleHTTPServer //python2.x
	python3 -m http.serve      //Python3
	```
- 查看本机IP（使用ifconfig）
	![Alt text](/img/屏幕快照 2015-07-08 下午9.08.41.png)
- 在手机safari输入访问地址（本地IP:8000),比如我的就是http://10.128.97.196:8000/prototype/（我的待访问页面放在prototype文件下）
**请注意：这里得保证手机网络跟电脑网络处于同一网段下**
- 用数据线连接手机到电脑

####3.在MAC上打开Safari,点击开发（develop）菜单，选择自己的手机设备
![Alt text](/img/屏幕快照 2015-07-10 下午5.27.22.png)
####4.点击图中蓝色网址，打开Safari控制台
![Alt text](/img/屏幕快照 2015-07-10 下午5.29.17.png)
####5.OK，可以调试了，手机会实时显示样式和修改

---
##andriod + Weinre（web in spector remote）
这个工具的[原理和结构](http://blog.csdn.net/dojotoolkit/article/details/6280924)请参见这篇文章，这里只说如何调试

####1.安装

 ```
 sudo npm install -g weinre
 ```
####2.启动

 ```
weinre --boundHost -all-
```
ok，这行命令在本机启动了weinre的Debug服务端，端口为8081。打开Chrome或Safari，访问localhost:8081，就可以看到weinre的基本信息。如下图：
![Alt text](/img/屏幕快照 2015-07-08 下午8.30.34.png)

####3.用手机打开待测试网页
- 首先，terminal中cd到项目地址
- 输入如下代码
```
python -m SimpleHTTPServer //python2.x
python3 -m http.serve      //Python3
```
- 这时终端提示server启动成功
    ![Alt text](/img/屏幕快照 2015-07-08 下午9.05.53.png)
- 查看本机IP（使用ifconfig）
	![Alt text](/img/屏幕快照 2015-07-08 下午9.08.41.png)
- 在手机浏览器输入访问地址（本地IP:8000),比如我的就是http://10.128.97.196:8000/prototype/（我的待访问页面放在prototype文件下）
**请注意：这里得保证手机网络跟电脑网络处于同一网段下**
	![Alt text](/img/7E536C863E4A813DF4944DA343ED92E1.jpg)


####4.链接weinre
至此，我们已经分别在localhost:8080端口打开了weinre,在手机上打开了待调试页面所在文件，接下来我们需要用weinre去检测待调试网页。方法就是，在调试网页的JS文件中加一句话。
	```
		<script src="http://10.128.97.196:8080/target/target-script-min.js#anonymous"></script>
	```
**其中10.128.97.196换成自己的ip地址**
####5.开始调试
点击debug client user interface 后的网址
![Alt text](/img/屏幕快照 2015-07-08 下午9.23.39.png)
出现上面页面，Targets下如果显示网址，则表示成功，点击这个网址变绿后就表示进入调试状态，然后点击Elements开始调试。这时电脑调试会同步在手机上。好啦，我们可以开始调试了。

#####注意：如果Targets显示none，有可能是以下原因：
1.手机跟电脑网络不在同一网段
2.检查网页中引入的JS中ip地址改了没有
3.刷新下手机网页**

---
##虚拟机调试：Genymotion
如果你没有android手机，或者项目要求的andriod版本号较早的话，我们就要用到模拟器。这里推荐Genymotion.

使用方法：
1. [下载安装Genymotion](https://www.genymotion.com/#!/download)(我好喜欢这个网站的主页颜色，心情超好的)
![Alt text](/img/屏幕快照 2015-07-10 下午5.10.15.png)
2. 添加一个虚拟机，点击上图Add
![Alt text](/img/屏幕快照 2015-07-10 下午5.11.24.png)
选择需要的版本，点击NEXT
3. 添加成功后会在首页显示
![Alt text](/img/4AADC3E7-C5E2-4146-A007-2433F3B017CF.png)
选择新 添加的虚拟机，点击Strart或者双击运行
4. 打开虚拟机的浏览器，在地址栏输入待测试网页，也就是这时候你把这个虚拟机当成真机，接下来的步骤跟上面真机调试一样啦。
![Alt text](/img/5BF4B498-9847-47EB-B5C0-CF0F6D0D228A.png)

###补充
另外据说第一种iOS的方法已经过时了，有新方法大家参考这篇吧。
[BrowserSync实时同步更新CSS、JS文件，全平台支持](http://www.codingserf.com/index.php/2015/03/browsersync/)
