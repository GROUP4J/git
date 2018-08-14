## git命令
### 查看分支结构
    git log --graph --decorate --oneline --[simplify-merges|full-history|simplify-by-decoration] --all

## 关联本地分支和远程分支
	git branch --set-upstream-to=origin/remote_branch your_branch
	关联目的是在执行git pull, git push操作时就不需要指定对应的远程分支，你只要没有显示指定，git pull的时候，就会提示你。其中，origin/remote_branch是你本地分支对应的远程分支；your_branch是你当前的本地分支。
