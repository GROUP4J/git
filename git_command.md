## git命令
### 查看分支结构
    git log --graph --decorate --oneline --[simplify-merges|full-history|simplify-by-decoration] --all

## 关联本地分支和远程分支
	git branch --set-upstream-to=origin/remote_branch your_branch
	关联目的是在执行git pull, git push操作时就不需要指定对应的远程分支，你只要没有显示指定，git pull的时候，就会提示你。其中，origin/remote_branch是你本地分支对应的远程分支；your_branch是你当前的本地分支。

## 冲突解决
	1，有可能产生冲突的命令
	（1）git merge <需要合并进来的分支名称>

	（2）git pull <远程仓库> <远程分支>

	（3）git rebase -i <要合并进来的分支名称>
	2，解决冲突
	发生冲突后，使用git status可以查看到冲突文件是红色字体显示的。打开文件，冲突部分会有特定表示如下


	冲突发生前，没有进行合并时，当前位置的代码

	=======

	合并进来的冲突代码

	>>>>>>>

	 

	用户需要根据具体业务删除或者保留对应的代码，同时将<< HEAD == >> 这些标示去掉。

	 

	注：

	有时>>>>>>>后面会跟一些描述信息，比如分支名称、提交时的注释等等。
=======
### 创建新分支
	git branch [branch_name]

### 切换分支
	git checkout [branch_name]

### 显示分支
	git branch [-a]

### 查看远程分支
	git branch -r

### 删除本地分支
	git branch -d [branch_name]

### 删除远程分支
	git push origin:[branch_name]

## fetch和merge
使用git fetch 更新远端跟踪分支

### git merge合并分支产生冲突
可以使用git status查看状态，git diff查看冲突

## 从远程仓库获取最新代码合并到本地分支
### 无冲突情况
1.git pull:获取最新代码到本地，并自动合并到当前分支   
 
    //查询当前远程分支版本
    git remote -v
	// 直接拉取并合并最新代码
	git pull origin master [从远端origin/master分支合并到当前分支]

2.git fetch+merge：获取最新代码到本地，然后手动合并 
2.1 额外建立本地分支 
   
    //查看当前远程版本
    git remote -v
	// 获取最新代码到本地临时分支
	git fetch origin master:master1
	// 查看版本差异
	git diff master1 [查看master1与当前分支的版本差异]
	// 合并最新分支到本地分支
	git merge master
	// 删除本地临时分支
	git branch -D master1

2.2 不额外建立本地分支  

    //查询当前远程版本
    git remote -v
	// 获取最新代码到本地（本地当前分支为[branch]，获取的远端分支为origin/branch]
	git fetch origin master [获取远端的origin/master分支]
	//查看版本差异
	git log -p master origin/master [查看本地master与远端origin/master的版本差异]
	// 合并最新代码到本地分支
	git merge origin/master


### git 远程强制更新到本地，覆盖本地工作空间

    git fetch --all
	git reset --hard origin/master [origin/master为要拉取的远程分支]
	git pull [检查是否为最新]

### git reflog显示日期
	git reglog --date=iso
