---
title: Hexo + Github Pages 个人博客构建指南
date: {{ date }}
tags: Hexo Tutorial
categories:
- Tutorial
- Hexo Tutorial
banner: /gallery/new-hexo.png
---

#### 简介&前言

早些时候，已经了解了一些类似的博客框架，但是一直也没有着手实践一回，最近使用Hexo构建了一个自己的博客，在此记录下Hexo + Github Pages博客构建过程。


#### 什么是 Hexo？

[Hexo](https://hexo.io/) 是一个快速、简洁且高效的博客框架。Hexo 使用 Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。

<!--more-->

#### 安装

Hexo版本信息:

* hexo: 3.2.2
* hexo-cli: 1.0.2

#### 安装前提

安装 Hexo 还是相当简单的，但是开始Hexo安装之前，必须检查电脑中是否已安装下列应用程序:

* [Node.js](https://nodejs.org)        - https://nodejs.org
* [Git](https://git-scm.com/downloads) - https://git-scm.com/downloads

建议可以再安装一个TortoiseGit工具来做为Github代码的部署工作. - https://tortoisegit.org/

安装并配置完成Nodejs和Git环境设置之后, 就可以开始Hexo博客之旅了.


##### 1. 先在Github中创建一个代码仓库，GitHub官方文档 - https://pages.github.com/

在此步骤中只需要注意仓库名称格式:

{% asset_img create-repo.png  create-repo %}


``` bash
"repository name".github.io.
```
把"repository name"替换成自己想要的名称即可.

##### 2. 使用Nodejs - NPM安装Hexo环境

``` bash
npm install -g hexo-cli
```
安装完成之后可以使用以下命令查看是否安装成功.

``` bash
hexo -v --> 查看hexo版本信息
```

##### 3. 使用Git或者TortoiseGit把代码仓库拉到本地，使用CMD进入本地仓库目录，初始化Hexo项目
P.S. 建议使用两个代码仓库，一个是源项目（Hexo编译），一个是正式博客的。因为Hexo在部署的时候会清空github仓库全量部署编译后的项目文件。

``` bash
cd "your local path"
hexo init --> 初始化Hexo项目
```
进行到这一步之后，Hexo(3.2.x版本)会自动生成所有组件，并下载好npm依赖.不需要再执行npm i.
此时已经生成了一个官方基础版本的博客了.可以使用以下命令进行本地预览:

``` bash
cd "your project path"
hexo clean && hexo generate && hexo server

INFO  Start processing
INFO  Hexo is running at http://localhost:4000/. Press Ctrl+C to stop.
```
Hexo会运行在http://localhost:4000/ 或 http://127.0.0.1:4000/, 在浏览器中输入此地址即可查看了.

##### 4. 简单配置Hexo,并部署博客到Github

暂时先使用官方默认主题，进行Hexo配置. 推荐使用[Atom](https://atom.io) 进行博客项目编辑.

如果不喜欢官方的默认的主题风格，可以去Hexo官方网站查找更多主题。找一个自己喜欢的!

* [Hexo主题](https://hexo.io/themes/)        - https://hexo.io/themes/

使用编辑器（Atom)，打开Hexo项目根目录中的_config.yml,此文件里面有很多配置，可以先不管，大多数都是比较简单的。
此时，我们只需要找滚动到文件底部找到deploy进行Hexo git部署配置.

其实，官方已经有很清楚的文档了, [Hexo官方文档](https://hexo.io/zh-cn/docs/)  - https://hexo.io/zh-cn/docs/

``` bash
# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git   --> 新版本中只能配置git
  repo: your repository url --> https模式的
  branch: master  --> your branch name.
  user: your github username
```

保存以上配置，Hexo 提供了快速方便的一键部署功能，让您只需一条命令就能将博客部署Github.

``` bash
cd "your local path"
hexo deploy
```
使用此命令是可能会出现以下错误信息.

``` bash
hexo deploy ERROR Deployer not found: git
```
此问题是因为没有安装hexo deployer git插件.使用以下命令进行安装，再次启动部署.

``` bash
npm install hexo-deployer-git --save
```
正常情况应该会成功部署博客到Github博客代码仓库.如果遇到其它问题，可以留言提问.

##### 5. 开启Github代码仓库的Github pages功能.

打开博客所在的Github代码仓库，进入设置，一般是最后一个选项 - Settings, 如下图所示:

{% asset_img repo-setting.png  repository setting %}

在Source的区域位置选择master作为博客的代码分支.目前Github只支持3种方式:

* master       --> Use the master branch for GitHub Pages
* master/doc   --> Use only the /docs folder for GitHub Pages.
* none         --> Disable Github page

设置完成Github pages功能，一般此页面会提示当前博客被部署到什么URL, 在访问之前，最好先检查一下代码是否完全部署到当前代码仓库.

Github pages默认提供的访问路径为:

``` bash
" https://yourusername.github.io/repositoryname.github.io/ "

Example: https://test.github.io/myblog.github.io/
```
到此，我们已经成功部署了官方默认版本的Hexo博客到Github了. 恭喜!

##### 6. 设置Custom domain(自定义域名).

使用Github提供的默认域名，不是特别很友好，我们可以在此配置一个自定义的域名。现在的版本只需要在此处设置即可。

1. 先申请一个自己的域名;
2. 在域名解析中设置一个2级子域名CNAME指向上面提到的域名https://yourusername.github.io 即可;一般很快可以访问了，主要基于DNS解析速度.

{% asset_img repo-cname.png  CDN Setting %}

##### 7. 添加百度CDN，为你的博客加速

国内访问Github pages速度还比较慢的，那这么个时候就需要一个CDN加速度，来帮助我们一下了.

1. 先申请一个百度账号，然后到百度云 - http://cloud.baidu.com 上去添加自己的博客网站，百度有一个免费版.
2. 添加自己的域名到百度云中，然后做一个CNAME映射到百度云的CDN服务器，然后百度云再映射到Github pages即可.


##### 8. 博客的性能优化

1. 静态文件压缩
   |- 图片进行无损压缩;
   |- html,css,js进行合并压缩;
2. 图片资源CDN加速
   |- 如果你是针对国内的话，可以使用七牛云 - http://qiniu.com 的空间存放图片.他们也有一个免费的计划，访问量不大的话可以使用;
3. SEO优化
   |- 主动提交你的博客到百度或者Google等各大搜索引擎，提高收录概率;

##### 9. 参考资料

1. Hexo官方文档 - https://hexo.io/docs/index.html
2. 博客主题     - https://github.com/ppoffice

{% asset_img new-hexo.png  Hexo %}
