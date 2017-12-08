# gitNote
git笔记，方便自己查看
----------------------------------------------------------------------------------------------------------------------------------------------------------
初始化git仓库   
	git init
添加文件到git仓库
git add file                  可以多次add
git commit  -m  "提交说明"                将add过的文件一次性提交
查看git仓库的状态使用命令
git status
查看修改过的文件,修改了什么使用命令
git diff  filename
查看git提交的历史记录使用命令
git log
还可以格式化输出的日志使用命令
git log --pretty=oneline
a18de9d277bdd450f62682ef07482795355f7e27   这是git中的版本号
把当前git版本退回到上一个版本可以使用命令                     上一个版本就是HEAD^     上上一个版本是HEAD^^    还可以写成HEAD~100
git reset --hard HEAD^
还可以使用
git reset --hard 版本号前7位
使用git reflog 命令可以查看输过的每一条命令
git checkout -- filename可以丢弃工作区的修改
用命令git reset HEAD filename可以把暂存区的修改撤销掉（unstage），重新放回工作区：
命令git rm用于删除一个文件
如果删错的话 可以用命令git checkout -- filename 进行还原
git remote add origin git@github.com:zhang-jiang-tao/gitTest.git   把本地仓库与github仓库相关联
把本地库的内容推送到远程     用git push命令          
git push -u origin master
由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支
还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。
从远程仓库克隆库到本地
git clone git@github.com:github名/远程仓库名.git
创建分支
git checkout -b 分支名称              创建并切换到dev(分支名称)分支
使用git branch 查看当前分支
切换分支
git checkout master   切换到master分支
合并分支
git merge  要合并的分支名称                  将dev合并到master分支
git branch -d dev                                  删除分支

查看分支：git branch

创建分支：git branch <name>

切换分支：git checkout <name>

创建+切换分支：git checkout -b <name>

合并某分支到当前分支：git merge <name>

删除分支：git branch -d <name>
git log --graph --pretty=oneline --abbrev-commit       可以看到分支的合并情况（分支历史）
it log --graph命令可以看到分支合并图。
git merge --no-ff -m "merge with no-ff" dev     合并分支并创建一个新的commit         用此命令合并后的分支有log   而fast forward 合并就看不出来曾经做过合并
把一个分支中的内容临时存储起来用     git status
用git stash list  查看git status保存的列表
把git status 存储的内容恢复有两种方法：
一是用git stash apply   恢复，再用git stash drop 删除
另一种是用git stash pop 在恢复的同时删除掉git stash中的内容
如果多次stash  恢复的同时 ，首先用命令  git status list 查看status列表
git stash apply stash@{0}              想恢复那个  就stash 几
如果要丢弃一个没有被合并过的分支，可以通过git branch -D <name>强行删除。
查看远程库的信息 用 命令 git remote
git pull  把最新提交从远程库里抓取下来 
推送分支 git push 远程库名 分支名
git branch --set-upstream dev origin/dev          指定远程库与本地库的分支
因此，多人协作的工作模式通常是这样：

首先，可以试图用git push origin branch-name推送自己的修改；

如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并；

如果合并有冲突，则解决冲突，并在本地提交；

没有冲突或者解决掉冲突后，再用git push origin branch-name推送就能成功！

如果git pull提示“no tracking information”，则说明本地分支和远程分支的链接关系没有创建，用命令git branch --set-upstream branch-name origin/branch-name。

这就是多人协作的工作模式，一旦熟悉了，就非常简单。
在需要标签的分支上，git tag name     就可以新建一个标签
使用git tag 命令可以查看所有标签
默认标签 是打在最新提交的commit上的，如果想对其他任意commit打标签，可以使用命令  git tag name 版本号
可以使用 tag show tagname 来查看标签信息
还可以创建带有说明的标签
 git tag -a v0.1 -m "version 0.1 released" 3628164           -a 代表 标签名 -m 代表说明文字
git tag -d 标签名                 删除标签
想要推送某个标签到远程可以使用  git push 远程库名 标签名
把本地标签全部推送到远程库使用命令
git push 远程库名 --tags
如果把标签推送到远程 ，要删除远程标签 需要先用命令  git tag -d 标签名 删除本地标签 然后使用命令 push 远程库名 :refs/tags/标签名      进行删除


