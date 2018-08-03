## Pre-requirements
python=3.6
tensorflow=1.8
rdkit：install rdkit by 'conda install -c rdkit rdkit=2018.03.3.0' 

## Description
Apply Variant AutoEncoder(VAE) on chembl molecules, based on the paper [Automatic Chemical Design Using a Data-Driven Continuous Representation of Molecules](https://arxiv.org/pdf/1610.02415.pdf).

## git usage guide

### 1. 查看命令：
`git status`: 查看当前哪些文件被修改了，哪些文件需要被提交，如果不知道接下来该敲什么git命令了，可以用git status看一下接下来该干什么

`git branch`: 查看分支，当前分支前有*标记；

`git log`: 查看历史

### 2. 提交命令：
`git add filename`：将filename文件暂存，保存filename文件所做的修改

`git commit -m "这里写提交log信息"`: 提交暂存区的修改，使用git log可以看到做了一次版本的提交

### 3. 分支相关命令：
master为主线，dev为开发线；每次从master新建一个分支dev，在dev分支上写完代码（实现一个小功能后），将dev merge到master上。

`git branch`: 查看所有分支，当前分支前有*标记；

`git checkout master`： 切换到master分支；

`git checkout dev`：切换到dev分支；

`git checkout -b dev`：切换到dev分支，若dev不存在，则创建；

`git checkout master` 之后 `git merge --no-ff dev`: 切换到master，并将dev合并到master

### 4. 远程相关命令：
git pull <远程主机名> <远程分支名>:<本地分支名>

`git pull origin master:master` 将远程（github上的仓库，origin是远程仓库的默认名字）的master拉到本地的master

`git push origin master:master` 将本地的master分支，推送到远程仓库（github）。
 
### 5. git应用流程实例（试运行版）:
① 将远程仓库的修改合并到本地（每次修改之前，最好先将远程的合并到本地）

`$ git pull origin master:master`

② 从master创建并切换到本地分支dev，在dev上修改代码(以下修改都在dev上，master保持原样不变)

`$ git checkout -b dev`

#### 此处修改代码，假如新建了a.py并修改了b.py

③ 将工作暂存
首先使用查看有哪些修改

`$ git status`

命令行会提示：b.py文件做了修改，a.py文件被创建，这些改动可以暂存

```shell
On branch dev
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)
        modified:   b.py
Untracked files:
  (use "git add <file>..." to include in what will be committed)
  a.py
```

然后使用`git add`将改动暂存

`git add a.py b.py`

④ 一次或者几次`git add`之后，工作告一段落，或者准备下班回家，将暂存的工作提交，在-m 后写上简单的介绍，介绍这次提交了的版本，有什么变化

`git commit -m "实现了xxx功能，修复了xxxbug，尝试了xxx功能等等"` 

⑤ 代码实现了部分小功能，dev开发完毕，需要合并到master上

首先切换到master上

`git checkout master`

然后将dev合并到master（--no-ff是一个比较好的合并模式）

`git merge --no-ff dev`

之后会弹出一个页面，写上merge的说明。linux下默认弹出vi编辑，写完按照下方提示，ctrl+x退出即可。

⑥ dev功能开发完毕，将改动保存到远程仓库

`git push origin master:master`
