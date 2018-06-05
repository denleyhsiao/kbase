---
title:  "Git使用"
date:   2017-06-09 9:00:00
categories:
- 工具
- Git
---

以下操作都是在windows环境下进行的.

<!-- More -->

# 下载
 [官网](http://git-scm.com)上获取或者点击[这里](https://code.google.com/p/msysgit/downloads/list)下载。

# 安装
无论是客户端还服务器端,都需要安装Git核心软件:Git/msysGit;

1.  客户端:
	* 安装TortoiseGit;
	* 安装语言包TortoiseGit-Language;
2.  服务端:
	* [使用Gitblit 在windows 上部署你的Git Server](http://www.cnblogs.com/keyindex/archive/2012/07/17/2594435.html)
	* [搭建 Windows 上 Apache + Git 服务器](http://www.devbean.net/2011/10/apache-git-server-on-windows/)

详细安装过程见[Windows 系统下Git安装图解](http://drupalchina.cn/content/windows-xi-tong-xia-gitan-zhuang-tu-jie).

# 使用
* 仓库名不要带空格，如`Microsoft SDK`；否则`git push`时会失败。
* 文件名中如果有中文时会出现无法提交的情况,比如我一个文件是:Windows批处理.html,在提交框中就只显示"Windows.html",安装最新版本的[Git](https://code.google.com/p/msysgit/downloads/list)/[TortoiseGit](https://code.google.com/p/tortoisegit/wiki/Download?tm=2)(具体是Git还是TortoiseGIT导致的问题目前没有测试确认), 或者是针对[UTF-8的特定版本](https://code.google.com/p/utf8-git-on-windows/downloads/list)可以解决此问题.
* [Git Windows客户端保存用户名与密码](http://www.cnblogs.com/dudu/archive/2011/07/06/git_save_username_password.html)
* [看日记学git](http://www.open-open.com/doc/view/a38fc67e70db4ece9f851dc0f531c543
)

注:
1. 软件Git核心软件时不能使用1.7.11版本,否则会出现错误"not found:did you run git update-server-info on the server";
2. 如在Linux环境下,Git安装如下：

* 安装curl-7.27.0.tar.gz以支持http访问;（make && make install);
* 安装Git (make && make install);
* 如果安装Git时找不到openssl相关文件，则运行: ./configure --with-openssl=/etc/ssl.

## Git Pages
在Git上呈现自己的个人主页(主要是项目说明性质的网页，个人博客), 其实它真正的幕后功臣是Makedown文本格式. 通过此格式，我们可以只关注文字，而不用对排版有深入的了解，就能用网页的方式，PDF格式呈现多彩内容。
注：不支持同时绑定多个域名，详见[Multiple domains in CNAME file节](https://help.github.com/articles/troubleshooting-custom-domains/)
* [Jekyll建站之旅](http://calefy.org/2012/03/03/my-process-of-building-jekyll-blog.html)
* [写作环境搭建(git+github+markdown+jekyll)](http://site.douban.com/196781/widget/notes/12161495/note/264946576/)
* [Github Page 绑定域名](http://kyle.xlau.org/posts/github-cname.html)
* [使用Github Pages建独立博客](http://beiyuu.com/github-pages/#github)
* [从 Octopress 到 Hexo](http://lucifr.com/2013/01/02/from-octopress-to-hexo/)
* [如何高效的使用github](http://www.ixirong.com/2015/06/07/git-and-github-repo/)

## Gitbook
* [如何写电子书](https://github.com/larrycai/kaiyuanbook)
* 电子书的未来
* 其它人的电子书
* 李笑来《知笔墨》
* Gitbook FAQ中显示记录数无法汉化？如：`16 ARTICLES`
* [Gitbook语法](https://cowmanchiang.me/gitbook/gitbook/contents/how/code.html)
* [Gitbook文档(中文版)](https://www.gitbook.com/book/chrisniael/gitbook-documentation/details)
* [GitBook 简明教程](http://www.chengweiyang.cn/gitbook/index.html)
* [Mac下GitBook制作电子书](http://liaoer.net/2015/04/30/Mac%E4%B8%8BGitBook%E5%88%B6%E4%BD%9C%E7%94%B5%E5%AD%90%E4%B9%A6/)
* [GitBook 插件](http://gitbook.zhangjikai.com/plugins.html)
* [Gitbook，这个开源出书平台了不起](https://linux.cn/article-6792-1.html):柯文哲

## Github
* [搬进 Github](http://gitbeijing.com/)文字版
* [手机上的github编辑工具:prose](https://github.com/prose/prose)
* [如何高效利用GitHub](http://www.yangzhiping.com/tech/github.html)
* [我在GitHub的工作是怎样的](http://blog.jobbole.com/21270/)
* [GitHub第一年的10个启示](http://blog.jobbole.com/13403/)
* [GitHub如何运作：时间并不决定一切](http://blog.jobbole.com/6492/)
* [GitHub如何运作：异步工作](http://blog.jobbole.com/6815/)
* [GitHub如何运作：创新很重要](http://blog.jobbole.com/7547/)

## GitStats

## Repo
负责依赖项目的统一管理.
详见[Repo的使用](http://blog.csdn.net/esther0401/article/details/7321492)

## Gitosis
权限管理工具。因为我们需要跟很多的人合作，每个人我们都希望给予他不同的权限，这样就不怕重要的项目被不重要的人看到了.
详见[Git+Gitosis+Repo整套部署方案](http://project-management.diandian.com/post/2012-03-02/16839283)

## Gerrit
代码审核服务器
详见[Gerrit工作流和原理](http://www.worldhello.net/2010/11/10/2059.html)

## Travis CI
开源的持续集成工具.
详见[利用Travis CI 让你的github项目持续构建(Node.js为例)](http://www.cnblogs.com/whitewolf/archive/2013/04/14/3019838.html)

# 问题集
* git如何从origin再push到另一分支(my)上：`git push my master`

## 忽略某个已纳入Git的文件的修改
* 忽略跟踪：`git update-index --assume-unchanged /path/to/file`
* 恢复跟踪：`git update-index --no-assume-unchanged /path/to/file`

## Windows下TortoiseGit安装失败
现象: 安装TortoiseGit-1.8.3.0-32bit.msi时提示:无法通过windows installer服务安装此安装程序包。您必须安装带有更新版本windows Installer服务的Windows";
方法: 安装[WindowsXP-KB942288-v3-x86](http://www.microsoft.com/downloads/zh-cn/details.aspx?FamilyID=5a58b56f-60b6-4412-95b9-54d056d6f9f4).

## 远程分支重命名
```
git checkout -b old_branch
git push --delete origin old_branch
git branch -m old_branch new_branch
git branch --unset-upstream
git push --set-upstream origin new_branch
```

## 无法push到远程的git服务器上
### Q1
现象：`error: unpack failed: error Permission denied`
原因：此项目是直接使用root用户通过WinSCP上传到gitblit服务器上的，而服务器只认其初始配置的denley用户
方法：进入服务器上此项目的目录，执行`chown -R denley:denley .`

参考：
[gerrit error: unpack failed: error Permission denied](https://www.bbsmax.com/A/A7zgYgbY54/)

### Q2
现象：
```
error: RPC failed; HTTP 413 curl 22 The requested URL returned error: 413 Request Entity Too Large
fatal: The remote end hung up unexpectedly
fatal: The remote end hung up unexpectedly
```
原因：服务器git.xxx.com使用了nginx代理服务器，其对上传文件的大小有缺省限制
方法：在nginx.conf的http节点上增加设置`client_max_body_size 20m;`,重启nginx服务即可

参考：
[Nginx – Error 413: Request entity too large](https://jorge.fbarr.net/2011/04/03/nginx-error-413-request-entity-too-large/)