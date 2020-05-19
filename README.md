# GitErrLog
在使用git过程中遇到的错误处理情况整理 （Sort out the error handling situations encountered during the use of git）

1. git push origin https://github.com/xxxx.git （推送本地仓库至远程命令）

   Err: fatal: invalid refspec 'https://github.com/xxxx.git'

   Solution: git remote add origin https://github.com/xxxx.git (本地仓库没有远程仓库相关信息，先添加 )


2. git push origin master （推送本地仓库至远程命令）

   Err:remote: Permission to username/projectName.git denied to pmlican.
    fatal: unable to access 'https://github.com/username/projectName.git/': The requested URL returned error: 403
    
   Solution: 修改git配置文件 （vim .git/config）（配置远程仓库账号密码信息，采用权限进行操作）
    修改前
    [remote "origin"]
          url = https://github.com/username/projectname.git

   修改为：
   [remote "origin"]
        url = https://username@github.com/username/projectname.git
        
        
        
3. 查看远程仓库相关信息：git remote -v

   删除远程相关信息：git remote rm xxx
  
  
4. git pull origin master (拉取远程仓库代码)

   From https://github.com/username/projectname
   * branch            master     -> FETCH_HEAD
   fatal: refusing to merge unrelated histories （github 的仓库和本地的没有一个共同的 commit 所以 git 不让提交，添加可选参数-allow-   unrelated-histories ）

   Solution：git pull origin master -allow-unrelated-histories


