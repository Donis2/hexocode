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

----

butterfly 5.5.0

hexo: 7.3.0
hexo-cli: 4.3.2

node: 22.12.0

插件更新方法: https://blog.zhheo.com/p/6d1f1f98.html