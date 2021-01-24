GIT常见命令
1.git init		//初始化
2.git status	//查看状态
3.git add <file>	//添加文件
4.git commit	//提交
5.git push		//推送到远程仓库
6.git pull		//从远程仓库拉取数据
7.git clone	//从远程仓库拷贝数据

8.git config --global user.name 'um'
git config --global user.email '135@email.com'	//配置个人信息 

9.git add *.html	//添加某一类文件
git add .		//添加所有文件

10.git rm --cached filename	//移除文件
git rm -r --cached filename/	//移除文件夹

11.git commit filename -m '...'	//提交文件

12.touch .gitignore		//忽略不想上传的文件，在.gitignore文件中
			//添加不想上传的文件（夹）名

13.git branch branchname		//创建分支
git chechout branchname/master	//进入分支/主线
git merge branchname		//合并分支，在主线中执行该命令

14.git remote add origin https://github.com/Mr-Wong-code/Mr_Wong.git		//连接远程仓库
git remote add 远程仓库名 远程仓库地址

15.git push -u origin master							//推送到远程仓库
git push 远程主机名	本地分支名：远程分支名					//使用-u默认后面的参数，
									//之后本地相同的仓库传到相同的远程主机可直接用git push
									//-f强制推送，不建议使用，应想用git pull

16.git clone https://github.com/Mr-Wong-code/Mr-Wong-code.github.io.git		//克隆项目


github使用步骤：
一、
git config --global user.name "Wong"
git config --global user.email "1036547912@qq.com"
查看配置结果：
git config user.name
git config user.email

二、
git init //会在本地创建一个.git文件
git add learning.txt //将文件从untracked变为staged，告诉git有该文件（添加到仓库）
git add java.txt 
git commit -m "commit a file"  //告诉git这些文件可以提交
更改了文件，查看状态和更改
git status
git diff learning.txt
git log

三、
git remote add origin git@github.com:Wong-code/Mr_Wong.git  //连接远程仓库，origin是远程仓库的小名，Wong-code是username，Mr_Wong是仓库名
git push -u origin master //将文件传到远程仓库



