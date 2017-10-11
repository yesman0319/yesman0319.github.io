---
title: SSH的生成与使用
---
## 划重点
 今天第一次用hexo，中间被各种新公司地点的办公网络限制等问题，搞的直上火；anyway，最终还是顺利装上并使用了。<br>
 借着这次机会正好把 生成ssh的公钥的一些命令顺便记录一下。方便以后再给github仓库传代码时，省的再去google、百度其他人文章了。
## https 和 SSH 的区别：
#### 1.前者可以随意克隆github上的项目，而不管是谁的；而后者则是你必须是你要克隆的项目的拥有者或管理员，且需要先添加 SSH key ，否则无法克隆。
#### 2.https url 在push的时候是需要验证用户名和密码的；而 SSH 在push的时候，是不需要输入用户名的，如果配置SSH key的时候设置了密码，则需要输入密码的，否则直接是不需要输入密码的。

## 在 github 上添加 SSH key 的步骤：

#### 1.首先检查你电脑是否已经有 SSH key 
运行 git Bash 客户端，输入如下代码：
		
	$ cd ~/.ssh
	$ ls

#### 2.创建一个 SSH key 

	$ ssh-keygen -t rsa -C "your_email@example.com"
 代码参数含义：<br>

-t 指定密钥类型，默认是 rsa ，可以省略。<br>
-C 设置注释文字，比如邮箱。<br>
-f 指定密钥文件存储文件名。<br>

以上代码省略了 -f 参数，因此，运行上面那条命令后会让你输入一个文件名，用于保存刚才生成的 SSH key 代码，如：

	Generating public/private rsa key pair.
	# Enter file in which to save the key (/c/Users/you/.ssh/id_rsa): [Press enter]

当然，你也可以不输入文件名，使用默认文件名（推荐），那么就会生成 id_rsa 和 id_rsa.pub 两个秘钥文件。
<br>
接着又会提示你输入两次密码（该密码是你push文件的时候要输入的密码，而不是github管理者的密码），<br>

当然，你也可以不输入密码，直接按回车。那么push的时候就不需要输入密码，直接提交到github上了，如：
	
	Enter passphrase (empty for no passphrase): 
	# Enter same passphrase again:

接下来，就会显示如下代码提示，如：

	Your identification has been saved in /c/Users/you/.ssh/id_rsa.
	# Your public key has been saved in /c/Users/you/.ssh/id_rsa.pub.
	# The key fingerprint is:
	# 01:0f:f4:3b:ca:85:d6:17:a1:7d:f0:68:9d:f0:a2:db your_email@example.com

当你看到上面这段代码的收，那就说明，你的 SSH key 已经创建成功，你只需要添加到github的SSH key上就可以了。

#### 3.给github添加ssh

##### 3.1首先你需要拷贝 id_rsa.pub 文件的内容，你可以用编辑器打开文件复制，也可以用git命令复制该文件的内容，如：
		
		$ clip < ~/.ssh/id_rsa.pub

##### 3.2登录你的github账号，从设置（Settings ）进入，然后点击菜单栏的 SSH key 进入页面添加 SSH key。

* 以上是参考网上的博客进行记录的.