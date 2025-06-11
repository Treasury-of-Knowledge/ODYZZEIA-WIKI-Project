---
title: SillyTavern 入门指北
description: 从部署酒馆到发送第一条消息
published: true
date: 2025-03-27T09:47:41.067Z
tags: 教程, 酒馆, clewd, 酒馆使用
editor: markdown
dateCreated: 2025-03-27T09:10:11.945Z
---

# SillyTavern 入门指北
> 教程作者: 42chen

本指北主要目的就是能从零开始, 用酒馆玩上 claude, 更细节的人物卡, 世界书, 预设什么的就不详细写了.

## Quick Start
前置条件:
- 梯子: 链接 github 和 npm
- 会用终端
- windows 系统(其他系统也可以用, 就是前面几步稍微有点不一样) 
- 安装了 node.js 和 git (不会装问问 gpt 怎么装)

### 1. 安装 [SillyTavern](https://github.com/SillyTavern/SillyTavern) (需要梯子链接 github)
打开文件资源管理器, 然后导航到要安装启动器的文件夹. 进入所需文件夹后, 在地址栏中键入 cmd, 然后按 enter 键.
![image](/all_upload_files_should_in_here/sandbox_area/42chen/1.webp)
弹出窗口, 运行以下命令 clone 项目
```bash
git clone https://github.com/SillyTavern/SillyTavern-Launcher.git
```
![image](/all_upload_files_should_in_here/sandbox_area/42chen/2.webp)
进入 SillyTavern-Launcher 双击 installer.bat
在弹出的窗口中输入 1 安装 SillyTavern 本体.
然后输入 y 创建桌面快捷方式, 再次输入 y 启动 SillyTavern-Launcher, 最后直接回车启动 SillyTavern 本体.

### 2. 获取 claude api (这里各位就各显神通了)


### 3. [可选]安装 [Clewd 修改版](https://rentry.org/teralomaniac_clewd) (需要梯子链接 github)
Clewd 所有功能仅针对 claude, 使用其他 ai 模型请跳过此步. 

如果 claude api 用的不是 `https://www.anthropic.com/api`, 我个人建议还是套一个 clewd. 最有用的功能有两个:
1. role 合并, 将连续的 H 或 A 合并为一个. (这个功能现在酒馆也支持了)
2. 融合信息模式 (Fusion Mode), 将信息融合到单一 user role 中, 用于少数提示词预处理存在问题的反代或中转. (但我个人用下来中转什么的基本都存在提示词预处理问题)

同理, 进入所需文件夹后, 在地址栏中键入 cmd, 然后按 enter 键, 再输入以下代码 clone 项目
```bash
git clone --depth 1 https://github.com/teralomaniac/clewd.git
```
双击 start.bat 运行. 第一次运行生成默认 config.js
然后打开 config.js, 在 `"api_rProxy"` 填入 api 地址, 在最后增加 `"3rdKey": "111"`, `111` 是 api 的 key, 如果 api 是接受 claude 格式就用 `3rdKey`, 如果是接受 openai 格式就用 `oaiKey`
![image](/all_upload_files_should_in_here/sandbox_area/42chen/3.webp)
最后再次双击 start.bat 启动测试一下.
![image](/all_upload_files_should_in_here/sandbox_area/42chen/4.webp)

### 4. 获取破限预设
这里选择 [Lily 1.0.3](https://rentry.org/lily_preset_for_sillytavern) 预设, 更多预设在 类脑 Discord 获取.  
以及破限配套的正则 [Lily 正则](/all_upload_files_should_in_here/sandbox_area/42chen/lily_regex.zip)

### 5. 获取角色卡
更多角色卡获取途径在后文介绍, 这里我写的 [绫地宁宁](https://discord.com/channels/1134557553011998840/1235307456268341281/1276392292848111616) 为例, 介绍如何下载 Discord 中的角色卡. 

在加入 [类脑 Discord](https://discord.gg/HWNkueX34q) 或者 [旅程 Discord](https://discord.gg/elysianhorizon) 后, 答题成功进入缓冲区, 虽然只能在特定频道发言, 但是已经能下载 Discord 中所有的资源.  

点击 [绫地宁宁](https://discord.com/channels/1134557553011998840/1235307456268341281/1276392292848111616) 跳转到对应楼层, 点击楼层的图片, 在右上角点击在`浏览器中打开`
![image](/all_upload_files_should_in_here/sandbox_area/42chen/113.webp)
在打开的标签页右键图片, 点击`图片存储为`将图片下载到本地. 在后文的步骤中就可以从本地导入这张角色卡.
![image](/all_upload_files_should_in_here/sandbox_area/42chen/14.webp)

### 6. 运行
启动 SillyTavern, 点击第一个按钮, 导入预设
![image](/all_upload_files_should_in_here/sandbox_area/42chen/5.webp)
导入完选择导入的预设
![image](/all_upload_files_should_in_here/sandbox_area/42chen/6.webp)
[仅使用 clewd 时需要]修改一下预设, 往下划一点, 在 `⚙️Custom Main` 中添加下面这两行.
```
<|messagesAPI|>
<|Fusion Mode|>
```
![image](/all_upload_files_should_in_here/sandbox_area/42chen/7.webp)
修改完划到最上面保存一下. 
![image](/all_upload_files_should_in_here/sandbox_area/42chen/8.webp)
导入预设配套的正则, 顺序无所谓.
![image](/all_upload_files_should_in_here/sandbox_area/42chen/19.webp)
导入角色卡, 点击角色卡后再次点击角色卡的头像可以更换角色封面.
![image](/all_upload_files_should_in_here/sandbox_area/42chen/110.webp)
给自己一个人设吧, 依照示例随便写一点就行. 那个图片按钮可以替换头像. 在右侧 `abab` 那个位置写上自己的名字.
![image](/all_upload_files_should_in_here/sandbox_area/42chen/111.webp)

[如果配置了 clewd]进入 clewd 文件, 点击 start.bat 启动 clewd

回到酒馆, 点击第二个按钮, 根据图片, 选择 Chat Completion, 确认聊天补全来源, 确认 Base URL, 填写密钥, 格式为 `3rdKey: 111` (和上文设置的一致), 然后点击连接, 然后选择 opus 模型, 或者 sonnet 3.7 也行.
![image](/all_upload_files_should_in_here/sandbox_area/42chen/112.webp)

现在, 选择角色卡, 输入消息, 点击发送, 如果万无一失, 就可以收到回复了.


## 破限推荐
破限才是能玩 r18 的原因, 道歉基本都是因为破限不行, 或者消息格式不对, 导致破限失效. 本人最推荐下面这些(其他在 [类脑 Discord](https://discord.gg/HWNkueX34q) 里面获取):
- Lily v1.0.3
  - 优点: 
    - 合乎 claude 规则的破限, 没有明显的规则误用.
    - 简洁
  - 缺点:
    - 额外功能不多, 比如文笔设定, 人称设定, 支持系统卡之类的.
    - 很久没更新了, 落后于时代, 破限力度存疑
- Lyean Preset
  - 优点:
    - 同样合乎 claude 规则, 并使用了更多的奇技淫巧
    - 更加复杂, 但破限力度强, 智商保留更多
    - 支持功能更多
  - 缺点:
    - 说实话想不到什么明显的缺点, 确实好用

## 角色卡获取途径
1. [类脑 Discord](https://discord.gg/HWNkueX34q) 是我所知最大的中文角色卡社区, 现在人物卡是在分脑 [旅程 Discord](https://discord.gg/elysianhorizon).
2. [chub](https://www.chub.ai/) 英文社区, 有些好卡在里面, 活跃度还算高
3. [janitorai](https://janitorai.me/) 英文社区, 据说上面同人卡比较多
4. 更多的可以看玩本地模型的[自由AI阵线](https://discord.com/invite/5YXAeFSqPr)的这个[帖子](https://discord.com/channels/1124998756715216976/1269125588845596783/1269125588845596783)

