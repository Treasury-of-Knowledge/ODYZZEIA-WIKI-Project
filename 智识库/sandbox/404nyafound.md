---
title: 随行终端𝐄𝐑𝐀𝐋𝐈𝐍𝐊⟡ 安卓一键部署脚本
description: あなたのそばにへ
published: false
date: 2025-09-03T14:39:03.818Z
tags: 
editor: markdown
dateCreated: 2025-09-03T14:29:59.233Z
---

## 「[随行终端 ERALINK](https://discord.com/channels/1291925535324110879/1385183883540303872/1385183883540303872)」

> あなたのそばにへ

`ERALINK`，基于多端合一/极限便携的理念而诞生的**Termux**终端脚本。

它的诞生，源于一个纯粹的愿望：将 [`SillyTavern`](https://github.com/SillyTavern/SillyTavern), [`ClewdR`](https://discord.com/channels/1291925535324110879/1374353271484973066/1374353271484973066) , [`gcli2api`](https://github.com/su-kaka/gcli2api) 等强大工具的繁琐部署与管理流程，化繁为简，随身携带。通过一个可扩展的模块化框架，提供可靠的一键部署体验。

本项目基于rezline的一键部署脚本分支，项目的成长，离不开原作者 `rzline` 、gcli2api作者`su-kaka`等老师的指导，在此致以诚挚的感谢。

## ❖ 特性 (Features)

**✦ 模块化架构 (Modular Architecture)**  
不再是臃肿的单体脚本，每个核心功能（如 SillyTavern 管理）都是一个独立的、可插拔的模块。这使得添加新功能或进行维护变得前所未有的简单。  
**✦ 动态化菜单 (Dynamic Menu)**  
主菜单界面会根据您启用的模块动态生成，为您呈现一个清爽、个性化的操作面板。您可以随时在设置中“召唤”或“隐藏”特定模块，定制您的专属工作台。  
**✦ 统一化管理 (Unified Management)**  
从依赖安装、版本检查、服务启停，到网络代理、SSH配置乃至最终的软件卸载，所有操作都被收纳于一个统一、可视化的管理界面中，告别散乱的命令。  
**✦ 轻量化体验 (Lightweight Experience)**  
基于纯 Shell 构建，无需繁重的运行时环境。ERALINK 追求以最轻盈的姿态，为您提供最可靠的服务。

## ❖ 功能 (Features)

**模块安装与更新** 一键安装/更新 `ClewdR`, `SillyTavern`, `gcli2api` 等模块，以及 `ERALINK` 框架自身  
**服务状态监控** 在主菜单实时展示所有模块的运行状态 (`[运行中]` 或 `[已停止]`)，让您对系统状况一目了然  
**版本智能检查** 启动时异步检查各模块与框架的最新版本，并与本地版本对比展示。支持缓存机制与手动强制刷新  
**模块显示管理**：在设置中自由选择要在主菜单显示的模块  
**安全卸载**：提供完整的卸载管理器，可选择性移除任一模块、依赖、配置文件乃至 `ERALINK` 自身  
**调试模式**：为开发者提供详细的后台日志输出  
**SSH 管理**：安装、启停 `OpenSSH` 服务，并配置开机自启  
**网络代理**：支持全局代理的开启/关闭、自定义地址与重置  
**开机自启**：一键配置 `ERALINK` 脚本自身的开机自启动

### 示例图：

\[[l临时图床](https://discord.com/channels/1291925535324110879/1385183883540303872/1412131771222327368)\] 

### 最新版本：2.0.1 \[[更新日志](https://discord.com/channels/1291925535324110879/1385183883540303872/1412128265908256911)\]

# 如何安装随行终端
## 事前准备
① 准备好一部安卓手机（鸿蒙和苹果请参考其他教程）
② （大陆用户）打开手机的流量开关，不使用wifi
③ （大陆用户）获取一个可以访问外网的梯子安装到手机上并启动，保持梯子连接
④ 推荐使用Edge浏览器
## 安装termux
在安卓手机上下载[termux](https://github.com/termux/termux-app/releases) 并安装
## 设置termux权限
权限设置：允许【自启动】、【关联启动】、【后台弹出页面】、【储存权限】、【管理所有文件】
电量设置：允许**【后台高耗电】**
禁止【暂停闲置应用的活动】
ps：如果发现**酒馆无响应，后台也无报错**，且已经设置了以上权限，很可能是你的手机限制后台进程，请尝试挂小窗
## 部署一键启动脚本
通过以下方式直接安装
打开termux后粘贴下方指令，必要时挂梯子
[手机端复制指令](https://discord.com/channels/1291925535324110879/1385183883540303872/1412800109564924045)
方式一（无代理 | **推荐**）：
```apt update && apt install curl unzip git nodejs jq expect -y && pkg upgrade -y && curl -L -o install.sh.tmp -C - https://github.com/404nyaFound/eralink/releases/latest/download/install.sh && mv -f install.sh.tmp install.sh && chmod +x install.sh && ./install.sh || { echo "安装过程中出错"; rm -f install.sh.tmp; exit 1; }}```
方式二（代理）：
```apt update && apt install curl unzip git nodejs jq expect -y && pkg upgrade -y && curl -L -o install.sh.tmp -C - https://ghfast.top/https://github.com/404nyaFound/eralink/releases/latest/download/install.sh && mv -f install.sh.tmp install.sh && chmod +x install.sh && ./install.sh || { echo "安装过程中出错"; rm -f install.sh.tmp; exit 1; }```
安装过程中，**看情况输入y或回车**
如安装报错，请尝试升级[termux版本](https://github.com/termux/termux-app/releases) ，或[切换镜像源](https://discord.com/channels/1291925535324110879/1385183883540303872/1405756821985165362)
安装完成后，会显示gui
可在系统设置中开关脚本自启动
## 安装酒馆、clewdr或gcli2api
默认只会显示 **酒馆** 及系统设置，如要安装clewdr或gcli2api，前往 **系统设置-管理模块显示** 中显示对应模块
在主菜单中，输入数字，选择安装clewdr/gcli2api和酒馆
安装过程中，看情况输入y和回车
等待安装完成，出现按任意键返回主菜单提示，即可返回主菜单查看安装状态
## 使用酒馆、clewdr或gcli2api
在主菜单，输入数字启动
（按ESC右边的菜单可以打开侧边栏，NEW SESSION可以创建新进程，通常一个进程放置clewdr，一个进程放置酒馆）
酒馆启动后会自动调用浏览器打开，也可手动输入链接，通常是127.0.0.1:8000
## ♢快速跳转 ♢
[【ClewdR】](https://discord.com/channels/1291925535324110879/1374353271484973066/1374353271484973066) 
[【gcli2api】](https://discord.com/channels/1134557553011998840/1405524233823457300/1405524233823457300)
## ♢结语喵♢
如好用请务必留言点赞，超级想看你们评论喵