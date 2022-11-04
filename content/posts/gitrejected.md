---
title: "Gitrejected"
subtitle: ""
date: 2022-11-04T11:35:39+08:00
author: ""
authorLink: ""
authorEmail: ""
description: ""
keywords: ""
license: ""
comment: false
weight: 0

tags:
- draft
categories:
- draft

hiddenFromHomePage: false
hiddenFromSearch: false

summary: ""
resources:
- name: featured-image
  src: featured-image.jpg
- name: featured-image-preview
  src: featured-image-preview.jpg

toc:
  enable: true
math:
  enable: false
lightgallery: false
seo:
  images: []

repost:
  enable: true
  url: ""

# See details front matter: https://fixit.lruihao.cn/theme-documentation-content/#front-matter
---

<!--more-->
## 在将已有项目提交到线上远程仓库时，报错[rejected] master -> master (fetch first) error: failed to push some refs

本文将介绍如何将已有项目提交到线上远程仓库以及中间遇到的问题 ##

- 一、提交过程（会了的小伙伴直接跳到第二步）：

在github上创建了一个仓库，并复制了仓库http地址 在我已有项目目录下，初始化一个本地仓库，即终端输入git init 将我的项目和github（gitee也一样）上的仓库建立个联系，即终端输入git remote add origin 仓库http地址 然后将所有项目文件添加到缓存区，即终端输入git add . 将缓存区文件提交到本地仓库，即终端输入git commit -m “提交我的项目文件” 将本地仓库提交到已经相关联好的github线上仓库，即终端输入git push -u origin master ， 这时就会报错：

- 二、报错解决办法

报错的原因是因为，每个仓库都有一个分支，也可以理解为大仓库里的小仓库，我们只是跟线上远程仓库有了关联，但没有跟线上远程仓库的某个分支关联，所以我们没法提交

在终端输入 git pull --rebase origin master 即可跟刚创建的线上远程仓库的默认分支master关联 这时再执行一下 git push -u origin master 即可将我们的项目文件上传到关联的线上远程文件中

大功告成！
