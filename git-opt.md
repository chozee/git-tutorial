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
直接修改冲突文件然后保存。
Git用<<<<<<<，=======，>>>>>>>标记出不同分支的内容

###### 查看分支合并情况
> git log
> 用git log --graph命令可以看到分支合并图

##### 显示分支合并记录（禁用Fast forward）
合并分支时，如果可能，Git会用Fast forward模式，但这种模式下，删除分支后，会丢掉分支信息。
如果要强制禁用Fast forward模式，Git就会在merge时生成一个新的commit，这样，从分支历史上就可以看出分支信息。
下面我们实战一下--no-ff方式的git merge

> git merge --no-ff -m "merge with no-ff" dev

##### 暂存工作区
> git stash
工作只进行到一半，还没法提交，预计完成还需1天时间。但是，必须在两个小时内修复该bug
> git stash list
查看暂存的内容
> git stash apply # 恢复暂存的内容
> git stash drop # 删除暂存内容
> git stash pop # 恢复并删除
> git stash apply stash@{0} #恢复指定的stash 

##### 暂存区与丢失
暂存区不提交会丢失？必须暂存stash？
修复bug时，我们会通过创建新的bug分支进行修复，然后合并，最后删除

##### 删除未合并分支
git branch -D 未合并分支

### 推送分支

推送分支，就是把该分支上的所有本地提交推送到远程库。推送时，要指定本地分支，这样，Git就会把该分支推送到远程库对应的远程分支上：
> git push origin master
如果要推送其他分支，比如dev，就改成：
> git push origin dev
但是，并不是一定要把本地分支往远程推送，那么，哪些分支需要推送，哪些不需要呢？
- master分支是主分支，因此要时刻与远程同步；
- dev分支是开发分支，团队所有成员都需要在上面工作，所以也需要与远程同步；
- bug分支只用于在本地修复bug，就没必要推到远程了，除非老板要看看你每周到底修复了几个bug；
- feature分支是否推到远程，取决于你是否和你的小伙伴合作在上面开发。

### 更新（抓取）分支
> git pull
如果git pull提示“no tracking information”，则说明本地分支和远程分支的链接关系没有创建，用命令git branch --set-upstream 分支名 origin/分支名

### 指定本地分支与远程分支的链接

进入指定的目录
> git branch --set-upstream dev origin/dev


# github
### “Fork”就在自己的账号下克隆了一个别人的仓库
> 一定要从自己的账号下clone仓库，这样你才能推送修改

### 让别人接受你的修改

> pull request

可以推送pull request给官方仓库来贡献代码。

### 显示颜色

> git config --global color.ui true

### 忽略特殊文件

在Git工作区的根目录下创建一个特殊的.gitignore文件，然后把要忽略的文件名填进去，Git就会自动忽略这些文件。
不需要从头写.gitignore文件，GitHub已经为我们准备了各种配置文件，只需要组合一下就可以使用了。所有配置文件可以直接在线浏览：https://github.com/github/gitignore
当然检验.gitignore的标准是git status命令是不是说working directory clean
有些时候，你想添加一个文件到Git，但发现添加不了，原因是这个文件被.gitignore忽略了。git add -f App.class
忽略文件的原则是：
- 忽略操作系统自动生成的文件，比如缩略图等；
- 忽略编译生成的中间文件、可执行文件等，也就是如果一个文件是通过另一个文件自动生成的，那自动生成的文件就没必要放进版本库，比如Java编译产生的.class文件；
- 忽略你自己的带有敏感信息的配置文件，比如存放口令的配置文件。


### Untracked files
表示未加入的文件








