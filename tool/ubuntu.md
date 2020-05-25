---
title:  "Ubuntu使用"
date:   2017-05-25 9:00:00
categories: 工具
tags: Ubuntu
---

主要针对阿里云服务

<!-- More -->

* 删除满足条件的文件: `find . -name '*_test*' -exec rm {} \;`

# PostgreSQL
* 配置文件：sudo vi /etc/postgresql/9.3/main/pg_hba.conf
* 服务重启：sudo service postgresql restart

# 下载地址
> [官方](http://releases.ubuntu.com/)

# 查看版本号
>1. cat /etc/issue
>2. cat /etc/lsb-release
>3. uname -a

# 设置网络代理
1. 设置网络
	* 全局设置: [详见配置文件设置](http://www.2cto.com/os/201204/127131.html)
	* 当前用户设置: `ifconfig eth0 210.34.6.89 netmask 255.255.255.128 broadcast 210.34.6.127`
2. 设置代理

# 设置环境变量
>1. [全局设置](http://jingyan.baidu.com/article/db55b609a3f6274ba30a2fb8.html):`gedit /etc/environment`---->`source /etc/environment`
>2. 当前用户设置: `gedit ~/.bashrc`---->`source ~/.bashrc`

# 重置root用户密码
>1. 任意用户登陆进入命令行;
>2. 执行`sudo passwd`即可重置密码

#修改源并升级更新
>1. 备份源: `sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup`
>2. 修改源: `sudo gedit /etc/apt/sources.list`
>----[Ubuntu 10.04 (Lucid) 更新源](http://www.cnblogs.com/dolphin0520/archive/2013/03/15/2960907.html)
>----[Ubuntu各版本下的更新源](http://pan.baidu.com/share/link?shareid=1362990598&uk=4278685087)
>3. 保存编辑好的文件，执行以下命令更新: `sudo apt-get update`