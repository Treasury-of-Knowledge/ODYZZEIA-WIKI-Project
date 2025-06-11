---
title: zeabur超简单vps部署酒馆教程
description: 80岁老奶奶用脚都能部署
published: true
date: 2025-03-30T03:24:01.924Z
tags: 
editor: markdown
dateCreated: 2025-03-30T03:17:53.087Z
---

# zeabur超简单vps部署酒馆教程
> 作者：方素琪 (discord@allenade_35238)
感谢momo（discord@joyful_parrot_64174）提供的vps测试本教程

相信很多人拥有vps的部署需求，尤其是当使用ios，无法在手机上使用酒馆的时候，今天给大家带来用zeabur的部署的使用教程，不需要敲命令行，动动你~~发财的~~小手点一点，就可以轻松愉快的随时在任何终端上访问你的酒馆啦~

> **我需要什么？**
> 1.一个vps（密码与密钥登陆皆可。如果你有钱可以去zeabur官网购买，只部署是免费的）💻
> 2.一个浏览器，让你可以打开zeabur官网🌏
> 3.一个人（你自己）<img class=emoji src=https://www.emojiall.com/images/60/blobmoji/emoji_u1f60e.png >
{.is-success}

> 请先确保你自备的vps需要开启如下端口（zeabur官网提示）
> **80、443、4222、6443、30000-32767**
{.is-warning}


> **我不需要什么？**
> 1.一块香喷喷的水果蛋糕（我知道它真的很好吃！）🍰
{.is-danger}

## 1.注册官网
zeabur其实就是一个部署平台，用来帮助快速把项目部署到服务器上的。
天啊这简直就是我们需要的不是吗？它甚至支持简体中文！
当然了，没什么好说的，不去[官网](https://zeabur.com/zh-CN)注册肯定没法用他家的服务。
![zeabur01.png](/all_upload_files_should_in_here/sandbox_area/fangsuqi/zeabur/zeabur01.png)
你可以通过邮箱或者github授权来注册。
> 上面的链接是官网链接，如果你**愿意支持作者**且**有在其上购买vps的需求**，可以使用[这个邀请链接](https://zeabur.com/referral?referralCode=fangsuqi)来注册，从而在购买时使双方获得邀请奖励。（如果没有购买意愿则不用）
{.is-info}

## 2.添加vps
在我的服务器页面，添加你的vps/购买vps。
![zeabur02.png](/all_upload_files_should_in_here/sandbox_area/fangsuqi/zeabur/zeabur02.png)
之后按引导即可，全是中文应该没有什么操作问题。

## 3.部署项目
添加完vps后，返回控制台（或者叫项目页面），点击创建项目,选中你刚刚部署好的vps。
如果一切就绪它应该是这样：
![zeabur03.png](/all_upload_files_should_in_here/sandbox_area/fangsuqi/zeabur/zeabur03.png)
随后点击项目左下角的加号出现如下弹窗：
![zeabur04.png](/all_upload_files_should_in_here/sandbox_area/fangsuqi/zeabur/zeabur04.png)
在这里我们**选择模板**，同时搜索SillyTavern
![zeabur05.png](/all_upload_files_should_in_here/sandbox_area/fangsuqi/zeabur/zeabur05.png)
选择下面那个官方源，点击Deploy（部署）。

## 4.后续配置
当部署完后，会显示如下：
![zeabur06.png](/all_upload_files_should_in_here/sandbox_area/fangsuqi/zeabur/zeabur06.png)
此时在网络页面，自定义一个域名以暴露在公网（或者绑定你自己的域名）随后等待完成（大概需要几分钟）：
![zeabur07.png](/all_upload_files_should_in_here/sandbox_area/fangsuqi/zeabur/zeabur07.png)
在设置-配置里，这里可以打开酒馆的配置文件，我们需要修改默认的用户名和密码
![zeabur08.png](/all_upload_files_should_in_here/sandbox_area/fangsuqi/zeabur/zeabur08.png)
![zeabur09.png](/all_upload_files_should_in_here/sandbox_area/fangsuqi/zeabur/zeabur09.png)
修改红框里的内容，username后面是用户名，password后面是密码。
最后，在浏览器的地址栏输入你的域名，部署完成。
![zeabur10.png](/all_upload_files_should_in_here/sandbox_area/fangsuqi/zeabur/zeabur10.png)
![zeabur11.png](/all_upload_files_should_in_here/sandbox_area/fangsuqi/zeabur/zeabur11.png)