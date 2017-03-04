# Git Note

### 提交到版本库
* `git add .` -> `git commit -m "msg"`
* `git commit -a -m "msg"`
* 重新提交并修改最后一次提交信息：`git commit --amend -m "msg"`

### 添加远程库
* 查看远程库：`git remote -v`
* 添加远程库：`git remote add upstream <url>`

### 修改远程库
* 修改远程库URL：`git remote set-url origin <url>`
* 删除远程库：`git remote rm origin`

### 更新upstream到本地
* 使用pull 例：`git pull <远程主机名> <远程分支名>:<本地分支名>` 例：`git pull upstream master:master`
* 如果合并需要采用rebase模式，可以使用–-rebase选项：`git pull --rebase <远程主机名> <远程分支名>:<本地分支名>`
* 使用fetch 然后merge：`git fetch upstream` -> `git merge upstream/master` or `git rebase upstream/master`
* 使用remote update：`git remote update` -> `git merge upstream/master` or `git rebase upstream/master`
* 在任何时候，你可以用--abort参数来终止rebase的行动，并且"mywork" 分支会回到rebase开始前的状态: `git rebase --abort`

### 更新到自己远程仓库(origin)
* `git push origin master`
* 第一次和远程库关联：`git push -u origin master`，由于远程库是空的，在第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。

### 分支管理
* 创建dev分支，然后切换到dev分支：`git checkout -b <name>`，命令加上-b参数表示创建并切换。
* 也可以用这两个命令创建dev分支：`git branch <name>` -> `git checkout <name>`
* `git checkout -b [分支名] [远程名]/[分支名]`
* 查看分支：`git branch`
* 查看远程分支：`git branch -a`
* 切换分支：`git checkout <name>`
* 切换远程分支：`git checkout --track origin/serverfix`
* 合并某分支到当前分支：`git merge <name>`
* 删除分支：`git branch -d <name>`

### Log
> [https://git-scm.com/book/zh/v1/Git-基础-查看提交历史](https://git-scm.com/book/zh/v1/Git-%E5%9F%BA%E7%A1%80-%E6%9F%A5%E7%9C%8B%E6%8F%90%E4%BA%A4%E5%8E%86%E5%8F%B2)

* Log：`git log`
* 单行显示Log：`git log --pretty=oneline`
* 单选简短Log：`git log --pretty=oneline --abbrev-commit`
* 图形化表示：`--graph` 例：`git log --pretty=oneline --graph --abbrev-commit`

### 版本回退
* 显示版本号：`git log` `git reflog`
* 回退到上个版本：`git reset --hard HEAD^`
* 根据commit id回退版本：`git reset --hard <commit id>`
* 回退单个文件：`git checkout <commit id> <file>`

### 撤销修改
> [https://git-scm.com/book/zh/v1/Git-基础-撤消操作#取消已经暂存的文件](https://git-scm.com/book/zh/v1/Git-%E5%9F%BA%E7%A1%80-%E6%92%A4%E6%B6%88%E6%93%8D%E4%BD%9C#取消已经暂存的文件)

* 工作区的修改全部撤销：`git checkout -- <file>`
* 暂存区的修改全部撤销：`git reset HEAD <file>`

### 删除文件
* 删除文件后：`git add/rm <file>` 然后提交：`git commit`
* 恢复误删的文件：`git checkout -- <file>`

### 储藏（Stashing）
* 储藏： `git stash`
* 查看储藏： `git stash list`
* 恢复的同时把stash内容删除： `git stash pop`
### 冲突处理
