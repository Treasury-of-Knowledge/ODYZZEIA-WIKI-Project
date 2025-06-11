---
title: 立绘差分与游戏界面-制作自己的酒馆Galgame的立绘插图！
description: 非常简单的喵
published: true
date: 2025-04-03T19:11:27.480Z
tags: 
editor: markdown
dateCreated: 2025-04-03T16:36:15.908Z
---


# 立绘差分与游戏界面-如何制作自己的酒馆Galgame

这篇教程会通过一个例子来教你使用AI画图来制作人物立绘与表情动作差分
并作为游戏的插图/状态栏，或者使用完整的Galgame界面

<big>PC端图片过小，鼠标长按图片可以放大</big>
或者右键复制图片链接，也可以前往[GitGud库](https://gitgud.io/lolodesu/lolobabytutorial/-/tree/master/教程附件/Forge教程?ref_type=heads)中查看

目录没啥用，可以跳过去喵

```txt
📚 立绘差分与游戏界面-如何制作自己的酒馆Galgame 🎭
│
├── 🛠️ 下载软件喵
│   ├── 🖼️ SD-forge
│   └── 🎨 Photoshop（也许可选？)
│
├── 🔮 Forge怎么用喵？！
│   ├── 💾 模型与LORA
│   ├── 🔌 安装Forge扩展
│   │   ├── 🈶 汉化界面
│   │   ├── 🔤 管理与翻译提示词
│   │   ├── 🖼️ 历史图库
│   │   └── 🖇️ 分区提示词couple
│   │
│   ├── ⚙️ 调整Forge设置
│   ├── ✏️ 填入立绘提示词
│   │   ├── 👍 正向提示词
│   │   └── 👎 负向提示词
│   │
│   └── 🌟 示例
│       └── 🧪 生成第一张立绘
│
├── 😊 表情差分
│   ├── ⚙️ 重绘设置解释
│   └── 🧮 示例
│       ├── 😠 生气表情制作
│       └── 🛠️ 错误修复技巧
│       └── 👕 给角色的衣柜增添新衣！
│
├── 🤸 简单动作差分
│   ├── 😢 擦眼泪动作示例
│   ├── 👕 换衣服技巧
│   └── 🎭 PS换脸与抠图教程
│
└── 🎉 结语:完结撒花
```

## 下载软件喵

我在制作这些立绘的时候只用到了

- SD-forge
- photoshop

其中，SD-forge可以在某视频平台上找到简单的一键安装包，非常易部署（请注意不要下载成sd-webui）
而Photoshop也是非常容易获取的，这里就不赘述了

## Forge怎么用──

虽然comfyui其实并不难并且很强大，Forge的后端就是comfyui，但是个人感觉Forge更容易让不熟悉工作流的小白们（比如我w）更加容易上手，而且用起来和Nai也差不多

首先说明的是，这个教程只保证你使用和我一样的画风（模型、LORA与画风提示词）时，能够跑出相对完美的效果

事实上，你仔细看可以看出我的立绘是非常偏向Flat color这种风格的，人物整体很少有反光，如果你的模型或Lora很注重人物皮肤或服饰的反光效果，使用这个方法跑的立绘大概会在人物身上有很多背景的反光（比如使用绿幕会出现绿色的反光）我个人也不知道有什么比较好的方法也没有尝试过寻找，如果你确实需要可以自行尝试看更换提示词，增加负面提示词或者其他LORA来规避这个现象

### 模型与LORA：让我们确定画风？

首先我们需要准备模型与LORA

- 模型：[waiNSFWIllustrious_v130.safetensors](https://civitai.com/models/827184/wai-nsfw-illustrious-sdxl)
- LORA：[<wan_flat_color_1.3b_v2.1>](https://civitai.com/models/1132089/flat-color-style)
  实际上……这是一个视频模型，他是有针对illustrious的lora？但是经过个人测试后，使用这个lora跑的立绘效果过于flat了，所以……我仍然以错误的方法使用这个1.3b的针对视频生成的LORA

将下载下来的两个.safetensors文件分别放在models/Stable-diffusion文件夹下和models/LORA文件夹下

### 安装Forge扩展：好物安利时间

这里顺便推荐一些Fogre用的扩展,

- 汉化界面: `https://github.com/hanamizuki-ai/stable-diffusion-webui-localization-zh_Hans`
- 管理与翻译提示词: `https://github.com/Physton/sd-webui-prompt-all-in-one`
- 历史图库: `https://github.com/zanllp/sd-webui-infinite-image-browsing`
- 分区提示词couple: `https://github.com/Haoming02/sd-forge-couple`

在上方Txt2img同级的选项卡中有一个扩展选项卡，点击之后，选择从网址安装，输入上方链接就可以安装
注意：安装后可能需要重载UI/重启

注：我已经尝试过sd-forge-layerdiffuse，但是效果并不理想，这个扩展更适合画透明的物体而非为动漫角色去掉背景，如果你有更好的方法可以告诉我，谢谢哦

![安装扩展](https://gitgud.io/lolodesu/lolobabytutorial/-/raw/master/教程附件/Forge教程/2安装扩展.png)

### 调整Forge设置：预备运动──

准备工作进行之后，我们来调整设置！

```txt
左上角UI：设置为全部
```

模型点击刷新后选择我们刚安装的waiNSFWillustrious13

```txt
CLIP终止层数：2
```

下方生成选项卡：

```txt
采样方法：Euler a
调度类型：Karras
迭代步数：我个人偏好28
分辨率：1024x1536
（如果想完美适配我的galgame界面，使用这个分辨率最好啦，我没测试过其他分辨率会怎么样）
Distilled CFG Scale：3.5
提示词引导系数（CFG Scale）：4.5
随机数种子：-1
（-1为随机，如果一直出相同的图大概是这里的问题哦）
```

在这个和生成相同级别的选项卡中有一个lora选项卡
（我真的很想问SD为什么把lora放在这里）

点击右侧的刷新按钮，可以到我们刚刚安装的lora，点击后提示词上会多出：
<lora:wan_flat_color_1.3b_v2.1:1>
这代表你的LORA也成功使用上啦

请查看！界面设置：
<https://gitgud.io/lolodesu/lolobabytutorial/-/raw/master/教程附件/Forge教程/1主界面设置.png>
![主界面设置](https://gitgud.io/lolodesu/lolobabytutorial/-/raw/master/教程附件/Forge教程/1主界面设置.png)

### 填入立绘提示词：画画

调整好了重点设置（或者按照你的喜好也许也行？），直接开始输入生成立绘的提示词！

#### 正向

```txt
<lora:wan_flat_color_1.3b_v2:1>,flat color,no lineart,very awa,masterpiece,best quality,year 2024,newest,highres,absurdres,
在这里填入你的人物与服装提示词
solo,(upper body),cowboy shot,standing,((green background)),((green screen)),simple background,(((tachi-e))),((((facing viewer)))),light smile,eye contact,looking at viewer,
```

上方的是我的画风串！最下方是生成立绘所使用的提示词！

#### 负向

```txt
nsfw,bad feet,missing toes,extra toes,lowres,bad anatomy,bad hands,text,error,missing fingers,extra digit,fewer digits,cropped,worst quality,low quality,normal quality,jpeg artifacts,signature,watermark,username,blurry,4-koma,sketch,(bad:1.05),error,fewer,extra,missing,worst quality,jpeg artifacts,bad quality,watermark,unfinished,displeasing,chromatic aberration,signature,extra digits,artistic error,username,scan,abstract,(blurry, lowres, low quality:1.1),ugly,(big head, bad anatomy:1.05),artist name,(watermark:1.1),bar censor,
```

负面应该都差不多……?如果你需要生成色色的内容，就把nsfw去掉并放到正向第一个喔

### 示例：我来画一个

人物与服装呢可以使用你自己已经有的，没有的话……可以去TAG仓库里自己搭配，或者如果你有很喜欢的一些元素但不知道是什么TAG，可以使用WD1.4标签器，上传你的图片并进行反推，看看其中的TAG都是什么
如果你随机跑图跑出了喜欢的角色或服装，但不知道对应的TAG，也可以使用WD1.4标签器来反推！
我这次案例中的人物串是这个：

```txt
1girl,loli,aged up,animal ears,brown hair,streaked hair,multicolored hair,pink hair,long hair,animal ear fluff,cat ears,red eyes,bangs,pink eyes,
ribbon-trimmed clothes,pink bandaid,brown hooded cape,hood,hair ornament,hoodie,sleeves past wrists,hood up,long sleeves,hairclip,sleeves past fingers,bare legs,
```

所以我的正向提示词：

```txt
<lora:wan_flat_color_1.3b_v2:1>,flat color,no lineart,very awa,masterpiece,best quality,year 2024,newest,highres,absurdres,
1girl,loli,aged up,animal ears,brown hair,streaked hair,multicolored hair,pink hair,long hair,animal ear fluff,cat ears,red eyes,bangs,pink eyes,
ribbon-trimmed clothes,pink bandaid,brown hooded cape,hood,hair ornament,hoodie,sleeves past wrists,hood up,long sleeves,hairclip,sleeves past fingers,bare legs,
solo,(upper body),cowboy shot,standing,((green background)),((green screen)),simple background,(((tachi-e))),((((facing viewer)))),light smile,eye contact,looking at viewer,
```

<small>是的其实这是一个vtuber（）</small>

万事俱备，点击生成吧！

<big>生成！</big>

![立绘](https://gitgud.io/lolodesu/lolobabytutorial/-/raw/master/教程附件/Forge教程/3立绘.png)

像这样就还不错呢！如果是这张图的话，似乎完全没必要使用photoshop，直接使用forge内置的大模型抠图，或者使用在线大模型，应该就可以扣完整，让我试试看

点击上方SPACE按钮，选择IMAGE Processing,安装，Launch，上传图片，Remove Background

超级完美——

![透明立绘](https://gitgud.io/lolodesu/lolobabytutorial/-/raw/master/教程附件/Forge教程/4透明立绘.png)

这样我们获得了我们的第一张立绘！

请注意，你的立绘应该避免以下问题：

- 四周被截断，如左右两侧显示不全，顶部没有显示完整等，这样放进背景里真的很难看，答应我不要这样做
- 身体错误的反射了来自背景的光，比如，大腿上有绿色的反光……后果会怎么样相比你也知道
- 身体动作幅度很大，没有站立姿势，或者头很歪（适当倾斜是正常的），就算看起来不错，但是做出立绘这样真的很难看……

有了完美的立绘已经是最好的开始了，但是一个游戏肯定要有不同的表情动作，甚至这个角色还需要穿其他衣服
现在，让我们来开始图生图重绘！

## 表情差分

在你刚刚的带着绿幕立绘下方，有一个画板按钮：发送到局部重绘，请点击！

![重绘](https://gitgud.io/lolodesu/lolobabytutorial/-/raw/master/教程附件/Forge教程/5重绘.png)

来到这边后，可以发现我们的提示词和设置都是正确的，如果你的不行……请手动调整一下吧！

### 重绘设置解释

我来简单介绍一下重绘中你需要知道的按钮意义（没提到的可以不用管）

蒙版边缘模糊度：想象一下PS的画笔，有的画笔非常锐利，写上去多少就是多少，而有的画笔呢是朦胧的带着一些模糊边缘，实际上的笔迹并不会完全填满整个画笔光标指示器，这里也同理！如果这个值太高，可能需要你多往外扩展的画一些，如果太太低，可能重绘的边缘会和原图的边缘分离并不连贯，所以需要根据你的需求调整

重绘蒙版内容/重绘非蒙版内容：重绘你画笔画到的区域，重绘的画笔画到**以外**的区域

**你可能需要大致理解大模型画画的原理**
它并不是和人类一样一笔一笔画，而是先将图片整个铺上许多噪点，然后根据你的提示词，将这些噪点逐渐降噪选择确定的颜色，保留出符合提示词的那些颜色像素，慢慢的变成了最终的图片

重绘区域：

- 整张图片：直接将整张图片铺上噪点，然后最终只保留你画笔画到的区域
- 仅蒙版区域：只在你画笔周围的区域（是个矩形）铺上和整张图片相同数量的噪点，然后最终只保留你画笔画到的区域

有什么区别？选择整张图片，重绘出来的图片更加连贯丝滑。而仅蒙版区域，重绘的区域会更加具有细节
如果你是希望更换表情，那我们应该选择整张图片，如果你是类似于人物占比太小导致脸部细节过少的场景，选择仅蒙版区域

- 重绘幅度：最重要！影响了铺噪点数量的多少，如果调高铺的高，大模型可能更少看清原来的画面是什么样，如果铺得少，大模型能改动的就很少。一会我会告诉你我是怎样选择的，通常来说这个没有什么固定的设置

### 示例

首先呢，对于这个立绘，她现在笑眯眯的，其实就很适合作为默认或者通常之类的立绘
但是我们可能还会需要类似于：愤怒、悲伤、哭泣、害羞等。并且我也建议你分为不同的如：愠怒、生气到极点、难过、悲伤、哭泣、大哭、微微脸红、害羞、害羞到捂脸等，画出相同情绪但不同程度的立绘，这也许会增加你的工作量？总之请以你个人需求为准啦

我们先来画一个愤怒的立绘！

直接这样用画笔将脸部盖住，不需要画的过于精细，但是你可以看到我的角色有一个发卡，我不希望换表情这个发卡也会变掉，所以我把他让了出来

![表情差分](https://gitgud.io/lolodesu/lolobabytutorial/-/raw/master/教程附件/Forge教程/6表情差分.png)

然后再正向提示词找个位置（我习惯于再末尾）增加表情的提示词：anger。我原本角色串中有个light simle，让我把他删掉……
并使用括号来为其增加权重，(((anger)))

我的设置是：

```txt
模糊度：17
蒙版模式：重绘蒙版内容
蒙版区域内容处理：原版
整张图片
**重绘幅度：65**
（如果你的表情没能重绘出来变化不大，请拉高.如果变化太大导致画面崩坏，稍微降低一点）
（另外，重绘出现少量的错误是允许的，之后我告诉你怎样修理！）
**勾选柔和重绘**
```

生成！

![愤怒差分](https://gitgud.io/lolodesu/lolobabytutorial/-/raw/master/教程附件/Forge教程/7愤怒差分.png)

生气的小猫也可爱捏
但是……你有注意到吗？我们仔细看的话脸部尤其是发卡附近，能看到有一些些绘画错误。如果你的要求不太高，或者说觉得这些无伤大雅，已经可以切换TAG来画下一张了，但是我的要求比较高……并且教程会需要，所以我告诉你如何修复这些问题？

答案就是：发送到重绘，扩大画笔，降低重绘幅度

直接就是一个大圆盖住脸（）

![修复](https://gitgud.io/lolodesu/lolobabytutorial/-/raw/master/教程附件/Forge教程/9修复.png)

然后，我将重绘幅度调整成了0.35，生成！

![修复后](https://gitgud.io/lolodesu/lolobabytutorial/-/raw/master/教程附件/Forge教程/10修复后.png)

呃、可以看到，修复后的图和原图相比，几乎没有区别，但是错误的地方更少了，并且看不出来有不连贯的地方
（但是我的例图由于第一次重绘的有些完美，导致效果不大，如果你的立绘重绘出现了一些错误并且通过调整重绘幅度无法解决，可以这样尝试。）

这就是表情差分的全部啦，是不是还挺简单的？是的，我尝试了很多方法，包括controlnet等，但是说实话，都不如这个方法简单好用。根据你的电脑，只需要最多几次按钮就可以获得一张很完美可用的表情差分立绘
（喂！可不要想着用这个方法来做Galgame圈钱哦——）

但是只是表情变化，情绪显得不是很足够呢……可以做到动作上也有变化吗？
可以的兄弟！

## 简单动作差分

事实上对于立绘来说，动作最好不需要太大，我个人的选择是只有比猫爪来表现生气，以及抬手擦眼泪
比猫爪生气说实话还蛮简单的，但是抬手擦眼泪……稍微难一点对吧？
我尝试了包括线稿、软边缘、姿势的controlnet，发现还是roll图最简单好用（目移）
所以为了避免增加额外的麻烦，我不会提供controlnet的姿势图以及教你怎么用，你真的需要学的话可以自己查看文档，并不难哦

那么，我是怎么画出类似这样的动作呢？

![擦眼泪](https://gitgud.io/lolodesu/lolobabytutorial/-/raw/master/教程附件/Forge教程/11擦眼泪.png)

其、其实和重绘表情一样简单直接（目移）

先、先修改提示词吧，

我把anger换成了这些`((((crying)))),(((((wiping tears))))),((((covering own eyes)))),(((hand up))),((((wiping face)))),`,是的，可以看到权重给的蛮夸张的
并且又没人规定表情必须用一个词，你也可以做用light smile和anger一起用，弄出一个又生气又笑的表情啦

但是，重绘只画脸肯定是不行了，怎么办呢……？把、把手也一起画上！

![重绘擦眼泪笔刷](https://gitgud.io/lolodesu/lolobabytutorial/-/raw/master/教程附件/Forge教程/12重绘擦眼泪笔刷.png)

可以看到，由于又蒙版边缘模糊度与柔和重绘，你需要和我一样画的范围尽量大点
而且你也不知道最终这个手会什么姿势……所以画大点更不容易再蒙版边缘之外啦

我也不确定重绘幅度多少比较好，我们试试看0.65

![错误生图](https://gitgud.io/lolodesu/lolobabytutorial/-/raw/master/教程附件/Forge教程/13错误生图.png)

呜哇……看起来，我们重绘幅度稍微小了一点呢？

而且，我在提示词上写了cape，但是实际上人物并没有用到……

偷偷把cape删了（）  

而且我忘记了腿上的创可贴，导致他消失了一点！

现在让我们把画笔让出关键的部分，然后稍微拉高点重绘幅度试试看

![重新调整](https://gitgud.io/lolodesu/lolobabytutorial/-/raw/master/教程附件/Forge教程/14重新调整.png)

```txt
重绘幅度:0.7
```

<big>[图：没画对，懒得放]</big>

呃、这一张图片她选择举起了右手，这和我们重绘区域不太符合，导致一只手悬浮的飘着，也算正常现象，所以……重ROLL
注：你也可以选择告诉模型抬起哪只手，但是我发现大模型搞不清对于人物的左右和对于镜头的左右，所以我选择不告诉他然后重ROLL到合适的……

你可以在总批次数那里选择如4之类的数字来一次出4张图

跑了大概12张（也就是3轮4张图）
我最终的重绘幅度增加到了0.85，你们也可以拿这个数值做参考呢

我最终的选图是这张

![最终选图](https://gitgud.io/lolodesu/lolobabytutorial/-/raw/master/教程附件/Forge教程/15最终选图.png)

呃、错误还挺多的是不啦w，记得应该怎么办吗（）

**发送到重绘，低重绘幅度，启动**

（记得调回生成一张图而不是四张x）

![最终修复](https://gitgud.io/lolodesu/lolobabytutorial/-/raw/master/教程附件/Forge教程/16最终修复.png)

完美！
什么？你说头发穿模了？
呃……也、也许后边的衣服是开口的头发可以穿出来（胡言乱语）

是的这是因为长发tag干扰到了，我们应该删掉长发tag，但是我是PS高手我会把这段PS掉（）

教程到这里就90了，我还没有讲的是如何为她换衣服和用PS抠图

## 增添衣柜

换衣服……若想简单点，则不得不用PS了呢

大概原理是：

```txt
重绘覆盖住脸部后，选择重绘非蒙版区域，更换服装TAG，生成
这样你会得到一张面部和面前头发相同，但服装变换了的立绘
之后我们把两张png扔到PS里，将新服装的图层放到旧服装的上边，然后用橡皮擦擦掉脸部露出下方原来的脸部表情（）
仔细用鼠标擦掉表情后，最后得到一张看起来完美的换衣后立绘
之后将之前所有表情的PNG都丢进来，用图层显示按钮(小眼睛)切换图层来更换不同表情并导出为PNG（也可以录制动作批量导出）
```

让我们来实操吧……（好想偷懒！）

![重绘换衣服](https://gitgud.io/lolodesu/lolobabytutorial/-/raw/master/教程附件/Forge教程/17重绘换衣服.png)

注意，尽可能的覆盖脸部和脸部周围的头发（但是不要覆盖到可能换衣的部分，比如帽子、围巾等）

更换服装提示词，我换成了school uniform

```txt
重绘幅度:0.8
**重绘非蒙版区域**
```

生成！

![换衣服成功](https://gitgud.io/lolodesu/lolobabytutorial/-/raw/master/教程附件/Forge教程/18换衣服成功.png)

啊哇，因为原来兜帽的原因，导致头发那里光影不对啦！
发送到重绘，勾画出错的地方，重绘区域：整张图片，重绘幅度:0.5

修复！

注意！千万要检查你修复好还有没有其他区域有错误————
常见错误的区域可能有头发边缘、脖子下巴之类的地方

可以分多次修复，也就是修复之后发现还有问题，发送到重绘，然后继续勾画修复的地方

![换衣服修复](https://gitgud.io/lolodesu/lolobabytutorial/-/raw/master/教程附件/Forge教程/19换衣服修复.png)

完美捏！

如果……你实在用不了PS的话，其实可以费力一点就和之前一样，继续用AI画表情差分

但是如果你安装了PS就可以继续看！接下来我先说如何换脸，最后会说如何抠图
（事实上这张图大模型抠图的效果就不好了……留出了绿色的背景）

## 超简单PS教程x

首先是换脸。将图片导入PS

接下来选择图层，将我们的新衣服放在上边，之前的表情放在下边

接着，我们使用橡皮擦工具，将脸部擦除露出下方不一样的表情

请细致一些，这个操作只需要进行一次，之后就只需要点击眼睛切换图层来更换表情并导出了

请看换脸视频

<video controls>
 <source src="https://gitgud.io/lolodesu/lolobabytutorial/-/raw/master/教程附件/Forge教程/21换脸视频.mp4" type="video/mp4">
</video>

抱歉，视频中上方区域没有好好擦除干净，导致能看出一条分界线，使用橡皮擦再擦擦就好了

最终成品：

![PS后愤怒](https://gitgud.io/lolodesu/lolobabytutorial/-/raw/master/教程附件/Forge教程/20PS后愤怒.png)

你可以将这个脸部被擦除的图层保留（）虽然有些恐怖。但是可以很方便的更换表情！

我、我就不放图片了哦

[面部被扣掉的水手服立绘]

接下来，我教你如何抠图，这真的很简单只需要不到30s！

<video controls>
 <source src="https://gitgud.io/lolodesu/lolobabytutorial/-/raw/master/教程附件/Forge教程/23抠图视频.mp4" type="video/mp4">
</video>

![抠图后愤怒](https://gitgud.io/lolodesu/lolobabytutorial/-/raw/master/教程附件/Forge教程/24抠图后愤怒.png)

差不多只需要30s左右就能扣完呢，真的很简单——

可能时看到头发啊边缘之类的效果不太好，嗯……实际上如果你追求比较高，可以用**反向橡皮擦来勾线将其擦回来**

工作量也不算大，大概两分钟就能做完？鼠标画也可以呢，毕竟PS现在的平滑绘画还挺强大的！

反向橡皮擦就是点击橡皮擦后，上方勾选 ✅抹到历史记录

但是我认为只是用爱发电而已（）没必要做这么完美吧ww这个效果已经足够啦

请看，带有背景的效果：

![带背景](https://gitgud.io/lolodesu/lolobabytutorial/-/raw/master/教程附件/Forge教程/25带背景.png)

背景来自于一个免费可商用的网站

## 结语

好啦，你已经看完全部教程了，希望有帮到你！
如果你真的制作了带有立绘的卡，请务必at我让我也观摩一下qwq

完结撒花
