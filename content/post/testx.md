---
title: "开始使用hugo写博客"
date: 2022-11-28T11:18:03+08:00
---

之前用过Hexo来生成静态博客，但是感觉写的东西比较浅显，没能坚持写下来。并且因为重装系统后，重新checkout的hexo博客因为node module过时的问题，无法正常运行，感觉nodejs的库还是不太稳定，于是放弃Hexo,转投go语言开发的hugo。


## 1 安装
windows下直接到github下载即可：hugo download.
下载后，解压hugo.exe到自定义的文件夹，将该文件夹路径添加到系统path就可以使用hugo命令了。
运行下面命令试试hugo是否完全安装好了。

    hugo version

## 初始化 & 配置
在任意目录cmd里运行下面命令即可创建一个名字为hugoBlog的博客文件夹

    hugo new site hugoBlog  

运行成功后，可以看见生成的hugoBlog目录里面有很多自动生成的文件夹。
我们通过git来管理博客文件内容，git初始化如下。

    cd hugoBlog
	git init

在首次运行之前，我们还需要为hugo添加主题模板，因为默认是没有内置主题的。
我们到themes.gohugo.io去找喜欢的主题，然后在hugoBlog目录通过git将主题下载到themes目录。 以maupassant-hugo这个主题为例：
    
    cd themes
    git clone https://github.com/rujews/maupassant-hugo.git
执行完成后，在themes目录可以看到下载的maupassant-hugo主题。

然后我们还需要按照maupassant-hugo主题的说明，编辑hugoBlog目录下的config.toml配置文件，个人的配置如下：

	baseURL = "http://stormwy.github.io"
	languageCode = "zh-CN"
	title = "Stormwy's Blog"
	hasCJKLanguage = true
	theme = "maupassant-hugo"
	enableRobotsTXT = true
	PaginatePath = "page"
	
	[author]
	    name = "stormwy"
	    homepage = "https://github.com/stormwy"
	
	[params]
	    subtitle = "当你坚持不懈、挥汗如雨的时候，造物主未必都能够明鉴；但当你放浪形骸、自甘堕落的时候，全世界必会将你抛弃。"
	    description = "就是一个普普通通的博客."
	    keywords = "博客"
	
	    customCSS = ["custom.css"]
	    #customJS = ["app.extra.js"]
	
	    search_provider = "google"
	
	[params.utteranc]
	    enable = true
	    repo = "stormwy/blog-comments"
	    issueTerm = "pathname"
	    theme = "github-light"
	
	[[params.links]]
	
	
	
	[[menu.main]]
	    identifier = "archives"
	    name = "归档"
	    url = "/archives/"
	    weight = 2
	
	[[menu.main]]
	    identifier = "about"
	    name = "关于"
	    url = "/about/"
	    weight = 3
现在可以运行看看效果了，运行下面命令，访问`[localhost:1313`](localhost:1313`)

    hugo server -D
写文章
通过下面命令新建文章，然后手动打开编辑该文件即可，每次保存文章，浏览器会自动重新渲染。

    hugo new post/MyFirstHugoBlog.md
发布博客
记得将需要发布的文章的内容里draft: false标识的值改为true，然后运行下面命令

    hugo
会生成静态文件到public目录，最后将这些静态博客文件推送到github page或者自己的静态文件服务器上即可。