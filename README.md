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
### 回退到某个版本
git reset --hard commit-id
**其实git reset 有非常多的参数，但是简单起见我们只去记住git reset hard**
### 操作日志
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