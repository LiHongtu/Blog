---
layout: post
title:  "Jekyll在Github上搭建个人博客"
date:   2015-02-16 13:52:59 +0800
categories: jekyll update
---

通过搭建Jekyll+Github Pages为记录思想、整理笔记和分享知识，并将其中承载的价值传播给他人。

Jekyll 是一个简单的博客形态的静态站点生产机器。它有一个模版目录，其中包含原始文本格式的文档，通过一个转换器（如 Markdown）和我们的 Liquid 渲染器转化成一个完整的可发布的静态网站，你可以发布在任何你喜爱的服务器上。Jekyll 也可以运行在 GitHub Page 上，也就是说，你可以使用 GitHub 的服务来搭建你的项目页面、博客或者网站，而且是完全免费的。

Github Pages 是面向用户、组织和项目开放的公共静态页面搭建托管服 务，站点可以被免费托管在 Github 上，你可以选择使用 Github Pages 默 认提供的域名 github.io 或者自定义域名来发布站点。Github Pages 支持 自动利用 Jekyll 生成站点，也同样支持纯 HTML 文档，将你的 Jekyll 站 点托管在 Github Pages 上是一个不错的选择。

> * 本地搭建Jekyll
> * 创建博客站点
> * 使用Github pages服务生成个人博客

------

##  本地搭建Jekyll

本次安装可以Windows下进行。

### 1. Jekyll介绍
Jekyll是一个静态站点生成器，它会根据网页源码生成静态文件。它提供了模板、变量、插件等功能，可以用来生成整个网站。

Jekyll生成的站点，可以直接发布到github上面，这样我们就有了一个免费的，无限流量的，有人维护的属于我们的自己的web网站。Jekyll是基于Ruby的程序，可以通过gem来下载安装。

Jekyll官方文档：http://jekyllrb.com/

### 2. 安装Ruby

下载Ruby : http://rubyinstaller.org/downloads/

安装Ruby，再安装RubyGems

```python
ruby --version
```


```python
gem update --system
```

### 3. 使用gem安装Jekyll

（1）使用命令，安装jekyll及所有需要的依赖，但不包括插件。

```python
gem install jekyll
```

安装jekyll的时候需要注意一下安装版本问题。


（2）查看Jekyll是否安装成功
```python
jekyll -v
```

#### 问题1：下载认证文件
```python
curl http://curl.haxx.se/ca/cacert.pem -o cacert.pem
```
设置环境变量，重新安装

## 博客编写、测试

### 1. 创建博客

切换到博客文件夹下，创建博客：
```python
jekyll new blog  #创建你的站点
```
这样就会创建一文件夹../blog，其结构如下：
1. 文件夹_layouts：用于存放模板的文件夹，里面有两个模板，default.html和post.html
2. 文件夹_posts：用于存放博客文章的文件夹，里面有一篇markdown格式的文章--2016-01-27-welcome-to-jekyll.markdown
3. 文件夹css：存放博客所用css的文件夹
4. _coinfig.yml：jekyll的配置文件，里面可以定义相当多的配置参数，具体配置参数可以参照其官网
5. index.html：项目的首页

### 2. Jekyll基础目录结构

    |-- _config.yml
    |-- index.html
    |-- _includes
    |-- _layouts
    |   |-- default.html
    |   `-- post.html
    |-- css
    |-- js
    |-- _posts
    |   `-- 2015-04-27-Like-Kissing.md
    |-- images
    |   `-- Leah.png 
    |-- CNAME
    |-- _404.html
    |-- About.md
    |—— feed.xml
    `-- README.md

目录文档详细说明。如下：
    
>     _includes 博客调用的网页模块（比如导航栏、底栏、博文内容显示、评论模块等），一般不需要管；
>     
>     _config.yml 博客配置文档（包括博客标题、favicon、博主 ID、头像、描述、联系方式等基本信息都在这个文档添加或修改）；
> 
>     index.html 博客架构文档；
>     
>     _layouts 存放博客调用的页面模板文件（比如博客主页、具体博文页）的文件夹
>
>      css 存放博客系统的页面渲染文档文件夹，主要用于调节诸如标题字体、博文字体大小颜色之类； js 存放博客调用的 JS 文档文件夹
>     
>     _posts 博客正文存放的文件夹。命名有规定，必须为「日期 + 标题」的模式，即「2015-04-27-Like-Kissing.md」，才能发布到博客里； 
>     
>     images 图片文件夹，存放博客相关素材，包括博客 favicon、博主头像等图片及博文贴图素材； CNAME 用于绑定个人域名的文档；
>     
>     404.html 「404 Not Found.」站点链接无法访问时的提示页面。 About.html 博客中的个人说明文档（About Me），以 html、md 格式为主； feed.xml 博客的 RSS 订阅； README.md 项目说明文档。用于 Github 个人项目主页的说明（描述）。

除此之外，还有诸如 fonts 文件夹，存放博客用的字体文件，或有主题是将 css/js/fonts/images 等文件夹合并到 _assets 为名的主文件夹中。404.html/feed.xml/CNAME 文件并非必须，但一般架构完整的博客都有。

### 3. 开启Jekyll服务
本地服务开启后，Jekyll服务默认端口是4000，所以我打开浏览器，输入：http://localhost:4000 即可查看效果

```python
cd blog    	 #进入blog目录,记得一定要进入创建的目录，否则服务无法开启
jekyll serve 	 #启动你的http服务 
```
### 4. 调试

在博客文件夹下中

```python
jekyll build --trace
```
将所有文章文件根据其模板进行编译，生成结果，放在根目录下的_site中


---

## 使用Github pages服务生成个人博客


### 1. 创建我们的仓库

repository name设置为username.github.com，选择Public仓库类型！

### 2. 为仓库创建Github Pages

创建仓库后，选择setting
点击Launch automatic page generator，然后编辑下标题和描述，任意选择一个模板，点击Publish。

如此，可以通过浏览器输入 http://username.github.io访问博客主页。

### 3. 将本地jekyll代码部署到Github上的仓库

前面已说明如何搭建Jekyll，我们可以在本地开发测试，推送代码到仓库，发布到线上

### 4. 克隆仓库到本地

请确保本地安装了git客户端，克隆username.github.com仓库到本地。
```python
git clone https://github.com/username/username.github.com.git
```
此你会看见当前存在username.github.com这个目录，启动jekyll服务
```python
cd username.github.com
jekyll serve -B
```
打开http://localhost:4000,即可看见本地创建主页效果，理论上和http://username.github.com 访问的应该是一模一样的。

### 5. 拷贝本地的jekyll目录到版本库

删除username.github.com下面的示例文件:
```python
rm -rf _site index.html params.json  stylesheets
```
拷贝本地blog下的所有目录及文件到username.github.com
```python
cp -r blog/* username.github.com
```
重启服务，看见本地jekyll的站点效果

### 6. 发布
```python
git add --all			   #添加到暂存区	
git commit -m "提交jekyll默认页面" #提交到本地仓库
git push origin master    	   #线上的站点是部署在master下面的
```
稍等10分钟左右，Github Pages有一定时间缓存,我们刷新username.github.io看看,已经ok了！


## 参考链接：

1. [jekyllcn](http://jekyllcn.com/)

2. [http://lingyu.wang/](https://segmentfault.com/u/lingyucoder/articles?page=1&sort=vote)
