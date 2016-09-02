---
title: Git 笔记
date: 2016-08-27 19:07:11
categories: 开发工具
tags: git
---

git常用操作笔记。

### 1、设置用户名和邮箱

``` bash
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com

git config --local user.name 'local username'
git config --local user.email 'local email'

// 查看配置
git config -e
git config -e --global
git config -e --system
```

### 2、设置别名
``` bash
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.last 'log -l HEAD'
git config --global alias.unstage 'reset HEAD --'
/*
* git add newFileName
* git unstage newFileName
/
git config --global alias.reset 'reset --hard'
```


### 3、创建、修改和合并分支
``` bash
// 获取分支
git clone ssh://git@git.sankuai.com/fe/fe.meishi.special.git
git pull

// 创建分支
git co -b newBranch
// 提交修改
git ci -am 'commit'
// 推送分支
git push origin newBranch
// 合并分支
git merge otherBranch
// 删除本地分支
git branch -D branchName
// 删除远程分支
git push origin :remoteBrancName
// 修改分支origin
git branch -u origin/master
```


### 4、回滚
``` bash
// 回滚所有记录
git reset --hard HEAD
// 回滚到某次提交
git log
git reset --hard commitHash
//  取消缓存新文件
git add newFile
git reset HEAD -- newFileName
```

### 5、代码diff
``` bash
// commit之前对比
git diff
//  git add 之后，commit之前
git diff --cachedgit diff HEAD
// 对比某个文件
git diff branchName fileName
// 对比分支
git diff branchName
git diff branchName otherBranch
```

### 6、整理提交记录
``` bash
git co oldBranch
git ci -am 'commit'
...
git co master
git co -b newBranch
git merge --squash oldBranch
```

### 7、远程代码仓库操作
``` bash
// 查看远程代码仓库(别名+仓库地址)
git remote -v
// 添加远程代码仓库
git remote add remoteAlias remoteLink
// 拉取远程分支
git fetch remoteAlias
// 删除远程代码仓库
git remote remove remoteAlias
// 重命名
git remote rename remoteAlias newAlias
// 修改远程代码仓库地址
git remote set-url origin newRemoteLink
```


### 8、查询提交历史
``` bash
// 查询关键字所在文件
git grep 'keyword'
// 查询提交记录
git blame -L 20,23 fileName
git blame -L 20,+10 fileName
git blame --since=3.weeks -- foo
```

### 9、添加submodule
``` bash
// 当前git项目根目录
git submodule add [submodule ssh]  dir/subModule
// 根目录下会生成.gitsubmodule文件
 cat .gitmodule
// 进入submodule目录
cd dir/subModule
// 查看远程仓库信息，和主分支相同
git remote -v
// 初始化submodule
git submodule init
// 更新submodule
git submodule update
// 修改submodule文件，保存步骤
cd  dir/subModule
git add --all
git ci -am 'edit submodule'
// 回到根目录
cd ../..
git st
git ci -am 'commit'
```

### 参考链接
[git book](https://git-scm.com/book/en/v2)



