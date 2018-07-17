---
title: 使用hexo写一篇博客
date: 2017-09-05 18:49:20
tags: [hexo, 技术]
---

我发现我已经健忘到了无可救药的地步了...
前几天刚弄好的博客，今天想记点东西，居然忘了如何写一篇新的文章了...  崩溃ing

先把如何使用hexo添加博文记录下来，以后有时间再慢慢整理吧:

<!--more-->

### 添加博文
1. hexo new ‘blog_title’
2. 位置: ‘source/_posts/blog_title.md’，编辑内容
3. hexo g; \#生成静态文件
   hexo d; \#部署

### 添加页面
1. hexo new page “<page_name>”
2. 位置: ‘source/<page_name>/index.md’, 编辑内容
3. 修改’themes/<theme_name>/_config.yml’里的‘menu’项，添加一项 ‘<menu_name>: /<page_name>’
4. 我用的是Next主题，可以在’themes/<theme_name>/_config.yml’的menu icon项里指定图标，然后在相应的语言文件‘themes/<theme_name>/languages/<language_file>.yml’里设置菜单项的当前语言名称
5. hexo g; \#生成静态文件
   hexo d; \#部署