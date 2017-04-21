# Git Note

### 提交到版本库
* `git add .` -> `git commit -m "msg"`
* `git commit -a -m "msg"`
* 追加文件，重新提交：`git commit --amend`
* 重新提交并修改最后一次提交信息：`git commit --amend -m "msg"` 然后：`git push <remote> <branch> --force`

### 添加远程库
* 查看远程库：`git remote -v`
* 添加远程库：`git remote add upstream <url>`

### 修改远程库
* 修改远程库URL：`git remote set-url origin <url>`
* 删除远程库：`git remote rm origin`

### 更新upstream到本地
* 使用pull 例：`git pull <远程主机名> <远程分支名>:<本地分支名>` 例：`git pull upstream master:master`
* 如果合并需要采用rebase模式，可以使用–-rebase选项：`git pull --rebase <远程主机名> <远程分支名>:<本地分支名>`
* 使用fetch 然后merge：`git fetch <远程主机名> <分支名>` -> `git merge <远程主机名>/<分支名>` or `git rebase <远程主机名>/<分支名>`
* 使用remote update：`git remote update` -> `git merge <远程主机名>/<分支名>` or `git rebase <远程主机名>/<分支名>`
* 在任何时候，你可以用--abort参数来终止rebase的行动，并且"mywork" 分支会回到rebase开始前的状态: `git rebase --abort`

### 更新到自己远程仓库(origin)
* `git push origin master`
* 第一次和远程库关联：`git push -u origin master`，由于远程库是空的，在第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。
* 强制push：`git push --force origin`

### 分支管理
* 创建dev分支，然后切换到dev分支：`git checkout -b <分支名>`，命令加上-b参数表示创建并切换。
* 也可以用这两个命令创建dev分支：`git branch <分支名>` -> `git checkout <分支名>`
* `git checkout -b <分支名> <远程主机名>/<分支名>`
* 查看分支：`git branch`
* 查看远程分支：`git branch -r`
* 查看所有分支：`git branch -a`
* 查看分支追踪：`git branch -vv`
* 切换分支：`git checkout <分支名>`
* 切换远程分支：`git checkout --track <远程主机名>/<分支名>`
* 创建一个追踪分支：`git checkout -b <分支名> --track <远程主机名>/<分支名>`
* 合并某分支到当前分支：`git merge <分支名>`
* 先`rebase`，如果有冲突，`git rebase --abort`，再换用`merge`
* 删除分支：`git branch -d <分支名>`
* 删除远程分支：`git push <远程主机名> :<远程分支名>`
* 删除远程分支：`git push origin --delete <branch name>`

### Tag
* 添加Tag：`git tag <tag name>`
* 添加Tag指定commit id：`git tag <tag name> <commit id>`
* 添加带有说明的标签，用-a指定标签名，-m指定说明文字：`git tag -a <tag name> -m <msg> <commit id>`
* 删除tag：`git tag -d <tag name>`
* 推送到远程：`git push <远程主机名> <tag name>`
* 推送全部尚未推送到远程的本地标签：`git push <远程主机名> --tags`
* 查看Tag：`git tag`
* 查看Tag信息：`git show <tag name>`

### Log
> [https://git-scm.com/book/zh/v1/Git-基础-查看提交历史](https://git-scm.com/book/zh/v1/Git-%E5%9F%BA%E7%A1%80-%E6%9F%A5%E7%9C%8B%E6%8F%90%E4%BA%A4%E5%8E%86%E5%8F%B2)

* Log：`git log <file name>`
* 单行显示Log：`git log --pretty=oneline`
* 单选简短Log：`git log --pretty=oneline --abbrev-commit`
* 图形化表示：`--graph` 例：`git log --pretty=oneline --graph --abbrev-commit`
* 记录每一次命令：`git reflog`
* 查看操作时间：`git reflog show --date=iso <branch name>`
* 显示每次提交的内容差异，用 -2 则仅显示最近的两次更新：`git log -p -2`
* `git diff`：显示暂存区和工作区的差异
* `git diff --cached [file]`：显示暂存区和上一个commit的差异
* `git diff HEAD`：显示工作区与当前分支最新commit之间的差异
* `git diff <commit id> <commit id>`：显示两次提交之间的差异
* `git show <commit id>`：显示某次提交的元数据和内容变化
* `git show --name-only <commit id>`：显示某次提交发生变化的文件
* `git show <commit id>:<file name>`：显示某次提交时，某个文件的内容
* `git blame <file name>`：显示指定文件是什么人在什么时间修改过

### 版本回退
* 显示版本号：`git log` `git reflog`
* 回退到上个版本：`git reset --hard HEAD^`
* 根据commit id回退版本：`git reset --hard <commit id>`
* 回退单个文件：`git checkout <commit id> -- <file>`

### 撤销修改
> [https://git-scm.com/book/zh/v1/Git-基础-撤消操作#取消已经暂存的文件](https://git-scm.com/book/zh/v1/Git-%E5%9F%BA%E7%A1%80-%E6%92%A4%E6%B6%88%E6%93%8D%E4%BD%9C#取消已经暂存的文件)

* 工作区的修改撤销文件：`git checkout -- <file>`
* 工作区的修改全部撤销：`git checkout -- .`
* 暂存区的修改全部撤销：`git reset HEAD <file>`

### 删除文件
* 删除文件后：`git add/rm <file>` 然后提交：`git commit`
* 恢复误删的文件：`git checkout -- <file>`

### 储藏（Stashing）
* 储藏： `git stash`
* 查看储藏： `git stash list`
* 储藏的工作重新应用：`git stash apply <stash@{2}>`
* 移除储藏：`git stash drop stash@{0}`
* 恢复的同时把stash内容删除： `git stash pop`
* 清空Stash：`git stash clear`

### Git config
* 查看当前用户（global）配置：`git config --global  --list`
* 查看当前仓库配置信息：`git config --local  --list`
* `git config --global user.name "YOUR NAME"`
* `git config --global user.email "EMAIL ADDRESS"`
* Generating a new SSH key：`ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`
* Test SSH connection：`ssh -T git@github.com`

### Other
* 二分法查找bug：`git bisect start` `git bisect good`
