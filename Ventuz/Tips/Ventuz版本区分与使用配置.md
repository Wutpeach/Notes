## 前言

>  目前Ventuz有5个版本：社区版（COMMUNITY）、核心版（CORE）、企业版（ENTERPRISE）、学习版（PLE）、非售卖版（NFR）
>
>  >本文首发在@一起学习Ventuz 公众号，所以水印无法避免。

我们可以在官网查阅到社区、核心、企业，3个版本的横向比对，同时页面下拉，可以发现一段PLE版的描述文字官网查询

![img](https://mmbiz.qpic.cn/mmbiz_png/C9uohSLsicrgjBI9uOo9C0XY0SRickmQ9nNZoupicRBc3b5txK8xqDjjf8Lh5W844PBKEucgKiaFGCEPYHSgicDaZSA/640?wx_fmt=png)

![img](https://mmbiz.qpic.cn/mmbiz_png/C9uohSLsicrgjBI9uOo9C0XY0SRickmQ9naTqAYEBb30UicRARtn2KPWOP2kzibiaVTTLKVR8woWcnicJrgwWNibldqtw/640?wx_fmt=png)

> 原型开发和学习版提供了与企业工作室相同的功能集，仅用于评估目的。为了确保它不被用于商业项目，输出结果是有水印的。用PLE保存的文件不能加载到任何其他版本。

还有一个神秘的NFR(Not For Resale)版本，功能与社区版、学习版相同，且输出没有水印，但每次打开软件会跳出警告启动画面，提示你不能在任何商业或付费项目使用该版本。

## 版本区别与选择

|          | 社区版                          | 学习版                          | 核心版                                            | 企业版   |
| -------- | ------------------------------- | ------------------------------- | ------------------------------------------------- | -------- |
| 面向群体 | 个人                            | 个人                            | 中小型企业                                        | 大型企业 |
| 功能     | 部分功能缺失                    | 部分功能缺失                    | 部分功能缺失                                      | 功能完整 |
| 售价     | 免费(许可有效期30天,可重复申请) | 免费(许可有效期30天,可重复申请) | Runtime(播放器)990欧永久 / 主体+Runtime1990欧永久 | 商议     |

核心版的主要服务对象是中小型企业(不过我觉得这个售价对于中小企业来讲也是一个不小的支出)

在销售方案上，核心版已经满足大部分企业的使用需求，并且很贴心的把Runtime拎出来单独售卖，这一部分预算可以交由甲方爸爸承担。

社区版 / 学习版的功能体验上与核心版基本无异，只有极少的限制，对于个人用户来说，这2个版本是再好不过的选择了，接下来我就重点分析2个版本的差异。

![img](https://mmbiz.qpic.cn/mmbiz_png/C9uohSLsicrgjBI9uOo9C0XY0SRickmQ9ntaUMjUkyojaianrVA1SbnnQD29groGZHLpcs18p2K2tyoYB7AKJySug/640?wx_fmt=png)


| 社区版-COMMUNITY(推荐)                   | 说明                                                         |
| ---------------------------------------- | ------------------------------------------------------------ |
| 节点总数最大为500                        | 官方手册上说你如果超过这个限制，那么水印就会究极进化，变成双重水印 |
| 只能导入导出社区版的项目文件             | 假如你有个好哥们用核心版导出了项目文件给你，那你可打不开咯   |
| 多种水印样式供你选择                     | 没有跳来跳去的水印咯                                         |
| **社区版的文件可以在核心版、企业版打开** | 通过社区版导出，还可以在其他版本流通                         |

| 学习版-PLE(备用)                         | 说明                                                         |
| ---------------------------------------- | ------------------------------------------------------------ |
| 没有节点数限制                           | (这一点待考证，仅仅在官方文档中没有说明节点限制，咱们就认为是无限制使用吧) |
| 可以打开任意版本的文件                   | 核心版项目文件？拿来吧你！                                   |
| 更牛逼的浮动水印，在你眼前跳来跳去       | 究极进化水印，在屏幕内四处跳动                               |
| **从学习版导出的文件，别的版本都打不开** | 只要通过PLE导出，那就只能在PLE中流通了                       |

上面2张表是我列举的2个版本之间的主要区别，可以看到社区版与学习版比较重要的一点就是前者导出的文件可以任意流通，后者导出的文件被锁定在PLE中。

对于我们个人用户，以学习交流为主，所以项目文件的流通性很重要，如果连基本的文件都打不开，那还咋学习交流。因此我推荐使用社区版。

学习版虽然流通性差，但是可以打开任意版本（包括核心版）的文件，这一点比社区版强。

**所以我推荐各位在官网申请2个License,一个社区版一个学习版，交替使用**

> 社区版和学习版的切换可以通过License控制，所以不用纠结装了社区版没法打开核心、企业版的文件，咱换个License变成学习版又可以继续学习啦！
>
> > 注意：免费申请的License有30天时限，到期后可以再次申请。目前raydata开放了永久学习版的资格申请，有需要的可以自行申请

## Raydata学习版

Raydata是Ventuz的国内代理，目前官网有RAYDATA商业版、个人版、专业版。我们要选择商业版进行下载，因为后2个版本是光启元自行开发的可视化工具，用于多端交互。

这个商业版目前开放了永久免费申请，下载安装后用微信登陆，扫码领取资格，激活成功后就可以使用Raydata学习(PLE)版本了

| Raydat商业版（PLE）                                          |
| ------------------------------------------------------------ |
| **保留了原版PLE的所有特性**：飘忽不定的水印，可以打开任意版本文件.... |
| **汉化了大部分界面以及节点参数**                             |
| 增加了大量封装节点                                           |
| **支持微信登陆，许可证绑定个人微信账号**                     |
| 开发了一些黑科技辅助Raydata(不清楚是否支持Raydata学习版)     |

这张表格里列出了Raydata(PLE)的一些特性，比较有趣的就是界面汉化、License绑定个人微信。如果你是英语苦手，不如使用这个版本，可以降低学习门槛。

> Raydata和Ventuz不能共存，因为它们使用的是相同的服务进程，服务冲突的情况下，其中一款会崩溃。
>
> > VZA导入Raydata，只需要修改文件后缀为RDA即可(RDA不能修改成VZA导入Ventuz)

## 初始化设置

安装Ventuz后可以在电脑的程序列表中找到Configuration Editor。打开这个程序进行一些必要的设置。

中文文本、显卡/音频输出、画布设置

![img](https://mmbiz.qpic.cn/mmbiz_png/C9uohSLsicrgjBI9uOo9C0XY0SRickmQ9nuZRhaowek8oM8j77EEqGttT55WTcwLNXw9TJpYIgxShRxNkE6HfSBQ/640?wx_fmt=png)

### 中文文本

点击MultiTouch,Remoting4,Syste Culture后的加号，取一个喜欢的名字，咱开始设置中文文本。（如果想要在Ventuz里边打中文，那么这一步必不可少。）

![img](https://mmbiz.qpic.cn/mmbiz_png/C9uohSLsicrgjBI9uOo9C0XY0SRickmQ9nlTSicsvS3TpRJhsN6WF48w1fUmj02WLOicl35q9RNlT2pVgFu0IsLunQ/640?wx_fmt=png)

点击EXTENDED(扩展)，看到Culture Setting这一栏，按照下图进行勾选

![img](https://mmbiz.qpic.cn/mmbiz_png/C9uohSLsicrgjBI9uOo9C0XY0SRickmQ9nBXxstopboia5Hv8mCFoO3aLK5ye4oicuh01y6Kfja5OibSHDmjyLCNyaw/640?wx_fmt=png)

**2D Font:**高品质2D文本的质量是正常文本的2倍，对性能要求高一些。实际使用过程中，勾选与不勾选的差别不是很大，为了节省性能，我们取消勾选。

**Culture:**选择文本格式化的Culture，默认中文即可。

**Character Sets:**选择使用字体和字样时要使用的Unicode范围。具体如下：

![img](https://mmbiz.qpic.cn/mmbiz_png/C9uohSLsicrgjBI9uOo9C0XY0SRickmQ9nl7kQWEJf8kJdfUyaVL4H4tf6CY3MPjkRQMmMIeVYibZnn8oMVbo2Y2g/640?wx_fmt=png)

### 视频输出

1. 点击Audio,Video...后的加号，取个喜欢的名称，然后点击设置。

2. 默认停留在Video选项卡下，我们点击步骤1的[+Stream]，确认驱动为N卡(A卡)后点击OK确认 如果没有显示N/A卡，可以看'常见问题'下的解决方案

![img](https://mmbiz.qpic.cn/mmbiz_png/C9uohSLsicrgjBI9uOo9C0XY0SRickmQ9ntuAQPTS3DpJSCJ1mSxOAj66GbqyIw0p1CkScFpek1DtKolwicJCtgGw/640?wx_fmt=png)

3. 点开新建的Outputs选项卡，按照以下设置勾选

![img](https://mmbiz.qpic.cn/mmbiz_png/C9uohSLsicrgjBI9uOo9C0XY0SRickmQ9nbbHnJAiawyjOC2lUvLk7JPWvC4N0ibP2fzlFeFk8xJSSU4PdWwOTtWJg/640?wx_fmt=png)

4. 下拉框内指定了几个帧率选项，可以依据自己显示器的最高帧率选择，默认NONE会使用显示器(显卡)所设定的帧速率 

**A：Virtual Fullscreen(虚拟全屏) （勾选）** 

不勾选状态：显卡被锁定在Ventuz应用程序上，并提供最好的性能。如果另一个应用程序收到输入焦点，该应用程序将被最小化。因此，强烈建议禁用所有的后台进程（如防病毒软件或自动更新服务），因为它们可能在演示过程中窃取焦点，导致r应用最小化。

勾选状态：启用无边框全屏，这种类型通常在项目的设计阶段使用，因为它允许用户激活另一个应用程序（例如内容创建软件），并窃取输入焦点，而不必重新初始化渲染器。虚拟全屏保持在屏幕上，不会像独占型那样被最小化。这种模式的缺点是与独占式全屏相比，性能较低。 

**B：Show Mouse Pointer(显示鼠标指针)（勾选）**

 VPR中显示鼠标，推荐开启，方便调试。在现场如果没有接入鼠标，是不会显示鼠标指针的。 

**C：Swap Sync(同步交换)（关闭）**

 需要硬件支持，用于集群控制，个人使用无需开启。

 **D：Prevent D3D Queuing(阻止D3D排队)（勾选）**

 勾选后会强制显卡提前渲染一个单帧，又能降低交互延迟，使集群始终交换算法能够正常工作。启用这个选项将使整个渲染性能降低大约3-5%。（机器性能一般会过剩，过剩性能能够降低交互延迟，何乐而不为呢） 

**E：Frame Rate Multiplier（帧速率倍增器）**

 用于内部计算全局固定帧速率乘数（暂不作解释，默认即可）

### 音频输出

点开Audio选项卡，选择自己当前使用的音频输出设备（不清楚的可以点击任务栏的小喇叭看看是哪个设备）

![img](https://mmbiz.qpic.cn/mmbiz_png/C9uohSLsicrgjBI9uOo9C0XY0SRickmQ9nriblIe2EmC1v5G8YkfBS9DicyoMpiaia6tfIfByQC8BaOiajibyaicJ7DdA5A/640?wx_fmt=png)

### 画布设置

咱们简单点，理解为设计端的画布尺寸，我这里默认创建一个1920X1080

(这里依据你的需求设置，我这么设置是因为我的显示器尺寸是1920X1080)

![img](https://mmbiz.qpic.cn/mmbiz_png/C9uohSLsicrgjBI9uOo9C0XY0SRickmQ9nrwJSGjkq39pXclnCRFSMXyxU9VEBUylz5sQPdTicBHnRjoQmF6iaibumA/640?wx_fmt=png)

## 常见问题

### 为啥我的Configuration Editor无法编辑？
请确保Ventuz Designer/Ventuz Runtime程序处于关闭状态再进行调试

### 为啥每次关闭设计端，都会弹出Microsoft .NET Framework
C#的编译错误，不用管，没关系，不影响：)

### 显示设置里没有我的显卡怎么办？
关闭Configuration Editor --> 打开NVIDIA控制面板 --> 管理3D设置 --> 全局设置 --> 调用显卡 

### 软件有撤销键吗，有吗？有吗？
没有，因为Ventuz是实时渲染引擎，需要占用大量系统资源，所以舍弃撤销功能。所以一定要养成良好的保存习惯，不然有你好果汁吃。

### 为啥我的电脑无法安装Ventuz？
请确认你的电脑系统是64位WIN10系统，并且版本在1607之上。你要是win7系统确实想装，可以下载一个证书(证书就不放了，推荐直接更新系统)

### 怎么关闭Checking for Online Content?
![img](https://mmbiz.qpic.cn/mmbiz_png/C9uohSLsicrgjBI9uOo9C0XY0SRickmQ9nmPYwbuKoNdvYVLy8wPibBEzJgNRv5ibiaovOeyPuJCZgTcHhSHUoZ9ZLw/640?wx_fmt=png)

取消勾选，同时一些网络资源也会在你的项目列表中消失，不影响程序内部的节点使用和案例查阅（F1）

### 软件出现致命错误闪退导致项目丢失咋办啊
如果没有启动自动保存功能，那么文件大概率就丢失了。所以在进行一些危险性操作的时候，记得保存！

### 怎么设置自动保存？
顶部菜单Scene > Load/Save Options > Auto Resource Import。勾选Auto Resource Import,在下面的参数中可以设置自动保存的时间间隔。
自动保存文件位置：项目文件保存地址 > 文件名称 > Scenes.revisions。

### 在Configuration设置页面IP频繁跳转
这个问题的触发条件是现场有多台设备，而且设备系统由一个PE盘刻录所导致的。

1. 首先找到任务栏的服务图标，右键 --> Open Configuration Floder

![img](https://mmbiz.qlogo.cn/mmbiz_png/C9uohSLsicrgjBI9uOo9C0XY0SRickmQ9n5OMkkcDnqcH2YlSVwtWibNlMgvRCLz5yAXo4NX0fsicVic46ERkBFUcBw/0?wx_fmt=png)

2. 在VMS文件夹下新建一个txt文本文档



![img](https://mmbiz.qlogo.cn/mmbiz_png/C9uohSLsicrgjBI9uOo9C0XY0SRickmQ9nRmspFn9DXmCHlxdzulHYO9uPy92lWe1hib3BxTicDe5icImO6QtycQhQA/0?wx_fmt=png)

3. 打开txt,任意输入内容，一定要独一无二的(推荐英文命名，写完后保存退出)

![img](https://mmbiz.qlogo.cn/mmbiz_png/C9uohSLsicrgjBI9uOo9C0XY0SRickmQ9ntSoxFZWroOAvop0GwOFoJ8Ton9ibrdSM20FpRurFU8ZOUtn26bmdc0w/0?wx_fmt=png)

4. 修改这个txt文本名为SystemID，同时删除后缀(这图有水印，凑合看...)

![img](https://mmbiz.qlogo.cn/mmbiz_png/C9uohSLsicrgjBI9uOo9C0XY0SRickmQ9niacU8v4ubIQBPOTXib6qxdn2mOg32kFxj0NSoxGMXsVFcFk5sfV9LTWw/0?wx_fmt=png)

5. 打开Configuration,在Machine Identfication输入你刚才取的名字

![img](https://mmbiz.qlogo.cn/mmbiz_png/C9uohSLsicrgjBI9uOo9C0XY0SRickmQ9npKPBkZvqvOEZ28rCQLfG0vXNYKh7BLgl0BKgzeibU5y7Vy00jVmSib8g/0?wx_fmt=png)

6. 保存退出，重启电脑，IP不蹦跶了

### 打开RPR文件后关不掉窗口咋办啊
Alt+Enter窗口化界面，下次打开依旧是最大化。