---
title:  "Gitbook使用"
date:   2017-08-04 9:00:00
categories: 
- 工具
- Git
---

用gitbook写电子书，你值得拥有

<!-- More -->

以下是在ubuntu 14.04下安装gitbook

1. sudo apt-get install nodejs
2. sudo apt-get install npm
3. sudo npm install gitbook-cli -g

# 绑定域名
以下操作假设项目名为`faq_proj`，域名为`domain_name`:

1. 在项目根目录中增加CNAME文件, 内容为：
> faq_proj.domain_name.com

2. 在gitbook的项目`SETTINGS`中，进入`Domains`中设置`Domain for content`为同上的内容，然后保存；

3. 在你的域名解析中，增加以下内容后保存：
> CNAME  faq_proj  www.gitbooks.io

  等待一会儿(10分钟内)就可以通过`http://faq_proj.domain_name.com`访问了。

具体可参考[Can I use a custom domain for my book?](https://help.gitbook.com/books/can-i-use-custom-domain.html)

# 部署多个服务 
同时部署多个gitbook服务出现问题：
> You already have a server listening on 35729  
You should stop it and try again.  

原因：gitbook启动的web服务默认监听4000端口，而重启监控进程默认监听35729端口，当开启一个服务后，此默认监听端口就已经被占用。

方法：`gitbook serve --lrport 35730 --port 4001`

# 生成文件失败
* 现象：
> InstallRequiredError: "ebook-convert" is not installed.
 
* 原因: 没有安装ebook-convert.  
* 方法:  
	1. 下载安装[calibre](http://calibre-ebook.com/download);
	2. 建立快捷方式: `ln -s /Applications/calibre.app/Contents/MacOS/ebook-convert /usr/local/bin`;
	3. 安装ebook-convert：`npm install ebook-convert`.

# 参考
[Linux系统上如何同时部署两个gitbook服务](http://blog.csdn.net/moxiaomomo/article/details/53026645)