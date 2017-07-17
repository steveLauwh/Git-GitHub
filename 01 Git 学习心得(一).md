## 什么是Git

* Git 是分布式版本控制系统。
* CVS 和 SVN 是集中式的版本控制系统。
* 集中式版本控制系统，版本库是集中存放在中央服务器里，必须联网才能工作。
* 分布式版本控制系统的安全性要高些，每个人电脑里都有完整的版本库，不需要联网。
* 安装 Git 后，使用 `git config` 配置信息，使用 `--global` 参数，表示该机器上所有的 Git 仓库都使用这个配置。
```
git config --global user.name "steveLau"
git config --global user.email "steveLau.me@github.com"
```
```
// 查看配置
git config --list 
```

## 创建版本库

* 版本库：仓库(repository)，可理解成一个目录，Git 管理该目录下所有文件。
* 初始化一个仓库：`git init` 把当前的目录变成 Git 可以管理的仓库，空仓库。
* 添加文件到 Git 仓库，两步骤：
  + git add file   // file 表示文件名，可添加多个
  + git commit -m "xxx" // xxx 表示提交内容信息，最好有意义，便于查看

## 查看工作区的状态

* `git status` 查看仓库当前的状态。
* `git diff` 查看修改内容，如 `git diff file.txt` 查看 file.txt 修改内容。

## 版本回退

* `git log` 显示从最近到最远的提交日志，嫌输出信息太多，可以加上 `--pretty=oneline` 参数。
* `git reset --hard HEAD^` 回退上一个版本，HEAD 指向的版本是当前版本，`HEAD^` 上一个版本，`HEAD^^` 上上一个版本。
* `git reset --hard commit_id` 指定回到未来的某个版本，其中`commit_id`表示你要回到未来那个版本的id。
* `git reflog` 查看命令历史，记录版本对应的 commit_id。

## 工作区和暂存区

* 工作区：电脑里能看到的目录。
* 版本库：工作区中有一个隐藏的目录 .git，它就是 Git 的版本库。
* Git 的版本库包括 stage 的暂存区，Git 为我们自动创建的第一个分支 `master`，以及指向 `master` 的一个指针 `HEAD`。
* 使用 `git add` 只是把文件提交到暂存区，然后使用 `git commit` 命令，才是真正把暂存区的所有内容都提交到当前分支。

## 管理修改

* `git diff HEAD -- file` 可以查看工作区和版本库里面最新版本的区别。
* 每一次修改，必须先使用 `git add` 提交到暂存区，要不然不会加入到 commit 中。

## 撤销修改

* `git checkout -- file` 把 file 文件在工作区的修改全部撤销。
* 如果使用了 `git add`到暂存区，没有 commit，可以用命令 `git reset HEAD file` 把暂存区的修改撤销掉，重新放回工作区；再使用撤销修改命令。

## 删除文件

* 命令 `git rm file` 用于删除文件 file。
