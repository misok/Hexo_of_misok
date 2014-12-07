title: Python爬虫
date: 2014-10-26
categories: Python
tags: [spider]

---------
今天学习用python写爬虫。
down了网上一个爬贴吧的爬虫，看懂了，也运行成功了。但是程序里面有中文还是运行不过，可是我做了处理啊，还是报错。下次专门来探索这个问题。
<!-- more -->

```
#!/usr/bin/env python
#-*- coding: utf-8 -*-


#---------------------------------------
#   process:baidutiebaspider
#   version:1.0
#   author：xm
#   date：2013-05-14
#   languange：Python 2.7
#   operation：input address with page berak,remove the last numbers,set the begin page and end page
#   function：download the range page and stored to html
#---------------------------------------

import string, urllib2


def baidu_tieba(url,begin_page,end_page):
    for i in range(begin_page, end_page+1):
        sName = string.zfill(i,5) + '.html' #自动填充成六位的文件名
        print 'downloading the' + str(i) + 'page，and store it with ' + sName + '......'
        f = open(sName,'w+')
        m = urllib2.urlopen(url + str(i)).read()
        f.write(m)
        f.close()


#-------- 在这里输入参数 ------------------

# 这个是山东大学的百度贴吧中某一个帖子的地址
#bdurl = 'http://tieba.baidu.com/p/2296017831?pn='
#iPostBegin = 1
#iPostEnd = 10

bdurl = str(raw_input('please input valid address\n')) #合法的地址是去掉pn=后面的内容
begin_page = int(raw_input('input the begin page\n'))
end_page = int(raw_input('input the end page \n'))
#-------- 在这里输入参数 ------------------


#调用
baidu_tieba(bdurl,begin_page,end_page)

```
