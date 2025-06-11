---
title: 软路由istoreos部署docker版sillytavern
description: 
published: true
date: 2025-03-31T10:55:28.659Z
tags: 教程, 酒馆, docker, 软路由
editor: markdown
dateCreated: 2025-03-31T10:55:27.520Z
---

# 前言
软路由最好用2C4G以上的配置（根据佬@ジョセフジョペロ的建议增加）


教程的重点是：**docker compose**和**config.yaml**


# 创建文件夹并上传文件
选一个位置创建文件夹sillytavern
下载`https://github.com/SillyTavern/SillyTavern/blob/release/docker/docker-compose.yml`至文件夹
~~上传帖子中的附件docker-compose.yml~~过时

# 执行docker compose并停止docker
点击顶栏的终端
输入命令 `docker compose up`
等待容器生成成功
进入容器界面，停止sillytavern容器

# 配置远程连接
重回sillytavern所在文件
进入config
打开config.yaml（一般用vim，或者导出到PC编辑后上传）

参考远程连接相关设置
## whitelist加上你的局域网地址
比如192.168.1.*
（也可以把whitelistMode改成false，毕竟局域网环境）

## listen改成true

# 启动容器
回到容器界面启动sillytavern
IP是你的软路由IP:8000