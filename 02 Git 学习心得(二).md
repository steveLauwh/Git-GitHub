## 远程仓库

* GitHub 提供 Git 仓库托管服务。
* 本地 Git 仓库和 GitHub 仓库之间的传输是通过 SSH 加密的。
* 步骤一：创建 SSH Key：ssh-keygen -t rsa -C "steveLau@github.com"  (Windows 下打开 Git Bash)；
  用户主目录里找到 `.ssh` 目录，里面有 `id_rsa`(私钥) 和 `id_rsa.pub`(公钥) 两个文件。
* 步骤二：在 GitHub 里，添加 “SSH Key”，在 Key 文本框里粘贴 `id_rsa.pub` 文件的内容。

## 添加远程仓库

* 本地已经创建一个 Git 仓库后，又想在 GitHub 创建一个 Git 仓库，并且让这两个仓库进行远程同步。
* 步骤一：在 GitHub 上新建一个仓库 Git-GitHub，复制SSH：git@github.com:steveLauwh/Git-GitHub.git。
* 步骤二：在本地的仓库下运行命令：`git remote add origin git@github.com:steveLauwh/Git-GitHub.git`，关联远程仓库。
* 步骤三：把本地库的所有内容推送到远程库上：`git push -u origin master`。
* 以后只要本地提交 `git push origin master`，就可以把本地 master 分支的最新修改推送到 GitHub。

## 从远程库克隆

* 远程库已经准备OK，使用 `git clone` 克隆一个本地库，如：`git clone git@github.com:steveLauwh/Git-GitHub.git`。
* Git支持多种协议，包括https，但通过ssh支持的原生git协议速度最快。

## 从远程库更新到本地库

* `git fetch origin master`           //从远程的origin仓库的master分支下载代码到本地的origin master
* `git log -p master.. origin/master` //比较本地的仓库和远程参考的区别
* `git merge origin/master`           //把远程下载下来的代码合并到本地仓库，远程的和本地的合并


## 创建与合并分支 (看作指针的移动)

* `master` 分支为 Git 主分支，`HEAD` 指向当前分支。
* 创建 dev 分支，然后切换到 dev 分支上: `git checkout -b dev`；等同于以下两条命令：创建分支 `git branch dev` 和 切换分支 `git checkout dev`。
* `git branch` 列出所有分支，当前分支前面会标有一个 `*` 号。
* 步骤一：`git checkout master` 切换回 `master` 分支。
* 步骤二：`git merge dev` 将 `dev` 分支的内容合并到 `master` 分支上。
* 步骤三：`git branch -d dev` 合并完成后，将 `dev` 分支删除。

## 解决冲突

* 当 Git 无法自动合并分支时，就必须首先手动解决冲突。解决冲突后，再提交，合并完成。
* `git log --graph` 查看分支合并图。

## 分支管理策略

* `master` 分支应该是非常稳定的，仅用来发布新版本，平时不能再上面干活。
* 使用 `git merge` 命令合并分支时，加上 `--no-ff` 参数，表示禁用 `Fast forward`，合并后的历史有分支。
```
git merge --no-ff -m "merge with no-ff" dev  //其中加上 -m 参数，把 commit 描述写进去
```

## Bug 分支

* `git stash` 将当前工作现场“存储”起来，等以后恢复现场后继续工作。
* `git stash list` 查看工作现场存储位置。
* Git 把 stash 内容存在某个地方，恢复有两个办法：
  + 用git stash apply恢复，但是恢复后，stash内容并不删除，你需要用git stash drop来删除
  + 用git stash pop，恢复的同时把stash内容也删了

## Feature 分支

* 开发一个新 feature，最好新建一个分支。
* 如果要丢弃一个没有被合并过的分支，可以通过 `git branch -D 分支名` 强行删除。

## 多人协作 (*)

* `git remote` 查看远程库的信息。
* `git remote -v` 显示更详细的信息。

* 步骤一：用git push origin branch-name推送自己的修改。
```
git push origin master 将本地的 master 分支推送到远程库 origin上
git push origin dev 将本地的 dev 分支推送到远程库 origin上
```

* 步骤二：如果推送失败，则因为远程分支比你的本地更新，需要先用 `git pull` 试图合并。

* 步骤三：如果合并有冲突，则解决冲突，并在本地提交。

* 步骤四：如果没有冲突或解决，再执行步骤一进行推送。

* 另外，`git pull` 提示“no tracking information”，那么使用在本地创建分支和远程分支链接关系没有创建，
  使用 `git checkout -b branch-name origin/branch-name`，本地和远程分支的名称最好一致。
```
git checkout -b dev origin/dev 要在本地 dev 分支上开发，必须创建远程 origin 的 dev 分支到本地。
```

