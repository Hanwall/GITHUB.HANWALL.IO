---
title: 在github搭建blog
date: 2018-10-24 17:52:33
categories: HOWTODO
tags: BLOG
---

国内程序员博客网站很多，著名有 cnblog, csdn, oschina这样的。使用blog其实有很多选择:

* 去上面的网站直接写博客就行了。（喜欢折腾）
* 自己搭建服务器
 * 自己购买服务器或者云主机搭建。（穷逼）
 * 本地搭建服务器用动态域名解析。（不能关机）
 * 使用一些免费的云服务搭建，比如Openshift。（速度感觉好蛋疼，而且v3版本的操作感觉有些复杂）
 * 使用GitHub的GitHub Pages功能来搭建。（主要是方便听说很好用。喜欢折腾的）

官方对GitHub Pages的定义是Hosted directly from your GitHub repository. Just edit, push, and your changes are live。

基础环境
OS:Window 10 + Debian Bash

### 安装git
```bash
   $ sudo apt-get install git
```

### 去github 创建项目，项目命名格式必须遵守：username.github.io，username是你的用户名。添加一个index页面，
```bash
   $  git clone YOUR_REPOSITORY_URL
   $  echo "test page" > index.md
   $  git add -A
   $  git commit -m "add index page"
   $  git push orign master
   #提交好之后就已经发布到网络了，
   #你可以通过https://username.github.io来访问了。在项目Setttings可以看到GitHub Pages功能模块，在这里可以修改相关设置，比如自定义域名。
   #github 默认使用 Jekyll构建你的博客。你可以自己选择其它的。目前比较流行的是hexo.
```

### 安装Hexo,需要node.js
```bash
   #去node.js官网https://nodejs.org/en/下载源码安装,这里需要注意hexo有版本要求，我用的最新的。
   $ wget https://nodejs.org/dist/v8.12.0/node-v8.12.0-linux-x64.tar.xz
   #然后这里的文件后缀是tar.xz,需要安装解压工具
   $ sudo apt-get install xz-utils
   $ chmod 775 ./node-v8.12.0-linux-x64.tar.xz
   $ tar xvJf node-v8.12.0-linux-x64.tar.xz
   $ sudo mv  ./node-v8.12.0-linux-x64 /opt
   #修改path
   $ vi ~/.bashrc
   $ export=$PATH:/opt/node-v8.12.0-linux-x64/bin
   #立即生效
   $ source ~/.bashrc
   $ npm -v
   $ npm install hexo-cli -g
```

### 使用hexo，官网https://hexo.io/zh-cn/教程很详细
```bash
   $ hexo init blog
   $ cd blog
   #修改_config.yml的配置注意空格,生成发布目录
   $ hexo generate
   #public文件夹的文件就可提交到你开始设置项目里
   #为了便于提交和管理，我删除了public目录，创建了一个window软连接
   $ rm -r ./publc
```
```cmd
   ::-----------window cmd-------
   ::需要编码ANSI
   mklink /d C:\Users\root\Documents\Workspaces\blog\public  C:\Users\root\Documents\Workspaces\username.github.io
   ::我也会把blog构建仓库提交到github，不然丢失挺麻烦的。
```

### 新博文
```bash
   $ hexo new "在GITHUB搭建BLOG"
```
   以上只是使用了最基本的操作，许多高级功能等待去发掘，比如自动部署等。


接下在可以愉快的发博客了。。。。。。。。。。。。。。
