---
layout: default
title: FileCleanUpBug
category: [技术, Bug]
comments: true
---

# 问题介绍
同事发布FileClueanUp程序时候出现一些问题,问题一般般,只是作为一个异常的笔记记录.







## String的index超出范围
程序只是简单的实现一个移动文件到另外的一个文件夹,同时打包压缩.

### 问题详情
程序运行时候不能正常运行,报错提示String的index超出范围.

### 解决方案
问题是一个小问题,直接打一个断点然后发现到了那处位置是由于文件夹内部是空的,然后读取时候作为一个文件去分割,造成指针超出范围的错误.

代码在这里并没有做为空判断,不是很符合规范,不过,直接建立文件夹,添加一个文件基本解决问题.

更为合理的解决办法当然是判断此文件夹里面没有文件的话,就直接不进行处理,退出程序即可.


## 调试程序时候发现无限拷贝

### 问题详情
本来判断文件不为空之后应该是正常拷贝的,但是却发现程序停不下来,断点挑时候发现原来是配置文件bug,配置文件中,目标文件夹是原文件夹的子文件夹,因此造成总是不为空判断.

#### 解决办法
将目标路径更改为其他路径即可解决现在的问题.

最好的结局办法自然是添加一个目标路径的过滤选项,不可以为原路径的子文件夹,或者只移动原文件夹的根路径下的文件.


## 发布程序运行报错int异常

### 问题详情
同事把软件调好之后直接发布,打包成jar之后再弄成exe,运行直接报错.显示一个什么int异常,具体情况已经忘记.

直接让同事重新弄发布的步骤,发现在打包成exe时候的一个图标的路径异常,然后导致生成的exe异常.

### 解决办法
产生的原因是由于代码拷贝时候,并没有注意到应用的图标路径的问题,修改为对应路径的图标之后,总算运行正常.


## 运行程序一闪而过

### 问题详情
由于程序只是拷贝文件,开发着并没有弄相应的UI,于是打开程序之后,只是一闪而过的界面.

### 解决办法
这个问题是因为界面不重要的缘故,因此程序并没有开发界面,如果想要看输出,可以在cmd,或者是powershell下面运行程序即可看到输出的日志.

根本解决办法自然是可以添加一个日志输出界面,或者添加一个等待用户输入之后的选项,不过这些会造成阻塞延时,视情况选择即可.


## 说明

[欢迎评论，欢迎指正,转载也请注明出处.](https://wangkun19930608.github.io/%E6%8A%80%E6%9C%AF/bug/2018/07/18/company-bug-filecleanup/)


### 版本记录

20180718 完成文章