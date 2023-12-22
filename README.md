# git
分布式版本控制，有本地仓库与与远程仓库的概念。
## git中的一些状态
git 工作目录下对于文件的增删改会存在几个状态，这些状态会随着git命令的执行而变化。
具体如下：
1. 未跟踪。新创建的文件本身其实和git没有任何关联
2. 未暂存。修改已经存在的文件，但是没有提交
3. 已暂存。提交到仓库按之前的缓冲区
4. 修改进入到仓库就变成了一次提交记录
其实其中这些状态只涉及到两个简单的命令
**仓库 <- commit <- 暂存区 <- add <- 工作区**
## git常见命令
### 创建空的仓库
```bash
git init
```
### 添加到暂存区
git add
跟踪指定的文件，或者将已存在的文件的修改存储到暂存区
### 提交到仓库
git commit 
将修改提交到仓储库，成为一个版本
### 查看状态
git status
### 查看仓库的历史提交记录
git log
git log 支持的选项参数
* --all 显示所有的分支
* --pretty=oneline 将提交信息显示为一行
* --abbrev-commit 使得提交的信息更加简短（主要就是提交id）
* --graph 以图的形式显示
**考虑到相关的参数实在是太长了，我们也可以给命令起别名alias "git-logl"="git log --pretty=oneline --all --graph --abbrev-commit"**
使用git log命令只可以查看到HEAD指针及其之前的版本信息，如果版本发生过回退操作，则可能会出现，HEAD指针之后仍存在历史提交版本的情况，而这些提交版本信息通过git log命令是看不到的。
### 回退到某个版本
git reset --hard commit-id
**其实git reset 有非常多的参数，但是简单起见我们只去记住git reset hard**
### 参考日志（操作日志）
其实除去版本日志，git也会记录操作日志。通过操作日志，我们就可以在回推到以前的某个版本后再次跳到后面的版本
git reflog

```text
操作完成的版本号 第二列可能是操作的序号 具体动作
a6ca4fc (HEAD -> main) HEAD@{0}: reset: moving to a6ca4fc
3bcc508 HEAD@{1}: reset: moving to 3bcc508
a6ca4fc (HEAD -> main) HEAD@{2}: commit: 添加了版本回退相关的命令介绍
87aba30 HEAD@{3}: commit: 添加了git log 的一些参数选项
06ad28f HEAD@{4}: commit: 添加了git log的相关笔记
3bcc508 HEAD@{5}: commit (initial): README 文件当前进度 常见命令 git status
```
**这个命令记录的单纯是从clone 开始用户所有在本地库中的操作**
## gitignore 文件
.gitignore 文件在其中可以指定那些文件不需要git来管理

## git 分支
使用分支这个功能，你可以把你的开发工作从主线开发任务上分离开来，进行重大的bug修改，开发新的功能，以避免影响开发主线。
其实即使存在多个分支，那么我们当前的工作区也只能存在某一个分支的某一个版本上
### 查看存在的分支及创建新的分支
查看当前存在哪些分支，当然也可以创建新的分支。
```bash
git branch # 查看当前分支
git branch 分支名称 # 创建新的分支
```
### 查看分支的提交情况
git-logl 
### 创建并且切换分支
git checkout -b 新分支的名称
### 创建并且切换分支
git checkout -b 新分支的名称
### 分支合并
分支合并是为了解决存在多个分支但是同时我们这几个分支的修改都是需要的。其实分支合并，主要还是在主分支上进行。使用到的命令是
git merge 分支的名称
### 分支删除
git branch -d 分支的名换 但是有的时候可能删除不成功，需要做各种检查，这时需要时使用git branch -D 分支的名称
