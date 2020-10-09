---
layout: post
title:  "个人主页建立记录"
date:   2020-10-09 19:51:14 +0800
categories: jekyll update
---

程序员必备小技能之一，作为测试文章记录一下吧。



## 选定使用工具

首先决定使用Jekyll生成静态网页，然后使用Github Pages服务作免费托管。



## 选定参考文档

中文的教程总是说不出的不舒服，我看的是[这里](https://medium.com/20percentwork/creating-your-blog-for-free-using-jekyll-github-pages-dba37272730a)，另外我使用的是Arch Linux系统而非Mac Os，所以关于Ruby和Gem的安装需要另外参考[这里](https://wiki.archlinux.org/index.php/Jekyll#RubyGems_(recommended))。最重要的是Jekyll的[官方文档](https://jekyllrb.com/docs/)。



## 安装与验证

首先安装好Ruby和Gem。

```bash
#首先升级
gem update
#安装jekyll和一个等会儿要用到的附属软件包
gem install jekyll bundler
```



安装过程很顺利，然后我打算选择熟悉的markdown语言作为markup language。

查看gem安装时输出的log，添加gem的bin目录到PATH环境变量中。然后验证安装。

```bash
#在特定文件里修改PATH：PATH=$PATH:/home/ranger/.gem/ruby/2.7.0/bin
jekyll -v
```



## 初始化文件夹并查看静态网页

设置一下bundle的path，给Blog选一个好名字`37Percent`，初始化文件夹：

```bash
bundle config set path 'vendor/bundle'
jekyll new 37Percent
```



成功的话就可以到`http://127.0.0.1:4000/`查看静态网页了，最初始的网页大概长成这个样子：

![](./2020-10-09-Blog-Setup-Log.assets/ScreenShot1.png)



## 把静态页面托管到Github Pages上

基本上跟着[这里](https://medium.com/20percentwork/creating-your-blog-for-free-using-jekyll-github-pages-dba37272730a)一步步执行命令就行，git的操作想必各位程序员都很熟悉，就不赘述了。

```bash
git init
git checkout -b gh-pages
git status
git add .
git commit -m "initial commit"
git remote add origin <git repo link>
git push origin gh-pages
```

## 想要发布新的博文？

修改`_posts`文件夹下的markdown文件即可。**加上选项能够动态预览更新效果哦：**

```bash
bundle exec jekyll serve --livereload
```

完成后`git add -p`确认添加的内容，然后`git commit -m "<Commit msg>"`提交，并`git push origin gh-pages`推送到Github上。
That's it!

## 发布静态页面

主要遵循Github Pages的[官方指南](https://docs.github.com/en/free-pro-team@latest/github/working-with-github-pages)。

## 美中不足

1. 网页的左右侧没有导航栏或目录一类的东西，感觉不太方便。可能在其他主题里可以设置。
2. Markdown中的图片没有正确显示，后续再改进。

## 其他资源和后续改进

1. Arch Wiki上提到了两个Repo：[这里](https://github.com/danielmcgraw/Jekyll-Base)和[这里](https://github.com/danielmcgraw/danielmcgraw.com)。
2. Jekyll的[官方文档](https://jekyllrb.com/docs/)中也有关于主题的[页面](https://jekyllrb.com/docs/themes/)。

---



*其实在尝试发布静态页面时就发现了一个问题：总是不能访问除了主页之外的页面？*

## 过程并不顺利！（正文开始）

没想到最后还是跟同学交流了一下得到了好看又兼容的博客template的minimal working example。然后三下五除二搭好了。

千万不要参考Github Pages的[官方文档](https://docs.github.com/cn/free-pro-team@latest/github/working-with-github-pages/setting-up-a-github-pages-site-with-jekyll)，因为就算你看的是英文文档，也是错误的（根据StackOverflow上的小伙伴反馈）。

随手记录一下，文档里写提示，为了保证本地和Github Pages渲染一致，需要规律性的更新：

```bash
bundle update github-pages
```

另外在安装`bundle`相关的组件时，提示Ruby Saas已经过了生命周期（Google了一下，甚至发现是在2019年3月过期的）。果然如魔法少女zzh所说，这个博客框架生态不怎么好？

恩，习惯了Arch Linux完善的Wiki，感觉开源社区如果生态不好，还是相当难受的。


