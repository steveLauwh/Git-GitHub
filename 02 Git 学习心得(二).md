## 远程仓库

* GitHub 提供 Git 仓库托管服务。
* 本地 Git 仓库和 GitHub 仓库之间的传输是通过 SSH 加密的。
* 第一步：创建 SSH Key：ssh-keygen -t rsa -C "steveLau@github.com"  (Windows 下打开 Git Bash)；
  用户主目录里找到 `.ssh` 目录，里面有 `id_rsa`(私钥) 和 `id_rsa.pub`(公钥) 两个文件。
* 第二步：在 GitHub 里，添加 “SSH Key”，在 Key 文本框里粘贴 `id_rsa.pub` 文件的内容。

## 添加远程仓库

* 本地已经创建一个 Git 仓库后，又想在 GitHub 创建一个 Git 仓库，并且让这两个仓库进行远程同步。
* 第一步：在 GitHub 上 新建一个仓库，如 https://github.com/steveLauwh/Git-GitHub.git
