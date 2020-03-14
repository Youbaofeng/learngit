本文是学习廖老师的文章后总结的学习笔记，大部分是指令的总结。
学习地址：https://www.liaoxuefeng.com/wiki/896043488029600

#安装Git

#自报家门
`$ git config --global user.name "Your Name"`
`$ git config --global user.email "email@example.com"`

# 创建版本库
## 创建空目录：
`$ mkdir learngit`
`$ cd learngit`
## 初始化：
`$ git init`
## 添加&提交：
`$ git add <file>`
`$ git commit -m <message>`


# 工作状态
> 要随时掌握工作区的状态，使用git status命令。

> 如果git status告诉你有文件被修改过，用git diff可以查看修改内容。

# 版本回退
> HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令`git reset --hard commit_id`

> 穿梭前，用git log可以查看提交历史，以便确定要回退到哪个版本。

> 要重返未来，用git reflog查看命令历史，以便确定要回到未来的哪个版本。

# 撤销修改
> 丢弃工作区的修改时，用命令 `git checkout -- file`

> 撤回暂存区的提交（git add 后），用命令 git reset HEAD <file>

> 撤回之后修改退回工作区，然后用 `git checkout -- file` 丢弃修改。

# 删除文件
>`git rm <file>`

# 添加GitHub SSH Key
> 第1步：创建SSH Key。在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有id_rsa和id_rsa.pub这两个文件，如果已经有了，可直接跳到下一步。如果没有，打开Shell（Windows下打开Git Bash），创建SSH Key：

`$ ssh-keygen -t rsa -C "youremail@example.com"`

> 第2步：登陆GitHub，打开“Settings”，“SSH and GPG Keys”页面：然后，点“New SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容,点“Add Key”.

# 添加远程库
## 创建远程库
 "+"  -->   "New repository"  -->  add Name and Description   -->  Create repository  -->get url(https:\\abcd..)
## 关联远程库
`$ git remote add origin https:\\abcd..`
## 推送
`$ git push -u origin master`   第一次推送-u
## 从远程库克隆到本地
`$ git clone https:\\abcd..`

# 分支 master dev willyou
> 查看分支：git branch

> 创建分支：git branch <name>

> 切换分支：git checkout <name>或者git switch <name>

> 创建+切换分支：git checkout -b <name>或者git switch -c <name>

> 合并某分支到当前分支：git merge <name>

> 删除分支：git branch -d <name>

> 删除没有被合并的分支 git branch -D <name>

> 查看分支合并: git log

## 分支策略
> 1 master

> 2 dev

> 3 axx 4bxx 5cxx 6willyou

> Fast forward:删除分支后，会丢掉分支信息 (默认)`$ git merge  "merge with Fast forward" dev`

> no-ff:禁用Fast forward `$ git merge --no-ff "merge with no-ff" dev`


# 现场快照 暂存处理BUG
>当手头工作没有完成时，先把工作现场`git stash`一下，然后去修复bug，修复后，再`git stash pop`，回到工作现场

>在master分支上修复的bug，想要合并到当前dev分支，可以用`git cherry-pick <commit>`命令，把bug提交的修改“复制”到当前分支，避免重复劳动。

# 多人协作
>查看远程库信息，使用`git remote -v`；

>本地新建的分支如果不推送到远程，对其他人就是不可见的；

>从本地推送分支，使用 `git push origin branch-name` ，如果推送失败，先用git pull抓取远程的新提交；

>在本地创建和远程分支对应的分支，使用`git checkout -b branch-name origin/branch-name`，本地和远程分支的名称最好一致；

>建立本地分支和远程分支的关联，使用`git branch --set-upstream branch-name origin/branch-name`；

>从远程抓取分支，使用 `git pull` ，如果有冲突，要先处理冲突。

# Rebase
`git rebase`
> rebase操作可以把本地未push的分叉提交历史整理成直线；

> rebase的目的是使得我们在查看历史提交的变化时更容易，因为分叉的提交需要三方对比。

# 标签管理
## 创建标签
> 命令git tag <tagname>用于新建一个标签，默认为HEAD，也可以指定一个commit id : git tag v0.9 f52c633

> 命令git tag -a <tagname> -m "blablabla..."可以指定标签信息；

> 命令git tag可以查看所有标签。

## 操作标签
> 命令git push origin <tagname>可以推送一个本地标签；

> 命令git push origin --tags可以推送全部未推送过的本地标签；

> 命令git tag -d <tagname>可以删除一个本地标签；

> 命令git push origin :refs/tags/<tagname>可以删除一个远程标签。

## Git配置 
> eg: $ git config --global color.ui true
## 忽略文件
> 忽略某些文件时，需要编写.gitignore；

> .gitignore文件本身要放到版本库里，并且可以对.gitignore做版本管理！

## 配置别名

> `$ git config --global alias.st status`  --> git st

> `$ git config --global alias.last 'log -1'`  --> git last

> `$ git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"`  --> git lg


# git 可视化工具:SourceTree


