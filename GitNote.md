# Git Note

### 提交到版本库
* `git add .` -> `git commit -m "msg"`
* `git commit -a -m "msg"`

### 添加远程库
* 查看远程库：`git remote -v`
* 添加远程库：`git remote add upstream <url>`

### 更新upstream到本地
* 使用pull 例：`git pull <远程主机名> <远程分支名>:<本地分支名>` 例：`git pull upstream master:master`
* 使用fetch 然后merge：`git fetch upstream` -> `git merge upstream/master` or `git rebase upstream/master`
* 使用remote update：`git remote update` -> `git merge upstream/master` or `git rebase upstream/master`

### 更新到自己远程仓库(origin)
* `git push origin master`
* 第一次和远程库关联：`git push -u origin master`，由于远程库是空的，在第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。

### 分支管理
* 创建dev分支，然后切换到dev分支：`git checkout -b <name>`，命令加上-b参数表示创建并切换。
* 也可以用这两个命令创建dev分支：`git branch <name>` -> `git checkout <name>`
* 查看分支：`git branch`
* 切换分支：`git checkout <name>`
* 合并某分支到当前分支：`git merge <name>`
* 删除分支：`git branch -d <name>`

### 版本回退
* 显示版本号：`git log` `git reflog`
* 回退到上个版本：`git reset --hard HEAD^`
* 根据commit id回退版本：`git reset --hard <commit id>`

### 撤销修改
* 工作区的修改全部撤销：`git checkout -- <file>`
* 暂存区的修改全部撤销：`git reset HEAD <file>`

### 删除文件
* 删除文件后：`git add/rm <file>` 然后提交：`git commit`
* 恢复误删的文件：`git checkout -- <file>`

### 冲突处理
