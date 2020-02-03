title: My Think About MR
date: 2016-01-07
updated: 2017-08-16
categories:
- [thinking]
tags: 
- VR
- MR
- Stanford
- Computer Graphics
- Computer Vision
- Unity
- OpenCV
- Oculus
- Hololens
- Michael Abrash
---

对VR/MR的历史，现状，趋势，商业模式，产品，技术路径等的一些想法... 经过思考，与价值观不符，已放弃此方向，但学习和思考的一些内容也许对他人有所帮助 <!--more-->

> History : 2016.01.07完成初稿；2016.08.26调整内容组织顺序，加入MR内容；2017.08.16 **放弃 VR/MR 方向， 转向 智能机器人 **

> 在信息时代，客观障碍已不复存在，所谓障碍都是主观上的。如果你想动手开发什么全新的技术，你不需要几百万美元的资金，你只需要在冰箱里放满比萨和可乐，再有一台便宜的计算机，和为之献身的决心。我们在地板上睡过，我们从河水中趟过。
    --- John Carmack &lt;&lt;DOOM启示录&gt;&gt;

AR/VR的主要应用领域是游戏，视频(VR直播，MR远程指导，telepresent)及工业设计辅助。游戏的市场规模不过1000亿美元。当前充斥人们眼球的影视娱乐产业，其市场规模比游戏还小。互联网市场规模大概在 3800 亿美元。

选择 Computer Graphics 作为技术方向，主要出于对特效电影的好奇。 选择 AR/MR游戏 行业方向，是因为觉得游戏是人们的刚需，可以一直做下去，可以持续的积累。同时VR技术有了一定的突破，比较的热门，是一个切入的机会窗口。 选择放弃，是因为游戏并不能改变现实，不过是一种自我催眠罢了，而且现实世界比虚拟世界更有价值，更有意义。

VR/MR从技术角度，除光学，IMU外，主要涉及Computer Graphics(3D, Rendering),Computer Vision(手势识别, 物体识别，SLAM)，NLP(语音识别，TTS语音合成)相关的技术

# 信息
> 知己知彼，百战不殆
    --- 孙子兵法

VR/AR是下一个计算平台，是手机一样的几十亿量级的市场规模，还是游戏机数百万的规模？ 不管怎样，这个趋势是大公司都不会轻易放弃的。
比游戏机有更多的应用场景，除了游戏，更多的是一种生产力工具，应用在企业场景，比如教育(3D展示)，医疗(3D教学)，工业(3D设计，远程指导)，办公(远程会议，省去很多差旅费)领域
即使是能做到像普通眼镜一样大小和重量，全视野FOV，视网膜级的pixel渲染，对于消费者而言，更多的应该是一个娱乐工具 ： 游戏，视频，直播


2019.11.14 John Carmack : "I'm going to work on artificial general intelligence(AGI). I think it is possible, enormously valuable, and that I have a non-negligilbe chance of making a difference there, so by a Pascal's Mugging sort of logic, I should be working on it."

2019.02.25 MWC19 上，微软发布HoloLens 2, 企业版售价3500美金(比第一代企业版便宜1500美金)，国内预售价24154
> 距离第一代Hololens的发布已经过去4年，更轻，视野更宽，定位更明确：企业应用(PTC, Vuforia/ThingWorx)
> 基普曼表示，微软正与飞利浦医疗保健、Bentley Systems、博世等公司合作，为各地企业提供混合现实解决方案。 
> Snapdragon 850, HPU 2.0, FOV 2倍(30° -> 52°), eye tracking, Azure Kinect(第四代Kinect，399美金), instinctual control

2017.06.05  http://www.roadtovr.com/apples-arkit-bringing-augmented-reality-hundreds-millions-iphones-ipads/
iOS11中的ARKit，Vision， coreML为苹果全面拥抱AR提供了OS层面的支持，iMAC Pro，Steam VR，Matal2则为VR提供了支持，可以想象未来推出AR眼镜也是顺理成章的事情，估计会引发新一轮VR/AR的投资，投机，应用开发热潮。

2017.02.27 Khronos在GDC公布VR和AR的标准组建立，[OpenXR](https://www.khronos.org/openxr)，预计需要18个月时间标准1.0版本才会出台，也就是要到2018年下半年，首先提出API，解决碎片化的问题，然后再加入AR的支持。
和Computer Graphics的标准OpenGL一样，微软和苹果会使用自己的API，而不参与这个API的制定。AMD, ARM, Imagination, Intel, Mediatek, Nvidia, Qualcomm, Razer, Sensics
Google, Huawei, LG, Nokia, Oculus, Samsung, Sony, Valve, Epic, Unity, Mozilla

2016.12.06 Khronos Group发起VR标准API : https://www.khronos.org/news/press/khronos-announces-vr-standards-initiative
> 对于建立类似OpenGL的标准，说明VR在硬件/OS层面的探索基本成熟，统一标准API，解决碎片化问题，有助于扩大生态链，加速应用开发普及。微软和苹果应该会建立自己的API，就和OpenGL vs Directx vs Metal一样
” If VR and AR want become the next computing platform, then OpenXR is a key technology to help make that happen.

2016.10.26 Microsoft Reveals VR Headsets : http://www.roadtovr.com/microsoft-reveals-vr-headsets-coming-from-top-manufacturers-starting-at-299
> 微软的Win10作为"one platform for VR, AR and MR."，联合PC行业的产业链玩家()进入市场，有利于扩大市场规模，有利于VR/MR设备的普及。
不管是VR还是MR型态，归根到底是立体化，三维空间的自然人机交互方式。
在智能手机时代几无作为的PC时代的玩家们在微软的Win10平台下(Intel，Nvidia, 惠普，联想，戴尔，宏碁，华硕)进入VR/MR战场；随着智能手机市场增长放缓甚至下滑，在智能手机时代崛起的玩家们在Google Daydream平台支持下(高通, 三星，华为，小米)也会迫切的加入战团；同时VR时代最先入场的玩家(Oculus, HTC, Valve)也在不断的进取，也许2-3年后VR/MR市场就会进入春秋战国时代。那时也许Apple后发制人建立自己的生态。在增量的蓝海市场上，这样的竞争有利于提升技术水平和产品体验，扩大市场份额，提供高中低不同层次的硬件产品。Hololens(3000$)，Oculus Rift(599 + 1000), HTC Vive(799 + 1000)，Win10 VR(199 + ), Samsung GearVR(99), Daydream View(79 + 649)
于是整个市场变成了： 微软(win10) + PC产业链 vs 谷歌(Android Daydream) + OHA手机联盟 vs 苹果(iOS)  复制的是苹果的软件(OS) + 硬件(iPhone) + 服务(AppStore)的模式。

2016.10.06 Oculus正在研发名为Santa Cruz的Standalone VR头盔 : http://www.roadtovr.com/oculus-working-on-inside-out-tracking-for-stand-alone-vr-headset-breaking

2016.10.04 Google将发布reference VR headset for its Daydream platform : http://www.roadtovr.com/google-announces-first-daydream-ready-vr-phone-breaking/

2016 年 9 月，微软为世界知名电梯厂商蒂森克虏伯公司提供了24000 台 HoloLens，这些设备将用来帮助公司技术员工更高效地处理电梯安装及检修等相关问题。
https://blogs.windows.com/devices/2016/09/15/microsoft-hololens-enables-thyssenkrupp-to-transform-the-global-elevator-industry
在行业应用上，可以支持远程指导，虚拟培训等，能确实帮助降低成本，提升效率，这是个商业机会。

2016.09.14 资本变脸：6个月时间里VR从狂欢到惨淡: http://tech.163.com/16/0914/09/C0TQ0DF800097U7U.html
> 大浪淘沙，洗掉不坚定者。未来1～2年只怕死掉的更多。我觉得目前主要的两个问题： 
1. 价格高，HTC VIVE 6888 + VR Reay PC 10000 + 游戏费用，接近2W人民币，有谁会买
2. 体验差，纱窗效应和晕动症没有解决，谁会为不完善的功能买单
答案是：重度游戏玩家，所以PS4的4000W用户有多少会买PS VR就是一个很好的指标。一个月后(2016.10.13)就可以有初步的答案。
现在做VR的要么背靠大树，要么做线下体验店，先活下来才是王道。

2016.08.17 Microsoft ‘Holographic Shell’ Aims to Immerse You in Windows by 2017 : http://www.roadtovr.com/microsoft-windows-holographic-shell-aims-to-immerse-you-in-windows-2017
> "one platform for VR, AR and MR." 结合Intel的新闻可以看到MS和Intel企图复制PC时代Windows + Intel Cpu的战略，制定行业标准。

2016.08.16 Intel进军虚拟现实领域 推出Alloy项目 : http://www.roadtovr.com/intel-project-alloy-mobile-vr-headset-positional-tracking-tetherless-idf-2016
> "2017年下半年开放硬件，提供API"，个人觉得在目前的技术水平下，这样的设备有些超前，要看具体的参数和效果；但理念更接近理想的VR设备型态: 1. 一体化 2. 手势交互 3. ‘inside-out’ tracking 4. VR & MR整合在一起

2016.05.18 Google I/O 2016，谷歌宣布Daydream虚拟现实平台 : http://tech.163.com/16/0519/08/BNDSEQDN00094P0U.html
> goolge采用基于Android平台来构建VR生态系统，通过优化Android系统，规范硬件参数及软件接口来标准化mobile VR产品，这样可以渐进的推进VR的普及，同时也为内容生产者铺平了道路。当然从中也可以看出google对VR的谨慎，也预示着整个VR行业还处于很早期的阶段，采用Daydream打造的设备也就是将samsung的Gear VR更规模化而已：2K屏，60HZ的帧率，基于controller pad的交互只是VR的初级型态而已，硬件水平的提升，更自然的交互机制等都依然在探索中. 

2016.04.15 德银VR报告 : http://tech.qq.com/a/20160415/009083.htm
> 德银对历史上新技术在不同阶段的市场形成进行了研究，发现有两项新技术的发展轨迹适用于VR： 1、最初的互联网（20世纪90年代中期）； 2、智能手机的普及（2007年至今）。基于这两项技术的发展轨迹，尤其是智能手机的发展，或许能很好地预测出未来10年VR的发展趋势，因为正是智能手机应用和生态系统推动了VR的发展，而且两者的内容分发机制看起来也是类似的。
任何技术的发展都会经历各种阵痛，PC在出现10年后才流行起来，智能手机用了5年时间才成为真正的移动主宰，但它们已经变得不可或缺，原因很简单，因为它们给了人们前所未有的、神奇有用的体验。VR也将如此，因为它代表着未来。

2016.03.28 第一台Oculus Rift已签收 创始人亲自送出 : http://m.yicai.com/news/4767358.html
> 从第一代PR1到第一台消费者产品，5年过去了；从2014年被收购，已经过去了2年时间

2016.02.29 Announcing Microsoft HoloLens Development Edition open for pre-order, shipping March 30 : https://blogs.windows.com/devices/2016/02/29/announcing-microsoft-hololens-development-edition-open-for-pre-order-shipping-march-30/
> MS宣布Hololens开发者版开放预售，2016年3月30日开始发货，3000美金一台.

2016.01.14 高盛：VR和AR将像PC一样改变世界, 2025年AR和VR硬件软件营收将达800亿美元 : http://tech.ifeng.com/wys/special/gsxnxshzqxsjxpcyygbsj/ [汉化全文](http://tech.qq.com/a/20160202/011274.htm)
> VR主要应用领域：视频游戏、事件直播、视频娱乐、医疗保健、房地产、零售、教育、工程和军事。
> 从目前的观察来看，AR比较适合服务企业级用户，用于提高效率，降低成本；而VR同时适用于消费者和企业用户，用于与众不同的体验。

2015.01.21 Microsoft announces Windows Holographic with HoloLens headset : http://www.theverge.com/2015/1/21/7867593/microsoft-announces-windows-holographic
> 微软正式公开Hololens的存在，MR概念

2014.03.26 Facebook以20亿美元收购Oculus : http://www.csdn.net/article/2014-03-26/2818974-facebook-to-acquire-oculus
> 这是一个非常关键的事件，自此VR/AR进入大众视野，无数的媒体，资本，公司，个人开始关注，投资，实践VR

2013.08.07 John Carmack Joins Oculus as CTO : https://www.oculus.com/en-us/blog/john-carmack-joins-oculus-as-cto/

2012.08.10 Palmer Luckey, Michael Abrash, and John Carmack discuss virtual reality at QuakeCon 2012 : https://youtu.be/8gaqQdyfAz8

2012.04 Palmer Luckey announced that he was building his sixth-­generation unit, which he called the Rift
2011.09 Palmer Luckey announced the wireless PR3
2010.11 Palmer Luckey announced the existence of PR1
> 参考[The Inside Story of Oculus Rift and How Virtual Reality Became Reality](http://www.wired.com/2014/05/oculus-rift-4/)

从历史的发展来看，很多革命性的技术发展都是发轫于军用，随着成本降低到商用，价格再降低及接受度提高最后到民用的过程，比如计算机(二战时曼哈顿计划用于计算导弹射程)，互联网(国防部核物理学家)，移动电话(战争用于通信)，VR(军事训练)，GPS()。而按照Ganter的技术发展周期理论，一项技术的应用从启动，上升，爆发，平稳，下降，是有规律可循的。

从技术的理论成熟，到工业界的产品开发，以及关联的产业链的成熟，最后消费者的应用。以VR为例，要达到20ms的延迟，需要使用OLED显示器，需要CPU, GPU运算力提升；要达到视网膜效果(60pixel/degree)，140度的FOV，则需要单眼8400个像素，也就是8K，这么多的像素，对应120 FPS的帧率，需要8400 x 6000 x 4 x 120 = 24Gbp/s的带宽。

1956年AI，在80年代末火过，90年代末沉寂，在2012年深度学习在ImageNet上的应用，以及2016年公众事件，AlphaGo打败李世石，60年的时间到了第三波，但并没有完全成熟；同样的VR的发展也是如此，在1968年，80年代的任天堂的VRboy，再到2012年发明Oculus Rift，到2014年Facebook以20亿美金收购Oculus的公众事件。

# 手机生态链
芯片		| ODM		| OEM		| 平台		| 应用		| 游戏 
--------	--------	--------	----------	
Intel, Nvidia	|

从2007年iphone发布开始，智能手机(移动互联网)的浪潮启动，人机交互的方式从2D革命化进入3D，

产业初期技术驱动 -> 产品驱动 -> 营销驱动

有3D游戏经验的人才将有绝对的优势，一旦市场成熟，大批创业公司拉高从业人员薪资水平，然后大批的培训，外包公司涌现，拉低从业人员的水准，这样的现象在JAVA，web，Android都一再出现过。

参考 智能手机 的发展
## 硬件
三星，华为，小米，LG， HTC，

中兴，酷派，联想，moto，nokia，黑莓，sony, HTC

design house，随着设备厂商自身的积累和投入，都变成了外包

CPU， GPU， memory， flash， camera， lcd， modem ... 

## 平台
Nokia symbain
Sumsung Tita
黑莓 
HP 
点心 OS
腾讯 tita

事实证明，硬件和系统只有大公司才能玩，甚至大公司都玩不好。

Qualcomm的VR/AR Solution : 
https://www.qualcomm.com/invention/cognitive-technologies/immersive-experiences

高通认为 [Augmented and Virtual Reality: The First Wave of 5G Killer Apps](https://www.qualcomm.com/documents/augmented-and-virtual-reality-first-wave-5g-killer-apps)

## 应用
游戏虽然竞争残酷，但工具类产品更激烈，因为工具缺乏粘性，用完就丢，只有最多3名玩家，最残酷的是入口应用，只有第一才有机会，而游戏在各个细分领域都可以有机会。 
所以其实游戏的成功率想对而言是最高的，当然对应的缺点就是很难形成垄断优势，且成功有一定的偶然性。
在机会上，初创企业大概有18个月的窗口期，一旦趋势启动，大公司携人力，资本，资源优势可以迅速的占领市场。

- 入口
刚需成就入口，互联网产品特性是满足刚性需求，因为其边际成本接近为0，这样也导致马太效应的放大，某一领域的领先者容易形成垄断地位。比如手机属于嵌入式领域，很难一家独大占据80%的市场份额，而QQ，google搜索都是处于垄断地位。

巨头们都有相应的入口，WEB上的优势移植到移动端：
腾讯 : QQ，微信，应用宝
百度 : 搜索，地图
阿里 ： 淘宝，支付宝
360 ： 手机助手
从PC时代，到Web时代，再到智能手机时代，硬件载体变化了，巨头通过移植已有的产品和业务可以占据优势，除此外那些新成立的公司更能证明不同的平台能提供的差异化的机会。
在入口上能造就1000亿美金市值的公司，概率非常低，在移动互联网时代，只有小米(2010)
从2007年之后成立的移动互联网知名公司：(独角兽 : 估值10亿美金)

- 工具
猎豹移动(2010), APUS(2014), 美图秀秀(2008)

- 社交
snapchat, what's app, line, 陌陌(2011), instragm, pinterest

- 电商
聚美优品(2010), 窝窝团(2010), 蘑菇街(2011)

- 游戏
supercell(2011), king(2009), Rivo, 莉莉丝(2013, dota传奇)

游戏类型，休闲，轻度，中度，重度演进模式。MMORPG
卡牌，棋牌，三消，策略，RPG，

- O2O
uber， Airbnb， 滴滴快的(2012), 美团(2010)

- 行业
旅游，教育，金融，医疗，

从2007年的移动互联网开启大幕，相关的公司及行业趋势：
- 平台
崛起：ios(apple), android(google)
衰落：windows mobile(microsoft ~ 2010.10), symbain(nokia 2000 ~ 2013.1.24), meego(intel 2010.2 ~ 2014.1.1), plam os (1996 ~ 2009.2.11), webos(hp 2009 - 2010), bada(samsung), 
http://tech.163.com/15/0130/14/AH7EFRUD000915BE.html

- 硬件
崛起：apple, samsung, 小米，华为
衰落：nokia, motorola, black

HTC是个很特别的例子，依赖早期的Android的红利崛起，大赚了一笔，由于不思进取，反应迟钝，机海战略导致衰落。
2007年Android正式发布，2008年，HTC退出第一款Android手机G1，2010， 2011年达到巅峰。
2012年，小米崛起。
- 软件
传统PC互联网公司在移动互联网时代基本都延续了自己的地位 http://www.forbeschina.com/event/188

在移动互联网时代的上市公司：
IM ： whats app, instagram, 陌陌(2014.12.11)
电商 ： 阿里巴巴(2014.9.19)，京东(2014.5.22)，聚美优品(2014.5.16)，
游戏 ： 蓝港互动(2014.12.30)，飞鱼科技(2014.12.5), superCell, king
O2O  : 途牛(2014.12.15)

- 盈利模式：
广告， **游戏** ，电商，增值(会员，内容付费，虚拟物品，打赏)
增值服务 : 会员费，内容付费，道具付费

不管是PC时代，PC互联网时代，移动互联网时代，除OS(Window, Browser, iOS/Android)外，游戏应用都是金矿，变现能力最强，而且是持续的现金流来源。在下一个时代(AI也好,VR/MR也罢)，也不会是例外，因为人的天性是好逸恶劳或者说游戏是人/动物的本性/基因。缺点是成功概率低，不具有垄断属性，因为人还有一个本性是喜新厌旧。

单纯只从Android系统中获利的是芯片，设备，方案等硬件厂商。软件公司，互联网公司则是受益于智能手机的崛起。最早赚钱的游戏，app, 无不是优先从IOS做起来之后才移植到Android.
Android只是扩展了移动互联网使用人群，扩大了软件产品的使用范围。

因此可以想象，如同Android for smart phone, tablet, auto, tv, wearable(watch, glass)一样，Anroid for VR也会崛起一批VR设备厂商.

VR可以应用到行业：游戏，视频，教育，房地产

# 趋势
> 人的商业知识和眼光不是天生的，需要不断地、有心地学习。经过多年的学习、思考和实践，我认定这样一个规律，就是：科技的发展不是均匀的，而是以浪潮的形式出现。每一个人都应该看清楚浪潮，赶上浪潮，如此，便不枉此生。
    --- 吴军 &lt;&lt;浪潮之巅&gt;&gt;

从PC -> PC互联网-> smart phone -> 移动互联网，我们可以看到这些发明是由于军事的需要而诞生，PC最开始是为了破解德国的密码，Web是为了天体物理学家共享信息；Internet起源于美国国防部的阿帕网；手机起源于军事通信的需要，机器人则是军事用途需要；

科技的发展是渐进演化发展的，随着计算能力及工艺能力的提升，低成本小型高计算能力的设备成为可能，现在智能手机的计算能力比曼哈顿原子弹计划使用的计算力还大，如果技术的发展继续朝小型化，更高算力(比如量子计算机的商业化)发展，

2016年开始，智能手机销量增长放缓，红利期即将结束，由增量市场转变为存量市场，那么下一个大的浪潮是什么？VR，MR，AI，无人驾驶，大数据，云计算？ 消费升级和个性化成为主流需求特征；健康医疗和文化娱乐是未来处于持续增长的重点行业。

技术热点/趋势： 云计算，大数据(机器学习)，人工智能(自动驾驶，无人机，机器人)，物联网(IOT)，VR/AR, 区块链

行业进入了深水区，中国与美国在IT技术上同步了。10年前，我们使用微软提供的API以及MSDN，再加上自己的一些工程经验的积累，基本可以搞定所有的业务需求，搞不定的也可以找微软背锅。5年前，使用Google提供的API，document，source code也能搞定所有的工作。而现在，云计算，大数据，深度学习，IOT，VR/AR，区块链，所有这些技术方向，都还未成型，大公司也还在早期探索阶段，研究与工程并行，更不谈一般公司了。对于普通的工程师而言，这可能是最好的时代，因为选对了方向，我们就可能处于浪潮之巅；但也是最坏的时代，因为前面没有人指路，只能靠自己摸索。

工业机器人的应用一直都有，消费机器人的价格，比VR设备搞几个数量级(PR2售价40万美金)，是更遥远的未来。

每一个都可能是The Next Big thing，选择哪一个方向? : VR, 机器人, IOT, 无人机，直播，AI

随着互联网发展进行平稳期，如水电油通信一样成为基础设施，下一个新的技术浪潮会是什么？ 也许是AI(无人驾驶，无人机，机器人)，VR/AR，云计算，大数据，IOT，区块链，5G
**或许并不是单一技术的崛起，而是所有这些技术互相推进形成的一个全新的科技时代，对工业，社会都会有巨大的影响**
5G + IOT + BlockChain + 大数据 + 云计算 + AI + VR + MR
这些新方向，包括AI，云计算，大数据，IOT, 5G, VR/AR，区块链都是有彼此的关联的，比如这一轮AI的应用是靠深度学习算法 + 云计算 + 大数据 来支撑的；AI特别是计算机视觉对VR/AR也是有帮助；VR/AR会推动5G的普及；5G，AR，区块链的普及推动IOT的发展，IOT的发展进一步提升AI的精度和准确度

通过硬件设备(手机，传感器，各种智能设备)获取数据，通过5G网络上传到云端，在AI的帮助下，做大数据的分析，然后进一步的优化反馈。未来的科技公司，更可能是软硬件结合的，互联网自身的发展(PC，和手机)已经成熟，接下来要与传统工业，农业，服务业结合，提升效率，降低成本，甚至创造新机会，新行业。

这些应用方向分别对应Stanford BS的不同tracks ：
AI     -> AI
VR/AR  -> Graphics
云计算 -> System
大数据 -> Information
向IOT这样的应用，更适合EE专业的人来做。

也许需要2～5年的"分水岭"实践的酝酿，比如AI目前在一些特定场景下精度超过人类，其主要的深度学习算法需要大量的数据和计算能力的支撑，很显然，大数据和云计算都是大型公司的专利，普通公司在平台上没什么机会，利用大公司的平台结合传统行业 + AI，提供技术服务和解决方案，可能是一条可行的模式。算法框架 + 云平台(GPU) + 大数据(公有，私有)
VR/AR可能是下一个计算平台，但离普通用户还遥远，商业模式还未成熟，利润微薄，现阶段先要活下来才是正道，要么背靠大树，要么收缩人力，接外包，做项目；
云计算/大数据，利用开源的工具做做业务可以，但想搭建平台已无可能，巨大的硬件/带宽投入就难以支撑；
IOT，需要等2020年5G成熟，行业标准建立，AI成熟后会有机会
AI子领域 : 计算机视觉，语音识别，自然语言处理，机器学习，机器人
AI应用： AI助手，自动驾驶，机器人，VR/AR，

IOT/VR -> 云计算/大数据/AI

从使用者角度看，在PC时代，人们用PC来工作(办公，计算)和娱乐(单机游戏，看小说，看VCD)；在PC互联网时代，人们用PC浏览器查找信息，沟通社交，在线娱乐，在线购物；在智能手机时代，人们用手机打电话，发短信，拍照，听音乐，打单机游戏，看小说；在移动互联网时代，除了可以兼具PC互联网时代和智能手机时代的功能外，还可以利用携带的GPS做地理相关的导航，打车；和PC，手机一样，VR是下一个计算平台，那么人们用VR可以做什么？ VR有独一无二的特征：在场感(present)
1. 在初期，因为性能缘故，一开始还是以不可移动的应用为主，可以涵盖PC互联网的所有可提供的功能 : 
本地娱乐 : 单机游戏，本地视频，看小说/可以动的小说，这个应该是最大的卖点，提供传统平面显示无法企及的立体体验
查找信息 ： 没有好的文字输入方式，查找信息反而比PC互联网时代困难，语音交互是个可行的方案？

2. 随着2020年5G的商用，网络带宽的提升，VR/MR设备可以联网应用
https://www.qualcomm.com/documents/augmented-and-virtual-reality-first-wave-5g-killer-apps
5G也许是VR/MR大规模商用的关键因素。
可以提供现有PC互联网的所有应用的VR版
在线娱乐：网络游戏，在线视频，在线直播
在线沟通：全息影像(不受时空限制的面对面交流)，
在线旅游：在家里走遍全球，Google Street/Earth 的立体版
在线购物：
在线教育：
在线健身:

3. 随着设备小型化，一体化，VR/AR融合，MR设备可以便携，随时随地使用
MR集成智能手机功能 : 通话，拍照，录像，GPS
MR 社交：
MR O2O：
MR 游戏：
MR AI助理：
MR ？

大众创业，大众创新，媒体的推波助澜，每年各种概念层出不穷。从雷军的"站在风口上，猪都能飞起来"火了之后，各种风口论被媒体推波助澜拿出来炒作。"台上三分钟，台下十年功"，急功近利的人们只看到了台上三分钟的风光无限，而不管台下10年的努力和坚持。

VR是昙花一现，还是长远的趋势？ 毕竟团购，O2O，3D打印，智能硬件都曾经是所谓的风口最后都销声匿迹了.

VR和AI都不是新概念，在90年代就火过， 互联网及智能手机的普及，推动技术的演进;廉价的，小，高性能的sensor，显示屏，CPU等硬件设备，以及多年累计的互联网数字内容为深度学习提供了必要的条件。

IT行业从来不缺乏新的概念，媒体和资本也擅长推波助澜，同样也擅长落井下石。 智能硬件，O2O，
从PC -> 互联网 -> 智能手机时代，有哪些方向是基本没有改变的？也就是对人而言是刚性需求：色情，社交，娱乐 : 利用/放大人性的弱点做生意。

正如Michael Abrash在[他的blog](http://blogs.valvesoftware.com/abrash/why-you-wont-see-hard-ar-anytime-soon/)里所说，[AR](https://en.wikipedia.org/wiki/Augmented_reality) 可以分为Video-passthrough(Soft AR) and see-through(Hard AR)两种类型。简单来说Soft AR是通过摄像头看外部世界，Hard AR则可以直接看到现实世界，只是会在上面叠加透明的虚拟3D画面。

在Hololens出来之前，主要AR应用都是Soft AR，典型的场景是使用手机摄像头完成对象的检测和识别。比如拍照时的人脸检测，儿童玩具的识别，通常检测到特征对象后会在显示屏幕上叠加2D或者3D的图形图像，也就是说我们看到的依然是2D的画面。但[Hololens](https://www.microsoft.com/microsoft-hololens/en-us/why-hololens)则不同，它是Hard AR，通过它可以直接在实现世界看到虚拟的3D对象，并可以交互。
毫无疑问，Hololens是All in one的终极方案：
- Standalone : 显示器，计算单元，电源都集成在一起
- Tetherless : 自带电池，移动，可便携
- Optical see-through
- inside-out tracking(SLAM)
- 支持手势识别，语音识别，凝视交互
- 基于跨平台的WUP系统
- 提供统一的SDK

因此可能是为了与传统的AR应用和概念区分开，便于认知，商业推广等，Microsft和Magic Leap都称他们的技术是MR : [Mixed Reality](https://en.wikipedia.org/wiki/Mixed_reality). 

所以我个人的理解AR指的是Soft AR，MR指的是Hard AR。按照这样的定义，在AR场景下，人机交互依然是2D空间的，而VR，MR则是在3D空间。
将AR, VR, MR做一些对比：
- 发展趋势
从Google Glass以及大量使用手机来实现的AR来看，AR已经没有发展前景；
目前主要是VR开始火起来，2016年号称VR元年，Oculus Rift，HTC Vive，Sony VR，Gear VR，Google Cardboard等各种VR设备从高端到低端是多如牛毛，内容也在持续的增加中，当然整个行业还处于早期，盈利模式还在探索，价格，体验，内容都还有很大的提升空间； 
MR可用的产品只有MS的[Hololens](https://www.microsoft.com/microsoft-hololens/en-us)，开发者版本的HoloLens已经于2016年3月30发售，售价3000美金. Hololens的型态更类似一体机VR，直接是终极型态的感觉。初此外还有神秘Magic Leap，但并无公开的产品，只有DEMO视频。以及[Meta2](https://www.metavision.com/)。

可以说MR是VR的增强版，因为除了呈现3D的虚拟世界外，还需要重建3D现实世界。同时因为MR要与现实世界进行交互，所以必须是可便携的，但实时重建整个现实世界还不切实际(未来应该是云端)，所以目前应用主要在B端受限的环境里。
从发展速度来看，消费者VR尚处于行业早期阶段，更不用说MR了，所以Hololens在5年内都是面向B端市场，C端应用是5-10年后的事情。

- 应用场景
AR是在真实世界上叠加虚拟画面，主要的应用是： 教育，游戏(火遍全球的Pokémon Go)；
VR会使人完全沉浸在虚拟3D世界里，更适合娱乐场景，主要的应用是： 游戏，直播，视频
MR则将虚拟的数字世界和现实的物理世界融合在一起，是应用更广泛的通用的工具，主要的应用： 游戏(MineCraft)，社交(holoportation), 行业(电商，医疗，教育，建筑，设计...)；

虽然MR的应用范围更多，但缺乏killer app场景，也许全息通信是一个，同样也需要5G的支持。

- 产品开发
AR应用的开发主要采用Unity + Vuforia(ARToolkit, OpenCV) + VS；
VR的开发以Unity/Unreal + Oculus VR SDK(Google VR SDK, Open VR SDK, ...) + VS；
MR或者说Hololens的开发也是使用Unity + [Hololens SDK](https://developer.microsoft.com/en-us/windows/holographic/documentation) + VS；
也就是说，不管AR， VR， MR，主要的开发工具是Unity(C#)，Unreal(C++)会是少数有实力团队的选择(有能力掌控C++和3D游戏引擎)。
还有一些其他工具，建模，动画：3D Max， Maya， *Blender*; 图像处理：PhotoShop, *GIMP*; 音频编辑： *Audacity*
从使用的技术及人员分工来看，传统3D游戏开发的团队(策划，技术，美术组合)有很大的先发技术及经验优势。

- 技术基础
从涉及到的技术方向来讲，不管是VR还是MR，都融合了计算机图形学(Computer Graphics)和计算机视觉(Compuer Vision)的专业知识。

从技术的角度来讲，AR主要基于Computer Vision(物体检测，识别，跟踪)及Computer Graphics(2D/3D图形，动画显示)；VR也是基于Computer Graphics(立体渲染，3D对象，UI)及Computer Vision(手势识别，Inside-out Tracking移动跟踪，眼球跟踪)；MR除了Computer Vision和Computer Graphics，还需要[SLAM](https://en.wikipedia.org/wiki/Simultaneous_localization_and_mapping)对现实世界实时扫描和建模。

相对于传统的3D游戏，VR和MR的难点在于设计和交互上。在VR，MR环境，人与虚拟数字世界是融为一体的。

个人认为与VR，MR的交互，最自然的方式是手势，在PC时代，人们使用键鼠与计算机交互，在mobile时代，人们使用更直接的触摸屏与计算机交互，在VR时代，除了视觉从2D进化到3D，交互方式也必然是更自然的手势和语音，基于Computer Vision的解决方案目前看是最廉价也是最有希望的。

在VR和MR中，我们与computer交互的方式从2D进化成3D，目前人与VR的交互还没有标准统一的方案(touch pad, game pad, gesture, 动作捕捉)；
MS的Hololens已经提供了三种方式：Gaze, Gesture, Voice input

在VR，MR这样的产业链上，有哪些商业机会？ 发轫于2007年，至今已接近10年的移动互联网的历史，应该可以给予我们很多启示。
VR更多的提供娱乐体验，所以游戏，电影，直播都是他的杀手级应用场景；而MR更多的是“提升成本，降低效率”的工具，可以应用到更多的场景中，但是缺乏杀手级应用。

# 商业
> 领先一步是先驱，领先三步是先烈 
  --- 任正非

**随着中国中产阶层的持续扩大及老龄化的到来，在未来，健康和娱乐会是非常有商业发展前景的方向，而消费升级，人们对产品质量和创意更在意，而不是价格。**

## 平台
平台(platfrom)是巨头的战场，应该是手机平台的延续，出现一个完全新的平台可能性很小。
- Microsoft : windows
- Google : Android
- Applie : iOS
- future ?
在早期可能有些design house基于Android给设备厂商做外包，毕竟大公司不会轻易投入大量资源，如同早期做手机ROM的公司:点心，给华为之类的做外包一样，但是一旦行业成熟，大公司自己招兵买马，这些design house就根本没机会了。

设计规范？目前并没有专门的VR OS，更不谈VR设计规范，一切还在探索之中. 但如果PC，手机的发展轨迹一样，OS及design spec必然会逐步成型，那个时候就是发展最盛，也是平稳发展期了。

趋势已定，对团队，对个人而言机会又有哪些？ 以史为鉴，参考智能手机的发展，对我们有巨大的参考意义。
平台： ?
硬件： Oculus Rift(Facebook/Oculus), HTC Vive(Valve, HTC), PS VR(Sony), Daydream(Google), Gear VR(Oculus/Samsung), Hololens(MicroSoft), MagicLeap(Google) 
芯片： vuforia, fastcv(qualcomm), RealSense(intel), GameWorks(Nvidia)
软件：  unity(unity 3D), Epic(unreal)

## 应用
价格及接受度是VR/MR设备普及的最大障碍，设备普及到一定的量之后，才有内容的爆发。设备的普及会是一个迭代漫长的过程，最开始的使用者会是企业/行业用户，然后是对价钱不敏感的游戏玩家，再然后是对技术接受度高，有购买力的中产阶层，最后是价格及质量都到一定的程度的学生用户。所以从使用者群体的演变来看，内容开发的目标可以根据用户的变化而改变：企业应用 -> 游戏应用 -> 通用应用。

技术为业务服务，为用户创造价值。做研究可以天马行空，考虑10年后的事情，做工程则需要考虑当下1-3年的应用。AI,VR都是60年前就已经在研究的技术，也都曾经在80年代火过然后又沉寂了，所以时机的把握至关重要。这一次VR,AI的最大特点是可用了，可以脱离实验室进入商业化阶段，虽然离普通消费者还有些距离，如何将技术应用落地，切实带来消费者价格的前所未有的体验，效率的大幅提升，这就是商业公司的这一波技术浪潮的机会所在了。作为个人也应该顺势而为，选择感兴趣的方向，提前储备技术和经验，等待时机。

在早期90年代，PC价格高昂，未普及时，最先使用PC的是办公室的白领和大学生们，主要是去网吧解决需求：找朋友，打游戏，看电影。VR/MR是否也会走这样的路？比较困难的是被智能手机的用户体验提高了审美和体验要求的人们很难接受体验不好的产品，这为早期推广建立了障碍。

> 虽然iPhone早在2007年年中就推出，但iOS应用商店一年后才上线。最初iOS应用也是乏善可陈，直至Instagram、WhatsApp、Uber和其他杀手级应用出现后，iOS生态系统才真正形成。直至2011年，即iPhone上市后4年，iOS应用下载量才真正腾飞。 --- [德银VR报告](http://tech.qq.com/a/20160415/009083.htm)

**2007年iPhone发布，2010年iPhone4发布，销量进入快速增长通道，2011年，App下载量开始腾飞，而手游则要到2013年才爆发，中间隔了6年。对比VR来说，在2016年各大VR设备开始出货，个人认为也许同样的需要经过3年的迭代，到2019年销量(考虑到2019年新一代的Holoens发布，2020年5G开始商用)才开始快速增长，再过3年后，到2022年内容开始爆发,而要全面普及则需要更长时间，因为在iPhone出现之前，手机行业就已经存在，用户只是更新换代，而不是初次选择。这些都只是预测，更具有指标意义的信号是: 1亿的设备保有量，以及100万的DAU**

**作为普通的程序员，可以根据VR发展的生命周期，有计划的安排要做的事情：2016 ～ 2019，可以做外包，行业应用(2B)先活下来，一边探索学习积累经验，一边时时关注行业趋势；2019 ~ 2022年，参考先行者的成功经验，避开探索者走过的坑，组建团队，开始制作游戏，有机会在2022年用户量爆发的时候取得先发优势，赚得一桶金。**

硬件和内容是一个"鸡生蛋"的问题，硬件的不成熟，平台的不标准，导致用户规模不大，从而应用的规模也做不起来。不过我们可以参考历史做一个对比：
计算机主流平台从Console -> PC -> Internet -> Web -> Mobile 
同期游戏平台也从大型机 -> PC(Win/Intel) -> Web -> Mobile 
在平台变化的过程中，诞生了不同的业务型态，游戏 始终是最盈利的商业应用，一方面平台具有垄断性，能搭建起平台的是行业里极少数最强实力的公司(技术，资金，人才，影响力)，比如Apple，微软，google；经过20多年，盈利模式和商业模式已经探索完整：
盈利模式：广告，增值，游戏，电商
商业模式：新闻门户，搜索，电商，社交，工具(Browser, 安全，IM)，视频，
互联网的特点是赢家通吃，形成垄断

主机/主机游戏
PC/单机端游
PC/网络游戏
网页/网页游戏
手机/手机游戏 

在硬件足够成熟前，应用和硬件互相促进，但一旦硬件成熟，应用将呈现爆发式增长，因为软件的边际成本接近为0. 但和智能手机中App的发展轨迹一样，当几个入口型应用及必须的工具应用一旦形成稳固的优势，其他应用将不再有机会，游戏App可能是例外，但付出的代价是获取每用户成本的飙升。所以对应用开发者而言，一定要利用先发优势，积累经验和口碑，并不断迭代，占据有利位置。

硬件的销售依靠应用来达成，没有满足真实的需求的应用，无法吸引用户买单。有什么内容是可以强烈吸引早期用户买单的，可以让用户有更高的容忍度，容忍早期的硬件设备的各种不成熟，在2016年3月体验了Gear VR之后，有如下几个问题：
1. 依然存在的"晕动症"
那种恶心想吐的感觉有可能让用户立即远离设备，从此不会再用。 MagicLeap研究的Light field光场相机以及Fover rendering
2. 纱窗效应明显
颗粒感和像素还是很明显，有“临场感”，但“沉浸感”还谈不上，要达到视网膜效果，需要单眼8K x 8K的分辨率，
3. 交互方式不自然
目前touchpad，gamepad，手柄依然是主要的交互方式，最佳的手势交互还没有看到商用的产品
4. 内容缺乏
只有几个优秀的短视频和DEMO，而且时间短
5. 功耗问题
S6使用10分钟就发热，需要冷却

按照手机的发展规律，从模拟信号的大哥大1990，到数字信号的功能机2002，再到智能手机，再到2007年Iphone，2010年Android的爆发，设备的规模数达到一定的量级，才有 内容的 崛起的根基。

从时机来看2016虽然号称VR元年，但其实整个行业处于很早期阶段，对于团队而言最重要的是有资金支持(不管是融资还是销售收入)可以活下去，对个人而言以持续的关注和学习为主，等待最佳时机.

除了游戏的铁杆粉丝外，AV会是一个驱动力. 想像一下，心仪的女优就在你眼前宽衣解带，有几个宅男能够抗拒，而且采用会员制的方式，可以有收入来源，已经有美国公司[这么做了](http://www.yxdown.com/news/201507/208722.html). 在中国这个方向肯定是不行的，最多打打擦边球，可以做一些写真视频之类的. 所以有可能的模式是设备搭配AV厂商，就像早期买录影带，VCD/DVD播放机是为了看电影一样。

早期应用(application)是游戏核心玩家，考虑到性能及移动限制，早期的市场倾向于企业应用：靠2B的业务来获得收入，维持公司运作，能活下去才是最主要的，并积累经验；在市场启动之后，最重要的是团队的执行力，对需求的快速反应能力。
2B的业务必定要有特定的价值(降低成本，提升效率)来抵消体验不佳的障碍。

可以想象的盈利路径： 制作游戏，即可以上线store收费，也可以和硬件厂商合作提供给 网吧，游戏厅，主题公园，积累经验并养活自己，然后在市场培育起来之后，再及时开发面向 普通消费者 的游戏类型。

### 游戏
游戏的分发渠道，除了各个硬件厂商的store之外: 网吧，游戏厅，主题公园，KTV(?)，影院等娱乐场所：
[HTC通过与顺网合作拓展网吧市场是很合理的市场战略](http://www.roadtovr.com/htc-partnership-aims-to-bring-vive-to-hundreds-of-millions-of-internet-cafe-users/)，只是内容(游戏，视频)缺乏是个需要时间来逐步完善的过程。
只是网吧的消费人群逐年减少，以 游戏玩家/学生 为主，这部分会有意愿尝试体验VR，而且早期依然是游戏为主，或者在影院模式下看2D/3D电影，AV或是Hgame会有很大的吸引力。
内容开发者通过网吧管理平台厂商合作，收取分成来获取收入。这个时候的游戏类型应该是以RPG, RTS， FPS这样的需要团体参与的网络对战游戏为主，而不是个体游戏。毕竟早期的游戏用户以 宅男 为主.
就像在PC游戏我们去网吧只为了打帝国时代，星际争霸，CS一样。还有一个就是因为VR的沉浸的原因，出于安全及交互的考虑，需要重新设计我们的座椅，也许类似Omni VR跑步机那样的座椅会是最好的方式。
游戏的成功有很大的不确定性和偶然性。

- 游戏类型
在硬件开始普及，进入个人消费者应用阶段后， 游戏类型的发展基本上会延续智能手机的模式：轻度(休闲，卡牌，旗牌，消除...) -> 中度(FPS, RTS) -> 重度(RPG) 

### 电影
美女写真，AV会是最先尝试的领域，如何叙事，如何引导
电影院也许会是最先尝试的地方，和早期的VCD/DVD/P2P/视频网站的发展模式一样。因为360度的缘故，电影向游戏化发展，可以有交互，有分支剧情；同样的因为显示效果的真实化，游戏可以渲染电影一样的效果，也就是游戏和电影出现融合。

### 直播
非常好的应用场景，可以说是刚性需求，解决大多数人不能在现场观看综艺节目，演唱会，体育比赛的痛点，而且也有会员费，打赏，广告，电商导流等盈利模式，也能让用户有参与感.
一旦技术成熟，最大的挑战其实在于内容的获取，优质的内容依然由传统的巨头把持。但可以作为技术提供方，对于现在的带宽而言，毫无疑问要采用P2P及CDN加速，PPSteam，pplive，迅雷等无疑有领先的技术优势.

直播会是最后兴起的模式，没有内容以及带宽的支撑，直播是无源之水。因为VR的特性，对延迟及画面质量有极高的要求，所以低质量的画面是难以忍受的。

从以往的互联网视频的历史来看，一定都是先有了点播，随着带宽及计算能力的增强，才会有直播的发展。 对于动辙50Mbps的带宽需求来说，也许5G才能抗的住，5G的商用也要到2020年了.

对这个方向来说，参考Youtube, 优库，斗鱼的发展模式，最后是拼资金，拼硬件，拼内容的业务，也就是巨头的战场，要盈利是漫漫长路。

http://it.sohu.com/20160609/n453737578.shtml

### 工具
现在只有 oculus store，作为入口，迟早要开发， 已经有http://www.sideloadvr.com/

除了传统的IM, Gallery, Video, Music等工具外，是否有三维空间特有的应用? AI助理 ??

### 行业
色情，电商，旅游，地产，广告，医疗，教育，军事等各种场景的应用，痛点依然是解决效率及成本问题，当然前提是设备本身的成本已经足够低。对这些行业而言，VR/MR不过是一个辅助工具，主要是增加效率，降低成本。

教育的应用，其实一直以来教育行业在政府的支持下，一直都是紧跟技术发展趋势的(多媒体课堂，MOOC，电子书包)，但义务教育的K12，是一个慢领域，赚钱比较慢。主要的收入来源于教育局的财政拨款，

对于教育的应用，需要细分考虑，考虑到VR/MR设备都有限制13岁以下未成年人使用，也就是适用于初中2年级以上的同学，而且因为价格的限制，那么应该是采用共享的方式使用，类似多媒体教室。
1. 学校的教学设备
2. 培优机构
3. 家庭购买

### 其他
就像所有的财富热潮一样，最终一定是少部分人赚大钱，大部分不赚钱，卖水的一定赚钱。所以提供第三方服务的公司其实会稳赚不赔，比如培训，美术外包，VR体验馆...

说完发展趋势，从产业链角度来预言今后可能的机会：

## 硬件
VR硬件设备四种形态(恰好对应到游戏的载体):
- Console VR
使用游戏主机作为载体，典型设备: *PS VR*
国内的主机厂商，腾讯，华为必然也是采用Android作为主机操作系统。

- PC VR
基于windows系统的PC，更好的体验，更高的成本，不方便移动(各种线缆)，空间受限，类似于 游戏主机，典型设备: *Oculus Rift*, *HTC Vive"
PC + HMD(Oculus Rift : 599美金，HTC Vive
799美金(国行 6888 RMB) ）至少1500$的价格非一般人能承受，只有技术尝先者，重度游戏爱好者会先尝试。 
和90年代中期一样，PC的价格很高，一般个人很少购买，所以网吧应运而生，而且VR的更沉浸的体验需要一定的空间，更适合网吧这样有动力提供更好的设备及场地的环境，缺点
不满足mobile VR体验的人会选择去网吧，当然前提是有足够吸引人的内容,就像早期大家去网吧主要是打星际争霸，玩帝国时代，看AV，用QQ聊天一样，这些都是强需求。

随着摩尔定律及技术的进步，PC及HMD的价格进一步下降，HMD的舒适度及体积越来越小的情况下，个人开始购自己专属的硬件:

配置: 
OS : win10
CPU : Intel I7
GPU : Nvidia Geforce 970, 980
Memory : 8G

按照Nvidia的调查，只有1%的PC能达到这样的配置要求，很显然，早期是游戏及开发者投入时间，金钱去尝试。

- Mobile VR (2015-2020)
基于Android系统的智能手机: 较低的成本，方便灵活，较差的续航能力，有利于快速普及，典型设备: *Google Cardboard*, *Samsung Gear VR*
VR设备作为手机的外部设备存在，手机(主要是Android系统)需要对framework，驱动做一些定制处理，比如对USB senseor的支持，对ATW的支持
Gear VR针对Android的修改让Samsung有技术上的领先优势，然后google在合适的时机整合到AOSP，这时候其他的设备厂商会纷纷跟进，降低VR价格和门槛，VR也即将成熟。

可以肯定， 三星开了头，最后VR设备的玩家，依然是智能手机时代的玩家，毕竟供应链，技术，渠道其实与智能手机是类似的。

john carmack : 
http://venturebeat.com/2015/03/04/oculuss-technology-guru-john-carmack-explains-why-hes-spending-all-his-time-on-mobile-vr/
http://www.roadtovr.com/oculus-cto-affirms-positional-tracking-priority-for-gear-vr

http://www.leiphone.com/news/201409/duUN7UvC2Sh0oJzA.html

- Standalone VR(2020 - 2025)
[A standalone VR headset is the future of VR](https://www.oculus.com/en-us/blog/virtual-realitys-bright-future/).
上述3中硬件形态都可以看作某种计算平台的外设存在，最终的发展方向一定是VR设备自身成为一种计算平台，拥有独立的硬件及OS. 是VR设备的终极形态，计算能力，续航能力还需要整个产业提升，还处于实验阶段，需要更长时间。最终的硬件形态也许类似于眼镜，足够的舒适，轻便，便于携带。

最有可能从mobile VR 演化而来，不再作为手机的外接设备存在，而是作为自成一体的VR设备存在。可以确定的是，同手机一样，最后绝大部分 *一体VR* 的OS也将会是Android，就如同Android在Phone, tablet设备上站稳脚跟之后，向TV, Wearable, Auto渗透一样，[向VR渗透](http://www.theverge.com/2015/3/6/8164543/google-is-reportedly-working-on-a-virtual-reality-version-of-android). 一旦google开放AOSP出来，类似于小米的Minui，点心，乐蛙这样的第三方ui也会出现，但这一次难度要大的多，因为一旦市场形成，各个大公司都会倾向于组建团队自行研发，类似于智能手机时代的小米公司也有可能出现。



技术上，Android for VR将 Gear VR所做的工作标准化，减少[渲染的延迟](http://mi.chinabyte.com/5/13287505.shtml)，支持3D显示

**结论是未来VR平台的OS依然会是由Android统治**

相对于手机，VR/MR设备还有个巨大的好处，解决颈椎病问题。随着PC的普及，不良座姿和久坐导致的颈椎病日益多发，智能手机的普及更加剧了这个问题。不管是吃饭，睡觉，走路，工作，更多人更长时间低着头盯着屏幕。结果是颈椎病的发病年龄更小，发病时间更短。而VR/MR则是需要不断的运动脖子来和虚拟的世界交互，这样不但会增强颈椎的韧性和强度，而且可以解决颈椎病。


至于MR，Hololens已经树立了标杆：移动一体化

### 计算设备
整机厂商依然是 深圳 的优势所在，但一旦大公司发力，进入价格战阶段，基本上就是和 智能手机 的发展轨迹一样，最后只剩下几家巨头企业。

同时硬件的发展受到摩尔定律的约束，比如智能手机从2011年高速发展，到2015年就已经增长缓慢()

在尝鲜者取得市场规模之后，整个行业进入增量市场阶段，每个参与者都能活的很滋润，依靠深圳的硬件设计及制造能力，市场快速扩大，并充分竞争，同时jiyu此丰厚利润的大厂开始介入，导致价格进一步下降，同时市场更趋饱和，进入存量市场之争，最终活下来几个巨头。

因为VR的硬件组件与智能手机有很多相同之处，所以现在的智能手机相应的模组方面的玩家依然是现有的智能手机产业链上的参与者。

- CPU : qualcomm, samsung
- GPU : nvidia, qualcomm, AMD
Intel & Nvidia在PC时代，而在移动互联时代则是Qualcomm，在AI,VR时代早期，Nvidia则占据先机
Nvidia GTX970

- Memory : Samsung
- Flash : Samsung
- display： OLED , samsung，LG，Sony
  2560X1440 ，2k屏幕的颗粒感，纱窗效应(screen-door effect)明显，也许4K会好一些，但4K功耗太高，对手机没什么用处。
2015.05.26 [Announcing the Acquisition of Surreal Vision](https://www.oculus.com/en-us/blog/announcing-the-acquisition-of-surreal-vision/)

> The Display Even the best LCD can take 15 milliseconds for all its pixels to change color. The Rift uses AMOLED screens, which can switch color in less than a millisecond. 

- Camera : sony 
- 输入： 传感器，蓝牙手柄，红外跟踪，动作捕捉
交互方式需要革新，从PC时代的键盘/鼠标，功能手机时代的键盘/滚轮，到智能手机时代的触摸屏/虚拟键盘，VR时代的输入方式，目前以触控板，手柄为主，对于游戏而言勉强能接受，但更自然的方式绝对是手势，毕竟像文字输入这样的工作用手柄来做是很痛苦的一件事，使用手指敲击虚拟键盘会自然得多。
Hololens定义了三种输入方式： gaze, gestures and voice 

### 外设
交互和跟踪(头部，全身)
Oculus Touch/ 
HTC lighthouse
触觉手套

## 投资
看趋势 -> 选行业 -> 选公司 -> 信息(财务，团队)

依然按照 产业链层次结构 进行选择，

A股市场：顺网科技(与HTC Vive合作网吧推广)，歌尔声学(光学，声学组件，SONY，Oculus供货商)，劲盛精密(HTC vive研发，生产)，奥飞动漫(投资布局)，
一级市场: 诺亦腾

对于VR游戏，游戏的不确定性太强，很难有直接的标的

看好VR直播，刚性需求，有明确的盈利的模式，有价值的再创造，提高效率，降低成本：对内容提供者，可以数量级的提高用户量；对VR直播平台，可以聚集用户，收取适当的中间费用；对用户可以花低成本体验现场演唱会；是多盈的局面。
目前主要的公司有NextVR(华人文化 入股 http://www.sootoo.com/content/665560.shtml)，传统的互联网视频公司(youtube, youku, )，互联网直播公司(?)

http://www.sootoo.com/content/665589.shtml
华人文化控股成立:黎瑞刚与阿里腾讯重构资本版图 http://finance.eastmoney.com/news/1670,20151102561579132.html

但是从Youtube，优酷等10多年一直亏损的情况来看，内容平台盈利的时机需要很长，而且还要不断面对监管。

# 技术
个人认为，游戏和直播是刚性需求，市场空间最大，直播本质上是流媒体技术的应用，一旦技术成熟，更重要的是内容和运营；游戏 也同样出如此，一旦探索出一套通用的VR/MR游戏范式，那么中重要的是创意，渠道。

VR对图形渲染效果的极致要求与当前硬件性能不足之间的矛盾决定了图形系统的优化是VR开发技术的关键所在，也就要求VR的开发者要有很深的图形学理论知识背景。

VR游戏与一般的3D游戏开发所需的技术是很相似的，除了rendering上有差异，主要的差异在交互及设计上，所以拥有3D开发经验的公司和个人在VR的开发上会拥有巨大的优势。

从技术架构的角度看：

Application  :   Game/LiveStreaming/
-----------------------------------
Engine       :   Unity/Unreal
-----------------------------------
SDK          :   Oculus Mobile SDK/Google VR SDK/Windows 10 SDK/VRWorks
-----------------------------------
Platform     :   Android/Windows
-----------------------------------
Graphics API :   Vulkan/DirectX
-----------------------------------
Hardware     :   CPU/GPU/Camera/Display/Sensors/...

可以看到技术架构层与之前说过的产业链其实是有对应关系的，作为个人而言，选择适合自己的位置，并专注和坚持才是最重要的。

Computer Graphics(Vulkan), Computer Vision(OpenVX), VR/AR(OpenXR)都有Khronos建立开放的标准API

从具体技术类别来说，Computer Graphics和Computer Vison是技术基础，Unity/Unreal是开发工具，VR/MR是平台，游戏是应用领域。对Computer Graphcis和Computer Vision的学习内容参考Stanford的课程安排。

学习以下专业知识之前，需要一些必要的基础知识，比如数学(微积分:MATH41, 线性代数:MATH51，概率:CS109)，计算机体系结构(CS107)，计算机系统(CS110)，算法(CS161)，C++编程(CS106X)，这些知识的学习可以参考Stanford的课程。

在Stanford的课程设计中，Real-World Computing包含了Computer Graphics， Computer Vision， Robotics三个专业方向的课程，根据自己的兴趣选择一个行业方向，坚持既可。
Computer Graphics的应用领域：游戏；电影；动画；CAD；数据可视化；VR/AR                     参见 Stanford CS148
Computer Vision的应用领域 : 3D重建；SLAM；对象(人脸，手势)检测，识别，跟踪；VR/AR          参见 Stanford CS131
VR的应用领域 : 2C(游戏，直播，电影)，2B(医疗，地产，零售，教育，工程，军事，旅游)             参见 高盛VR/AR报告
AR的应用领域 : 2C(游戏，社交)，2B(医疗，零售(家居,服装和汽车)，教育，工程)                  参见 高盛VR/AR报告


## Computer Graphics
图形学，渲染，动画，游戏应用的入门

> Computer Graphics's Holy Grail : Virtual Reality.  
  --- [Pat Hanrahan : Stanford CS 348B](http://graphics.stanford.edu/courses/cs348b/lecture/introduction/slide_001) 

如果有充裕的可支配的时间，比如大学时期，可以按照Stanford的课程安排全面，系统，循序渐进的学习Computer Graphics，Computer Vison。对于可支配时间不连续的情况，只能根据实际需要有选择的学习，不管如何，stanford大学设计的[专业课程体系](https://exploredegrees-nextyear.stanford.edu/schoolofengineering/computerscience/)是我终身学习的指路明灯。

基础打的越牢，可选择的空间越大。Computer Graphics(计算机图形学)理论是所有后续相关知识的基础，只有理解Computer Graphics的原理，才能理解OpenGL API的设计原理，才能理解游戏引擎的设计和概念。

### [Stanford CS148 - Introduction to Computer Graphics](http://cs148.stanford.edu)
**Prerequisites: C++, CS107, MATH51**
**Reading:**
- Fundamentals of Computer Graphics, 4th Edition
- OpenGL Programming Guide: The Official Guide to Learning OpenGL, Version 4.3 (8th Edition)

**Topics:**
Scanline Rendering; OpenGl pipeline; Triangles; Rasterization; Transformations; Shading; Triangle Meshes; Subdivision; Marching Cubes; Textures; Light; Color; Cameras; Displays; Tone Mapping; BRDF; Lighting Equation; Global Illumination; Radiosity; Ray Tracing; Acceleration Structures; Sampling; Antialiasing; Reflection; Transmission; Depth of Field; Motion Blur; Monte Carlo; Bidirectional Ray Tracing; Light Maps.
**Target:**
rendering a CG Image
**目标：渲染出一个构想的CG场景画面**

计算机图形学

本课程大纲式的介绍了计算机图形的基本概念和原理：光栅化，变换，OpenGL，纹理，渲染，材质，光线跟踪，几何建模，动画等。因为是课程，所以内容都是提纲挈领，具有指导意义，主要目标是熟悉基本概念和进一步深入学习的方向，这里是[我的学习笔记](https://wangwh0204.github.io/2016/06/21/stanford-cs148-introduction-to-computer-graphics-and-imaging)。有些内容可能看不懂，可以google，也可以在学习和练习下面的内容后再回来理解，这是一个反复和循环的过程。

1. [Fundamentals of Computer Graphics](https://www.amazon.com/Fundamentals-Computer-Graphics-Fourth-Marschner/dp/1482229390/)
CS148参考本书的部分章节，在学习完CS148的Lectures后，就可以完整系统的阅读本书内容，从而加深理解，这是[我的读书笔记](https://wangwh0204.github.io/2016/07/28/fundamentals-of-computer-graphics-3rd)。

2. [Learn OpenGL](http://learnopengl.com/)
这篇关于OpenGL的在线教程，循序渐进，更贴近实战，作者最后还基于OpenGL封装了一些简单的类，并实作了一个游戏Breakout。可以跟着教材学习和实践，一定要亲自动手写代码，这是[我的学习笔记](http://wangwh0204.github.io/2016/10/19/learn-opengl)，在编码时遇到OpenGL API相关问题可以参考&lt;&lt;OpenGL Programming Guide 8th&gt;&gt;。

在2016.02.16 Khronos 发布[Vulkan 1.0 Specification](https://www.khronos.org/news/press/khronos-releases-vulkan-1-0-specification)，相应的产业链上的芯片驱动，引擎，应用，工程师使用Vulkan还需要一段时间爱你，可以提前学习，这样有一定的先发优势。

3. Real-Time Rendering
FCG是对图形学涉及到的理论，算法，应用的综述，RTR则如其名，更加深入到Real-time Rendering的细节中。

学完以上知识，就对计算机图形学有一个基本的认知，入门之后，还需要在实践中学习更多。

### Unity
在学习前，可以参看https://en.m.wikipedia.org/wiki/Unity_(game_engine)对unity的历史背景有个了解。
本课程使用来讲解。Unity3D是一个游戏引擎，提供了所见即所得的编辑器，基础组件，高层抽象，第三方plugin集成，广告，支付，性能分析等等工具以及完善的文档和例子，在他基础上可以更快速高效的构建游戏。但不管使用哪种引擎，对Computer Graphics基础知识的掌握都是必须的前提条件。目前开发3D应用主要有2个引擎：Unity，Unreal. Unity的好处是使用广泛，上手容易，可以快速开发；Unreal最大的好处是开放源代码，可以更好的掌控，当然前提是要有足够的实力去掌握它。
Game开发一般包含几个主要技术topic : Graphics(Rendering, Animation, Math/Physics, UI), Scripting, Networking, AI, Audio, 后续对Unity，Unreal的学习也以此为分类逐个进行。
GamePlay基于上述几个技术点实现业务，GameEngine则提供具体的实现，并模块化，

Rendering : CS148
Animation : CS248
Math/physics : CS205A
UI : CS147
Scripting :  提供脚本语言用于快速构建游戏核心玩法原型；适应业务需求的快速变更；主要的脚本语言是Lua，Python
Networking : CS140 网络的重点在Server端
AI : CS221 主要是自动寻路 A*算法
Audio : 

相对而言，不管目标设备是Oculus Rift，还是DayDream Viewer，或者Hololens，Unity都是最佳的快速开发工具，除了设备/平台厂商提供各自SDK的Unity Plugin，Unity公司本身也在和这些公司合作，提供Native的集成。 
因此对它的掌握有助于快速开发3D应用。采用理论与实践相结合，Learning by doing的学习方法会更有效率。

先将Manual看一遍，熟悉Unity及相关概念；再根据tutorial，做做实际的练习，改改属性和代码，加深理解；最后再设计和实现一些小游戏。

Unity使用Mono来跨平台部署，也就是Unity Editor，Unity Enigne都可以做到跨平台发布，那么Unity Engine暴露的API也顺理成章的使用C#作为脚本语言调用，而很多团队为了快速开发和热更新，在C#基础上又做了一层Lua绑定，用Lua来开发

1. C#
Unity目前支持C#及UnityScript(类JavaScript)，参考[这篇文章](http://blogs.unity3d.com/2014/09/03/documentation-unity-scripting-languages-and-you/)，选择学习C#. 如果没有编程经验可以通过阅读[&lt;&lt;Learning C# Programming with Unity 3D&gt;&gt](http://www.amazon.com/Learning-C-Programming-Unity-3D/dp/1466586524/) [记](http://wangwh0204.github.io/2016/02/20/learning-csharp-programming-with-unity3d)入门；

Unity使用的Mono CLR，支持的C#版本是2.0，因此在使用一些高级的语法特性时要注意。

IL2CPP

- Essential C#
熟悉C#的语法，语义，也可以与C++，Java做个对比，对于有C++编程基础的人来说，C#入门会很容易，重点在于有差别的地方，比如delegate, event, attribute, LINQ, lamba等

2. Unity Manual
将[Unity Manual](https://docs.unity3d.com/Manual/index.html)和[Unity Tutorials](https://unity3d.com/learn/tutorials)结合起来按topic阅读文档和实践：
Graphics, Physics, Scripting, Networking, Audio, Animation, UI, AI 

3. Unity Tutorials
参考例子代码，实际动手实践和思考，学习一些小游戏是如何设计和实现的。
模仿是最好的学习，通过阅读，分析其他人的代码，然后加入自己的想法，做一些修改和调试，可以更深刻的理解和提高实践水平。
- Unity官方案例精讲
这本书包含了Unity Tutorial里的[Space Shooter tutorial](https://unity3d.com/learn/tutorials/projects/space-shooter-tutorial),[Survival Shooter tutorial](https://unity3d.com/learn/tutorials/projects/survival-shooter-tutorial)例子的讲解。

- Unity游戏设计与实现
通过本书的例子练习不同类型的游戏如何设计和实现，可以加深对Unity的理解和应用，并开始了解制作游戏的思路，方法。

### [Stanford CS248 - Interactive Computer Graphics](http://cs248.stanford.edu)
**Prerequisites: CS148**
**Reading:**
**Topics:**
The course has a strong focus on computational geometry, *animation*, and *simulation*. Topics include splines, implicit surfaces, geometric modeling, collision detection, animation curves, particle systems and crowds, character animation, articulation, skinning, motion capture and editing, rigid and deformable bodies, and fluid simulation.
**Target:**
make a video game
**目标：制作一个包含Animation，Particle，Rigidbody的单机3D游戏**

CS148 focus在Rendering知识, CS248则focus在Geometry(建模), Animation, Simulation(Particles, Rigid Bodies)三个方面，本课程的目标是创建一个游戏。

课程的内容介绍Animation涉及的基本理论和原理，具体的实践结合[Unity](http://unity3d.com)来实现。

关于Computer Animation的书籍还有：

- Computer Animation : Algorithms and Techniques

- Advanced Animation and Rendering Techniques: Theory and Practice

The Computer Animator's Technical Handbook
The Animator's Survival Kit

### [Stanford CS205A - Math for Robotics, Vision and Graphics](http://cs205a.stanford.edu)
**Prerequisites: MATH51, CS106b/X**
**Reading:**
- Numerical Algorithms 	Solomon, Justin. 
为后续的Graphics, Vision, Robotics的学习储备必要的数学知识

其他参考书籍：

- Mathematics for 3D Game Programming and Computer Graphics, 3rd
3D游戏与计算机图形学中的数学方法

- Computational Geometry: Algorithms and Applications, 3rd

### Dive Into Graphics

如果想更深入的研究Computer Graphics技术，以游戏开发，操作系统GUI，CAD软件，CG特效为职业方向，可以继续学习如下课程：
- [Stanford CS348A - Computer Graphics: Geometric Modeling](http://cs348a.stanford.edu)
- [Stanford CS348B - Computer Graphics: Image Synthesis Techniques](http://cs348b.stanford.edu)
本课程主要以Physically Based Rendering为授课内容
- [Stanford CS348C - Computer Graphics: Animation and Simulation](http://cs348c.stanford.edu)
**Prerequisites: CS148 and CS205A. ** 更多的是Physics Based Animation

如果是以 游戏引擎 为职业方向，则可以深入学习[Unreal](https://github.com/EpicGames/UnrealEngine)源代码，将理论和实现结合。

## AI
AI在AR/VR的应用与在智能机器人上的应用有一些共同的地方，比如通过Computer Vison感知真实世界，包括SLAM，3D Scene Understanding，手势识别； 通过Speech Recognition，TTS，NLP与人交互等。从这个意义上来说，AR/VR设备也是一种AI设备。

# 产品
对于VR/MR的应用，需要Computer Graphics技术来Rendering，Animation；Computer Graphics可以用于 机器人 的Simulation模拟仿真；

VR/MR是Computer Graphics和Computer Vision两种技术相结合的很好的应用；而且这种应用的适用范围足够大到成为一个平台，形成一个行业。

VR/MR从技术和工程的角度来看，尚处于探索，研发期，从设备到OS再到API，SDK都还没有形成标准，不利于内容的开发和产业链整合，从设备来讲在更远的未来，VR与MR将合二为一，只需要一个开关即可控制。

VR应用相对3D应用，一个是从视觉体验看，从平面(flat screen)变成立体(stereo screen)；第二是交互方式发生很大变化，个人处于虚拟世界中，需要重新探索设计的新模式；第三个是对硬件的要求更高，是3D技术的自然延伸。

在做VR应用开发前，有必要了解一下VR的基本原理及技术挑战，VR还处于技术探索期，还没有系统性，经验性的书籍，更不用说形成经典的书籍了，不过还是有先行者的一些思考和实践，可供学习，这样可以少走弯路，少填一些坑。
VR的成熟是在现有的移动硬件上自然的进化，光学设备，OLED屏幕，传感器，GPU等硬件基础元件的性能，大小，价格的不断进化，软件上在渲染上则需要对现有3D渲染管线进行改进；交互方式则完全不同以往，需要重新思考和探索；

1. stereo rendering(立体渲染)
2. optical distortion(光学畸变)
3. motion-to-potion latency(20ms)
4. inside-out tracking
5. HCI(voice, gesture, gaze, touchpad)

MS和Magic Leap提出的概念，也就是See-through AR，真实世界和虚拟世界是融合在一起的，而不像VR那样是纯粹的虚拟世界。在未来MR和VR将会融合为一体，通过一个开关即可切换。目前可以用的MR设备就是Hololens，对应的OS是Win10，SDK是Holograph SDK，一个完整的从硬件到OS再到SDK的链条。
而VR还在摸索整合当中，设备很多种，OS也是基于Windows和Android，SDK也没有统一，OpenVX是可能的方向。

一种全新的人与机器的交互方式。
视觉，听觉，触觉，嗅觉和味觉

如前面所说，目前主要应用于2B市场，在2C市场还需要3-5年时间，MR技术，设计，依然在探索过程中...2B的业务一定是提升效率降低成本的刚性需求，这就要求深耕行业知识。

一般的AR应用使用Unity + Vuforia开发，现在则使用HoloLens + Win10 + Unity + Vuforia + VisualStudio

因为技术还处于探索阶段，并没有很成熟，成系统的书籍资料
目前不管是VR还是MR，并没有形成成功的可复制的设计，交互模式，依然在探索和试错中。

对Computer Graphics，Unity，VR的学习和实践，这些知识的储备都是为了这一步: 构建自己的VR应用. 不是简单的demo，而是完整的自己想要玩的游戏，此所谓“厚积薄发"。

相比现有的主机游戏，PC游戏，网页游戏，手机游戏，VR游戏在设计上是一个全新的领域，正如Jason Rubin所说 : 
> Virtual reality requires an entirely different approach; from systems and protocols to game design and storytelling, everything is being reimagined from the ground up to deliver experiences that are entirely new and magical. --- [Jason Rubin joins Oculus](https://www.oculus.com/en-us/blog/jason-rubin-joins-the-team-and-oculus-at-e3-2014/)

- [Michael Abrash' blog](http://blogs.valvesoftware.com/abrash/)
Michael Abrash的Blog文章写于他在Valve做VR & AR相关研究的2012 - 2014年之间，在2014年初，Facebook收购Oculus后，他随即加入Oculus担任Chief Scientist，这之后他的想法主要在Oculus Connect上以演讲的形式呈现。
关于Michael Abrash的职业经历散落在他的blog里面。他的BLOG对我在学习VR的影响很大，开阔了我的视野，重要的是指明了方向，他的文章重点关注基本原理以及VR未来发展方向的构想。
普及了VR/AR相关知识，并做了很多技术/产品趋势的预言。

- [Stanford EE267 - Virtual Reality](http://stanford.edu/class/ee267/)
要对VR有一个全局的认知，可以参考stanford大学在2016.03.28开设的关于VR的课程：[Stanford EE 267: Virtual Reality](http://stanford.edu/class/ee267/)，内容包括：VR历史，Graphics Pipeline and OpenGL, stereo rendering，IMU, Unity, Haptic Perception, etc...这里是我的[学习笔记](http://wangwh0204.github.io/2017/04/03/stanford-ee267-virtual-reality)

- [Stanford CS211 - Content Creation in Virtual Reality](http://cs211.stanford.edu/)
内容还未开放

- [Stanford CS213 - Creating Great VR: From Ideation to Monetization](http://cs213.stanford.edu/)

MKTG 559: Designing for VR/AR

Author VR in VR https://github.com/Unity-Technologies/EditorVR

[Stanford CS377M - HCI in Mixed and AR](http://cs377m.stanford.edu)
- 3D User Interfaces: Theory and Practice, Second Edition 
https://www.safaribooksonline.com/library/view/3d-user-interfaces/9780134034478/

Displays
*Tracking and Registration.* How do we understand the world and provide that information to the person and system. 
*Rendering & Authoring, Shadows, Relighting, Occlusions. *
*Perceptual & Cognitive Issues.* Visibility, object relationships, registration errors, layer interference, individual differences, depth perception cues. 
*Interaction Techniques.* 3DUI, Selection & manipulation, Tangible AR, Wayfinding, System Control, 
*Authoring.* Creating AR systems, content in AR systems, out of system and in-situ authoring. AR-specific infrastructure. Unity. 
*Visualization:* Types of representation, situated visualization, situated learning, situated analytics. Spatial data. ZUIs in AR. 
Applications: Enterprise, Consumer, Medicine, Manufacturing, Education, Games, Art, Media, & Humanities

## Platform
除了硬件，OS，VR/MR SDK，Unity/Unreal，Application
和PC，Mobile Phone的产业链一样，掌握OS平台的公司拥有最大话语权，掌握应用入口的公司次之。
在PC时代，是微软/Intel联盟；在Mobile时代，是Google/Qualcomm，Apple/Apple；在VR/MR的OS层面，不大可能有新的平台产生，而是延续Windows，Android，iOS三足鼎立的态势。

参与各方，微软，Applge，Google依然控制着OS，同时提供VR/MR SDK，以及参考硬件

Unity/Unreal

Oculus SDK/OpenVR/VRWorks
OpenGL/Vulkan
Windows/Android
CPU/GPU/BSP

目前最佳的VR体验平台是PC，但未来主流的VR OS(不管是Mobile VR，还是Standalone VR)毫无疑问是Android，对Android图形系统的研究有助于更好的开发移动VR应用，当然最主要的是我之前对Android平台有过开发经验。
整个行业还处于探索初期，目前并没有统一的API，各个设备厂商自行设计自己的一套API，好在

平台提供如下支持，以简化VR开发工作：

Side-by-side stereo rendering.
Lens distortion correction.
Head tracking.
Spatial audio.
3D calibration.
Stereo geometry configuration.
User input event handling.

1. Oculus VR
在Android提供VR系统支持前，Oculus已经和Samsung合作开发基于Android的Mobile VR设备: Gear VR。Oculus(主要是John Carmack)通过改造Android系统支持VR，包括ATW，FrontBuffer Rendering，并提供了SDK用于Native及Unity，Uneral等引擎的封装来开发Oculus VR上的VR应用。

Oculus Mobile SDK提供了C语言的Native API，也提供了Unity的Plugin。

2. Google VR
2016.05.18  Google IO大会上公布Android N(7.0)支持VR模式，并提供[Google VR SDK](https://developers.google.com/vr/)

2016.08.22  Android 7.0 的[源代码被推送到AOSP](http://android-developers.blogspot.com/2016/08/taking-final-wrapper-off-of-nougat.html)

DayDream除了提供基于C语言的Native API，以及 Unity Plugin，同时也对Android系统进行了改造以适应VR的要求，最主要的改进是达到motion-to-potion的20ms延迟，对Daydream代码的研究，有助于理解VR在OS层面的实现机制。

在2016.09.22开始，Unity提供Native的Google VR SDK集成的Technical Review版本：https://unity3d.com/partners/google/daydream

对于Oculus Mobile VR和Google VR SDK，我的判断是，Oculus会做出妥协，支持Google VR SDK，这样在Mobile端(Android)上达成统一，标准的API。

### Oculus Rift

- Unity VR Topic
特别的，在2015.12.09 Unity post 一篇关于可以开始在Unity上开发VR应用的[blog](http://blogs.unity3d.com/2015/12/09/get-started-with-vr-sample-pack-learning-articles/)，VR topic相关的文章也被增加到了[Unity Manual](https://docs.unity3d.com/Manual/VirtualReality.html)和[Tutorials](http://unity3d.com/learn/tutorials/topics/virtual-reality)

- Oculus VR Sample
[Introducing the Oculus Sample Framework for Unity 5](https://developer.oculus.com/blog/introducing-the-oculus-sample-framework-for-unity-5/)

- Oculus VR Best Practices
将3D Game改造成VR Game，主要的差别在交互体验上，Oculus作为行业的先行者，探索和总结了一些经验教训：
- [Oculus Best Practices](https://developer.oculus.com/documentation/intro-vr/latest/concepts/book-bp/)

- [Oculus Developer](https://developer.oculus.com/)
主要是参考Oculus在VR开发中的经验，心得，减少自己探索的弯路。https://developer.oculus.com/
- [Squeezing Performance out of your Unity Gear VR Game](https://developer.oculus.com/blog/squeezing-performance-out-of-your-unity-gear-vr-game/)
- [Squeezing Performance out of your Unity Gear VR Game Continued](https://developer.oculus.com/blog/squeezing-performance-out-of-your-unity-gear-vr-game-continued/)
- [Unitys UI System In VR](https://developer.oculus.com/blog/unitys-ui-system-in-vr/) [译](xxx)


- [VR Sickness, The Rift, and How Game Developers Can Help](https://developer.oculus.com/blog/vr-sickness-the-rift-and-how-game-developers-can-help/)

- [Optimizing VR Graphics with Late Latching](https://developer.oculus.com/blog/optimizing-vr-graphics-with-late-latching/)

- [Asynchronous Timewarp Examined](https://developer.oculus.com/blog/asynchronous-timewarp-examined/)   译 ： http://blog.csdn.net/zangle260/article/details/44945421

### [Hololens](https://developer.microsoft.com/en-us/windows/mixed-reality)
Hololens主要提供了Stereo Display，Natural Interaction(Gaze，Gesture，Voice)，Spatial Perception(Spatial Sound，Spatial Mapping)特性，花了2个月时间对Hololens/MR的应用，设计，开发有了一定的熟悉，这里是我的[学习笔记](http://wangwh0204.github.io/2017/05/25/windows-mixed-reality)

微软的Hololens提供了参考硬件设备，Win10提供了OS，Holographic SDK则提供MR API，提供了Spatial Reconstruction的能力，物体识别和虚拟场景则要分别交给Vuforia和Unity来实现。

- [Vuforia](https://www.vuforia.com/)
世界上最广泛使用的商用AR SDK，提供跨平台的发布，物体识别，大部分AR从业者都在使用Vuforia + Unity开发产品。

## VR/MR Game
除非是在学术界做科研，否则在工业界，技术就是要为产品服务，产品则为市场需求而生。不合时宜的技术，比如90年代的深度学习，没人买单的产品，比如Motorola的铱星项目，最终以失败告终。

游戏本质上是一种创意商品，与影视，小说，动漫一样，提供一种不同形式的文化娱乐方式。游戏行业发展至今，已经有一些规律和经验可以借鉴，除了学习技术，我们也要从更高层的视角来学习和思考行业，吸收经验，少走弯路，包括发展历史，产业链分工，商业模式，制作经验，团队管理等。

VR/MR是一个计算平台，除了平台本身外，在这个平台上做什么，才是需要真正思考的，是实现事业的载体。想象一下，一旦几年后，VR/MR和手机一样成熟了，难道还去追另一个新的热点，平台么？ 对于以游戏作为终身职业的人来说，VR/MR只是像曾经的PC，Web，手机一样提供了一种全新的娱乐平台。

技术最终要为应用服务。从产业链现状来看，还是技术架构来看，VR/MR除了设备，OS，API之外，应用层面的应用是我们的主要目标。不管VR还是MR平台，游戏都是最有前(钱)途的应用方向，从历史来看，不管是PC时代，还是互联网，移动互联网时代，游戏都是刚需，且是最赚钱的方向；在未来AI时代，低端重复的工作有机器/AI来完成，人们因此有大量的空闲时间，所以文娱产业还会有爆发性的增长，基于VR/MR的娱乐方式(影视，游戏，动漫，小说)可以提供更沉浸的体验，必然会成为新的浪潮，也必然会引发社会对人的价值的再思考。

- 游戏改变世界
要用做游戏的思维方式来工作，学习，社交。但所谓改变世界难免拔的太高，太把自己当回事，更多的是一种思维方式的变化。比如团队合作，即时反馈，表扬甚于批评...

-  **娱乐至死**
自省用。对商业来说，利用人性的弱点来获得财富，对个人来说，至少要知道娱乐并非生活的唯一，而且是比较低层次的需求。

- 爆款
娱乐业商业，营销策略，一款产品就够了，但这是多年的经验磨练出来的。从各个游戏厂商，不管是Billizard，Valve，SuperCell，只需要数款产品即可。对用户来说，一款产品足以，比如歌手通常就一个代表作，演员就几个代表作，对游戏公司也是如此。但从团队的角度，是经过多款产品的试错，和持续的试错，反馈，打磨而成的。
从SuperCell的经验，专注一款同时通过小规模试错来获得改进或放弃。

- The Art of Game Design, 2nd
游戏设计的艺术

特别的，对于VR/MR的应用场景和idea，可以看看科幻小说(SF)，电影，动漫来增长见识，开阔眼界，吸收其他人的想法，比如&lt;&lt;神经漫游者&gt;&gt; 1984, &lt;&lt;Snow Crash&gt;&gt;(雪崩) (Neal Stephenson 1994),  &lt;&lt;Rainbow’s End&gt;&gt; 彩虹尽头 (Vernor Vinge 2006) , &lt;&lt;Ready Player One&gt;&gt; Ernest Cline 2011 [玩家一号]
视频可以看看  &lt;&lt;黑客帝国&gt;&gt;, &lt;&lt;刀剑神域&gt;&gt;，&lt;&lt;黑镜&gt;&gt;

通常，一款游戏的制作涉及到策划，程序，美术三种角色，也许还要加上运营。
先了解一个游戏的开发过程是怎样的，有个宏观的认知和理解，团队角色及分工，开发过程等相对于其他的软件开发团队有什么不一样的地方?
游戏编程涉及下面几个主题：Graphics(Rendering, Math/Physics, Animation, UI), Scripting, Networking, Audio, AI

游戏开发已经细分为客户端和服务器，客户端又细分为gameplay programming， game engine programming

- Game Coding Complete, 4th
介绍游戏编程中涉及到的几个技术领域，与Unity等引擎的主题一致，包括渲染，物理，动画，UI，脚本，网络，音频，AI

- Game Engine Architecture

有了idea，也知道如何设计，如何编程实现，那就可以制定计划，先实现核心玩法，然后迭代增量开发。
根据需求做技术预研及demo实作，实现核心玩法

对游戏设计，编程有了理解后，最困难的是如何创造能让用户购买的创意产品。模仿，改进，创新也许是最佳的路径。

游戏引擎，比如Unity和Unreal，除了提供完整的开发Editor外，技术上主要由如下几个topics： Graphics(Rendering，Physics, Animation, UI), Scripting, Networking, Audio, AI讲学习的重点放在Graphics相关的实现上。
对VR/MR引擎的研究重点放在VR/MR的特有特性上： Stereo Rendering，Spatial Perception，Interaction Input，Natural UI上。
游戏引擎一般包括Graphics(Rendering, Animation, Physics/Math, UI), Scripting, Networking, AI, Audio等主题，这些主题并无特定顺序，根据实际需要学习和实践。

