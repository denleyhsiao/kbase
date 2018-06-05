---
title: Git子模块
date: 2018-01-25 12:32:11
categories: 
- 工具
- Git
---

当项目依赖于子模块时，坑真多

<!-- More -->

# 问题
## 更新项目时
* `git pull`之后，立即执行`git status`, 如果发现submodule有修改，立即执行`git submodule update`
* 尽量不要使用`git commit -a`， `git add`命令存在的意义就是让你对加入暂存区的文件做二次确认，而`git commit -a`相当于跳过了这个确认过程。
* 更复杂一些，如果你的submodule又依赖了submodule，那么很可能你需要在`git pull`和`git submodule update`之后，再分别到每个submodule中再执行一次`git submodule update`，这里可以使用`git submodule foreach`命令来实现： git submodule foreach git submodule update

## 删除子模块依赖时


## 修改子模块依赖时
先删除一个submodule

1. 删除`.gitmodules`中对应submodule的条目
2. 删除`.git/config`中对应submodule的条目
3. 执行`git rm --cached {submodule_path}`。注意，路径不要加后面的“/”。  
   例如：你的submodule保存在`third_party/CppUnit/`目录。执行命令为：`git rm --cached third_party/CppUnit`

再更新submodule的URL

1. 更新`.gitmodules`中对应submodule的条目URL
2. 更新`.git/config`中对应submodule的条目的URL
3. 执行 git submodule sync

注：其实后面的1、2步可以合并为：`git submodule add http://xxx/third_party/CppUnit.git third_party/CppUnit`

## 更新子模块内容时
有些时候你需要对submodule做一些修改，很常见的做法就是切到submodule的目录，然后做修改，然后commit和push。

这里的坑在于，默认git submodule update并不会将submodule切到任何branch，所以，默认下submodule的HEAD是处于游离状态的(‘detached HEAD’ state)。所以在修改前，记得一定要用git checkout master将当前的submodule分支切换到master，然后才能做修改和提交。

如果你不慎忘记切换到master分支，又做了提交，可以用cherry-pick命令挽救。具体做法如下：
1. 用 git checkout master 将HEAD从游离状态切换到 master 分支, 这时候，git会报Warning说有一个提交没有在branch上，记住这个提交的change-id（假如change-id为 aaaa)
2. 用 git cherry-pick aaaa 来将刚刚的提交作用在master分支上
3. 用 git push 将更新提交到远程版本库中


# 递归更新子模块
```
git submodule foreach --recursive git submodule init 
git submodule foreach --recursive git submodule update 
```

# 参考
* [使用Git Submodule可能遇到的坑](http://mobile.51cto.com/aprogram-393324.htm)
* [Git Submodule使用完整教程](https://yq.aliyun.com/articles/27002)