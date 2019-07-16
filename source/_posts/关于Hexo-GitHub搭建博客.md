layout: post
title: Hexo+GitHub搭建个人博客
date: 2018-04-20 18:51:34
tags: Hexo+GitHub
---

![github和hexo](https://miskashimg-1252832325.cos.ap-guangzhou.myqcloud.com/关于Hexo-GitHub搭建博客/github和hexo.jpg)

<center>Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。

我搭建博客主要是记录一些技术性文章和一些日常嘛，顺便提高文笔也是挺好的(￣▽￣)"

总之搭建博客百利无一害，但是你必须要有写下去的那份心(→_→)

总之就这样(ง •_•)ง</center>

<!--more-->

安装 Hexo 相当简单。然而在安装前，您必须检查电脑中是否已安装以下程序：d=====(￣▽￣*)b

---



Git官方下载地址(ﾉ*･ω･)ﾉ--- <https://git-scm.com/>

Node.js官方下载地址(ﾉ*･ω･)ﾉ-----<https://nodejs.org/en/>

而这两个安装都没什么太大的要求，几乎都是无脑点击下一步(￣、￣)

>安装Git时有个地方要注意（⊙ｏ⊙）

![安装时右键的BASH HERE](https://miskashimg-1252832325.cos.ap-guangzhou.myqcloud.com/关于Hexo-GitHub搭建博客/安装时右键的BASH HERE.jpg)


---
然后你只需要在桌面或者文件夹内右键点击`Git Bash Here`

---

输入安装Hexo的指令(。・∀・)ノ(详细查看Hexo的FAQ<https://hexo.io/zh-cn/>)

	npm install hexo-cli -g      安装Hexo
	hexo init blog               建立所需要的文件在BLOG文件夹内
	cd blog                      打开blog文件夹
	npm install                  安装npm
	hexo server                  开启本地测试服务

![安装HEXO成功图](https://miskashimg-1252832325.cos.ap-guangzhou.myqcloud.com/关于Hexo-GitHub搭建博客/安装HEXO成功图.jpg)
<center>这是安装好Hexo的结果</center>

---

Hexo的一些常用指令(。・∀・)ノ(详细查看Hexo的FAQ<https://hexo.io/zh-cn/>)

	Hexo clean	清楚博客缓存

	Hexo deploy	部署到远程站点

	hexo generate	生成静态文件

	hexo server	运行服务器

	hexo new "New Post"	创建一个新帖子

	Ctrl+C	退出当前状态

---
	接下来就是管理GitHub仓库(ง •_•)ง

你需要建立一个新的仓库

![GitHub的首页](https://miskashimg-1252832325.cos.ap-guangzhou.myqcloud.com/关于Hexo-GitHub搭建博客/GitHub的首页.jpg)

然后按照你的NAME来输入`Repository name`  ~(￣▽￣)~*

![建立仓库](https://miskashimg-1252832325.cos.ap-guangzhou.myqcloud.com/关于Hexo-GitHub搭建博客/建立仓库.jpg)

然后点击`Create repository`完成创建库(ง •_•)ง

---

接下来就是完成`Github pages`的配置问题了ε=ε=ε=(~￣▽￣)~

点击进`settings`的`Github pages`中的`Choose a theme`

![GitHub pages](https://miskashimg-1252832325.cos.ap-guangzhou.myqcloud.com/关于Hexo-GitHub搭建博客/GitHub pages.jpg)

然后进入到一个选择主题的页面，感觉逼格很高有木有（*゜ー゜*）

![pages theme选择页面](https://miskashimg-1252832325.cos.ap-guangzhou.myqcloud.com/关于Hexo-GitHub搭建博客/pages theme选择页面.jpg)

进入完成`Github pages`的界面,点击`Commit changes`即可完成配置

![确认commit changes](https://miskashimg-1252832325.cos.ap-guangzhou.myqcloud.com/关于Hexo-GitHub搭建博客/确认commit changes.jpg)

---

接下来就是配置SSH密钥的环节=￣ω￣=

首先你可以尝试是否可以进入到.ssh的目录(ps:请在`Git Bash here`执行)

	cd ~/.ssh

如果进入不了你就可以输入

	ssh-keygen -t rsa -C "邮箱"

生成后在其反馈的地址中寻找

	一般有两个文件
	id_rsa
	id_rsa.pub

打开`pub`后缀的文件,将里面的内容复制下来，进入到库设置中的`Deploy keys`输入密钥即可

![ssh密钥](https://miskashimg-1252832325.cos.ap-guangzhou.myqcloud.com/关于Hexo-GitHub搭建博客/ssh密钥.jpg)

---
###进入你的`Hexo`配置文件

	_config.yml      网站配置文件
	
	theme            网站主题
	title            网站标题
	subtitle         网站副标题
	author           网站作者
	language         网站语言
	timezone         网站时间地区
<p></p>	

>在最底下的加入部署命令
>
	deploy:
	type: git
	repo: https://github.com/name/name.github.io.git
	branch: master

---

最后一步d=====(￣▽￣*)b

在你的博客文件夹位置右键进入`Git Bash Here`

输入指令生成静态文件并上传博客
	
	hexo clean          清除博客缓存
	hexo generate       生成静态文件
	hexo deploy         部署到Github

---

然后就是图片的URL（图床）O(∩_∩)O

这里推荐使用的是七牛图床，有着10GB免费存储，每月10GB免费下载流量，用来做博客的图床再合适不过

可以参考[十七蝉](http://blog.shiqichan.com/use-qiniu-store-image-for-hexo/)dalao的blog

上传插件就用[Qshell](https://github.com/qiniu/qshell)的就可以了

你还可以看看七牛云开发者中心的[FAQ](https://developer.qiniu.com/faq)里面有很多的问题解决方式供你参考o(*￣▽￣*)o

我个人用的就是腾讯云的对象储存，没啥缺点，和七牛云差不多

---

> Timezone 网站时区--[`点击查看时区列表`](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)
> 
	TypeError: Cannot read property 'utcOffset' of null
	出现这种问题就是你的配置文件的timezone设置问题了，上海时间就设置为Asia/Shanghai


>

---
	[]~(￣▽￣)~*感谢你的观看，如果有问题可以联系我