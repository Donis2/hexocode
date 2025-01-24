---
title: windows for docker安装halo
date: 2025-1-24
updated: 2025-1-24
tags: 'docker,halo'
categories: 教程
keywords: 'docker,halo,windows上使用halo,本地搭建halo'
description: windows上本地搭建halo
top_img: 'https://www.halo.run/upload/2022/03/logo.svg'
comments: true
cover: 'https://www.halo.run/upload/2022/03/logo.svg'
copyright_author: 柳溪斋主
copyright_author_href: 'https://donis2.github.io'
copyright_url: 'https://donis2.github.io/posts/a7e5c6ee.html'
abbrlink: f887098f
toc:
toc_number:
toc_style_simple:
copyright:
copyright_info:
mathjax:
katex:
aplayer:
highlight_shrink:
aside:
abcjs:
noticeOutdate:
---


作者: Jerry
連結: https://butterfly.js.org/posts/dc584b87/
來源: Butterfly
版權屬於作者所有。商業用途請聯絡作者獲得授權，非商業用途請註明出處。
# 安装WSL2

## 打开虚拟机平台和子系统两个选项

### 1

先在任务栏搜索 `windows功能` 然后打开选项卡。

![](https://pic1.imgdb.cn/item/678d12b9d0e0a243d4f5b2be.png)

### 2

勾选下面两个选项，然后重启。

![](https://pic1.imgdb.cn/item/678d12a8d0e0a243d4f5b2b3.png)

## 安装WSL

### 安装


```cmd
wsl --install

```

运行 WSL 并默认安装 Linux 的 Ubuntu 发行版所需的功能。

### 升级WSL2


```cmd
wsl --update

```

### 设置默认WSL版本为WSL2


```cmd
wsl --set-default-version 2

```

### 把子系统转移到D盘

```cmd
wsl --shutdown   #停止所有正在运行的子系统
wsl -l -v        #查看所有安装过的子系统
wsl --export <上一条命令查看到的子系统名字，默认是Ubuntu> D:/<要改的路径>/取个名字.tar   #（注意要写.tar后缀，这是在导出安装了的子系统）
wsl --unregister <子系统名字>   #删除原来在c盘的子系统
wsl --import <子系统子系统名> D:\子系统在D要存放的位置\ D:\<要改的路径>\刚刚取的名字.tar --version 2

```

迁移完成

# 安装docker

## 安装

访问下面GitHub网站下载windows的安装包。

`https://github.com/tech-shrimp/docker_installer/releases`

假设你把`docker_desktop_installer_windows_x86_64.exe` 下载到 `D:/Edge下载/` 找个文件夹里面。

然后再D盘兴建文件夹`D:\Docker\docker`

最后再cmd中运行下面代码：


```cmd
start /w "" "D:\Edge下载\docker_desktop_installer_windows_x86_64.exe" install --installation-dir=D:\Docker\docker
```

就开始安装docker，并且docker的安装位置在 `D:\Docker\docker`中。

## 汉化

访问 [汉化包仓库](https://github.com/asxez/DockerDesktop-CN)[asxez/DockerDesktop-CN: Docker汉化 Docker中文版 Docker汉化包 DockerDesktop汉化 Docker Windows Docker MAC](https://github.com/asxez/DockerDesktop-CN)

下载对应版本的汉化包，不知道版本的运行`docker version`命令，然后把汉化包名字改成`app.asar`，在把它复制粘贴到\\docker\\frontend\\resources下面的同名文件。确认替换之后，重启docker就可以汉化了。

## 改镜像源

点击右上角齿轮设置

打开下面界面。

![](https://pic1.imgdb.cn/item/678d12a8d0e0a243d4f5b2b4.png)

点击docker引擎，粘贴下面代码：


```json
{
  "builder": {
    "gc": {
      "defaultKeepStorage": "20GB",
      "enabled": true
    }
  },
  "experimental": false,
  "registry-mirrors": [
    "https://izhmiia0.mirror.aliyuncs.com",
    "https://docker.1panel.live",
    "https://hub.rat.dev"
  ]
}

```

你也可以网上找其他的镜像源

到此，windows for docker安装完毕

# halo搭建

## 子系统里放'.halo'文件

访问[halo官网](https://www.halo.run/),点击‘快速开始’，点击’使用 Docker 部署‘。往下翻，复制docker创建容器命令。

然后打开wsl2下载的子系统的控制台，我用的kali-Linux。

在下面这种Linux系统的终端里输入复制的创建halo的命令：
![](https://pic1.imgdb.cn/item/678d12c1d0e0a243d4f5b2bf.png)

之后你会在这个位置，访问kali-Linux->\\root\\.halo 这个目录下看见halo的相关文件。![](https://pic1.imgdb.cn/item/678d12c1d0e0a243d4f5b2c0.png)

## windows中放‘.halo‘文件

如果你想在D盘里面编辑'.halo'文件

要修改halo创建容器命令：

```cmd
docker run -it -d --name halo -p 8090:8090 -v d:/Docker/Halo:/root/.halo2 -e JVM_OPTS="-Xmx256m -Xms256m" registry.fit2cloud.com/halo/halo:2.20

```

这个命令就是让’.halo‘文件创建到‘d:/Docker/Halo’文件夹下面。效果相同。

到此配置结束。

访问localhost:(你创建容器命令里面设置的端口，默认8090)就可以本地使用Halo了
