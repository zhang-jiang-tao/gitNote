# gitNote
git笔记，方便自己查看
----------------------------------------------------------------------------------------------------------------------------------------------------------
<p>初始化git仓库命令</p>
<pre><code>git init</code></pre>
----------------------------------------------------------------------------------------------------------------------------------------------------------
<div>
<p>git将文件添加到库命令</p>
<p>1.首先将文件add到暂存区命令</p>
<pre><code>git add file	可以多次add</code></pre>
<p>2.再将文件commit到master分支命令</p>
<pre><code>git commit  -m  "提交说明"                将add过的文件一次性提交</code></pre>
</div>
-----------------------------------------------------------------------------------------------------------------------------------------------------------
<p>查看当前git状态命令</p>
<pre><code>git status</code></pre>
<p>查看修改过的文件,修改了什么使用命令</p>
<pre><code>git diff  filename</code></pre>
<p>查看git提交的历史记录使用命令</p>
<pre><code>git log</code></pre>
<p>还可以格式化输出的日志使用命令</p>
<pre><code>git log --pretty=oneline</code></pre>
<p>git中的版本号如下一串字符</p>
<pre><code>a18de9d277bdd450f62682ef07482795355f7e27</code></pre>
<p>把当前git版本退回到上一个版本可以使用命令 </p>
<p>上一个版本就是HEAD^     上上一个版本是HEAD^^    第100个版本还可以写成HEAD~100</p>
<pre><code>git reset --hard HEAD^</code></pre>
<p>也可以通过git版本号来回退</p>
<pre><code>git reset --hard 版本号前7位</code></pre>
<p>查看在git命令窗口输过的命令</p>
<pre><code>git reflog </code></pre>
<p>丢弃工作区的修改命令</p>
<pre><code>git checkout -- filename</code></pre>
<p>把暂存区的修改撤销掉（unstage），重新放回工作区</p>
<pre><code>git reset HEAD filename</code></pre>
<p>删除文件</p>
<pre><code>git rm filename</code></pre>
<p>如果删错的话 可以用命令</p>
<pre><code>git checkout -- filename	进行还原</code></pre>
<p>把本地仓库与github仓库相关联</p>
<pre><code>git remote add origin git@github.com:github用户名/远程库名.git</code></pre>
<p>把本地库的内容推送到远程 </p>
<pre><code>git push origin 分支名称</code></pre>
<p>如果远程仓库是空的，第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支</p>
<p>还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令</p>
<pre><code>git push -u origin master</code></pre>
<p>从远程仓库克隆库到本地</p>
<pre><code>git clone git@github.com:github名/远程仓库名.git</code></pre>
<p>创建分支</p>
<pre><code>git checkout -b 分支名称              创建并切换到dev(分支名称)分支</code></pre>
<p>查看当前分支</p>
<pre><code>git branch</code></pre>
<p>切换分支</p>
<pre><code>git checkout master   切换到master分支</code></pre>
<p>合并分支</p>
<pre><code>git merge  要合并的分支名称                  将dev合并到master分支</code></pre>
<p>删除分支</p>
<pre><code>git branch -d dev </code></pre>
<p>查看分支的合并情况（分支历史）</p>
<pre><code>git log --graph --pretty=oneline --abbrev-commit </code></pre>
<p>查看分支合并图。</p>
<pre><code>git log --graph</code></pre>
<p> 合并分支并创建一个新的commit         用此命令合并后的分支有log   而fast forward 合并就看不出来曾经做过合并</p>
<pre><code>git merge --no-ff -m "merge with no-ff" dev</code></pre>
<p>把一个分支中的内容临时存储起来</p>
<pre><code>git status</code></pre>
<p>查看git status列表</p>
<pre><code>git stash list</code></pre>
<p>把git status 存储的内容恢复有两种方法：</p>
<p>一是用<pre><code>git stash apply</code></pre>恢复，再用<pre><code>git stash drop</code></pre> 删除</p>
<p>另一种是用<pre><code>git stash pop </code></pre>在恢复的同时删除掉<pre><code>git stash</code></pre>中的内容</p>
<p>如果多次stash  恢复的同时 ，首先用命令<pre><code>git status list </code></pre>  查看status列表</p>
<p> 想恢复那个  就stash 几</p>
<pre><code>git stash apply stash@{0} </code></pre>
<p>如果要丢弃一个没有被合并过的分支，可以通过<pre><code>git branch -D <name></code></pre>强行删除。</p>
<p>查看远程库的信息</p>
<pre><code>git remote</code></pre>
<p>把最新提交从远程库里抓取下来 </p>
<pre><code>git pull </code></pre>
<p>推送分支</p>
<pre><code>git push 远程库名 分支名</code></pre>
<p>指定远程库与本地库的分支</p>
<pre><code>git branch --set-upstream dev origin/dev</code></pre>
<p>因此，多人协作的工作模式通常是这样：</p>
<p>首先，可以试图用<pre><code>git push origin branch-name</code></pre>推送自己的修改</p>
<p>如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并</p>
<p>如果合并有冲突，则解决冲突，并在本地提交</p>
<p>没有冲突或者解决掉冲突后，再用<pre><code>git push origin branch-name</code></pre>推送就能成功</p>
<p>如果git pull提示<pre><code>no tracking information</code></pre>，则说明本地分支和远程分支的链接关系没有创建，用命令<pre><code>git branch --set-upstream branch-name origin/branch-name</code></pre></p>
<p>这就是多人协作的工作模式，一旦熟悉了，就非常简单。</p>
<p>在需要标签的分支上,新建一个标签</p>
<pre><code>git tag name</code></pre>
<p>查看所有标签</p>
<pre><code>git tag</code></pre>
<p>默认标签 是打在最新提交的commit上的，如果想对其他任意commit打标签，可以使用命令 <pre><code>git tag name 版本号</code></pre></p>
<p>查看标签信息</p>
<pre><code>tag show tagname </code></pre>
<p>还可以创建带有说明的标签</p>
<pre><code>git tag -a v0.1 -m "version 0.1 released" 3628164           -a 代表 标签名 -m 代表说明文字</code></pre>
<p>删除标签</p>
<pre><code>git tag -d 标签名  </code></pre>
<p>想要推送某个标签到远程可以使用 </p>
<pre><code>git push 远程库名 标签名</code></pre>
<p>把本地标签全部推送到远程库使用命令</p>
<pre><code>git push 远程库名 --tags</code></pre>
<p>如果把标签推送到远程 ，要删除远程标签 需要先用命令</p>
<pre><code>git tag -d 标签名 删除本地标签</code></pre>
<p>然后使用命令<pre><code>push 远程库名 :refs/tags/标签名</code></pre>    进行删除</p>