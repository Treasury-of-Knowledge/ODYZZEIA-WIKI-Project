---
title: 新一站式宝宝教程-flash
description: 
published: true
date: 2025-07-16T05:51:33.280Z
tags: 教程, 酒馆, 酒馆使用
editor: markdown
dateCreated: 2025-07-16T04:21:19.440Z
---

# 一站式宝宝教程-flash-07-16 

# 0 简介

> 作者: KKTsN(橘狐) （Discord @kk1189_61801）采用 [CC BY-NC-SA 4.0许可协议](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.zh-hans)

最后更新日期: 20250716
本教程包括的内容:

1. 安装酒馆
2. 酒馆基础设置
3. 酒馆更新、备份
4. 获取并使用主流API/预设/角色卡/插件等资源
5. 酒馆基础功能/玩法
6. 基础报错解决
7. Discord相关
8. 其他进阶教程链接

本教程**不**包括的内容:

1. 具体角色卡的具体问题
2. 第三方API问题
3. 云酒馆（作者没用过）

> 所有'xxx'都代表'这里应该有内容，但不一定是什么内容'，**不是真的三个X**
> **不要使用XXVPN, XX加速器等连端口都看不到的代理工具，这种梯子往往质量极差**

> **请善用搜索**
{.is-success}


---

# 1 酒馆安装

## 1.1 Windows-推荐使用Git安装

**作者的环境: Windows 10 22H2**

### 1.1.1  安装Git & 配置

  第1步: 同时按键盘上Win键和X键，在弹出的列表中选择  Windows PowerShell，会出现一个蓝色背景的框框（PowerShell）

![dakdpcwershell.png](/all_upload_files_should_in_here/sandbox_area/kktsn/dakdpcwershell.png)

  第2步: 复制这条命令： `git -v`，粘贴到PowerShell中（点一下右键即可粘贴），回车执行

  第3步: 

 - 如果弹出的是`git version xxx`，说明已经安装了Git，请跳到 安装node & 配置

 - 如果是`'git'不是内部或外部命令……`，说明没有安装git（或没有添加到path）请继续向下看第4步

  第4步: 
  2种方法安装git，若其中一种无效或失败，请尝试另一种

  - 复制这条命令到PowerShell中执行: `winget install --id Git.Git -e --source winget ` 以一键安装git

  - 打开[git官网](https://git-scm.com/downloads/win) ，点击图片中的按钮，下载安装包手动安装。

![gitxxzd.png](/all_upload_files_should_in_here/sandbox_area/kktsn/gitxxzd.png)

  - 安装过程中有很多选项，**全部默认即可**

  第5步: 重启PowerShell，再次执行` git -v`，检查是否出现了`git version xxx`，出现即为安装成功

### 1.1.2 安装node & 配置

第1步: 用安装Git时同样的方法，打开PowerShell（如果刚刚把它关掉了的话）

第2步: 复制这两条命令： ` node -v `和`npm -v`，到PowerShell中执行

第3步: 

 - 如果弹出的是`vxx.xx.xx`和`xx.xx.xx`，说明已经安装了node，请跳到3.安装酒馆
 - 如果是`'node'不是内部或外部命令……`，请继续向下看第4步

第4步: 
2种方法安装node，若其中一种无效或失败，请尝试另一种

- 复制这条命令到PowerShell中执行: `winget install OpenJS.NodeJS.LTS -v 20.10.0 ` 以一键安装v20的node
- 到[node官网](https://nodejs.org/zh-cn/download) 下载node的安装包并手动安装，如图（推荐使用LTS版本的）

![nodexxzd.png](/all_upload_files_should_in_here/sandbox_area/kktsn/nodexxzd.png)

第5步: 重启PowerShell，再次执行` node -v`，检查是否出现了第3步中的成功信息



所有依赖全部配置成功后，执行`git -v`，`node -v`和`npm -v`的结果应该如下图⬇️

![yildanvliggs.png](/all_upload_files_should_in_here/sandbox_area/kktsn/yildanvliggs.png)

### 1.1.3 安装酒馆

第1步: 确保能连上外网
稳定的翻墙手段请自行搜索，这里不介绍

第2步: （可选）配置npm镜像
同时按Win键（就是那个有WINDOWS图标的键）和X键（字母X），在弹出的列表中选择Windows PowerShell，会出现一个蓝色背景的框框（PowerShell）

![dakdpcwershell.png](/all_upload_files_should_in_here/sandbox_area/kktsn/dakdpcwershell.png)

在PowerShell中输入: `npm config set registry https://registry.npmmirror.com `执行
等几秒，直到PowerShell又变为可以输入命令的状态，输入`npm config get registry`执行
如果输出的是`https://registry.npmmirror.com`那么就修改成功了

如图⬇️这里第一次`npm config get registry`后输出的是原版站点，修改后第二次用这个 输出的变成了镜像站

![uevinpmjkxl.png](/all_upload_files_should_in_here/sandbox_area/kktsn/uevinpmjkxl.png)


第3步: （可选）配置git代理/TUN模式
> 由于一些镜像源似乎会导致无法安装或更新酒馆及一些扩展，这里为git配置代理
> 当然，也可以使用代理工具的TUN模式（或称虚拟网卡模式）
{.is-info}

⬆️如果看不懂以上两行，也不用担心，直接跟着下面走就可以

方法1: 配置代理

1. 打开你的代理工具，找到它使用的端口（clash verge默认是7897, 而v2ray默认是10808）如果不知道在哪里找，可以在网上搜索'xxx（代理工具的名字）怎么查看使用的端口'
2. 在PowerShell中输入:

```
git config --global http.proxy http://代理服务器地址:端口
git config --global https.proxy https://代理服务器地址:端口
```

两条分别输入，把代理服务器地址:端口 换成**自己的地址+端口**，比如本地v2ray默认是`127.0.0.1:10808`
那么使用的命令就是

```
git config --global http.proxy http://127.0.0.1:10808
git config --global https.proxy https://127.0.0.1:10808
```

输入完成后可以使用
`git config --global --get http.proxy`
`git config --global --get https.proxy`
确认代理设置成功

![gitueviddli.png](/all_upload_files_should_in_here/sandbox_area/kktsn/gitueviddli.png)

方法2: 开启TUN模式
方法请自行搜索: `(自己的代理工具名称) 如何开启TUN模式（虚拟网卡模式）`



第4步: 在你喜欢的地方**新建一个文件夹**，用来安装酒馆
注意 **这个文件夹（以及其上级的所有文件夹）名字里都不要有中文或中文标点！**

错误示例: D:\游戏\我的酒馆
正确示例: D:\Games\SillyTavern

如果不会新建文件夹，请用搜索引擎搜一下 或者问ai



第5步: 在**这个文件夹内部**打开PowerShell
进入这个文件夹（现在它应该是空的），按住键盘上shift别松手，点鼠标右键，即可看到'在此处打开poweshell窗口'，点击它

![zdciiudakdpowershell.png](/all_upload_files_should_in_here/sandbox_area/kktsn/zdciiudakdpowershell.png)

第6步: git clone
在刚刚打开的PowerShell窗口中输入
`
git clone https://github.com/SillyTavern/SillyTavern -b release 
`
回车执行。会出现一大堆代码，但是不用管
直到出现Resolving deltas: 100% (xxx/xxx), done. 并且PowerShell内恢复成可以输入的状态，就安装完成了

如图就是完成了⬇️

![jqgranvliggspowershell.png](/all_upload_files_should_in_here/sandbox_area/kktsn/jqgranvliggspowershell.png)

第7步: 安装npm依赖并启动酒馆
打开上一步完成后新出现的文件夹（名字应该叫SillyTavern），找到start.bat（如果没有开显示文件扩展名那么就叫start），双击它，酒馆会自动安装npm依赖。

耐心等待几分钟，弹出的黑框内可能会有些warn但是不用担心。
依赖安装完成后，酒馆应该会自动启动，在默认浏览器中打开酒馆。

如果没有自动打开，在浏览器中打开这个蓝色的链接，也可以手动进入酒馆。

![uzdsddkdjqgr.png](/all_upload_files_should_in_here/sandbox_area/kktsn/uzdsddkdjqgr.png)

就是红框中的那个⬆️

> 这个**在酒馆启动时首先弹出的黑框**就是所谓的**后台, 后端，在酒馆运行期间不要关闭它！**
{.is-warning}



## 1.2 安卓-推荐使用一键脚本

请参考[这里](https://wiki.类脑.org/%E6%99%BA%E8%AF%86%E5%BA%93/sandbox/%E6%97%A0%E5%90%8D%E6%B0%8F/%E5%AE%89%E5%8D%93%E4%B8%80%E9%94%AE%E9%83%A8%E7%BD%B2%E6%95%99%E7%A8%8B)的教程 




## 1.3 其他

- linux, macos等系统的部署请参考[酒馆官方文档](https://docs.sillytavern.app/installation/linuxmacos/)
- ios（苹果手机）无法本地部署，可以参考[这个](https://wiki.类脑.org/%E6%99%BA%E8%AF%86%E5%BA%93/%E7%B1%BB%E8%84%91%E6%95%99%E7%A8%8B/%E6%90%AD%E5%BB%BA%E9%83%A8%E7%BD%B2/zeabur%E8%B6%85%E7%AE%80%E5%8D%95vps%E9%83%A8%E7%BD%B2%E9%85%92%E9%A6%86%E6%95%99%E7%A8%8B)云酒馆教程


# 2 酒馆更新与备份

## 2.1 更新

> **还能用就尽量别更新，尤其是手机一键脚本安装的酒馆，有更新失败无法启动的风险**
{.is-warning}


### 2.1.1 Windows Git安装

只需运行酒馆根目录下（就是start.bat那个目录里）的`UpdateAndStart.bat`
和安装酒馆时一样，更新时也需要挂梯子.

如果这个`UpdateAndStart.bat`不见了或者出了什么问题，也可以尝试在根目录下打开PowerShell或cmd，执行git pull

### 2.1.2 Windows 压缩包等方式安装

 解压即用的酒馆（如各种所谓整合包，魔改酒馆等）**无法一键更新**

建议备份数据后，用Git重装一个

### 2.1.3 安卓一键脚本

安卓一键脚本一般都有更新酒馆的功能，**确保网络环境稳定**后在一键脚本中选择更新酒馆即可
> 再次提醒，一键脚本更新酒馆 一旦更新坏了导致无法启动，几乎只能重装，而且安卓备份恢复数据很麻烦，更新前请三思
{.is-warning}

## 2.2 备份与恢复数据

### 2.2.1 Windows

只需备份酒馆根目录下的**data**文件夹，这个文件夹里有酒馆绝大多数的数据。

将这个文件夹复制，放到别的安全的目录里（比如另一块硬盘或者移动盘上），就完成备份了。

恢复时，只需将放到别处的data文件夹放回根目录，覆盖原有的文件。

### 2.2.2 安卓本地

虽然同样是备份data文件夹，但由于安卓系统的原因，会麻烦很多。
智识库内已有[备份教程](https://wiki.类脑.org/%E6%99%BA%E8%AF%86%E5%BA%93/sandbox/Y%E3%82%99%E3%82%99%E3%82%99/%E9%85%92%E9%A6%86%E8%A7%92%E8%89%B2%E5%8D%A1%EF%BC%8C%E8%81%8A%E5%A4%A9%EF%BC%8C%E6%89%A9%E5%B1%95%E6%95%B0%E6%8D%AE%E7%9A%84%E5%A4%87%E4%BB%BD%E4%B8%8E%E6%81%A2%E5%A4%8D)


# 3.酒馆基础设置

> 酒馆的默认设置有很多不合理的地方，这里一项一项来调整它们
{.is-info}


1. 进入一个新安装的酒馆，首先出现的就是这个页面 直接`保存`就好

![iuuiuevi1.png](/all_upload_files_should_in_here/sandbox_area/kktsn/iuuiuevi1.png)

2. 上面一排按钮里逐个来改，首先点第二个按钮，也就是长得像个插头那个

![iuuiuevi2.png](/all_upload_files_should_in_here/sandbox_area/kktsn/iuuiuevi2.png)

3. 将`API`这一项从`AI Horde`改为`聊天补全`，`提示词后处理`选择`严格`

![iuuiuevi3.png](/all_upload_files_should_in_here/sandbox_area/kktsn/iuuiuevi3.png)

4. 然后点最左边的按钮，这就是预设界面。注意酒馆自带的这个Default预设有很多问题，不要用它，获取预设教程在后面

![iuuiuevi4.png](/all_upload_files_should_in_here/sandbox_area/kktsn/iuuiuevi4.png)

5. 点从左往右第四个按钮，也就是书📖+地球🌐那个；打开全局世界信息/世界书激活设置，改为图示的样子(上下文百分比拉到100,包括名称和匹配整个单词取消勾选）

![iuuiuevi6.png](/all_upload_files_should_in_here/sandbox_area/kktsn/iuuiuevi6.png)

6. 点第五个按钮，也就是人+齿轮⚙️那个，这里要改的东西比较多

![iuuiuevi7.png](/all_upload_files_should_in_here/sandbox_area/kktsn/iuuiuevi7.png)

  - **打开**`AI回复计时器`，`显示消息楼层`，`显示消息词符数`，在`机器人消息中允许{{user}}`,`在机器人消息中允许{{char}}`
  - **关闭**`click to edit`, `自动修复markdown`, `禁止外部媒体`, `在响应中显示标签`
  - 调整 `要加载#条消息`到一个比较低的值，推荐30以下

# 4. 获取API/预设/角色卡等

## 4.1 获取API

API 即 AI的来源，没有有效的API连接就无法给AI发送消息
目前主流的API有 Gemini Claude Deepseek等，这里逐个介绍获取方式

### 4.1.1 DeepSeek

> - 优点: 中国大陆可直连，可流式输出（就像在网页/手机用ds一样，随着回复的生成，逐词逐句地显示）
> - 缺点: 上下文（即AI一次能处理的文字量）很短，模型能力一般
{.is-info}


这里仅介绍官方渠道，硅基/火山/OR等第三方渠道教程请自行搜索

第1步: 打开[DeepSeek开放平台](https://platform.deepseek.com) 注册登录，如果在国内需要手机号验证

第2步: 点击左侧的`API Keys`，创建一个key

![ds1.png](/all_upload_files_should_in_here/sandbox_area/kktsn/ds1.png)

>    **务必保管好key！ 别人一旦知道你的key，不需要登录你的账号 就可以使用你充值的余额！**
> 
>    **如果不慎泄露，建议删除泄露的key，重新创建**
{.is-warning}


第3步: 点左侧的`用量信息`或`充值`，充一点钱（支持微信支付宝等国内支付渠道）注意无法退款

![ds2.png](/all_upload_files_should_in_here/sandbox_area/kktsn/ds2.png)
第4步: 充值完成以后，刚才创建的key就可以使用了。在酒馆API连接页面（插头）中，聊天补全来源选择DeepSeek，DeepSeek API 密钥填入刚刚创建的key

第5步: 点击连接，下方的红灯变为绿灯'可用'后，点击发送测试消息，若能收到ai回复（酒馆有绿框弹窗）则配置成功，可以在酒馆中使用DeepSeek API了

![dslmjpiggs.png](/all_upload_files_should_in_here/sandbox_area/kktsn/dslmjpiggs.png)
（这里DeepSeek模型中 chat是V3, reasoner是R1 R1也就是网页/app中'深度思考'时用的那个模型）

### 4.1.2 Gemini

> - 优点: 完全免费+额度高，常用模型2.5Pro的能力还可以，几乎无审查
> - 缺点: 直连对网络（梯子）要求高、涉及敏感内容无法流式输出、有时谷歌服务器爆炸导致用不了
{.is-info}


这里仅介绍使用AI Studio API的渠道，教程和图片都来自类脑社区@molilili1

> 由作者经验，使用指纹浏览器+固定IP可提高免手机号注册概率，减小谷歌封号可能，如果使用电脑，推荐以下所有操作在camoufox等指纹浏览器中进行

第0步: 获取指纹浏览器（以camoufox为例）

1. 访问https://github.com/daijro/camoufox/releases 并下载压缩包，解压
2. 双击camoufox.exe打开

第1步: 获取谷歌号

由于谷歌封号，不推荐用自己绑定了大量其他服务的大号来获取API 建议使用小号

已有可用小号的话可以直接看第2步

1. 访问[登录谷歌账号的地方](https://accounts.google.com) 创建账号
2. 填写了一堆信息后，谷歌会要求手机号验证（如果梯子质量很好的话可能不需要），可以尝试用+86手机号验证或者使用接码平台（涉及付费这里不作推荐）

第2步: 创建项目和key

1. 打开[gc控制台](https://console.cloud.google.com/projectcreate) ，登录谷歌账号

![studioirjmxlmu1.png](/all_upload_files_should_in_here/sandbox_area/kktsn/studioirjmxlmu1.png)

2. 项目名称随便填，位置就无组织就可以 点击蓝色的创建按钮


3. 创建完毕后会跳转到另外一个网页（如图1），不用管它 打开[aistudio的apikey页面](https://aistudio.google.com/apikey)（如图2）
   ![studioirjmxlmu2.png](/all_upload_files_should_in_here/sandbox_area/kktsn/studioirjmxlmu2.png)

![studioirjmxlmu3.png](/all_upload_files_should_in_here/sandbox_area/kktsn/studioirjmxlmu3.png)

4. 在ai studio中点击蓝色按钮 创建API 密钥，选择刚刚创建的项目，点击 在现有项目中创建API密钥

![studioirjmxlmu4.png](/all_upload_files_should_in_here/sandbox_area/kktsn/studioirjmxlmu4.png)

5. 复制创建的API密钥（点击图中圈出来的位置就能复制），这就是我们说的**key**

![studioirjmxlmu5.png](/all_upload_files_should_in_here/sandbox_area/kktsn/studioirjmxlmu5.png)

>    **再次提醒，务必保管好key 别人知道你的key，不需要登录你的谷歌账号 就可以使用你的额度**
> 
>    **如果不慎泄露，建议删除泄露的key，重新创建**
{.is-warning}


第3步: 改改配置（安卓跳过这一步）
> 由于Windows系统的各种代理工具默认不会让酒馆的流量走代理，以及gemini api对网络环境要求较高，这里先改几个配置，预防网络问题

两种让酒馆走代理的 方法选一个:
    1. 开启 代理工具的TUN模式（虚拟网卡模式），具体教程可在网上搜索: (你的代理工具名字如clash,v2ray等)+怎么开启tun模式
    2. 改酒馆配置文件
- 首先打开酒馆根目录下的config.yaml，搜索'requestProxy',找到如图所示这一段
- 将enabled后面的false改成true, url改为你的代理工具的代理服务器地址:端口，具体如何查看 每个代理工具都不同，可以自行在网上搜索: (你的代理工具名字如clash,v2ray等)+怎么看端口
- 例如, v2ray的默认端口是10808，这里url后面就改为 127.0.0.1:10808
- 最后保存, 重启酒馆

![jqgrueviddli.png](/all_upload_files_should_in_here/sandbox_area/kktsn/jqgrueviddli.png)

> 由于gemini API不对香港、俄罗斯等国家或地区提供服务，使用gemini API时，梯子节点绝对不能选择港澳、俄罗斯等国家或地区的
{.is-warning}


第4步: 在酒馆中使用

1. 在酒馆API连接（插头）页面中，聊天补全来源选择Google AI Studio

2. Google AI Studio API 密钥 填写刚刚得到的key

3. Google 模型 选择`gemini-2.5-pro` **（严格一致，没有任何preview exp 日期等后缀）**

> 如果这一步在Google 模型列表中找不到gemini-2.5-pro，说明您使用的酒馆版本太低，请更新到最新版
{.is-info}


4. 点击连接，等待下方红灯变为绿灯 后，**先找个预设用，再点测试消息**，若能收到ai回复（酒馆有绿框弹窗）则配置成功，可以在酒馆中使用Gemini API了

![geminiiggslmjp.png](/all_upload_files_should_in_here/sandbox_area/kktsn/geminiiggslmjp.png)

**强调 用default预设点2.5pro的测试消息会导致空回报错，点测试之前先找个预设用**

额外: Gemini限额

- 基础限额为: 每个项目每天100条，6百万tokens (可以简单理解成字数)，上下文为25万
- 每个账号可以拥有多个项目，项目之间配额独立
- 也就是说 在一个号上开多个项目即可让单号限额翻好几倍，具体教程可在类脑搜索


### 4.1.3 Claude

本教程作者没玩过Claude，可以参考智识库的[这个教程](https://wiki.类脑.org/%E6%99%BA%E8%AF%86%E5%BA%93/%E7%B1%BB%E8%84%91%E6%95%99%E7%A8%8B/%E8%8E%B7%E5%8F%96AI%E6%B8%A0%E9%81%93/Pro%E9%80%80%E6%AC%BE%E6%B5%81%E6%95%99%E7%A8%8B)



## 4.2 获取预设&正则

预设的用处主要有二: 

- 破限（让ai能输出敏感内容）
- 指导（告诉AI怎么写，写什么）

而正则是用来去除思维链，摘要等我们不希望出现在正文中，被我们看到的内容的

如何获取:
第1步: 打开discord社区中的预设区
[类脑](https://discord.com/channels/1134557553011998840/1134822069222264874)
[旅程](https://discord.com/channels/1291925535324110879/1374295248322170963)

![yuuequ.png](/all_upload_files_should_in_here/sandbox_area/kktsn/yuuequ.png)

第2步: 可以按标签筛选，选择自己玩的模型，挑自己喜欢的预设下载。每个预设风格都不同，可以都试试，找到最适合自己的
第3步: 作者一般会给预设文件+正则文件（文件大小大的一般是预设，小的是正则） 如图，全部下载下来

![yuuehevgzeuiyi.png](/all_upload_files_should_in_here/sandbox_area/kktsn/yuuehevgzeuiyi.png)

第4步: 在酒馆中导入

- 预设文件需要导入到预设界面（上面一排按钮最左边那个）里面
- 正则文件需要导入到扩展-正则中（具体看本部分末尾的一图流）

> **预设必须和对应的正则配合使用，用哪个预设就开对应的正则，其他预设的正则要关掉**
> **调整开关正则时，务必在新对话中进行，由于酒馆BUG 开关正则可能导致当前聊天记录丢失**
{.is-warning}


## 4.3 获取角色卡

角色卡是指导AI怎么写，换句话说 写什么样的故事，扮演什么样的角色的
酒馆使用的角色卡格式为PNG或JSON（PNG格式的自带卡面）

如何获取:
第1步: 在 Discord 类脑/旅程的频道列表中找到**角色卡区**，这里被分成了多个频道，点进去就能看到很多角色卡

![kaqu.png](/all_upload_files_should_in_here/sandbox_area/kktsn/kaqu.png)

> 类脑的**帖子备份区** 多数帖子没有卡，**拟态复原区的卡（如果有）在最下面一楼**
{.is-info}

第2步: 卡的作者会指路哪一层的**图片就是卡**，下载这张图片就可以导入酒馆了

![vcka1.png](/all_upload_files_should_in_here/sandbox_area/kktsn/vcka1.png)
![vcka2.png](/all_upload_files_should_in_here/sandbox_area/kktsn/vcka2.png)
（这张大头图片就是角色卡⬆️）
- 电脑客户端: 直接右键点击图片，选择保存图片
- 手机客户端: 点开大图长按，选择保存图片
- **网页端**: 必须点开大图后，选择右上角的'在浏览器中打开'，然后在新打开的页面中保存图片（右键另存为或者长按）

**注意卡的作者会标明这张卡需要什么扩展来正常运行，玩卡之前先安装扩展**

## 4.4 插件/美化/世界书/快速回复 等

以上几种都是让酒馆体验变得更好的

- 插件允许酒馆实现额外的功能，如渲染html美化等
- 美化可以让酒馆看起来更美观
- 世界书可以为AI补充额外的知识，或者让ai写出不同的文风等
- 快速回复允许你点击按钮输入一些预定的语句，节省打字时间

如何获取:

- 在Discord 类脑/旅程的频道列表中找到 工具/插件/美化/世界书 区，点进去就能看到很多资源

![ziyrqu.png](/all_upload_files_should_in_here/sandbox_area/kktsn/ziyrqu.png)

- 同样可以按标签筛选

### 导入扩展/正则/角色卡/快速回复/美化/预设/世界书 之 一图流

（如果看不清可以下载图片放大看）

![v3nbbe.png](/all_upload_files_should_in_here/sandbox_area/kktsn/v3nbbe.png)


# 5. 酒馆基础玩法

## 5.1 一些酒馆自带功能

![sjtngh.png](/all_upload_files_should_in_here/sandbox_area/kktsn/sjtngh.png)

以上功能都在输入框左边的'三条横线'按钮里
- 开始新聊天: 字面意思，在当前角色卡开启一个新聊天
- 管理聊天文件: 这里可以在不同的，已保存的聊天中切换，也可以导出聊天记录或删除聊天记录
- 删除消息: 删除一定的'楼层'（AI或用户的一次发言称为一层），注意这里只能从最下一层向上方 连续地删除
- 重新生成: 也叫'roll'，'重roll'，让ai重新生成最后一次的回复内容

---
下图中，消息右上角的"铅笔"✏️按钮就是编辑消息按钮，也叫'小铅笔'
![xnqmbi1.png](/all_upload_files_should_in_here/sandbox_area/kktsn/xnqmbi1.png)

点击它，可以看到消息变成了下面的样子:

![xnqmbi2.png](/all_upload_files_should_in_here/sandbox_area/kktsn/xnqmbi2.png)
中间的黑框内可以直接编辑消息的内容，手动改正AI的小错误或者修改自己之前的消息，都可以
- 1 绿色✅按钮:保存编辑结果
- 2 垃圾桶🗑按钮: 删除这一层（和三条杠里的删除消息不同，这里是可以隔空删楼 不需要连续的）
- 3 ❌按钮: 退出编辑而不保存

> 另外，点击小铅笔后显示的内容是未经正则处理，没有被渲染的，所谓的原文 当AI输出不完整时，可以点开小铅笔看看缺失的内容到底是真的没有输出，还是被正则等错误地隐藏了
{.is-info}


## 5.2 调整预设

现在的预设基本都提供了大量可调整的功能，可以根据自己的需要开关这些功能。
如图，只要点击这些小开关就能开关了
![yuuekkgr.png](/all_upload_files_should_in_here/sandbox_area/kktsn/yuuekkgr.png)
具体功能以作者的解释为准。一些说法是通用的，在此介绍:

- **上下文长度（以词符数计）:** 允许AI使用多少上下文。如果实际使用的上下文超过了这个值，酒馆会不发送最早的一部分聊天记录，以节约上下文。一般来说用预设作者给的值就好

- **最大回复长度（以词符数计）:** 允许AI在一次回复中写多少字（虽然1token≠1个字）。一般来说用预设作者给的值就好

- **流式传输**: 简称流式，指最大回复长度下方的小开关。开了以后会随着回复的生成，逐词逐句地显示结果，就像用网页deepseek一样。

  - **AI Studio API的 Gemini 不能开流式玩，因为流式输出时是边输出边审查，会被截断（输出到一半停了）**

- **上下文:** 目前向AI发送一条消息会使用多少token。包括预设内容，世界书，角色描述，聊天记录等
  - '上下文太长了'指的就是一次向AI发送的东西太长了，AI处理不过来导致各种问题

- **总词符数:** 预设条目列表上方的一个数字，即当前使用的上下文长度

- **头部:** 一般指预设靠近最上方的，规定AI角色的条目，如'你是xxx，一个xxx……' 
  - 一些API提供商（如谷歌）在某预设被大量使用后，会标记预设头部，导致无法破限或回复异常变慢，此时需要打开**防429**或自行修改预设头部（看基础报错解决部分）

- **防429:** 指gemini预设中 靠近最上方的一个条目，内容通常是大量使用随机宏的乱码，用于绕过谷歌的标记机制

- **思维链:** 也叫'COT'，指预设中要求AI在输出正文前，'思考'并输出的一些内容，如'当前处于何种情境？时间？地点？社会关系？角色当前姿势？'
  - 如果角色卡要求'关闭预设思维链'，只需关闭预设中从'思维链开始'到'思维链结束'的所有条目

- **文风:** 字面意思，指导AI以何种风格写作，对正文影响很大

- **禁词/反八股:** 字面意思，防止AI使用某些表达。效果一般

- **防绝望/黑化/阴谋论:** 防止AI笔下的角色动不动就黑化，陷入绝望，或者搞阴谋论（以前的gemini这个问题很严重）

- **小COT:** 要求AI每创作一段就在正文中进行'思考'，然后再创作下一段。通常用来防绝望/反八股等

- **防抢话:** 防止AI代替user（也就是玩家）做决定
  - 如果开防抢话，必须将**预设条目中的**字数控制调低 （不是上下文滑条下面的最大回复长度）

- **反截断:** 防止审核拦截危险的正文导致空回复。**当前不空回就不用开，出现空回了再开**

- **小总结:** 也叫'摘要'，让AI在每次回复的正文后带上一段对本次回复中情节的摘要，配合正则可以做到距离当前较远的聊天记录只发送摘要（而不发送全部正文），节省上下文
  - 注意小总结只对开了以后新生成的楼层生效
  - 小总结必须和正则一起使用，一起开一起关，否则没有效果

- **字数控制:** 要求AI每次输出的正文不能超过/低于xx字
  - 由于AI并不知道自己写了多少字，给出超高的字数要求时AI并不会遵守得很好

- **总结前文:** 也叫'大总结'，一般在预设靠近底部的位置。要求AI停止剧情推进或角色扮演，在本次回复中仅进行对前文的总结

- **尾部:** 预设最靠下的几个条目。这部分曾经是用来绕过输入截断的（现在谷歌把输入截断关了），现在多用于强调用户本次输入、让AI开始思维链等



## 5.3 总结

- 当聊天记录太长，单次发给AI的信息（字数）太多，AI一次处理不过来，就会产生各种问题。例如忘事、幻觉、发癫、掉格式等等
- 因此需要进行总结，即将之前的聊天记录交给AI，让AI总结其中的重要事件，以后就不发送全部的正文，只发送这些重要事件的概要

### 总结教程（By Yoolieer）:

1. 假设已有 100 条对话记录，在聊天框输入：  
   `/hide 0-100` 隐藏全部内容；  
   `/unhide 0-50` 显示前 50 条。  
2. 让 AI 总结前 50 条内容。  
3. 再次输入 `/hide 0-50` 隐藏前 50 条，  
   `/unhide 51-100` 显示后 50 条，让 AI 继续总结剩余内容。  

> 建议每次总结文本控制在 50K 字符以内。  

4. 检查预设中是否有“总结前文”功能，若有，则开启该条目后向ai随意发送一个1即可
   没有的话，可直接发送文本：`<Request:暂停剧情，本回合无需输出正文内容。请将之前发生的事进行总结，按时间或逻辑顺序保留关键信息，省略冗余描述>`
5. 将 AI 输出的总结内容复制到世界书新建条目中，位置建议放在角色定义之后，并开启“蓝灯”标记。
6. 重复上述操作，直到所有内容都已精简总结。之后，使用`/hide 0 - y`命令隐藏原始对话，建议保留最近的 5-10 层，用于保持文风和格式。
   附加说明：

- `/hide x-y`：隐藏第 x 至 y 层内容，使 AI 无法读取  
- `/unhide x-y`：恢复第 x 至 y 层内容的可见性
  备注：此方法推荐配合预设内的摘要（小总结）功能一起使用，可以非常好的控制住上下文。





# 6. 基础问题解决

查阅这一部分 可以自己解决一些问题

## 6.1 酒馆安装/更新

6.1.1 Windows安装酒馆 git clone那一步报错: could not connect to the server等

  - 网络问题，试着开启代理软件的TUN模式或者给git设置代理，还不行换节点，换梯子
  - 更新失败时报错相同同理
    6.1.2 提示'git'或'npm'等不是内部或外部命令……
  - git或node等依赖未安装，回到本教程的1.2再看看吧
    6.1.3 安卓安装/更新报错
    看看[这个](https://discord.com/channels/1134557553011998840/1368905598334406717/136890559833440671)

## 6.2 酒馆使用

6.2.1 酒馆变得很卡

- 先重启酒馆（后台也要关掉重开），看看是不是偶然问题
- 如果重启酒馆后依然很卡，调低'用户设置'中的'要加载 # 条消息' （这个选项仅影响显示，不影响发送给ai的实际内容）
- 检查是否开了很多 多余的正则，关掉
- 如果用了提示词模板这个拓展，更新一下，老版本的有性能问题
- 如果是前端卡 很卡，调低酒馆助手渲染器中的渲染深度



6.2.2 安装/更新扩展时出错（按**报错中的关键词**来找）：

- **ENOENT**: 未安装git或未把git添加到环境变量，请自行在网上搜索解决方法 或问AI，安装或添加后**先重启酒馆，再尝试安装拓展**
- **already exists**: 上一次安装出问题了，到酒馆目录下/data/default-user/extensions 或 \public\scripts\extensions\third-party 中，手动删除这个拓展的文件夹，重启酒馆后再次尝试安装
- **not found**: 安装链接填错了，检查一下 复制得是否正确
- **newline**: 同上
- **Connection**: 网络问题，请使用作者提供的 无需国外网络环境的链接来安装。如果没有，可以开梯子TUN模式，或给git设置代理（教程网上有），还不行考虑节点/梯子问题，换
- **不报错也没反应**: 网络问题，同上

注意 非git安装的拓展无法使用git更新，推荐删掉后用git重新安装

6.2.3 模型列表中没有想选的某个模型（如gemini-2.5-pro）

- 酒馆版本太低了，更新酒馆
- 如果不想更新，可以使用自定义模型插件，具体可以在dc社区内搜索

6.2.4 Check the server connection and reload the page to prevent data loss/ST Server cannot be reached Verify that the server is running and accessible

- 都是酒馆后台掉了。由于安卓系统限制后台应用活动，安卓本地酒馆尤其容易出现这个问题。
- 解决方法：安卓需要把酒馆’挂小窗’（具体操作方法请搜索’(你的手机型号)+怎么挂小窗’

## 6.3 API报错

**注意API问题报错时，以后台的报错信息为准，在答疑区等提问时也请带上后台截图**

**每节的标题是后台报错信息中的关键字**

6.3.1 ETIMEDOUT

- 原因: 网络问题，根本连不上gemini服务器

- 解决:

  - (WINDOWS专用，手机不需要这一步) 检查是否让酒馆走代理或开启了梯子TUN模式（见4.1.2)

  - 更换节点

  - 更换梯子

6.3.2 socket hang up

- 原因: AI太久没回复，酒馆主动切断了连接
- 解决:
  - 这是酒馆本身的问题，推荐使用有'假流式'功能的反代
  - 具体可以到类脑, 旅程等社区内搜索, 或者到dc答疑区询问

6.3.3 client network disconnected before……

- 同ETIMEDOUT

6.3.4 user location is not supported for the api use

- 梯子节点不对，**不要选港澳 俄罗斯的节点**
- 如果已经选了其他地区的节点，还是报错这个，考虑节点用的人太多被标记，再换

6.3.5 not found / unexpected model name format

- 模型已经被下架，不再能用了
- 或者自定义模型插件填的模型名字不对

6.3.6 429
gemini429的原因很多，需要更进一步排查

1. 若后台提示超出的限额为'TokensPerMinute':

  - 上下文超过模型每分钟能处理的token了
  - 需要总结隐藏前文以降低上下文长度
  - 不停点重新生成也可能触发这个

2. 若提示超出的限额为'TokensPerDay'或'RequestsPerDay':

  - 这个key超过了当天的限额（2.5pro为每天100条/6百万token)
  - 换一个来自不同项目的key用

3. 若报错信息很短，没有明确提示超出哪项限额:

  - 考虑预设或节点被谷歌标记
  - 打开预设头部的防429 或 自己改预设头部（具体教程可在dc搜索），梯子换个节点

4. 若提示'don't have a free tier quota':

  - 选错模型了，选到了preview系列的2.5pro
  - 换成正确的模型: `gemini-2.5-pro`

6.3.7 500

- AI Studio API直连一般不会出现这个报错，不过最近上下文超过131k有可能会出这个
- 建议总结隐藏前文等，降低上下文到131k以下

6.3.8 503

- 这个模型用的人太多了，提供商的服务器过载了
- 如果发现只有自己在503,建议换个节点/预设；如果大家都在503就只能等了

6.3.9 空回复

- 报错信息中有PROHIBITED CONTENT或 candidates empty等都是空回复，即生成的回复被审核拦截了
- 请依次逐个尝试以下解决方法:
  - 开反截断:打开预设中的反截断条目（一次只开一个，从较弱的开始，还是空回再开强的）
  - 预设反标记: 预设被谷歌标记可能导致空回，开预设中的防429, 或者改预设头部
  - 换预设: 直接换个破限更强的预设
  - 卡的问题: 外审对一些内容尤其敏感，世界书，角色描述等含有这些内容就容易空回 目前已知的包括直接描述年龄<18岁等，将这些内容删改掉
  - 最近输入的问题: 如果突然出现无论怎么开反截断换预设都是空回，可能是因为最近的输入内容（如给ai发的最后一条消息，或上一条ai回复）中有特殊的敏感内容。请尝试给ai发一些不一样的内容，或者删掉上一条ai回复再重新生成
  - 回复消息中插入太多d0(世界书深度/生图插件等)了，关闭世界书条目或调整条目深度，关闭插件或调整生图插件提示词深度(建议d1尝试)

6.3.10 Unexpected token 'xxx' ……

- 解决方法同空回

6.3.11 (Claude的)  413

- 克的报错，上下文超了，总结吧
- 如果第一句就413, 考虑是不是买到了免费cookie？

6.3.13 (Claude的) 429  （By 羽树）	

- cookie额度已耗尽
- 添加cookie: 按照教程，添加新的cookie，或等待额度刷新，每5小时重置一次

6.3.14 (Claude的) 403  （By 羽树）	
原因: 凌晨a社加大网络环境审查力度, 梯子节点质量不达标
解决:

- 开启全局/tun模式: 视梯子来源，请保证起码能够开启全局模式
- 更换节点: 更换梯子节点或梯子(以美国为佳，可通过ping0.cc网页自查)
- 更换预设:(未经严格实证)尝试更换预设后，部分情况可继续使用
- 等待: 若方法均失效，则只能够等待审查波动结束

## 6.4 API其他问题

6.4.1 重复（By 羽树）	

- **现象:** 
  - 在同一轮生成新的回复时，生成的回复内容重复或极其相似
  - 推进新回复时，重复上文内容
- **原因1:**回复内容被api缓存 
- **解决:** 
  - **开启预设防缓存条目**:开启防429随机数即可防止缓存重复
  - **使用左下角功能栏的重新生成**:(会删除你本轮多次生成的回复，且未实证效果)
  - **更换API尝试**:若有多个项目api，可尝试更换
- **原因2:**上下文过长，超出模型token量舒适区
- **解决:**
  - **更换模型**:若使用模型为gemini flash系列，则建议使用gemini pro进行尝试
  - **总结上文**:对上文内容进行大总结，并隐藏已总结的楼层
  
6.4.2 增殖 （By IACER）
    gemini如果出现外文、标点符号（逗号、省略号）、某个词语大量出现的情况，我们一般称之为增殖，解决方法（选一）：
    -回退到第一次出现这种情况的楼层，删除该楼之后的所有内容，然后重新roll
    -进行一次大总结，然后将出现问题的楼层全部隐藏（记得检查大总结内容，可以手动删一下防止大总结内也被增殖）

## 6.5 其他

6.5.1 酒馆无法启动 报错 EADDRINUSE

- 端口被占用了，检查是不是重复开了两个酒馆的后台？
- 如果没有，检查是不是哪个程序占用了默认的8000端口
  6.5.2 导入正则/世界书失败 提示 invalid xxx
- 文件不对，检查是不是把预设之类的导入进去了



> **更多问题可以查阅[@XuanYuk的工具书](https://docs.google.com/document/d/1Mj8m3xOpXggHI2XtG-MiZbk2reQpa4K4tjaqaWrKIps/edit?usp=sharing)** 
如果以上内容无法解决您的问题，可以在DC社区的答疑区提问
提问API有关问题（如连不上，报错，效果不好等）时，务必带上插头截图（API连接那个页面的截图），后台截图，反代日志截图（如果用了各种反代）
{.is-info}

# 7 DC社区有关常见问题

- 类脑/旅程在哪进？
  类脑永久邀请链接: `https://discord.gg/6kdVgVgcRx`
  旅程永久邀请链接: `https://discord.gg/elysianhorizon`

- 为什么没法在卡区/预设区说话？
  新加入类脑/旅程的成员会经历72小时的**缓冲区**，在此期间只能在答疑区和新人开帖区说话
  **答完题**72小时后自动离开缓冲区

- 怎么看子区/标注？

  电脑:

![dmnckjziqu.png](/all_upload_files_should_in_here/sandbox_area/kktsn/dmnckjziqu.png)

  手机:
  ![uzjikjbnvu.jpg](/all_upload_files_should_in_here/sandbox_area/kktsn/uzjikjbnvu.jpg)

  

- 怎么回顶？
  对于已经离开缓冲区的成员，只需在聊天框内输入`/回顶`，会在输入框上方显示出指令
  选择回顶指令并发送，会有机器人发送一个仅您可见的回顶按钮，点一下就能回到帖子顶部
  对于还在缓冲区的新人，需要使用回顶区
  回顶区链接，点进去就能看到教程:
  [类脑](https://discord.com/channels/1134557553011998840/1365567153390227508/1368639259992396017)
  [旅程](https://discord.com/channels/1291925535324110879/1369174832637284413/1369175882270375972)

- 为什么有的频道看不见？
  到频道列表最上方的'浏览频道'中找找，发现想看的频道后，勾上右侧的框，它会常驻在频道列表中
  特别地，深渊区需要先在'深渊之门'频道中领取一下身份组才能看
  如果浏览频道中没有您想看的频道，可能是您当前没有查看所需的权限？

- dc自带的搜索太难用了，有没有好一些的
  请使用**搜索频道**（缓冲区也能用，点进去有教程）

# 8 其他教程链接

> 这部分为已经熟知了以上基础内容，想要进阶使用酒馆的朋友准备
{.is-info}


[使用脚本一键创建大量项目并获取gemini key](https://discord.com/channels/1134557553011998840/1388829444881256488/1388829444881256488)
（真单号无限额度）

Claude/Gemini反向代理:
[类脑教程区](https://discord.com/channels/1134557553011998840/1134717476505137215)
[旅程反代区](https://discord.com/channels/1291925535324110879/1374344730569216061)

Vertex渠道使用gemini: 
[绑卡v ](https://discord.com/channels/1134557553011998840/1355668576194793604/1355668576194793604)
[快速v](https://discord.com/channels/1134557553011998840/1355668576194793604/1369541325002899456)

[AI Studio 逆向 使用Gemini ](https://discord.com/channels/1134557553011998840/1380129283430940712/1380129283430940712) （满血一百万上下文，并且几乎无503, 但空回/截断问题更严重）

[酒馆插件（扩展）导航](https://discord.com/channels/1134557553011998840/1392379963239301221/1392379963239301221)

[小白入坑写卡的完整学习路径与教程导航](https://discord.com/channels/1134557553011998840/1380047244321095710/1380047244321095710)

[写预设教程](https://discord.com/channels/1134557553011998840/1381186929390915584/1381186929390915584)

[文生图](https://discord.com/channels/1134557553011998840/1327838280254754836/1327838280254754836)

---

结束，感谢读到这里

如果发现本教程有问题或者有已经过时的地方，可以到DC类脑/旅程找作者@kk1189_61801
可以在教程协作区的[帖子里](https://discord.com/channels/1134557553011998840/1394720496364421183/1394720496364421183) 直接at作者，或者到答疑区提问