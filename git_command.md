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

	<<<<<<< HEAD

	冲突发生前，没有进行合并时，当前位置的代码

	=======

	合并进来的冲突代码

	>>>>>>>

	 

	用户需要根据具体业务删除或者保留对应的代码，同时将<< HEAD == >> 这些标示去掉。

	 

	注：

	有时>>>>>>>后面会跟一些描述信息，比如分支名称、提交时的注释等等。

