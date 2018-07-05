---
title:  "Git安装"
date:   2018-06-28 20:31:00
categories:
- 工具
- Git
---

Mac下遇到的Git安装问题

<!-- More -->

# 问题
MAC环境下
1. 更新git版本：缺省版本一般都比较低：2.10.1 (Apple Git-78)，而目前最新版本是：2.17.1
2. 安装中文版
3. 中英文自由切换：解决使用中文版的git遇到错误时，根据中文错误提示很难搜到解决办法

# 前提
已安装brew
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew update
```

# 安装
* 英文版安装：[官方下载](https://git-scm.com/)，这个会覆盖系统缺省版本
* 中文版安装：
```
brew install git --with-gettext
brew link git --force
```

# 切换
切换完成后需重新打开终端
* 使用英文版：`brew unlink git`
* 使用中文版：`brew link git --overwrite`

# 验证
* 当前版本：`git --version`
* 当前语言：`git --help`显示的内容是中文还是英文

# 卸载
* 英文版：`sh /usr/local/git/uninstall.sh`
* 中文版: `brew uninstall git --force`