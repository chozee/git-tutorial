参考： http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000

##### 本地仓库关联远程仓库
> git remote add origin git@github.com:你的名字/你的response.git
>> 添加后，远程库的名字就是origin，这是Git默认的叫法，也可以改成别的，但是origin这个名字一看就知道是远程库。

##### 把本地库的内容推送到远程
git push -u origin master --第一次
> 把本地库的内容推送到远程，用git push命令，实际上是把当前分支master推送到远程。
> 由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。

从现在起，只要本地作了提交，就可以通过命令：
> git push origin master

##### clone远端仓库
> git clone git@github.com:你的账户名/你的response.git

##### 创建分支
> git checkout -b dev
git checkout命令加上-b参数表示创建并切换，相当于以下两条命令：
> git branch dev
> git checkout dev

##### 查看当前分支
git branch命令查看当前分支
> * dev
  master

git branch命令会列出所有分支，当前分支前面会标一个*号。

##### 切换分支
> git checkout master #（要切换的分支）

##### 合并 merge
切换到master或者其他要合并分支之后执行：git merge命令用于合并指定分支到当前分支。
> git merge #（要合并的分支）

##### 删除分支
> git branch -d dev

##### 查看冲突文件
> git status

##### 解决冲突






