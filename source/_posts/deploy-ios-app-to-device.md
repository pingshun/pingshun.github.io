---
title: Xcode7--免证书真机调试
date: 2017-09-22 18:46:37
tags: ios
---

Xcode7之前，想要真机调试，必须花99刀购买开发者账号，而且步骤繁琐，需要下载证书。随着Xcode7的推出，大幅度的简化了真机调试的步骤，对ios开发工作者和正在学习ios开发的众多码农们，可以说是个不小的福利。现在，我就详细的向大家介绍一下如何免证书真机调试。

<!--more-->

第一步：准备工作（Apple ID,iphone手机,Xcode7)

　　　　　　Apple ID  申请网址：https://appleid.apple.com/cn（Apple ID作为在苹果官网执行任何操作的通行证，申请步骤非常简单）;
　　　　　　iphone手机  这个就不用多说了，真机调试没有手机就白谈了;
　　　　　　Xcode7  可以从AppStore中下载;

第二步：打开Xcode 选择屏幕左上角Xcode-> PReferencese

第三部：选择Account 点击左下角的+按钮登陆Apple ID

第四步：登陆你的Apple ID

第五步:登陆成功之后，在右侧会显示小伙伴的账号在iOS和Mac上都是free的，双击这一列（或者点击选择view details）

第五步：这里需要一定时间获取你的Apple ID的开发者信息，点击iOS Development 后面的create ，然后稍等片刻，直到create按钮不见了。

第六步：到了这里基本上已经结束----开始真机测试：打开需要真机测试的项目插上手机（Xcode第一次链接手机会很慢，可以选择Xcode菜单栏中的window->devices查看手机是否准备就绪了），选择项目文件-> General - > Team -> 选择你属于你的Apple ID ，再点击Team 下面的fix issue修复Team 正下方的警告。

第七步：最后一个问题，你最终会发现Xcode会弹出一个框（process launch failed: Security），这里需要打开你手机的设置->通用- > 描述文件-> 选择你的Apple ID - > 点击信任 

　　　　至此，真机调试的过程就搞好了，是不是比以前简单多了？？？

转载于 [Xcode7--免证书真机调试](http://www.knowsky.com/884666.html)