---
title: learn_git
date: 2017-10-08 20:36:54
tags: git
toc: true
reward: true
comments: ture
categories: 杂项
---
### 创建git
```
git init 
git add readme.txt  #加到暂存区
git commit -m "wrote a readme file"
git status #查看当前的文件和仓库里的文件有什么不同
git diff readme.txt  #具体找出不同
git diff HEAD -- readme.txt
```
### 版本回溯
<!-- more -->
```
git log #查看历史记录,以便确定回退到哪个版本
git log --pretty=oneline ##
git reset --hard HEAD^ #HEAD:当前版本 HEAD^:上一个版本 HEAD^^:上上一个版本
git reset --hard 3b96adca   #不要关闭窗口，找到最新版本的commit id 可以回到未来
git reflog#关闭窗口后，又想恢复到最新版本，需要找到新版本的commit id
```
###### 撤销修改
```
git checkout -- readme.txt #自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。总之就是让这个文件回到最近一次git commit或git add时的状态
git reset HEAD readme.txt #git add以后，又想回到最初的版本，用git reset HEAD file将暂存区的修改撤销掉，重新放回工作区
```
###### 删除文件
直接删除文件，但是在版本库里还有,需要利用git删除一下
```
git rm file #删掉版本库里的文件
git checkout -- file #恢复删掉的文件
```
### 远程仓库
```
sudo ssh-keygen -t rsa -C "youremail@example.com" #该电脑使用的密钥,ubuntu在root目录下，ls -ah，将id_rsa.pub里的内容复制到“SSH Keys”页面里
```
在github上创建new repository(pcl_examples)然后：

```
git remote add origin git@github.com:fgq1992/pcl_examples.git
git push -u origin master #第一次
git push origin master #之后
git clone git@github.com:fgq1992/pcl_examples.git
```
### 分支管理
```
git branch  #列出当前分支
git branch <name> #创建分支
git checkout <name> #切换分支
git checkout -b <name> # 创建+切换分支
git merge <name> #合并某分支到当前分支
git merge --no-ff -m "merge with no-ff" dev #合并时创建一个新的commit，这样就能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并
git branch -d <name> #删除分支
```
### Reference
https://www.liaoxuefeng.com/

