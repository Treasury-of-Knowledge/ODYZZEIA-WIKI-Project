---
title: 酒馆SillyTavern安装指南
description: 
published: true
date: 2026-04-05T04:21:17.662Z
tags: discord
editor: markdown
dateCreated: 2026-03-07T15:26:11.912Z
---

# 酒馆SillyTavern安装指南&酒馆初始设置

原作者：FoX | 𝓚𝓚𝓣𝓼𝓝(橘狐)

## 酒馆的安装和初始设置

这篇指南让你学会下载安装酒馆，调整一些初始设置，踏上玩酒馆之路的第一步！

## 我的系统能不能装酒馆？

截至2026年3月，酒馆在各平台的可用性如下：

- Windows：
  - Win8及以后的系统均可安装！
  - Win7及再早的远古系统，由于无法运行所需的NodeJS，无法安装。
- Linux ：几乎所有Linux系统都能装！而所謂的vps多數就是使用linux系統
- MacOS（苹果电脑）：绝大多数版本的MacOS都能装！
- Android（安卓手机）：需要手机能安装并正常运行Termux这个应用。
  - 部分鸿蒙系统的设备根本打不开Termux，所以装不了。但是最近有新鴻蒙手機用户說在出境易下載termux就能夠正常使用，歡迎測試
- IOS（苹果手机）：装不了。

當然就算是使用鸿蒙系统或者苹果手机，也并非完全玩不上！你可以用云酒馆，即在云服务器（vps)上部署一个酒馆，用手机连接到服务器来玩。这一点我们稍后介绍。

# Windows安装酒馆

有3种比较主流的安装方式：
- Git 安装：推荐！稍微麻烦一点，但功能最全面。点一下就能一键更新，几行命令就能切换版本。
- 压缩包安装：解压就用，最方便。但是没法一键更新（准确说根本没法更新）或者切版本。反正酒馆使用也离不开Git，为什么不用Git装呢？
- Docker安装：不推荐，麻烦。

这里主要介绍前2种。

注意：**不要用酒馆文档介绍的那个SillyTavern Launcher**，不好用，还会装一堆没用的东西浪费时间。

## Git安装

### 1. 安装Git
Git是用来安装酒馆以及后续插件的。到[git官网](https://git-scm.com/)，点右边的Install for Windows那个大橘色按钮：
![snipaste_2026-02-01_19-04-38.png](/all_upload_files_should_in_here/sandbox_area/1009/snipaste_2026-02-01_19-04-38.png)
再点这个Click here to download：
![snipaste_2026-02-01_19-05-21.png](/all_upload_files_should_in_here/sandbox_area/1009/snipaste_2026-02-01_19-05-21.png)
会下载一个exe，运行即可。安装途中会让确认很多东西，**全都不用改，**一路下一步过去就好。

### 2. **安装NodeJS**

酒馆依赖于NodeJS运行，没有这个东西酒馆根本开不起来。

打开[NodeJS官网](https://nodejs.org/zh-cn) ，点获取NodeJS。

![snipaste_2026-02-01_19-06-18.png](/all_upload_files_should_in_here/sandbox_area/1009/snipaste_2026-02-01_19-06-18.png)
出现的下一个页面里，在⁨⁨`的NodeJS`⁩⁩右边这个选版本的地方，把版本换成⁨⁨`v22.22.0(LTS)`⁩⁩，不要用最新版。
![snipaste_2026-02-01_19-07-53.png](/all_upload_files_should_in_here/sandbox_area/1009/snipaste_2026-02-01_19-07-53.png)
别的都不用改，直接点下面绿色按钮里的Windows安装程序。

下载下来以后双击msi文件，一路下一步就行。

### 3. **验证下NodeJS和Git是否安装好了**

按win（一般在键盘上空格和Alt的左边！）+ X，选择Windows PowerShell （管理员），输入：
```
git -v; node -v; npm -v; Read-Host " "
```

把这一行命令直接粘贴进去，按回车。如果输出是三行版本号，例如：
```
git version 2.52.0.windows.1
v22.14.0⁩⁩ 
10.9.2
```

那么就没问题，如果报错了说明其中一个没装好，重装即可。
如果出现了'因为在此系统上禁止运行脚本'的报错，只需在powershell里输入这行命令：
⁨
> set-ExecutionPolicy RemoteSigned

按回车，系统会问是否确定，输入Y确定即可。(这个命令需要管理员权限，不过应该不会有人在自己的电脑上不是管理员吧)
有些版本的系统不会让确认，也没关系，然后再⁨⁨`npm -v`⁩⁩确认一次即可。

### 4 **安装酒馆**

首先，git的流量默认不会走系统代理（换种说法，不能被梯子'加速'）。所以在从github上下载酒馆的时候，可能会速度很慢或者直接超时了，开了系统代理也解决不了。这有两种办法，二选一即可：
- 打开梯子的**TUN模式**，也叫虚拟网卡模式。注意**不是全局模式**！不同梯子的操作方法不同，请自行搜索。
- 为git永久设置代理。再按win+x打开powershell（之前那个没关的话，用之前的也行），输入这两行命令并按回车执行：

``` 
git config --global http.proxy socks5://127.0.0.1:梯子端口
git config --global https.proxy socks5://127.0.0.1:梯子端口
```

**注意把梯子端口四个汉字换成你梯子实际的端口**，比如clash verge默认是7897，v2rayn默认是10808. 如果不知道，请自行搜索。另外clash for windows（图标是一个深蓝色小猫的）已经很久不更新了，不要用了，可以用clash verge替代。

设置好以后，可以用⁨⁨
``` 
git config --global --get http.proxy
git config --global --get https.proxy
```
查看代理是否设置成功。

弄好以后，打开或者新建一个没问题的文件夹：
- 不能在C盘受系统保护的文件夹里，⁨⁨⁨⁨`C:\windows`⁩⁩⁩⁩ 不行！
- 路径不能有中文，⁨⁨⁨⁨`D:\我的酒馆`⁩⁩⁩⁩ 不行！

点进去，按住键盘上shift，右键点空白处，选择⁨⁨⁨⁨`在此处打开 PowerShell 窗口`⁩⁩⁩⁩。
![snipaste_2026-02-01_19-16-39.png](/all_upload_files_should_in_here/sandbox_area/1009/snipaste_2026-02-01_19-16-39.png)

在打开的窗口里，输入：

```
git clone https://github.com/SillyTavern/SillyTavern -b release
```

按回车。
![snipaste_2026-02-01_19-17-07.png](/all_upload_files_should_in_here/sandbox_area/1009/snipaste_2026-02-01_19-17-07.png)
之后会出现一大堆提示，都不用管，等一会。等PowerShell恢复到这个可以输入的状态以后就是安装完了（或者失败了）。
![snipaste_2026-02-01_19-17-42.png](/all_upload_files_should_in_here/sandbox_area/1009/snipaste_2026-02-01_19-17-42.png)


这种方式安装的酒馆默认是最新版，截至2026年2月是⁨⁨⁨⁨`1.16.0`⁩⁩⁩⁩。不过这个版本和很多社区制作的第三方扩展有冲突，目前比较推荐的稳定版是⁨⁨⁨⁨`1.13.4`⁩⁩⁩⁩或者⁨⁨⁨⁨`1.14.0`⁩⁩⁩⁩，更低的版本完全不推荐。这两个版本之间还有一个1.13.5, bug非常多基本用不了，同样不要装。

- ⁨⁨⁨⁨`1.13.4`⁩⁩⁩⁩是很多第三方扩展的'长期支持版本'，最稳定，但是模型列表还停留在Gemini 2.5 版本，而且有一个会导致内存占用异常偏高的漏洞（可以自己修复，加两行代码的事，感兴趣的可以自行搜索）。
- ⁨⁨⁨⁨`1.14.0`⁩⁩⁩⁩是更新的版本，主流模型列表和现在（2026年1月21日）一致，爆内存问题也修复了，但和某些扩展可能会不兼容。本教程作者用的就是这个版本。


要安装某个指定的版本，可以使用
```
git clone -b 1.数字.数字 --depth 1 https://github.com/SillyTavern/SillyTavern
```
把'数字'这两个汉字换成版本对应的即可。这种方式安装的酒馆体积较小，仅有100mb左右，而且不缺少任何内部的功能。但无法通过git pull更新。

总之现在已经安装完酒馆了！点进新出现的文件夹（应该叫SillyTavern），找到start.bat（没开显示后缀的话就叫start），双击，会出现一个黑框又开始跑代码，等一会就好了。第一次启动时间会比较久。启动完之后，酒馆会自动在默认浏览器里打开。
![snipaste_2026-02-01_19-25-21.png](/all_upload_files_should_in_here/sandbox_area/1009/snipaste_2026-02-01_19-25-21.png)

![snipaste_2026-02-01_19-23-10.png](/all_upload_files_should_in_here/sandbox_area/1009/snipaste_2026-02-01_19-23-10.png)

## 压缩包安装

选择压缩包安装可能是因为网络问题，⁨⁨`git clone`⁩⁩的时候实在下载不动，或者单纯图方便。而且酒馆内置的一键安装插件功能必须要装Git，不然你只能手动从github下载插件再找文件夹解压进去，非常不方便。
总之即使选择了压缩包安装，我也推荐你按照上面的教程装一个Git For Windows.
压缩包安装非常简单：

1. 首先同样是安装NodeJS。没有这个酒馆开不起来的。
2. 到 [酒馆的release页面](https://github.com/SillyTavern/SillyTavern/releases) ，找到你想要的版本（同样推荐1.13.4或者1.14.0, 不要选1.13.5或者1.15.0，而1.16.0謹慎選擇因爲吃性能），点下面的Assets展开，然后点⁨⁨`Source code (zip) `⁩⁩的蓝字，会下载一个压缩包。
![snipaste_2026-02-01_19-26-20.png](/all_upload_files_should_in_here/sandbox_area/1009/snipaste_2026-02-01_19-26-20.png)
3. 把压缩包解压到一个安全的目录，不要放C:\windows这种里面，路径不要带中文或者别的英语之外的语言。
  - 不会解压的读者请自行搜索。太过基础这里不再花费篇幅介绍。
4. 双击⁨⁨`start.bat`⁩⁩，等一会让npm安装依赖，然后酒馆会自己在浏览器里弹出来。


## Docker安装

 "在 Windows 上使用 Docker 真的很复杂。你不仅需要在“启用或关闭 Windows 功能”中激活“适用于 Linux 的 Windows 子系统”（WSL），还需要在 BIOS 中开启虚拟化支持（Intel VT-d 或 AMD SVM），而不同品牌电脑（或主板）的设置方法都不尽相同。有时，在某些系统上甚至找不到这些选项。 " ── SillyTavern官方文档

因此不做过多介绍。感兴趣的请自行看酒馆官方文档：[官方文档](https://docs.sillytavern.app/installation/docker/#building-the-docker-image)

# Linux或MacOS

这两个系统的用户肯定对终端操作更为熟悉，所以这里不详细介绍。
流程差不多，装NodeJS和Git然后⁨⁨`git clone`⁩⁩，linux用docker也很方便。
具体看[官方文档](https://docs.sillytavern.app/installation/linuxmacos/) 


# 安卓
安卓虽然基于 Linux 内核，但无法直接运行酒馆这种依赖 NodeJS 的应用。所以我们需要借助Termux。Termux是一个安卓终端模拟器，在手机里构建一个微型的 Linux 环境。如果你的手机系统根本安装不了，或者打不开Termux，那就不能本地安装酒馆。
如果是在github上面下載的[termux](https://github.com/termux/termux-app)
![snipaste_2026-02-01_19-35-31.png](/all_upload_files_should_in_here/sandbox_area/1009/snipaste_2026-02-01_19-35-31.png)
## 避免在這裏重複討論了，可以直接去查看下面的教程 ：
1.<a href="/智识库/sandbox/1009/钓鱼佬的工具箱-安卓酒馆部署脚本" class="is-internal-link is-valid-page">钓鱼佬的工具箱-安卓酒馆部署脚本</a>
2.<a href="/智识库/sandbox/无名氏/安卓一键部署教程" class="is-internal-link is-valid-page">安卓一键部署教程</a>
3.<a href="/智识库/sandbox/1009/安卓termux手动部署-無脚本" class="is-internal-link is-valid-page">安卓termux手动部署-無脚本</a>

（注意termux里命令要长按屏幕粘贴）
接下来介绍几个termux环境常用的命令：
- ⁨⁨`ls`⁩⁩：列出当前目录下所有的文件和文件夹。
- ⁨⁨`cd (文件夹名字)`⁩⁩：进入当前目录下的一个文件夹，区分大小写。
- ⁨⁨`cd .. `⁩⁩：回到上一级。（.. 就是两个点，不是省略号）
- ⁨⁨`bash xxxx.sh`⁩⁩ ：运行某个.sh脚本，酒馆里通常是start.sh，用于启动酒馆。需要在脚本同目录下使用，也就是先⁨⁨`cd SillyTavern`⁩⁩才能⁨⁨`bash start.sh`⁩⁩
- ⁨⁨`chmod +x (文件名)`⁩⁩: 给某个文件赋予执行权限，bash xxxx.sh的时候发现没权限可以用这个先给一下。
- ⁨⁨`git pull`⁩⁩：用于更新酒馆，必须先进入酒馆目录，记得备份数据。备份教程下面有。
- ⁨⁨`git checkout （版本号）`⁩⁩：用于切换酒馆版本，必须先进入酒馆目录。记得备份数据。
- ⁨⁨`nano （文件名）`⁩⁩：编辑某个文本文件，比如酒馆的config.yaml，或者配置自动启动的.bashrc。有mt管理器的话用mt管理器，比nano好用，不过mt不能编辑.bashrc

看不懂以上也没关系，以后问AI就行。
再输入这一串：⁨⁨`nano ~/.bashrc`⁩⁩，在里面加入这几行：
⁨⁨
> #Update Termux packages
> alias pkgup="pkg update && pkg upgrade"
> #Start SillyTavern
> alias st='cd ~/SillyTavern && bash start.sh'
> #Update SillyTavern
> alias stup='cd ~/SillyTavern && git pull --rebase --autostash'



然后按ctrl+o，y，回车，ctrl+x。ctrl需要用手机键盘上方，termux那个ctrl。
这样以后启动termux的时候，只需要输入st，按回车，就是启动酒馆了；stup就是更新酒馆。

由于安卓系统会限制后台应用，而你在切换到打开酒馆的浏览器时，实际运行着酒馆的Termux就成了后台应用，所以会被限制，然后出各种问题（比如进不去酒馆，一直出settings could not be saved等）。一个比较通用的解决方法是**把Termux挂小窗**，具体方法每个手机系统不同需要自行搜索。如果还是出问题进不去酒馆之类的，可以先清一下浏览器缓存，再换个浏览器尝试能不能解决。



## 云酒馆
原作者：FoX | 𝓚𝓚𝓣𝓼𝓝(橘狐)
（这部分道馆考试题里没有，觉得自己不需要的可以跳过。）

云酒馆指的是把酒馆架在VPS（一种24小时跑着的服务器）上，然后从各种设备连到VPS去玩。优点是方便，任何设备只要能开网页就能玩，开酒馆和开个视频网站差不多快，以及真正意义上的多端同步。缺点是折腾一点，然后买VPS要花钱。

橘狐并不玩云酒馆，所以橘狐这里简单放几个教程链接，不過我1009mc覺得下面都挺不錯的，都可以去看看：
比较全的教程，从买VPS到打开酒馆和其他配置都有 by ChiefX：[「白中白」VPS云酒馆搭建](https://discord.com/channels/1134557553011998840/1401772231142674522/1401772231142674522)

两个我认为云酒馆必装的插件，by GG：
1.[ST-Manual-Saver](https://discord.com/channels/1134557553011998840/1425889068637622373/1425889068637622373) 取消自带的自动保存聊天记录，改为手动保存，极大节省云酒馆流量消耗
2.[ST-Frontend-Tokenizer](https://discord.com/channels/1134557553011998840/1420468922943143987/1420468922943143987) 解决云酒馆消息发送速度慢
或者直接查看<a href="/智识库/sandbox/粉色妖精小姐～♪/1Panel部署云酒馆教程" class="is-internal-link is-valid-page">1Panel部署云酒馆教程</a>

更简单的一键部署酒馆脚本 by 苏糖：[vps云酒馆交互式苏小糖搭建版本管理脚本](https://discord.com/channels/1134557553011998840/1464885372663369739/1464885372663369739)

# 备份与更新酒馆

**定期备份是好习惯，尤其对酒馆来说。**

对于就自己一个人用的本地酒馆，值得备份的只有酒馆根目录下的⁨⁨⁨`data\default-user`⁩⁩⁩这个目录，还有⁨⁨⁨`config.yaml`⁩⁩⁩。准确说是里面的以下文件或文件夹：

- characters （角色卡）
- chats （聊天记录）
- extensions （选择为自己安装的扩展）
- OpenAI settings （预设）
- themes （美化）
- User Avatars （用户头像，没传过不用备份）
- worlds （世界书）
- groups (如果玩过酒馆自带哪个群聊)
- settings.json （设置和正则）
- secrets.json （密钥）
- stats.json （角色卡相关的统计信息）

直接备份整个⁨⁨⁨`data`⁩⁩⁩也是可以的，但是不要备份⁨⁨⁨`backups`⁩⁩⁩文件夹，这个文件夹本身就是聊天记录和settings.json的备份，而且体积经常很大。如果插件扩展不在data\default-user/exntensions 那就是因爲安裝時選擇了for all

- ⁨for you 的插件在 `SillyTavern/data/default-user/exntensions/`⁩
- for all 的插件在 ⁨`SillyTavern/public/scripts/extensions/third-party/`⁩

对于Windows用户，直接把以上文件夹复制一份到其他目录就可以了
安卓用户则稍微麻烦一点，可以看这个教程：[酒馆喂饭级备份与恢复聊天扩展数据](https://discord.com/channels/1134557553011998840/1327980841497788457/1327980841497788457)


**不要随便更新酒馆。只有当你明确知道某个你需要的功能必须更新才有，或者某个问题必须更新才能解决，并且做好备份的情况下，才可以更新酒馆。**

更新的方法倒是非常简单：

- 对于Windows Git安装，直接使用酒馆根目录下的⁨⁨`UpdateAndStart.bat`⁩⁩即可，会更新到最新版。
- 对于Windows 压缩包安装，如前文所述，无法一键更新。
- 安卓一键脚本安装，使用一键脚本里的更新功能。
- 安卓Git安装，先⁨⁨`cd SillyTavern`⁩⁩到酒馆目录，再⁨⁨`git pull `⁩⁩。

如果想更新到指定版本，可以先进酒馆目录，然后⁨`git checkout 版本号`⁩，比如⁨`git checkout 1.13.4`⁩.  注意这样切版本以后无法再直接git pull更新版本，需要先⁨`git checkout release`⁩。


# 酒馆初始设置

刚装的酒馆有很多地方需要调整，这里我们一边认识酒馆的按钮一边调。

第一次启动的时候会让选语言和设定user名称。这两个稍后都可以再调，直接保存即可。
![snipaste_2026-02-01_19-41-11.png](/all_upload_files_should_in_here/sandbox_area/1009/snipaste_2026-02-01_19-41-11.png)
进来以后，首先看上面一排按钮，从左往右数。第一个，看起来像三个滑条的，是预设 preset。打开会发现这里是什么kobold预设，是用不了的，稍后改。
![snipaste_2026-02-01_19-43-13.png](/all_upload_files_should_in_here/sandbox_area/1009/snipaste_2026-02-01_19-43-13.png)
然后是第二个按钮，长的像个插头，这是API连接设置，因为长得像插头就叫插头了。当有人说'看看插头'的时候，意思是让你点开这个然后截图发出来。

![snipaste_2026-02-01_19-44-45.png](/all_upload_files_should_in_here/sandbox_area/1009/snipaste_2026-02-01_19-44-45.png)
这里默认是AI Horde，类脑玩的都是谷歌Gemini，A社Claude等在线的聊天补全API，所以要点API的下拉选单，换成聊天补全（不是文本补全！），下面的提示词后处理选择'合并相同角色连续的发言'。
![snipaste_2026-02-01_19-45-40.png](/all_upload_files_should_in_here/sandbox_area/1009/snipaste_2026-02-01_19-45-40.png)


注意有些预设或插件会特别要求提示词后处理选择别的，这时候选它们要求的那个就行。

改完插头，再回去看预设，它已经变成'聊天补全预设'了，熟悉的样子。不过这个自带的default预设根本用不了，在实际和ai聊天之前，记得先去社区里找个预设用。

绿色锁链按钮是将预设和插头配置绑定，实际并不方便还容易捣乱，建议点成灰色的，这样就不绑定了。
![snipaste_2026-02-01_19-47-05.png](/all_upload_files_should_in_here/sandbox_area/1009/snipaste_2026-02-01_19-47-05.png)


接下来我们点开从左往右第三个按钮，这是世界书。酒馆默认的世界书设置需要改一下，如图：
![snipaste_2026-02-01_19-49-26.png](/all_upload_files_should_in_here/sandbox_area/1009/snipaste_2026-02-01_19-49-26.png)
- 上下文百分比改为100
- 包括名称和匹配整个单词取消勾选


第四个按钮是用户设置，为了和user设置区分，这个我们简称设置。点开，这里要调整的比较多，如图：
![snipaste_2026-02-01_19-53-27.png](/all_upload_files_should_in_here/sandbox_area/1009/snipaste_2026-02-01_19-53-27.png)
第五个是背景设置，可以给酒馆换背景图片。
![fce99036c240271a.png](/all_upload_files_should_in_here/sandbox_area/1009/fce99036c240271a.png)


第六个是扩展，以后导入正则，装插件调插件都在这里。
![snipaste_2026-02-01_19-55-03.png](/all_upload_files_should_in_here/sandbox_area/1009/snipaste_2026-02-01_19-55-03.png)

第七个就是user设置了，为了和用户设置区分，这个简称user。
![snipaste_2026-02-01_19-55-33.png](/all_upload_files_should_in_here/sandbox_area/1009/snipaste_2026-02-01_19-55-33.png)


最后一个是角色卡，可以在这里切换或者管理不同的角色卡。
![snipaste_2026-02-01_19-55-48.png](/all_upload_files_should_in_here/sandbox_area/1009/snipaste_2026-02-01_19-55-48.png)
（如果你装的是某种魔改版的压缩包酒馆，上面可能会多一个两条杠，打开是什么表格的按钮，这是内置了一个类脑的表格插件进去。不建议用这种酒馆）

## 酒馆网络相关配置

由于酒馆的流量默认也不会走代理，所以可能会明明开了梯子的系统代理，酒馆还是连不上Google或A社等境外服务。这个问题仅限PC酒馆，手机酒馆没有。

这里提供3种解决方法：

1. 开启梯子的TUN模式。同上，请自行搜索你用的那款梯子怎么开。
2. 为酒馆配置代理。
  - 首先打开酒馆根目录下的config.yaml。推荐用VSCode或者至少NotePad3打开，不要用windows自带那个记事本。
  - 找到以下内容：
⁨⁨
``` 
# -- REQUEST PROXY CONFIGURATION --
   requestProxy:
# If a proxy is enabled, all outgoing HTTP/HTTPS requests will be routed through it.
   enabled: false
# Proxy URL. Possible protocols: http, https, socks, socks5, socks4, pac
   url: "socks5://username:password@example.com:1080"
# Proxy bypass list. Requests to these hosts won't be routed through the proxy.
   bypass:
     - localhost
     - 127.0.0.1
{.is-info}
```


（这里我假设读者没有自己改过这个文件，或者下的是什么魔改酒馆已经改过它了。）
（一些版本的酒馆没有那些井号后面的英语注释内容，不过也没关系。）

首先你需要知道自己梯子的端口，在上文给git配置代理的地方已经写过了。然后将：
- ⁨⁨`enabled: false`⁩⁩ 改成 ⁨⁨`enabled: true`⁩⁩
- ⁨⁨`url:`⁩⁩ 后面那一串，引号里的内容改成⁨⁨`socks5://127.0.0.1:梯子端口`⁩⁩。引号不要丢
- ⁨⁨`bypass`⁩⁩ 不动，这里是访问某些域名时不使用代理，如果读者懂的话可以自行编辑

![snipaste_2026-02-01_19-58-33.png](/all_upload_files_should_in_here/sandbox_area/1009/snipaste_2026-02-01_19-58-33.png)3. 自己建一个中转站。其实不难，而且免费。不过限于篇幅这里不做详细介绍了，感兴趣的朋友可以到教程区自行搜索。


## 其他config.yaml的修改
除了上文提到的代理，我还建议读者对默认的⁨⁨`config.yaml`⁩⁩做以下修改：


```
# Server port
port: 8000
```


这意味着酒馆会在本地8000端口上打开，即你需要在浏览器里打开⁨⁨`127.0.0.1:8000`⁩⁩。但是8000是一个很容易冲突的端口，你可以把它改成8123之类没那么规律的，这样不容易冲突。

```
backups:
  # Common settings for all backup types
  common:
    # Number of backups to keep for each chat and settings file
    numberOfBackups: 50
```

酒馆默认会为每个聊天保存最多50个备份，太多了，而且现在一些扩展会导致聊天记录变得很大，大量备份很快就会把你设备的储存空间占满。改成3就行了。

```
performance:
  # Enables lazy loading of character cards. Improves performances with large card libraries.
  # May have compatibility issues with some extensions.
  lazyLoadCharacters: false
```

把lazyLoadCharacters改成true应该可以让酒馆启动的时候变快一些。

---

**重要，前面的都可以不改，这段一定要改**

搜索`hostWhitelist`，找到这部分：

```
hostWhitelist:
  enabled: false
  scan: true
  hosts: []
```
这里分成两种情况，如果你只在本地设备上玩，没有远程连到酒馆的需求，把这段改成这样（用下面这个框里的覆盖上面那段，注意缩进）

```
hostWhitelist:
  enabled: true
  scan: true
  hosts:
    - localhost
    - 127.0.0.1
    - "[::1]"
```


如果酒馆是服务器上的云酒馆，或者其他需要通过公网远程访问的情况，用这一段：
```
hostWhitelist:
  enabled: true
  scan: true
  hosts:
    - localhost
    - 127.0.0.1
    - "[::1]"
    - "你的公网IP"      # 例如: 123.45.67.89
    - "你的域名"        # 例如: 我的云酒馆.com (不要带 http://)
```



云酒馆/通过公网远程连接的，再搜索`basicAuthMode`，找到：
```
basicAuthMode: false
basicAuthUser:
  username: "user"
  password: "password"
```

改成：
```
basicAuthMode: true    # 开启登录验证
basicAuthUser:
  username: "你的用户名"
  password: "你的强密码"
```
总之，只在本地玩的改一处，有远程需要的改两处。
这是为了解决酒馆的一个安全漏洞。如果不改以上内容，攻击者可以通过恶意链接获得和你本人相同的权限，能随便篡改，偷取或者删除你酒馆里的任何东西。不要有侥幸心理（比如'我从来不点那种可疑的链接'），一定要改！！
限于篇幅这里介绍的比较简略，不知道怎么改或者改完进不去酒馆了可以问AI。

## 欲知后事如何...

至此，你已经跟着本教程独立地安装好了酒馆SillyTavern，并调整好了所有基础配置，离和AI聊上第一句已经非常非常近了！

限于篇幅，我把获取API的教程都放在下一个基础道馆里，因为这篇教程相对于其他基础道馆教程已经很长了。稍后见！🦊