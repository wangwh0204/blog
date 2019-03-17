title: hello github
date: 2015-11-04
updated: 2015-12-08
categories: 
- [others]
tags: 
- git
- github
- markdown
- hexo
---

这是我在github上的第一篇blog，本blog的内容即描述如何在github上完成本篇blog. <!--more-->所有内容基于如下知识和工具构建:
# git
[git](http://git-scm.com/)是一个分布式版本控制系统(VCS)，通过完整的阅读一遍[pro git](http://git-scm.com/book/zh/v2)这本书可以熟悉git及github的概念和用法.

# github
[github](https://github.com/)是一个基于git软件开发社区.阅读[got github](http://www.worldhello.net/gotgithub/index.html)进一步熟悉github

# markdown
[markdown](http://daringfireball.net/projects/markdown/syntax)是一个简单的基于文本的标记语言，我主要使用[markdown](http://wowubuntu.com/markdown/index.html)和[github flavored markdown](https://help.github.com/articles/github-flavored-markdown/)标记来写文章

# hexo
虽然github官方推荐使用jekell来做blog内容，但我对ruby没兴趣，正好最近在了解JavaScript，所以采用基于[node.js](https://nodejs.org/)的[hexo](https://hexo.io/)来维护blog内容。

# do it in Linux
## 安装git, nodejs, hexo
参考https://hexo.io/docs/
``` bash
$ sudo apt-get install git-core
$ curl https://raw.github.com/creationix/nvm/master/install.sh | sh
// restart terminal
$ nvm install 4
$ npm install -g hexo-cli
```
## 在github创建blog仓库
在github创建新仓库 wangwh0204.github.io，这个仓库就可以直接作为[个人blog站点](http://www.worldhello.net/gotgithub/03-project-hosting/050-homepage.html)的内容。通过 http://wangwh0204.github.io 即可访问，内容由hexo生成。

## 使用hexo
- 初始化hexo
``` bash
$ hexo init blog
$ cd blog
$ npm install
$ npm install hexo-deployer-git --save
```
- 配置_config.yml
``` yaml
title: 知行合一，敬天爱人
subtitle: just do IT. keep it simple & stupid.
description: steven's thinking
author: steven wang

url: http://wangwh0204.github.io

new_post_name: :year-:month-:day-:title.md

theme: jacman

deploy:
  type: git
  repo: git@github.com:wangwh0204/wangwh0204.github.io.git
  branch: master
```

- 选择 theme
参考 https://hexo.io/themes/ 和 http://www.zhihu.com/question/24422335 挑选适合自己口味的主题，我选的是[jacman](https://github.com/wuchong/jacman)，参考http://wuchong.me/jacman/2014/11/20/how-to-use-jacman/ 进行定制

``` bash
$ git clone https://github.com/wuchong/jacman.git themes/jacman
```
  修改_config.yml : theme: jacman , 并配置themes/jacman/_config.yml文件

- 旧文章
旧文章需要做如下改造：
    1. 用符合Markdown格式改写
    2. 文件名使用:year-:month-:day-:title.md方式命名
    3. 在文件头部加入称为[front-matter](https://hexo.io/docs/front-matter.html)的metadata信息，例如:
``` yaml
      title: hello github
      date: 2015-11-04
      updated: 2015-12-08 13:38
      categories:
      - [others]
      tags: 
      - git
      - github
      - markdown
      - hexo
      ---
```

- 新文章
``` bash
$ hexo new <title>
```
或者 直接copy 写好的md文件到source/_post目录

- 预览
``` bash
$ hexo server
```
打开浏览器输入 http://localhost:4000 查看效果，根据需要做相应的调整。

- 发布
``` bash
$ hexo generate --deploy
```
hexo会生成静态文件到public目录，并根据_config.yml的配置自动push到github。

## blog源文件管理
hexo会将md文件处理成可以静态访问的web页面，并自动推送到github。但通过hexo编写的.md文件本身并没有做版本管理，为了方便在不同的机器上操作，可以再建一个仓库来管理。
1. 在github新建仓库 blog
2. 本地操作
经过上面的步骤，blog的initial 版本已经就绪，现在直接在之前hexo init的目录进行操作
``` bash
$ git init
$ git remote add origin git@github.com:wangwh0204/blog.git
// 如果是在新机器上使用，需要使用 git clone git@github.com:wangwh0204/blog.git，否则每次都要输入密码
// 要确保.gitignore里面有node_modules/ public/ .deploy
$ git add .
$ git commit -m "initial commit"
$ git push -u origin master
// 既然已经完成此次commit,发布新的内容到blog site
// 部署的时候出现SSH相关问题参考 https://help.github.com/categories/ssh/
$ hexo g -d
```
## 开启评论
多说 不在运营，使用[Gitment](https://github.com/imsun/gitment)作为新的评论系统。Gitment的idea很有创意，复用了github的issue comment。配置参考：
https://leejoker.github.io/2017/10/11/%E6%8A%98%E8%85%BEhexo%E7%B3%BB%E5%88%97%E4%B9%8B%E5%9C%A8jacman%E9%87%8C%E9%9B%86%E6%88%90gitment%E8%AF%84%E8%AE%BA%E7%B3%BB%E7%BB%9F/#

