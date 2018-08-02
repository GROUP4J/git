克隆group中的项目到本地，修改后提交，无法直接提交  
报错信息：Pushing to Git returning Error Code 403 fatal: HTTP request failed  
因为是组织，所以只有添加到组织中的用户可以提交，故提交时需要增加用户信息  

    git remote set-url origin https://yourusername@github.com/user/repo.git
    // 用户名@提交地址

然后提交代码
    
    git push origin master
即可
