---
layout: post
title: "「博客」博客说明文档"
subtitle: "NO1 Blog"
author: "Yuzj"
header-img: "img/post-bg-halting.jpg"
header-mask: 0.3
catalog: true
tags:
- 博客搭建
---

### [我的博客在这里 &rarr;](https://yzjacc.github.io/)


### 关于收到"Page Build Warning"的email

同时,你需要更新你的本地jekyll环境.

使用`jekyll server`的同学需要这样：

1. `gem update jekyll` # 更新jekyll
2. `gem update github-pages` #更新依赖的包

使用`bundle exec jekyll server`的同学在更新jekyll后，需要输入`bundle update`来更新依赖的包.

参考文档：[using jekyll with pages](https://help.github.com/articles/using-jekyll-with-pages/) & [Upgrading from 2.x to 3.x](http://jekyllrb.com/docs/upgrading/2-to-3/)


## 关于模板(beta)

我的博客仓库——`huxpro.github.io`，是经常修改的，而且还会有人乱提交代码，因此给大家做了一个稳定版的模板。大家可以直接fork模板——`huxblog-boilerplate`,要改的地方我都说明了。或者可以直接下载zip到本地自己去修改。

```
$ git clone git@github.com:Huxpro/huxblog-boilerplate.git
```

**[在这里预览模板 &rarr;](http://huangxuan.me/huxblog-boilerplate/)**

## 各版本特性

##### New Feature (V1.5.2)

* 当你fork了我的仓库之后，还要删掉里面的关于我的文档是不是感到略烦躁呢？**Boilerplate** 模板将帮助你快速开始，方便合并与更新。
* `-apple-system`被添加到了字体规则里面了，这套字体格式能将iOS9默认的新字体**San Francisco**表现的非常漂亮。
* 解决了代码过长自动换行的bug,替换为横向滚动条。详情请见[issue#15](https://github.com/Huxpro/huxpro.github.io/issues/15)

###### 其他历史版本个人觉得没有必要了解，看看英文就行了。



## 支持

* 你可以自由的fork。如果你能将主题作者和 github 的地址保留在你的页面底部，我将非常感谢你。
* 如果你喜欢我的这个博客模板，请在`huxpro.github.io`这个repository点个赞——右上角**star**一下。

## 说明文档

* 开始
	* [环境要求](#environment)
	* [开始](#get-started)
	* [写一篇博文](#write-posts)
* 组件
	* [侧边栏](#sidebar)
	* [迷你关于我](#mini-about-me)
	* [推荐标签](#featured-tags)
	* [好友链接](#friends)
	* [HTML5 演示文档布局](#keynote-layout)
* 评论与 Google/Baidu Analytics
	* [评论](#comment)
	* [网站分析](#analytics) 
* 高级部分
	* [自定义](#customization)
	* [标题底图](#header-image)
	* [搜索展示标题-头文件](#seo-title)

#### Environment

如果你安装了jekyll，那你只需要在命令行输入`jekyll serve`就能在本地浏览器预览主题。你还可以输入`jekyll serve --watch`，这样可以边修改边自动运行修改后的文件。

经 [@BrucZhaoR](https://github.com/BruceZhaoR)的测试，好像两个命令都是可以的自动运行修改后的文件的，刷新后可以实时预览。官方文件是建议安装bundler，这样你在本地的效果就跟在github上面是一样的。详情请见这里：https://help.github.com/articles/using-jekyll-with-pages/#installing-jekyll


#### Get Started

你可以通用修改 `_config.yml`文件来轻松的开始搭建自己的博客:

```
# Site settings
title: Yuzj Blog             # 你的博客网站标题
SEOTitle: Yuzj Blog			# 在后面会详细谈到
description: "Cool Blog"    # 随便说点，描述一下

# SNS settings      
github_username: yzjacc     # 你的github账号
weibo_username: yuzijun      # 你的微博账号，底部链接会自动更新的。

# Build settings
# paginate: 10              # 一页你准备放几篇文章
```

Jekyll官方网站还有很多的参数可以调，比如设置文章的链接形式...网址在这里：[Jekyll - Official Site](http://jekyllrb.com/) 中文版的在这里：[Jekyll中文](http://jekyllcn.com/).

#### write-posts

要发表的文章一般以markdown的格式放在这里`_posts/`，你只要看看这篇模板里的文章你就立刻明白该如何设置。

yaml 头文件长这样:

```
---
layout:      post //布局
title:      "Hello 2019" //标题
subtitle:   "Hello World, Hello Blog" //描述
date:        2019-06-20 12:00:00 //日期
header-mask: 0.3 /透明度
catalog:     true //目录
multilingual:true //语种改变
mathjax:     ture //数学符号
iframe:      //HTML5布局
layout:      keynote//iframe布局
iframe:     "http://####/js-module-7day/"
header-img: "img/post-bg-2015.jpg" //标题图片
lang:        en/ch //语言
header-img-credit and header-img-credit-href
nav-style: invert and header-style: text
tags: //标签
    - Life
---

```

#### 

我的博客标题是 **“Yuzj Blog”** 但是我想要在搜索的时候显示 **“于子俊的博客 | Hux Blog”** ，这个就需要SEO Title来定义了。

其实这个SEO Title就是定义了<head><title>标题</title></head>这个里面的东西和多说分享的标题，你可以自行修改的。

## 致谢

1. 这个模板是从这里[IronSummitMedia/startbootstrap-clean-blog-jekyll](https://github.com/IronSummitMedia/startbootstrap-clean-blog-jekyll)  fork 的。 感谢这个作者
2. 感谢[@BrucZhaoR](https://github.com/BruceZhaoR)的中文翻译 

3. 感谢 Jekyll、Github Pages 和 Bootstrap和Hux!