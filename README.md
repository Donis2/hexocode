# hexocode
hexo的本地源码




git config --global user.name donis2
git config --global user.email 2561055937@qq.com


git config --global user.name liuxizhaizhu
git config --global user.email 3277006245@qq.com



```git
#上传整个源码

git init
git add .
git pull origin main
git commit -m "init"
git branch -M main

git remote add origin https://github.com/Donis2/hexocode.git 
# 出现"error: remote origin already exists"就意思是不用执行这个命令了，直接下一个

git push -u origin main

```


