## 远程仓库

* GitHub 提供 Git 仓库托管服务。
* 本地 Git 仓库和 GitHub 仓库之间的传输是通过 SSH 加密的。
* 第一步：创建 SSH Key：ssh-keygen -t rsa -C "steveLau@github.com"  (Windows 下打开 Git Bash)；
  用户主目录里找到 `.ssh` 目录，里面有 `id_rsa`(私钥) 和 `id_rsa.pub`(公钥) 两个文件。
* 第二步：在 GitHub 里，添加 “SSH Key”，在 Key 文本框里粘贴 `id_rsa.pub` 文件的内容。

## 添加远程仓库

* 本地已经创建一个 Git 仓库后，又想在 GitHub 创建一个 Git 仓库，并且让这两个仓库进行远程同步。
* 第一步：在 GitHub 上新建一个仓库 Git-GitHub，复制SSH：git@github.com:steveLauwh/Git-GitHub.git。
* 第二步：在本地的仓库下运行命令：`git remote add origin git@github.com:steveLauwh/Git-GitHub.git`，关联远程仓库。
* 第三部：把本地库的所有内容推送到远程库上：`git push -u orign master`。
* 以后只要本地提交 `git push origin master`，就可以把本地 master 分支的最新修改推送到 GitHub。

## 从远程库克隆

* 远程库已经准备OK，使用 `git clone` 克隆一个本地库，如：`git clone git@github.com:steveLauwh/Git-GitHub.git`。
