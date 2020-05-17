# 常用git命令



## 1. 管理远程仓库

​		git remote用于管理远程仓库

​		git remote 不带参数时可以参看远程仓库名称

​		git remote -v 可以查看远程仓库名称和网址

​		git remote add  仓库名  仓库地址  添加远程仓库，同时设置远程仓库的名字，一般仓库名称是origin，当然你也可以写成其他的名字

​		git remote rm  origin       删除名字为origin的远程仓库



## 2.管理本地分支

​		git branch 用于管理分支

​		git branch 分支名        创建分支

​		git checkout 分支名      切换到特定分支

​		git  checkout -b 分支名 相当于创建分支后还切换到新创建的分支

​		git branch -d 分支名   删除某个分支

​		git merge 分支名   合并某个分支到现在的所处的分支

## 3.管理远程分支

​		git branch -r 可以查看远程仓库的分支情况

​		git branch -a 可以查看所以分支的情况，即本地分支和远程分支

git push的用法：

​		git push <远程主机名>  <本地分支名>：<远程分支名>

​		需注意的是，分支的推送顺序写法是<来源地>：<目的地>

​		如果省略远程分支名则表示将本地分支推送到与之存在“追踪关系”的远程分支（通常两张同名），如果远程分支不存在，则会被新建。

​		git push <远程主机名> --detete <删除分支名>

​		git push <远程主机名>   :<远程分支名>

​		省略本地分支名相当于推送了一个空的本地分支到远程分支上，就相当于删除了远程分支

## 4.fetch、pull命令的用法

​		git fetch <远程仓库>

​		这个命令用于取回远程仓库上的更新到本地仓库，默认是取回远程仓库上的所有更新，如果要取回指定分支上的内容，可以使用：

​		git fetch <远程仓库> <分支名>

​	

​		git pull <远程主机名> <远程分支>：<本地分支>

相当于将origin远程仓库中master分支上的内容与本地master分支合并

如果远程分支是与当前分支合并，可以省略冒号后的内容

## 5.分支合并

​		将远程分支和本地分支合并：

​		git merge origin/master

​		或者

​		git rebase origin/master

​		表示将当前分支与远程分支合并



## 6.tag命令的用法

​		查看所有的标签git tag

​		删除某一个标签git tag -d tagName

​		查看标签里面的信息git show tagName

​		创建带注释的标签 git tag -a tagName -m "annotate"

​		轻量级标签 git tag tagName

​		切换到某一个标签 git checkout tagName



​		针对历史的commitId打标签 ：

​		git log --pretty=oneline --abbrev-commit 

​		git tag tagName commit_id

​		git tag -a tagName -m "annotate" commit_id 

​		查看标签，带筛选条件

​		如： git tag -l v1.4.2.*

​		将标签推送至github

​		git push --tags

​		git push --tag origin

​		git push origin tag_name

​		删除远程的标签 git push origin :refs/tags/tagName

​		列出远程所有的分支和标签 git ls-remote



## 7.回滚

​		git reset *--hard commitId

​		git push -f origin master

 		git reflog 来查看每一次命令的记录