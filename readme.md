# git复习笔记

# 1、git用户创建

## 1、项目级别用户

git config user.name

git config user.email

随便定义都可以，和github上没任何关系

## 2、系统级别用户：

在项目级别定义上加上参数：--global。

在一个项目仓库中，项目级别的用户大于系统级别的，类似表格单元格大于行。



# 2、git分类

## 1、工作区

编辑文件的区域。

## 2、暂存区

git add ，标记索引之后的区域。

## 3、版本库

git commit，也就是本地仓库。。

## 4、远程仓库

像gitee，github这样的。



# 3、git工作方式

## 1、单个团队

一个团队的，直接push，pull。

## 2、多个团队

fork，push，pull，merge。



# 4、git基本操作

## 1、添加文件到暂存区

git add files

git add -A

## 2、提交暂存区文件到本地库

git commit -m "commited message"

## 3、查看本地日志

git log：显示当前版本到初始化版本。

格式显示：

- git log --pretty=oneline：显示当前版本到初始化版本。（git log参数版本变形）
- git log  --oneline：显示当前版本到初始化版本。（git log参数版本变形）
- git  reflog：显示最新版本到初始化版本。

## 4、恢复历史记录

git reset

1. 基于索引值

   git reset --hard 索引记录

2. 基于“^”

   只能后退版本

   回退一个版本：git reset --hard^

   回退两个版本：git reset --hard^

3. 基于“~”

   只能后退，用于后退多个版本。

   git reset --hard~N

## **hard、soft、mixed参数的区别**

hard：回退本地仓库版本，包括工作区、暂存区的所有文件都会被删除。

soft：回退到本地仓库版本和暂存区版本，但是工作区的文件被删除，相当于回退到需要git commit。

mixed：回退到本地仓库版本，但是没有暂存区文件，只有工作区文件（表示没有添加索引），相当于回退到需要git add，git commit。

多句话总结：hard只能回到本地仓库历史版本，无法找回未提交的文件，而soft、mixed可以找回未提交的文件，只是文件属于工作区还是暂存区的问题。

一句话总结：回退版本，某个版本号下未提交的文件不想要就用hard，想要未提交而已经添加了索引的文件就用soft，想要未提交而没有添加索引的就用mixed。