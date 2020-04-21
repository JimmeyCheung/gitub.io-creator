---
title: "如何使用hugo搭建个人博客"
date: 2020-04-21T13:25:47+08:00
draft: false
---
## 注:xxx在下文中代指github的用户名  
1. 安装对应操作系统的hugo[安装地址](https://github.com/gohugoio/hugo/releases).
2. 为了能够在bash命令中执行hugo命令,添加hugo所在文件夹路径到PATH环境变量中.使用命令`hugo version`检测是否安装成功.
3. 新建站点和博客内容
``` javascript
// 新建一个hugo站点
hugo new site xxx.github.io-creator 
// 新建个人博客myBlog,博客内容可使用markdown在"---"段落后书写
hugo new posts/myBlog.md
```
4. 添加默认主题ananke
```
cd xxx.github.io-creator
git init 
git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke
echo 'theme = "ananke"' >> config.toml
```
5. 下载自定义主题安装
* git clone 主题地址到themes目录
* 删除主题中的.git文件: rm -rf ./themes/.git
* 修改config.toml文件中的theme指定主题名
6. 使用命令进行配置: 
``` javascript
// 在本地服务端启用站点浏览博客页面
写法一:  hugo server -D
写法二(不浏览草稿,手动修改draft为false):  hugo server
注意: "---"段落中的date不能晚于当前时间,否则不会显示在博客中
// 生成public目录文件
写法一(发布全部内容包括草稿): hugo -D 
写法二(不发布草稿): hugo 
/* 
 * 分别给xxx.github.io-creator 和 public 文件夹添加本地仓库
 * 由于public文件包含在xxx.github.io-creator文件中
 * 请在xxx.github.io-creator文件下的.gitignore文件中加上public文件夹
 */
cd public 
git init
git add .
git commit
```
7. 在github新建两个库xxx.github.io-creator和xxx.github.io,分别对应本地的xxx.github.io-creator仓库(用于备份,可选)和public仓库(对应github pages的站点)
``` javascript
// 连接远程仓库xxx.github.io和本地仓库public.并将public代码提交
cd public 
git remote add origin git@github.com:xxx/xxx.github.io
git push -u origin master
```
8. 提交完成后在github对应仓库的Settings的github pages查看站点地址进行访问
