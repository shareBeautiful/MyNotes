title: git 常用笔记
tags:
  - git
categories:
  - git
author: zhou
date: 2017-08-08 11:06:00
---
### git 设置
```
$ git config --global user.name "用户名"
$ git config --global user.email "用户邮箱"
```

### git ssh创建
```
$ ssh-keygen -T rsa -C '邮箱地址'
```

### git 初始化
```
$ git init
```

### git 克隆
```
$ git clone
```
### git 添加
```
$ git add *
```
### git 删除操作
#### 1. 删除
> ```
$ git rm file
```

#### 2. 恢复
> ```
$ git checkout -- file
```

### git 提交
```
$ git commit -m "提交的内容"
```
### git 远程操作
#### 1. 添加远程仓库
> ```
$ git remote add origin 远程地址
```

#### 2. 查看远程仓库
> ```
$ git remote -v
```

#### 3. 删除远程仓库
> ```
$ git remote rm origin
```

### git 拉取
```
$ git pull origin master
```

### git 远程推送
```
$ git push -u origin master
```

### git 删除远程
```
$ git remote rm origin
```

### git 分支操作
#### 1. 创建分支
```
$ git checkout -b 分支名字
```
#### 2. 切换回主分支
```
$ git checkout master
```
#### 3. 删除新建的分支
```
$ git branch -d 分支名字
```
#### 4. 推送分支到远程仓库
```
$ git push origin 分支名字
```

### git 分支更新与合并
#### 1. 更新并合并
> ```
$ git pull origin 分支名称
```

#### 2. 合并其它分支到当前分支
> ```
$ git merge 其它分支名称
```

#### 3. 在合并改动之前查看差异
> ```
$ git diff 分支1 分支2
```

### git log查看仓库历史
```
$ git log
```