---
title: comfyUI宝宝教程v0.1
description: 
published: false
date: 2026-03-07T15:34:45.519Z
tags: 教程, comfyui
editor: markdown
dateCreated: 2026-03-04T16:32:50.366Z
---

# ComfyUI宝宝教程（施工ing）
> 教程作者：rosemary.rosemary——175高冷御姐/高贵优雅威严的血族始祖

## 概述
  ComfyUI 是一个基于节点式工作流的开源图形用户界面，专门用于设计和执行 AI 图像生成模型（以 Stable Diffusion 系列为主）的创作流程。

  在 AI 绘画领域，大多数工具将复杂的技术参数隐藏在简单的按钮和滑块之后，而 ComfyUI 选择了一条不同的路径——它将 AI 生成过程的每一个环节都拆解为独立的“节点”，让用户像搭建流程图一样，从零开始构建自己的图像生成流水线。这种设计理念使其既像一个**可视化编程环境**，也像一个模块化的 AI 图像工厂。
  
**注意：本教程基于Windows10系统制作**

## 一、前置需求
### 1.硬件
显卡推荐：NVIDIA显卡（30系可跑，推荐40系及以上）（AMD显卡也可，但是性能浪费较为严重）
内存：16g及以上，32g及格
固态硬盘
### 2.运行环境
注：本教程使用的示范整合包自带运行环境，无需额外安装环境
#### Python
#### git
### 3.软件配置
#### 预留固态硬盘空间
#### 打开梯子的代理模式和虚拟网卡模式
> 若无另外说明，本教程所有文件均放在该硬盘中
{.is-warning}

至少需留有100g～150g左右的空间，**不要把任何文件随便放在C盘！！！**
#### 设置虚拟内存
（1）右击桌面上的“此电脑”，点击“属性”
（2）在设置界面找到“高级系统设置”
（3）在“高级”选项卡中“性能”栏选择“设置”
（4）在“高级”选项卡中更改虚拟内存
（5）**选中一个固态硬盘**，更改为“自定义大小”，按照你现有有的内存大小（单位：g）进行设置（注意：你最终填入的数字是以mb为单位）：
初始值：内存大小×1.5×1024 mb
最大值：内存大小×2×1024 mb

**这里以32g实体内存为示范**
![1.png](/all_upload_files_should_in_here/sandbox_area/rosemary/1.png)

（6）**点击“设置”，然后电击“确认”**
（7）弹出提示后重启电脑

### 4.生物资源
（1）一颗大脑
（2）一双眼睛
（3）一双手

## 二、整合包部署
> 本教程以b站up“**秋葉aaaki**”的**comfyUI整合包v2**作为示范
{.is-info}

### 1.整合包获取

（1）在哔哩哔哩搜索“**秋葉aaaki**”（请注意鉴别，假冒账号很多）
（2）打开秋葉个人主页动态，找到一个2026年1月19日发布的动态，使用动态中的链接打开夸克网盘
（3）下载“**comfyUI-aki-v2**”压缩包
> 不要下载v3版本！！！我们将更换默认的部分文件，使用v3可能会导致你最终因为缺少某些文件报错！最新的不一定是最好的！
{.is-warning}

（4）将压缩包解压至硬盘根目录，完成后打开该文件夹，双击打开“绘世启动器.exe”，等待更新完毕，进入启动器主界面。
![2.1.png](/all_upload_files_should_in_here/sandbox_area/rosemary/2.1.png)

## 三、工作流部署
> 本教程以“**Aaalice**”的**v12.2一键包**作为示范
{.is-info}

### 1.设置
（1）在启动器侧栏找到“设置”，关闭“网络设置”中的所有条目
![3.png](/all_upload_files_should_in_here/sandbox_area/rosemary/3.png)

（2）打开“高级选项”，关闭“激进提速策略
![4.png](/all_upload_files_should_in_here/sandbox_area/rosemary/4.png)”

（3）打开“版本管理”，选择“拓展”栏目，点击“刷新列表”，先将所有插件取消勾选，仅勾选以下插件
> 有部分插件名字相似！不要选错！！！
{.is-warning}

![5.png](/all_upload_files_should_in_here/sandbox_area/rosemary/5.png)

（4）删除未勾选的插件，点击“一键更新”
（5）选择“内核”栏目，点击“刷新列表”，在稳定版中切换至v0.8.0
（6）选择“安装新拓展”，在下方“拓展url”中填入：https://github.com/Aaalice233/ComfyUI-Aaalice-Pack-Unpack-Tool
（7）等待安装完成
（8）在等待时间下载该压缩包：[aaalice的工作流_一键包_v12.2_正式版.cpack.zip](/all_upload_files_should_in_here/sandbox_area/rosemary/aaalice的工作流_一键包_v12.2_正式版.cpack.zip)

### 2.配置
（1）安装完成后，在启动器首页（一键启动），点击“自定义节点”，选择“ComfyUI-Aaalice-Pack-Unpack-Tool”文件夹→“exe”文件夹→双击“comfy-pack-unpack.exe”
（2）git和python正常来说会自动检测地址，压缩包选择你刚刚下载好的那个，comfyUI手动选择”ComfyUI-aki-v2“内的”comfyUI“文件夹
**我的演示下载在d盘根目录，确保最后几个地址是对的就行**
![6.png](/all_upload_files_should_in_here/sandbox_area/rosemary/6.png)

（3）点击”开始解包“，等待复刻环境完成，**完成后仔细检查日志中是否出现红色报错**
> 若出现以下报错，再次点击”开始解包“，会自动检测缺失文件，直至无任何报错出现
{.is-danger}

![7.png](/all_upload_files_should_in_here/sandbox_area/rosemary/7.png)

（4）打开“版本管理”，选择“拓展”栏目，点击“刷新列表”，找到”comfyUI-Danbooru-Gallery“插件，点击更新该插件
> 其他插件能用就不动
{.is-warning}

（5）在启动器首页（一键启动），点击右下角”一键启动“，等待所有文件安装完成后自动在默认浏览器开启页面


## 四、使用（简易版）

### 1.工作流导入
（1）如图
![8.png](/all_upload_files_should_in_here/sandbox_area/rosemary/8.png)

（2）在comfyUI的目录中按下图找到图中所示json文件，打开
![9.png](/all_upload_files_should_in_here/sandbox_area/rosemary/9.png)

### 2.推荐设置
> 截图右下角一般会带有底图，白框框出的区域就是屏幕所在位置，地图可以直接点击跳转
{.is-info}

> **按住空格键在用鼠标拖动可以避免选中节点（非常好用）**
{.is-info}

（1）下载模型，图中为基础版必下
![10.png](/all_upload_files_should_in_here/sandbox_area/rosemary/10.png)

（2）关闭弹窗，底图直接送入放大（你也不想跑一张图就系统通知你一次吧）
![11.png](/all_upload_files_should_in_here/sandbox_area/rosemary/11.png)
![12.png](/all_upload_files_should_in_here/sandbox_area/rosemary/12.png)

（3）新手务必务必将”底图“和”放大“的checkpoint（底模）设置为同一个
（4）**批次大小设置为1，不要动！！！**，需要批量跑图更改右上角”运行“右侧数字即可
![13.png](/all_upload_files_should_in_here/sandbox_area/rosemary/13.png)

（5）固定提示词串默认只开”默认质量串“，其他的根据后续学习凭感觉使用
![14.png](/all_upload_files_should_in_here/sandbox_area/rosemary/14.png)

### 3.lora管理器
> 非常好用的管理器，非常推荐学习！！！之后所有的底模和Lora都通过这个下载！！！
{.is-info}

**教程位置如下**
红箭头为视频教程（推荐），**蓝箭头为Lora管理器按钮，点此进入，里面还有一个文字版教程**
![15.png](/all_upload_files_should_in_here/sandbox_area/rosemary/15.png)


## 五、其他常见问题自查