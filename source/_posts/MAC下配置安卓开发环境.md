title: mac下安装安卓开发环境
date: 2014/11/05
categories: Android
tags: [mac, android, 环境]


---
这两天配置安卓环境，看上去蛮简单的，但是遇到了好多问题，看网上很多教程都写的比较简单，所以来写一个详细点的。

---
<!-- more -->
## 需要的东西
###1.JDK 

**注意：这里有一个问题，mac从某一版本之后就取消了集成的jdk，所以需要下载。具体哪一版本我忘记了，如果你是10.几以后那肯定没有。**

测试办法：终端输入： java -version

如果显示   java version "1.6.0_65"类似，说明你的电脑已经安装了jdk，否则，请移步官网安装。
<http://www.oracle.com/technetwork/java/javase/downloads/index.html>
        
###2.Eclipse ADT
###3.SDK

网上很多教程都教分别下载以上东西，android官网已经把他们集成为ADT Bundle了，非常方便，可以直接下载。下载地址：
<http://developer.android.com/sdk/index.html>

下载时一般网站会自动识别你的系统平台，如果有需要，可以直接点击页面下面view all downloads and sizes查看其他平台。或者可以单独下载SDK

![view](/img/download.png)


注意下载完成后不要把文件分开放。

###下载后的内容包括：
Eclipse + ADT plugin
Android SDK Tools
Android Platform-tools
The latest Android platform
The latest Android system image for the emulator

**下载完成后，解压后把文件夹放在适当的位置，注意这边为了避免以后出现各种莫名其妙的问题，最好是放文件夹的路径上的所有文件都不包含中文和空格。不然真的会出现各种恶心的问题**

---

## 配置环境变量

1.启动Terminal终端工具

2.输入cd ~/ 进入当前用户的home目录

3.看是否存在bash_profile,如果不存在则创建： touch.bash_profile

4.如果存在,就打开并编辑： open .bash_profile

在里面添加sdk的tools和platform-tools的路径,注意每个路径要用:隔开,并且这个路径换成你自己的刚才解压后的sdk的实际路径.


exportPATH=$PATH:/Users/xm_file/android/adt-bundle-mac-x86_64-20140702/sdk/platform-tools:/Users/xm_file/android/adt-bundle-mac-x86_64-20140702/sdk/tools
 

5.保存关闭

6.更新： source .bash_profile

ok了,在Terminal终端工具里输入adb -version看看,是否出来类似的界面:

Android Debug Bridge version 1.0.31

如果出来了,说明adt已经Ok。

至此，环境已经搭建完成。

## 创建HellloWorld

###1.首先，打开eclipse。

理论上，现在eclipse自动安装了最新版的sdk和API

今天的版本是是：
SDK tools：23.0.2
SDK Platform-tools:20
SDK Build-tools：20
Android 4.4W（API 20）

上面API安装的是手表的，你需要先下载一个手机API。比如API19（最好把里面的东西全部下载了，尤其是镜像。）
![notice](/img/API.png)

其中，打勾的是必须下载的。

###那么，问题来了！
这里下载任何东西都是在谷歌网站上，不出意外如果你没翻墙下载不下来，或者翻墙了用的校园网也莫名其妙下载不下来。（这个问题曾经恶心了博主很久）。这里介绍一个超级好用的办法！！！！你不用翻墙，也不用担心校园网。

####步骤如下：
####打开Android SDK Manager,按住command+,号键，出现如图所示界面：
![cool](/img/command.jpg)

####在「HTTP Proxy Server」和「HTTP Proxy Port」输入框内填入mirrors.neusoft.edu.cn和80，并且选中「Force https://... sources to be fetched using http://...」复选框。设置完成后单击「Close」按钮关闭

这时候体验快速下载吧！这是国内镜像！放心大胆的使用吧！

至此，就可以建立工程使用了。运行你的HelloWorld吧！

如果开发HelloWorld还有问题，请移步至：<http://blog.csdn.net/chchong1234/article/details/8975834>


---

###一些问题：
1.博主因为第一次没搞定eclipse，所以还下载了android studio,界面是我喜欢的类型，下载后里面自动安装的是Android L系统。但是注意，运行L需要JDK7以上版本。如果想尝试，也是一个不错的选择。

2.如果最后运行代码时，提示R文件找不到，那么很可能是之前存放SDK的路径中包含了中文。



