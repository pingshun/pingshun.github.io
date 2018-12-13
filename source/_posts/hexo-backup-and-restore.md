---
title: hexo博客的备份与恢复
date: 2018-08-23 14:51:28
tags: [hexo]
---
使用hexo搭建好博客以后，一般都会发布到比如github之类的公网上，本地保留一份源文件。但是天有不测风云，难免会遇到源文件丢失、损坏等情况，所以hexo提供了一个将源文件也备份到git上的方法。
刚好最近换了一台电脑使用了一次从github上恢复的功能，中间路子不熟，遇到了一点麻烦，所以把这个过程记录下来，以备不时之需。
<!--more-->
### 备份
备份很简单，这里以github备份为例(别的也没用过。。。)：只需要在工程目录下的_config.yml文件中，寻找deploy段。如果你使用过hexo deploy将博客deploy到github上的功能的话，应该已经存在了一个配置类似于
>\- type： git

>  repository: https://github.xxxx

>  branch: master

找到这段之后，在后面追加一个配置：

>\- type: git

>  repository: https://github.com/xxxx [跟上面一样]

>  branch: src

>  extend_dirs: /

>  ignore_hidden: false

>  ignore_pattern:

>    public: .

>    node_modules: .

加上这段配置之后，再做git deploy的时候，会同时把源文件push到src这个branch里面，以后就不怕丢失了

### 恢复
如果你换了电脑，或者到了需要恢复的时候，千万先不要做hexo d以免github上的源文件被覆盖！！！你需要做的是以下几步:
1. 把源文件的branch也就是上面的src branch拷贝到本地
git clone -b src https://github.com/xxxx/xxxx.git
2. 安装必要的node模块
进入目录，执行 npm install

完成这一步，按理说你应该已经恢复整个工程了

### 问题
按说完成上面那套动作之后，应该所有东西都OK了，直接

> hexo g

> hexo d


就可以继续愉快的发博客了，然鹅...

现实总是如此残酷，我完成这些之后，使用hexo s在本地看一下，神马东西都没有。。。。

经过一顿折腾，终于找到问题：

hexo d备份的时候，并没有将我用的theme目录push到github上，所以导致hexo generate的时候报错


解决办法：

将用到的主题(我的是next)手动下载到themes目录下面

### 进一步的问题
通过上面的解决，博客功能基本上全恢复了。但是，因为主题备有备份，所以主题相关的配置就丢失了，需要自己重新做主题的配置，也就是修改themes/next/_config.yml

解决办法：

我没有研究为什么themes/next没有被上传到github上，我猜大概是因为，我的next也是从github上下载的，是一个单独的git目录。我想一定有办法可以解决，将next也跟你的源文件一起备份，但我实在没时间找资料了。

我的解决办法是在themes目录下新建一个目录，比如config_backup，然后将next/_config.yml文件以及别的修改过的配置文件拷贝到这个config_backup下面。

这样再做hexo d的时候，这些配置文件就被备份了，以后直接拷贝回去就能恢复了