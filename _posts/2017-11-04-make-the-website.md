---
layout:     post
title:      "Creat your personal blog "
subtitle:   "搭建一个独立博客———基本流程"
date:       2017-11-4
author:     "Yonga"
header-img: "img/make-website-bg.jpg"
tags:
    - Jekyll
    - blog
---

>拥有一个属于自己的个人博客（Github page + jekyll）

**更新于2018/1/28**

想用另一台笔记本写blog的时候，要配置环境，又看了一下自己写的这篇文章，发现还是不能完全靠这篇文章配置好环境，不过我又去问“度娘”问题，解决了一些问题，以下是**完善好的**流程~~

# 全局预览

1.	注册 GitHub 账号
2.	域名
3.	设置 DNS
4.	安装 Git 环境
5.	SSH key 添加到 github
6.	安装 jekyll 本地编译环境
7.	jekyll 模板
8.	学习 markdown 语法
9.	支持
10.	上传到 github

>开始我的表演啦

## 注册 GitHub 账号

>  先进这个网站注册一个账号 <https://github.com/>


>  GitHub 是一个非常了不得的开源社区

创建一个**repository**，
  名称为 （你的Github用户名.github.io） 点击 "Create repository"

OK,你在 GitHub 上拥有了第一个仓库，为你的个人网站做好了准备~



**记住你的用户名噢，会经常用到的**

## 域名
* 拥有一个属于自己的独立域名，下文介绍
* 如果还不想立即拥有自己的域名，你也可以使用 Github Pages 提供的域名访问，如下：

		<http://你的Github用户名.github.io  >

域名注册商很多，我推荐**Godaddy**,因为godaddy能买到我很想很想要的 **.me**域名
>想在 Godaddy 购买域名 <https://sg.godaddy.com/zh> 
>
>在 Godaddy 付款前，如果你购买期限很长，记得使用**促销码**（搜索引擎看看）

进入 **Godaddy** ，在搜索栏输入很符合你 **personal style** 的名字->搜索->把你喜欢的域名加入购物车->购买（可以使用支付宝）->进入你的邮箱激活->done!
  


## 设置 DNS

推荐使用 [DNSPOD](https://www.dnspod.cn/) 域名解析

登录你的 **Godaddy**

去设置 **DNSPOD** 的域名服务器

	"我的产品"->点击"DNS"->域名服务器使用自定义（添加如下）
	f1g1ns1.dnspod.net
	f1g1ns2.dnspod.net

注册好 **DNSPOD** 的账号后
	
	进入 "域名解析"->点击"添加域名"->"添加记录"（添加如下：）
	192.30.252.153（记录类型：A）
	192.30.252.153（记录类型：A）
	你的 Github 用户名.github.io（记录类型：CNAME，主机记录：www）
	

OK,你的 DNS 设置好了~



## 安装 Git  环境
[GIT 下载地址](https://git-for-windows.github.io/)

测试一下你安装好了吗：

	打开 gitbash->输入命令：git version->出现了对应的版本->done！

接下来，设置 github 账户信息：

	打开 gitbash ,输入以下两条信息：
	$ git config --global user.name "你的 Github 用户名" 
	$ git config --global user.email "你的邮箱" 
  
## SSH key 添加到 github
接下来进行 SSH 加密设置(加密传输到你的 github 仓库)

	打开 gitbash,输入如下：
	$ ssh-keygen -t rsa -C"你的邮箱" 

	（注意：C是大写的，注意空格） 

	出现了 Enter file which to save the key(...):
	你可以直接按 Enter 键 or 输入你记得住一个密码

当你完成所有命令时，去（C:\Users\你的计算机用户名）找到 .ssh 文件夹，用记事本的方式打开 id_rsa（文件类型为**.pub**），复制里面的内容。

回到你的 github 页面，右上角你的头像那里，如下操作：

	找到"Settings"->点击 "SSH and GPG keys"->"New SSH key"->粘贴刚复制的内容->"Add SSH key"->done!

你的 SSH 设置好了~



## 安装 jekyll 本地编译环境

1.安装 [ruby](https://rubyinstaller.org/downloads/) 


* 下载 **rubyinstaller** (选择对应你电脑的版本，比如我的电脑时64bits,我就选择x64)
* 下载对应你的 **rubyinstaller** 的 **DevKit** 并安装
* 安装ruby(记得勾选 **Add Ruby executables to your PATH**)

接下来检测你是否安装好：	

	打开 gitbash ,分别输入以下两条信息：
	ruby  -v
	gem   -v
	分别出现对应的版本，说明安装成功了！

2.继续配置 Ruby

	在 gitbash ,分别输入以下两条信息：
	gem install bundler
	gem install mongo
	可能这两步需要你耐心的等待~

 
3.安装 jekyll
	
	在 gitbash 输入如下：
	$ gem install jekyll
	


4.安装 jekyll-paginate

	在 gitbash 输入如下：
	$ gem install jekyll-paginate

想要更了解怎么使用 jekyll 建立你的网站，进入[任意门](http://jekyllcn.com/docs/structure/)


5.使用 jekyll 对本地的项目实时预览

到你项目的根目录下，如下操作：

	打开 gitbash ,输入如下：
	$ jekyll serve
	
打开浏览器，输入：http://127.0.0.1:4000

是不是看到你网站的初模型了~


假如，你输入 **Jekyll serve** ，在浏览器输入 http://127.0.0.1:4000 你想要的页面出不来，然后 gitbash 出现了一段有这样的句子：
>Deprecation: The 'gems'configuration option has been renamed to 'plugins'.Please update your config file accordingly.

这时，你需要在你的存放 blog 的根目录下找到 config.yml ,使用 plugins 替换掉 gems

在试一下 Jekyll serve ,在浏览器再次输入 http://127.0.0.1:4000 ，就能看到你搭建的 blog 了~

检测的是否安装成功技巧:（你安装的软件名 空格 -v）


## jekyll 模板
*	你可以制作一个结构样式都有自己风格的网站，纯手工的

*	Fork 已有的开源博客仓库，你可以在这 [jekyll 模板](http://jekyllthemes.org/page3/)选一个适合你的模板

接下来介绍怎样 Fork（以我自己的为例）：

进入[我的github](https://github.com/DianaGreen/DianaGreen.github.io) 
		
	 点击右上角的 "Fork" ，fork 的分支存到了你的 repo（仓库），点击 "Setting"->在 "Repository name"修改为
	你的 Github 用户名->点击 "Rename"->打开 "CNAME" 文件，
	把里面的内容修改为你自己的域名（比如我自己的： yonga.me ）->done!

OK，你可以用你自己的域名访问你的 GitHub pages 了

你可以直接下载 zip 在本地进行修改
1.	把 _posts 文件里的内容全都删掉（这里放的是你的文章，注意文章命名格式!）
 
2.	在 _config.yml 文件里修改信息

## 学习 markdown 语法

推荐使用 **MarkdownPad2** 来编写你的文章
>学习半个小时的 [markdown](http://www.appinn.com/markdown/)
>
对你编写文章十分方便

下载 [markdownpad任意门](http://markdownpad.com/download.html)

可能刚开始编写 markdown 时，会弹出一个问题。进去这个[任意门](http://markdownpad.com/faq.html#livepreview-directx)，下载 ** Awesomium 1.6.6 SDK**
 好了，快去写你的文章吧~
## 支持
如果我的这篇文章对你有帮助，希望你能在 <https://github.com/DianaGreen/DianaGreen.github.io> 点个      **"star"** ,非常感谢你的支持~

## 上传到 github

 >如下操作都在 gitbash 进行

* 在你本地项目根目录下，执行 git 命令

		git init
*	将所有文件添加到你的仓库中(**.**代表所有 ，注意空格)
	
		git add .
*	把 add 的文件 commit 到仓库中

		git commit -m "注释语句"
	

*	将本地的仓库与 github 的仓库关联

	 	
		如：git remote add origin  https://github.com/DianaGreen/DianaGreen.github.io

意思就是：git remote add origin +你 github 上的 web URL

操作：打开你 github 的第一个仓库-> "Clone or download"->复制链接（web URL）


*	准备上传到 github 前，pull 一下（本地的当前分支自动与对应的 origin 主机"追踪分支"进行合并。）

		git pull origin master
*	最后一步，**push** 一下（将本地分支的更新，推送到远程主机）

		git push -u origin master

然后输入你的 Username 和 Password 就好了，到你的 github 仓库看一下，是不是看到更新了，对，就是的~


现在你可以用过你的**域名**或者**你的用户名.github.io**来访问你的网站了~大功告成


>希望这篇文章能帮助到你~
>这篇文章已经帮助到我自己了，可能这就是做笔记的重要，嗯！ 多写 blog~

