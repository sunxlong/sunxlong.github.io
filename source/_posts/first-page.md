---
title: 使用HEXO搭建博客
date: 2017-11-06 14:52:11
tags: 
- 前端
- NodeJS
categories: [项目,代码]
---

简要介绍下Hexo搭建博客的相关知识，主要内容如下

+ Hexo的安装、使用、发布
+ NexT主题安装与配置
+ Hexo优化

<!--more-->	
	
详情文档参考请移步至[**Hexo中文网**](https://hexo.io/zh-cn/)

安装
===

环境
---

系统：Win7 64bit

- Node版本: v0.12.0

- Hexo版本：3.1.1

- Git版本： 1.9.5.msysgit.1

安装HEXO
---

```
npm install hexo-cli -g //下载hexo包  
hexo init blog //初始化一个博客项目，项目名称叫blog  
cd blog	 
npm install //安装依赖  <br>
hexo server //启动http服务，预览项目
```

用浏览器打开 ``http://localhost:4000/`` 或者 ``http://127.0.0.1:4000/``就能看到网页了
推荐使用现代化浏览器``(Chrome)``获得最佳效果

按 ``Ctrl+C`` 停止本地预览服务

使用
===

hexo的目录结构
---

```
.
├── .deploy       #需要部署的文件
├── node_modules  #Hexo插件
├── public        #生成的静态网页文件
├── scaffolds     #模板
├── source        #博客正文和其他源文件, 404 favicon CNAME 等都应该放在这里
|   ├── _drafts   #草稿
|   └── _posts    #文章
├── themes        #主题
├── _config.yml   #全局配置文件
└── package.json
```

全局配置_config.yml
---

配置文件的冒号':'后面有空格

```
# Site #站点信息
title: lmintlcx #标题
subtitle: 做人不卖萌跟咸鱼有什么区别 #副标题
description: lmintlcx lm lcx blog #描述
author: lmintlcx #作者
language: zh-Hans #语言
timezone: Asia/Shanghai #时区
# URL #链接格式
url: http://blog.lmintlcx.com #网址
root: / #根目录
permalink: post/:title.html #文章的链接格式
permalink_defaults:
# Directory #目录
source_dir: source #源文件
public_dir: public #生成的网页文件
tag_dir: tags #标签
archive_dir: archives #归档
category_dir: categories #分类
code_dir: downloads/code
i18n_dir: :lang #国际化
skip_render:
# Writing #写作
new_post_name: :title.md #新文章标题
default_layout: post #默认模板(post page photo draft)
titlecase: false #标题转换成大写
external_link: true #新标签页里打开连接
filename_case: 0
render_drafts: false
post_asset_folder: false
relative_link: false
future: true
highlight: #语法高亮
  enable: true
  line_number: false #显示行号
  auto_detect: true
  tab_replace:
# Category & Tag #分类和标签
default_category: uncategorized #默认分类
category_map:
tag_map:
# Date / Time format #日期时间格式
## http://momentjs.com/docs/#/displaying/format/
date_format: YYYY-MM-DD
time_format: HH:mm:ss
# Pagination #分页
per_page: 20 #每页文章数, 设置成 0 禁用分页
pagination_dir: page
# Extensions #插件和主题
## 插件: http://hexo.io/plugins/
## 主题: http://hexo.io/themes/
theme: next
# Deployment #部署, lmintlcx是我的用户名, 同时发布在 GitHub 和 GitCafe 上面
deploy:
  type: git
  repo: 
    github: https://github.com/lmintlcx/lmintlcx.github.io.git,master
    gitcafe: https://gitcafe.com/lmintlcx/lmintlcx.git,gitcafe-pages
# Disqus #Disqus评论系统
disqus_shortname: 
plugins: #插件，例如生成 RSS 和站点地图的
- hexo-generator-feed
- hexo-generator-sitemap
```

命令行使用
===

常用命令
---

```
hexo help #查看帮助
hexo init #初始化一个目录
hexo new "postName" #新建文章
hexo new page "pageName" #新建页面
hexo generate #生成网页, 可以在 public 目录查看整个网站的文件
hexo server #本地预览, 'Ctrl+C'关闭
hexo deploy #部署.deploy目录
hexo clean #清除缓存, **强烈建议每次执行命令前先清理缓存, 每次部署前先删除 .deploy 文件夹**
```

复合命令
---

```
hexo deploy -g #生成加部署
hexo server -g #生成加预览
```

### 简写

```
hexo n == hexo new
hexo g == hexo generate
hexo s == hexo server
hexo d == hexo deploy
```

### 安装插件

<plugin-name> 为插件名

```
npm install <plugin-name> --save #安装
npm update #升级
npm uninstall <plugin-name> #卸载
```

### 安装主题

<repository> 为主题的 git 仓库, <theme-name>为要存放在本地的目录名

```
git clone <repository> themes/<theme-name>
```

修改主题配置

```
theme: <theme-name>
```

### 编辑文章

```
hexo new "标题" 或者 hexo n 标题
```

在_posts目录下会生成文件 标题.md

```
title: 标题
date: 2015-09-20 13:18:46
tags:
- 标签1
- 标签2
- 标签3
categories: [分类1,分类2,分类3]
---
正文, 使用 Markdown 语法书写
```

编辑完成后保存，``hexo server`` 预览

## 发布

可以部署到GitHub或Coding
发布到GitHub 项目主页需要把 branch 设置为 gh-pages

```
deploy:
  type: github
  repo: https://github.com/git-lt/blog.git
  branch: master
```

或者发布到Coding

```
deploy:
  type: git
  repo: https://git.coding.net/coderlt/blog.git
  branch: master
```

发布

```
hexo deploy
```

出现以下提示说明部署成功

```
[info] Deploy done: github
```

在浏览器输入``localhost:4000``即可访问刚刚新创建的博客  