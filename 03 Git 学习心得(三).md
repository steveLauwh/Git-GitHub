## 标签管理

* 发布一个版本时，通常先在版本库上打一个标签 tag，这样就可以确定打标签时刻的版本。
* tag 就是一个让人容易记住的有意义的名字，它跟某个 commit 绑在一起。

## 创建标签

* `git tag <name>` 就可以打一个标签。
  ```
    git tag v1.0
  ```
* `git tag` 查看所有标签。
* 找历史提交的commit id：`git log --pretty=oneline --abbrev-commit`。
* 当忘了打标签，找到历史的 commit id，然后使用 `git tag <name> commit-id`。
  ```
    git tag v0.8 12345
  ```
* `git show <tagname>` 查看标签信息。
* `git tag -a <tagname> -m "xxxxx"`可以指定标签信息。
* `git tag -s <tagname> -m "xxxxx"`可以用PGP签名标签。

## 操作标签

* `git push origin <tagname>` 可以推送一个本地标签。
* `git push origin --tags` 可以推送全部未推送过的本地标签。
* `git tag -d <tagname>` 可以删除一个本地标签。
* 先删除本地标签，再 `git push origin :refs/tags/<tagname>` 可以删除一个远程标签。
  ```
    git push origin v1.0
    git tag -d v1.0
    git push origin :refs/tags/v1.0
  ```

## 使用 GitHub

* 参与各种开源项目。
* 步骤一：在 GitHub 上，可以任意 Fork 开源仓库，然后从自己的账号下 git clone。
* 步骤二：在本地进行修改，利用 Git 推送到 GitHub 上
* 步骤三：在 GitHub 上发起 pull request 给官方仓库来贡献代码。

## 自定义 Git

* `git config --global color.ui true` 命令输出不同颜色。
* 编写 `.gitignore` 文件的作用是让 Git 忽略特殊文件。
* 所有配置文件可以直接在线浏览：https://github.com/github/gitignore。
* `.gitignore` 文件本身要放到版本库里，并且可以对 `.gitignore` 做版本管理。
* 配置别名
  + 当前用户的 Git 配置文件放在用户主目录下的一个隐藏文件 .gitconfig 中。
  + 每个仓库的Git配置文件都放在.git/config文件中。
  ```
    用 git st 表示 git status。
    git config --global alias.st status
  ```








