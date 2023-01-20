# 0基础,开发基于khl.py的kook机器人

## 第一章  准备工作

### 1-1  开发环境

  欢迎阅读这篇kook机器人开发文章，即使你没有任何编程基础，你也会编写出好用的机器人
准备材料
1.浏览器（edge，谷歌，火狐等等）
2.python3.10环境
3.python编辑器（pycharm，vscode，vim等等）

首先，你要有一个流畅的浏览器方便后期编写东西时更方便。
接下来，[python官网](https://www.python.org/)下载python3.10,当前python3.10支持大部分库
有了地基接下来开始去拿建筑材料了。
pycharm是一个很好的建筑材料，具有大部分的功能，能让你编写的更加顺利[pycharm](https://www.jetbrains.com/pycharm/).
有了地基和建筑材料，接下来我们就能开始机器人的制作了

### 1-2  准备环境

​    在正式开发之前，我们在pycharm找到file-setting-plugins搜索chinese插件进行安装并重启，你就能得到一个汉化版的pycharm了。：）
​    接下来我们要拥有kh.py这个包,你可以使用`pip3 install khl.py`进行安装或者用pycharm的python packages进行安装。

### 1-3  （可选）安装其他包

在我们之后的学习中，我们需要更多的python第三方包来使用，以下是本人推荐的一些好用的包
1.本地轻量化数据库TinyDB
这个包在你学完python基础语法后就可以使用它。
tinydb数据库是由纯python编写，易上手
安装命令：`pip install tinydb`
使用教程：[TinyDB数据库教程](https://zhuanlan.zhihu.com/p/558487927)

### 1-4  获取token

当我们编写机器人的时候，总要指定我们编写的是哪一个机器人，这样子，token就出来了。
在我们获取token之前，我们还要拿到开发者身份，这个十分简单。

1.打开kook

2.打开左下角的个人设置

3向下找到高级设置

这样你就可以打开开发者模式了
接下来我们要创建一个机器人并获取token

1.打开[机器人管理](https://developer.kookapp.cn/app/index)这个网址

2.打开新建应用

3.输入您的机器人名称

4.点击机器人头像，打开机器人设置

5.打开机器人栏目

6.复制token

这样子我们就得到机器人的“身份证”啦。
