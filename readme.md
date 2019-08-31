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

## 2、跨团队

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

hard、soft、mixed参数的区别

hard：回退本地仓库版本，包括工作区、暂存区的所有文件都会被删除，回退的时候最新文件不存在。

soft：回退到本地仓库版本和暂存区版本，但是工作区的文件被删除，相当于回退到需要git commit，回退的时候最新文件还存在。

mixed：回退到本地仓库版本，但是没有暂存区文件，只有工作区文件（表示没有添加索引），相当于回退到需要git add，git commit，回退的时候最新文件还存在。

多句话总结：hard只能回到本地仓库历史版本，无法找回未提交的文件，而soft、mixed可以找回未提交的文件，只是文件属于工作区还是暂存区的问题。

一句话总结：回退版本，某个版本号下未提交的文件不想要就用hard，想要未提交而已经添加了索引的文件就用soft，想要未提交而没有添加索引的就用mixed。

## 5、找回删除的文件

都是reset。

1. 找回删除添加索引已经提交到本地仓库的文件。

   

2. 找回删除添加索引未提交到本地仓库的文件。

## 6、比较文件的差异

git diff [版本号] [filename] ，工作区与暂存区、本地版本仓库比较，git add之后再git diff没有信息，因为git add已经确定差异没问题。

1. 带版本号表示与本地仓库某个版本比较，不带表示与上一个版本比较。
2. 带文件名表示比较特定文件，不带表示比较所有文件差异。
3. 只显示有修改的附近内容，不会显示所有。

## 7、分支管理

类似Java分模块，一个分支代表一种功能或者某个开发人员自己的模块，开发完成了就合并到master。

### 疑问：hot_fix

### 1、查看分支

git branch -v

### 2、创建分支

git branch 分支名字

### 3、切换分支

git checkout 分支名字

### 4、合并分支

以a分支合并到b分支为例

1. 切换到b分支：git checkout b
2. 合并：git merge a

### 5、解决冲突

如果多个分支修改同一个文件同一个位置，则需要人工解决再git add，git commit。



# 5、git远程仓库操作

以github为例。

## 1、pull操作

这命令包括了fetch、merge两个依次执行的命令

- git pull 远程仓库别名 分支名

  等价于：

  - git fetch 远程仓库别名 分支名

  - git merge 远程仓库别名 分支名

    

## 2、冲突解决

提交之前，需要先pull下来，如果有冲突就先解决冲突，然后再提交，注意，git commit 后面不能加文件名字。

## 3、团队工作

# 6、eclipse集合git操作

.classpath，.project，.settings目录需要忽略，因为不同版本不同eclipse配置不同，如果提交了，那么也会造成非代码项目的冲突。

编写忽略本地文件：

1. 编写java.gitignore文件
2. 在.gitconfig全局配置文件中设置java.gitignore文件路径。

# 7、git工作流

## 1、集中式工作流

全部都在master上工作，和SVN没差别。

## 2、gitflow

充分利用分支。

## 3、forKing

跨团队的模式。

# 8、gitlab服务器搭建

