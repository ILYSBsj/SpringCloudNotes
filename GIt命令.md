##git命令
###长期存储密码：
git config --global credential.helper store
###初始化
1、git init      （建立本地仓库）
2、git add  *  (将代码添加到本地仓库，《*是添加全部代码，代码全部更新》)
git add -A 
3、git commit -m "first commit"
4、git remote add origin https://github.com/hongduhong/test.git  
（将本地仓库的代码提交远程github的仓库，《后面的地址就是之前创建github的远程仓库地址》）
5、git push -u origin master  

###403报错问题:
1、使用code登录。token没用
2、控制面板——>用户账户——>凭证管理器——>Windows凭据，删除。
3、在电脑C盘目录——>用户——>Administrator，找到.gitconfig文件，打开编辑修改成自己的账号密码。

###添加到2个远程：
git add -A 
git add  *  (将代码添加到本地仓库，*是添加全部代码，代码全部更新)
git commit -m "first commit"
git push -u origin master  //github qq邮箱
git push -u origingitee master  //gitee 手机号

###下载：
git pull origingitee master