---
title: 1Panel部署云酒馆教程
description: 
published: false
date: 2026-03-03T14:43:28.519Z
tags: 教程, 部署, 云酒馆
editor: markdown
dateCreated: 2026-03-03T13:56:39.160Z
---

# 1Panel部署云酒馆教程
> 教程作者：粉色妖精小姐～♪ 原贴[云酒馆部署教程1panel面板](https://discord.com/channels/1134557553011998840/1432990231694671893)


## 前期准备
1.准备一台服务器

2.ssh工具或者其他连接ssh的方式也可以

3.如果你是手机 那么可能需要找一下网页版的ssh工具当然也有手机版的工具 后续如果需求多可能会再出个教程



## 开始操作
首先我们需要从你购买服务器官网的后台得到ip地址 还有用户名 密码

比如我的就是
```
用户名:user
ip：192.168.233.128
密码: 123456
```
有些人的用户名可能是root 无伤大雅


接下来我就已我使用的ssh工具来进行演示 我使用的ssh工具为finalshell 如果跟我是一样的工具可以跟着做 不是一样的工具 操作也是类似的

点击这个文件夹
![select_folder.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/select_folder.png)

点开文件夹以后我们接着依次点击 创建ssh连接来连接我们的服务器
![click1.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/click1.png)

按照下面的图片依次填上你在购买服务器的官网后台获取的信息 如下：
![example1.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/example1.png)
填写完毕以后点击确定

随后我们再次点开文件夹的位置
![select_folder2.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/select_folder2.png)
找到我们刚才创建的那个连接比如我的是
![suibian.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/suibian.png)
双击即可启动

来到下面这个页面就已经成功连接上你的服务器了
![page1.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/page1.png)
如果出现错误说明前面信息不对 请自己核对


接下来 开始正式流程 如果你跟我一样 不是root 输入以下指令
```
sudo -i
```
如果你本来就是root 则不需要
![sudo_(1).png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/sudo_(1).png)
然后输入密码 
# 请注意 如果你在命令行输入密码 你是看不到密码的 这并不是bug 继续完整输入密码即可

回车以后你就会发现变成了root
![root_(1).png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/root_(1).png)

接下来输入下面这串命令回车安装1panel 
这是官方安装命令 如果你不能使用 请自行到官网去下载离线包安装 官网也有教程
```
bash -c "$(curl -sSL https://resource.fit2cloud.com/1panel/package/v2/quick_start.sh)"
```

下面根据需求选择 输入数字后回车
![1panel_install_1.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/1panel_install_1.png)
![1panel_install_2.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/1panel_install_2.png)
下面的操作 如果你的vps在国外 这里可以不用填y
![1panel_install_3.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/1panel_install_3.png)
需要注意的有些服务器 可能需要到购买服务器的的官网后台去开放端口 请询问客服

出现下面这个页面就是成功了
# 然后请复制好这些信息 以后访问需要
![1panel_install_4.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/1panel_install_4.png)

随后访问链接 比如我的是 http://192.168.233.128:35349/2e6133c3f2
我是虚拟机演示 所以你们访问的时候使用访问外部地址
到这个页面 就输入上面的面板用户 和面板密码 登陆即可
![login_(1).png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/login_(1).png)


登陆以后进入到以下页面 随后点击左侧导航栏的终端
![1panel_installation1.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/installation/1panel_installation1.png)

在终端输入以下命令后回车执行
![1panel_installation2.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/installation/1panel_installation2.png)


执行以后我们点击系统后选择文件
![1panel_installation3.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/installation/1panel_installation3.png)

点击这个位置来到主页面
![1panel_installation4.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/installation/1panel_installation4.png)

下面跟着依次进行点击即可
![1panel_installation5.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/installation/1panel_installation5.png)
![1panel_installation6.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/installation/1panel_installation6.png)
![1panel_installation7.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/installation/1panel_installation7.png)
![image_(1).png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/installation/image_(1).png)

打开这个文件以后按照需求看看是否需要修改
![1panel_installation9.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/installation/1panel_installation9.png)
改完以后记得保存

随后回到终端 新建一个终端
![1panel_installation10.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/installation/1panel_installation10.png)

输入以下命令后回车
![1panel_installation11.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/installation/1panel_installation11.png)
随后输入再继续输入
```
docker compose up -d
```
回车运行

出现以下提示说明安装成功了
![1panel_installation12.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/installation/1panel_installation12.png)

我们还需要在进行一些设置 再次回到文件
![1panel_installation13.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/installation/1panel_installation13.png)
依次进行选择打开文件
![1panel_installation14.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/installation/1panel_installation14.png)
![1panel_installation15.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/installation/1panel_installation15.png)

打开文件以后按照下面的操作进行修改
![1panel_installation16.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/installation/1panel_installation16.png)
![1panel_installation17.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/installation/1panel_installation17.png)
![1panel_installation18.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/installation/1panel_installation18.png)
# 注意 用户名和密码不要设置太过简单
设置完成后保存

保存关闭文件以后选择容器
![1panel_installation19.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/installation/1panel_installation19.png)

依次进行选择重启一下容器
![1panel_installation20.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/installation/1panel_installation20.png)
![1panel_installation21.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/installation/1panel_installation21.png)


重启以后在网页输入你的服务器ip:8000 即可访问酒馆
![1panel_installation23.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/installation/1panel_installation23.png)

如果需要看后台 点击容器的日志即可查看
![1panel_installation22.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/installation/1panel_installation22.png)

# 备份数据同步教程
按照操作 找到data文件夹
![1panel_installation24.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/installation/1panel_installation24.png)
![1panel_installation25.png](/all_upload_files_should_in_here/sandbox_area/elysia/1panel_sillytavern/installation/1panel_installation25.png)
在更多找到压缩 随后下载即可 反之 备份的data覆盖现在的data即可 
操作完备份或其他操作以后 跟上面一样 记得重启容器


进阶操作:
	让酒馆变得更安全可以给酒馆套域名 前提是有域名 详细可以看[1panel酒馆套域名教程](https://discord.com/channels/1134557553011998840/1432990231694671893/1447335715338977423)