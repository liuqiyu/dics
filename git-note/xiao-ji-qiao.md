# 一些需要注意的小技巧


>  避免git多人开发存在冲突，在`.gitignore`文件中添加以下代码

```

// # Editor directories and files
.idea
.vscode
*.suo
*.ntvs*
*.njsproj
*.sln

// 若添加后还存在.workspace.xml冲突问题，

git  rm -r --cached .idea  

git add .
 
git commit -am 'delete workspace.xml' 

git push -f
```

> 本地项目上传到github

```
git init

git add .

git remote add origin https://github.com/liuqiyu/dd.git

git push -u origin master
```

> 强制本地代码覆盖服务器

`git push -f`

<hr>


查看所有版本： git log

回退到某个版本： git reset --hard 139dcfaa558e3276b30b6b2e5cbbb9c00bbdca96  

git push -f -u origin master  



