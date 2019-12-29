title: Windows Mixed Reality
date: 2017-05-25
updated: 2017-09-04
categories:
- [technology]
tags: 
- MR
- Hololens
- Unity
---

有机会使用Hololens真机做一些调研工作，也为后续的项目做好技术和设计知识储备。这里是一些学习中的笔记。<!--more-->

从学习Hololens开发的结果看，技术上与3D游戏的开发类似(特别是渲染，动画)，在设计上则需要重新探索，那么Hololens的核心价值在于立体显示上，商业价值在于提升效率，能更加高效的设计，沟通，理解。
Hololens中使用了很多AI技术，包括手势识别，语音/命令识别，Spatial Mapping()，Spatial Understanding(墙壁识别)，可以看做是Computer Vision里的SLAM和3D Recognition的应用。

# [Hololens](https://www.microsoft.com/en-us/hololens)
Mixed reality: Your world is the canvas
Microsoft HoloLens is the first self-contained, holographic computer, enabling you to engage with your digital content and interact with holograms in the world around you.

相对PC，平板，手机这样的2D空间设备，Hololens有如下几点完全不一样的地方：
- 3D(三维空间)
从2D空间的正方形一个面，到3D空间的立方体6个面

- Stereo Display(立体视角)
立体相对平面，有了深度信息，更接近现实世界的感受

- Interaction(人机交互)
从鼠标，键盘，触摸屏这样的2D交互到Gaze，Gesture，Voice这样的自然交互方式

- Spatial(空间感知)
一种全新的方式，基于SLAM技术的空间感知，以及基于Computer Vision的空间理解；除此外Spatial Sound让人更有身临其境的感觉，达到Vitual与Real融为一体

但从Hololens(Development Edition)的使用上，还有提高的地方：
- 价格要降低
3000美金，23000人民币，对于普通消费者来说难以承受，而且还没有通话功能；和一台PC或者高端手机一样，1000美金应该是可以大规模普及的价格
- 舒适度要提高
重量579g，而且是勒住头部，长时间使用会不舒服；而且FOV比较小(40度?)，眼睛经常要上下运动，会比较累
- 交互方式需要丰富
目前的文字输入还是能够接受的，只是长时间使用胳膊会酸胀；而且手势太少，只有air tap和bloom，有些交互不自然，比如上下滚动内容比较困难；移动，拉伸3D物体还是传统的2D的方式，不自然
- 杀手级应用
在PC平台上，办公软件和游戏是杀手应用；在手机平台的通信，社交，游戏是杀手应用；那么在Hololens上，还没有杀手应用场景，我个人觉得[Holoportation](https://www.microsoft.com/en-us/research/project/holoportation-3/)最有希望(因为这就是科幻里梦寐以求的全息投影，用来社交，直播，会议交流)；相对而言VR的杀手应用应该会在游戏，视频，直播领域产生。
- 场景理解
包括环境光照的感知，物体的材质，物理特性等
目前只有基本的plane和wall的识别，对于真实世界场景的识别(CV)，理解(AI)还需要提升


对于新一代的Hololens，具体时间和规格并没有详细的信息，根据网上透露的消息，微软将在2019年直接出适用于消费者的第3代，可持续关注。

从技术的角度来说，融合了Computer Graphics(Stereo Rendering)，Computer Vision(SLAM, 3D Scene Recognition)，Speech Recognition，NLP

## [Why Hololens](https://www.microsoft.com/en-us/hololens/why-hololens)
Mixed reality brings people, places, and objects from your physical and digital worlds together. This blended environment becomes your canvas, where you can create and enjoy a wide range of experiences.

- Holograms enhance the real world
Interacting with holograms in mixed reality enables you to visualize and work with your digital content as part of your real world. 

- A more natural way to interact
Holograms are responsive to you and the world around you. Microsoft HoloLens enables you to interact with content and information in the most natural ways possible: Gaze, Gesture, Voice
Gaze : Bulit-in sensors let you use your gaze to move the cursor so you can select holograms. Turn your head and the cursor will follow.
Gesture: Use simple gesture to open apps, select and size items, and drag and drop holograms in your world.
Voice: Use voice commands to navigate, select, open, command, and control your apps. Speak directly to Cortana, who can help you complete tasks.

- Connect, create, and explore
Transform the ways you communicate, create, collaborate, and explore. Your ideas are closer to becoming real when you can create and work with holograms in relation to the world around you.

- collaborate and communicate
When you collaborate, it’s easier to show than to tell. Your Skype contacts can overlay sketches and holograms on physical objects in your view.

- Create what you imagine
Shape holograms to fine‑tune a design, share ideas, and understand your creations in relation to the real world.

- Visualize your work
Go beyond what a 2D render can do by working in 3D. Make smarter decisions and prototype faster when you can inspect every vantage point.

- Explore places and ideas
See holograms from your colleague's perspective even if she's on the other side of the world. Explore ideas in the real world, inside and out.

## [Hololens Hardware](https://www.microsoft.com/en-us/hololens/hardware)
更具体的参数在https://developer.microsoft.com/en-us/windows/mixed-reality/hololens_hardware_details

- Optics
see-through holographic
Holographic resolution: 2.3M total light points

- Sensors
1 IMU, 4 environment understanding cameras, 1 depth camera, 1 2MP photo/HD video camera, 1 ambient light sensor

- Human understanding
Spatial sound, Gaze tracking, Gesture input, Voice support

- Input/Output/Connectivity
volume up/down, brightness up/down, wifi 802.11ac, bluetooth 4.1 LE

- Power
Battery life(2-3 hours of active use, up to 2 weeks of standby time)
Passively cooled(no fans)

- Processors
Intel 32bit, Holographic Processing Unit

- Weight
579g

- Memory
64GB flash, 2GB RAM

## [Apps](https://www.microsoft.com/en-us/hololens/apps)
第一波应用，有游戏(RoboRaid，Fragments，Yong Conker，MinaCraft)，IM(Skype, 试验中的Holoportation), 辅助设计工具(HoloStudio, Actiongram)，教育(HoloAnatomy)，缺社交类应用。

Cortana作为Win10内置的 "虚拟AI助理"，现在是没有可视化的形象的

- [Skype](https://www.microsoft.com/en-us/hololens/apps/skype)
语音视频通话工具，语音效果非常良好，也可以远程视频通话，PC上的Skype可以看到Hololens上的MR场景，也可以对MR场景做涂鸦，放置3D物体等...

- [HoloStudio](https://www.microsoft.com/en-us/hololens/apps/holostudio)
Build 3D in 3D with natural gestures and movement, creating holograms with holographic tools modeled from tools in the real world.
在Hololens中创作Hologram的工具，导入3D Model(FBX)，导出Hologram
可以使用OneDrive来保存到云端，也可以导出到3D Builder用3D Printer打印出来，还可以分享Sketchfab.com

- [Actiongram](https://www.microsoft.com/en-us/hololens/apps/actiongram)
Actiongram enables new forms of storytelling. Move, resize, rotate, and record holograms in your home, creating videos you can share with friends.
可以将Hologram放置在现实世界中，用来制作一种混合现实的视频，还可以展示一些动画，粒子，特效，做一些酷炫的视频效果。

https://blogs.windows.com/devices/2016/03/14/introducing-actiongram-a-completely-new-holographic-storytelling-medium

- [HoloTour](https://www.microsoft.com/en-us/hololens/apps/HoloTour)
Feel like you’re really there
A combination of panoramic video, holographic scenery, and spatial sound creates a virtual travel experience with a real sense of presence and depth.

一个Rome全景视频的例子，Experience an immersive combination of 360-degree video, spatial sound, and holographic scenery with HoloTour

- [RoboRaid](https://www.microsoft.com/en-us/hololens/apps/RoboRaid)
交互，效果良好的MR FPS游戏

- [Yong Conker](https://www.microsoft.com/en-us/hololens/apps/young-conker)
利用现实世界空间，设计游戏玩法和交互方式，MR平台才有的特殊游戏类型。
Young Conker transforms your furniture, floors, and walls into the stage for a mixed reality platforming adventure.
Every level you finish becomes fresh again when you play it in a different room, or rearrange your furniture.
Use spatial mapping and custom AI to dynamically generate game levels and character placement.

- [Fragments](https://www.microsoft.com/en-us/hololens/apps/fragments)
You become the detective in a high-tech crime thriller. Experience compelling new possibilities for storytelling and gameplay.
Life-sized holographic characters are aware of your presence and interact with you and your space as if they’re really in the room.

室内解谜游戏，与虚拟角色，在半真半虚的场景中互动，很有代入感，容易让人沉浸其中，是游戏和电影叙事方式的融合。Room solver AI

## Commercial
按照 [Satya Nadella hints that Microsoft's mind-blowing new product HoloLens is really 5 years away](http://www.businessinsider.com/nadella-hints-hololens-is-5-years-away-2015-9)，所以3~5年内，Hololens以2B应用为主。

Microsoft Hololens transforms how you work with 3D data. Unlock new possibilities for business and productivity.

- AEC&Design
Preview designs at scale and reconstruct 3D models quickly. Work more safely with eyes up and hands free. Clients, designers, remote teams, and on-site engineers can collaborate, visualize, and create in 3D, bringing complex designs to life.

- Education
Approach curriculum from a new point of view when students can investigate, walk around, and delve inside their subjects. HoloLens blends physical objects and environments with 3D data, helping to increase students’ engagement and understanding of abstract concepts. Around the world, educators are exploring how holographic visualization can help increase students’ engagement and joy of learning. With Microsoft HoloLens and Windows Mixed Reality, students can discover new dimensions to their subjects and reach deeper understanding when they learn in 3D. Learning comes alive when flat illustrations become 3D images students explore, alter, and examine from every angle. 

- Gov't & Utilities
Visualize complex data with holograms to collaborate in 3D project environments while optimizing flexibility, safety, and cost-efficiency. Enable remote, cross-functional teams to connect and share.

- Retail
Lower the barrier to purchase when customers can go beyond physical inventory, sampling different product features from virtual catalogs. Retail planners and merchandisers can visualize designs, share plans with others, and walk through their floorplans before they build.

- Healthcare
Envision a surgery before it starts, or a hospital before it’s built. Learn and direct medical training in real-world environments. Plan and research the right healthcare solutions for your patients when you can visualize the human condition as it truly is—in 3D.

- Manufacturing
Create flexible, safe holographic training scenarios in the real world. Give clients 3D prototypes they can visualize and inspect. See and identify problems before work starts. Teams can deliver results faster when they understand and iterate in mixed reality.

除了Development Edition，微软还提供了Commercial Suite，Key features:
- Kiosk mode
With HoloLens kiosk mode, you can limit which apps to run to enable demo or showcase experiences.
- Mobile Device Management
Your IT department can manage multiple HoloLens devices simultaneously using solutions like Microsoft Intune.
- Windows Update for Business
Controlled operating system updates to devices and support for long term servicing branch.
- Data security
BitLocker data encryption is enabled on HoloLens to provide the same level of security protection as any other Windows device.
- Work access
 Anyone in your organization can remotely connect to the corporate network through virtual private network on a HoloLens.
- Windows Store for Business
Your IT department can also set up an enterprise private store, containing only your company’s apps for your specific HoloLens usage. 

# [Windows Mixed Reality](https://developer.microsoft.com/en-us/windows/mixed-reality)
最开始微软将Hololens所使用的技术称为Holographic，后又改为[Windows Mixed Reality](https://developer.microsoft.com/en-us/windows/mixed-reality),这些技术也应用到了VR设备上( inside-out tracking, six-degrees of freedom. )，微软通过与传统的PC厂商(Acer, ASUS, Dell, HP, Lenovo)合作，拓展[Win10平台/SDK到VR领域](https://blogs.windows.com/windowsexperience/2016/10/26/empowering-a-new-wave-of-creativity-with-the-windows-10-creators-update-and-surface-studio)。 可以看出微软对3D的决心，将操作系统3D化，将UI 3D化，支持3D内容的创作，分享，体验

https://developer.microsoft.com/en-us/windows/mixed-reality提供了构建MR体验所需的开发(Development)，设计(Design)，教程(Academy)文档：

- [Development](https://developer.microsoft.com/en-us/windows/mixed-reality/development)
介绍MR应用场景，技术细节，包括Coordinate Systems，Rendering，GGV实现原理，Spatial Perception，以及具体在Unity中的编程实践

- [Design](https://developer.microsoft.com/en-us/windows/mixed-reality/design)
关于MR设计的原则，MR Interaction Design，MR App Patterns，MR fundamental UI elements

- [Tutorials](https://developer.microsoft.com/en-us/windows/mixed-reality/academy)
使用例子代码，详细介绍core Windows Holographic features including: Gaze, Gesture, Voice, Spatial Sound, Spatial Mapping以及Sharing Holograms，所有代码都可以在https://github.com/Microsoft/HolographicAcademy/找到

- [Toolkit](https://developer.microsoft.com/en-us/windows/mixed-reality/Community.html#open_source_projects)
微软提供大量的开源的工具库和例子应用，帮助更好的理解和加速构建过程：HoloToolkit, HoloToolkit-Unity, MRDesignLabs, Galaxy Explorer, HoloLens Companion Kit

- [Case study](https://developer.microsoft.com/en-us/windows/mixed-reality/category/case_studies)
对于微软制作的第一类应用，微软也提供相关信息如何制作这些App, 这些经验教训有助于我们设计，开发自己的MR应用。

开发，设计，教程文档彼此之间交叉引用，我倾向于使用Learning by doing的方式针对一个主要的特性集中的学习理论，设计，编程等知识，所以按照我的学习，理解和实践过程将文档内容重新做了编排，整理。

## [Development Overview](https://developer.microsoft.com/en-us/windows/mixed-reality/development_overview)
开发MR应用需要[设备和工具](https://developer.microsoft.com/en-us/windows/mixed-reality/install_the_tools)，目前的最佳工具组合: Hololens + Win10 + [VS2017](https://developer.microsoft.com/en-us/windows/downloads) + Unity + Vuforia
Hololens : 开发者版本23488, 企业版39188
Win10 : 家庭版888，专业版1817
VS2017 : 专业版4850, 企业版58260
Unity Pro ：$125 x 12 x 7 = 10500
Vuforia : $99 x 12 x 7 = 8316

这样算下来，光开发环境的成本就要10万RMB，还未算上开发PC的配置(i7 + GTX1080 + 16G RAM)

微软将MR应用开发所需的API整合进[Win10 SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk)，并以[Universal Windows Platform](https://docs.microsoft.com/en-us/windows/uwp/get-started/universal-application-platform-guide)形态构建。All mixed reality apps are Universal Windows apps, and all Universal Windows apps can be made to run on Windows Mixed Reality devices.  一般的为PC和Phone开发的UWP 2D应用也可以在Holoens上运行，但是为Hololens开发的3D应用无法在一般的PC设备上运行。

Mixed reality experiences are enabled by new Windows features for environmental understanding. These enable developers to places a hologram in the real world, and allow users to move through digital worlds by literally walking about.These are the fundamental building blocks for mixed reality development: 
Input : Gaze, Gesture, Voice
Perception : World coordinates, Spatial Sound, Spatial mapping
除了Stereo Rendering外，这里提及的几个概念就是MR的核心内容，主要是空间的感知和交互，在后续的文档里会详细的说明。

The environmental understanding features like coordinates, spatial sound and spatial mapping provide the necessary capabilities for mixing reality. Spatial mapping enables holograms to interact with both the user and the world around them. Coordinate systems allow the user's movement to affect movement in the digital world.

- [Mixed Reality](https://developer.microsoft.com/en-us/windows/mixed-reality/mixed_reality)
Mixed reality is the result of blending the physical world with the digital world. Mixed reality is the next evolution in human, computer, and environment interaction and unlocks possibilities that before now were restricted to our imaginations. It is made possible by advancements in computer vision, graphical processing power, display technology, and input systems. The term mixed reality was originally introduced in a 1994 paper by Paul Milgram and Fumio Kishino, ["A Taxonomy of Mixed Reality Visual Displays."](http://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)

Real World vs Virtual World
Physical World vs Digital World

Environmental input captures things like a person's position in the world (e.g. head tracking), surfaces and boundaries (e.g. spatial mapping and spatial understanding), ambient lighting, environmental sound, object recognition, and location.

The experiences that overlay graphics on video streams of the physical world are *augmented reality*, and the experiences that occlude your view to present a digital experience are *virtual reality*. As you can see, the experiences enabled between these two extremes is mixed reality.

Skype for HoloLens, Fragments and RoboRaid are best experienced with HoloLens. Likewise, 360° video is best experienced on immersive devices. HoloTour showcases the best of what both types of devices can do today when trying to push towards the center experience of mixed reality.

6DOF的移动，指的是可以在X,Y,Z三个轴上平移和旋转 

个人认为未来的VR/MR设备将融合，通过一个开关即可切换，而AR这种Video-through方式依然是平面而非立体视角，只是手机的自然延伸，是一种过渡形态。VR/MR是两种不同的应用场景，可以满足不同的需求，因此会共存。

- [Hologram](https://developer.microsoft.com/en-us/windows/mixed-reality/hologram)
HoloLens lets you create holograms, objects made of light and sound that appear in the world around you, just as if they are real objects. Holograms respond to your gaze, gestures and voice commands, and can interact with real-world surfaces around you. With holograms, you can create digital objects that are part of your world.
A hologram is made of light and sound.  HoloLens doesn't remove light from your eyes, so holograms can't be rendered with the color black. Instead, black content appears as transparent.
A hologram can be placed in the world or tag along with you. A hologram interacts with you and your world

https://developer.microsoft.com/en-us/windows/mixed-reality/hologram_stability


### [MR Application Types](https://developer.microsoft.com/en-us/windows/mixed-reality/types_of_mixed_reality_apps)

MR的应用类型，主要分为下面三种：
- Enhanced environment apps(Hololens only)
One of the most powerful ways that mixed reality can bring value to users is by facilitating the placement of digital information or content in a user’s current environment. This is an enhanced environment app. 这可以理解为一般的MR，真实和数字世界融合在一起。
- Blended environment apps
Given Windows Mixed Reality’s ability to recognize and map the user's environment, it is capable of creating a digital layer that can be completely overlaid on the user’s space. Thin layer respects the shape and boundaries of the user’s environment, but the app may choose to transform certain elements best suited to immerse the user in the app. This is called a blended environment app. 这可以认为是传统的AR应用，需要对场景，物体做识别
- Immersive environment app
Immersive environment apps are centered around an environment that completely changes the user’s world and can place them in a different time and space. These environments can feel very real, creating immersive and thrilling experiences that are only limited by the app creator’s imagination. 这个就是VR。

https://developer.microsoft.com/en-us/windows/mixed-reality/types_of_mixed_reality_apps详细列出了不同应用形态下的可参考的例子，可以作为启发新idea，获得产品灵感的起点。比如
“Mixed reality wayfinding in an office space”这个就可以用在商场/停车场的导览上。

It is important for an app maker to understand early in their development process as to where along this spectrum their experience lies. This decision will ultimately impact both the app design makeup and the technological path for development.

在Holoens中运行的是Win10，为了兼容一般的UWP 2D应用，所以MR提供两种[App views](https://developer.microsoft.com/en-us/windows/mixed-reality/app_views): 
- immersive views
When an app is drawing in the immersive view, no other app is drawing at the same time -- holograms from multiple apps are not composited together. By continually adjusting the perspective from which your app renders its scene to match the user's head movements, your app can render world-locked holograms that remain at a fixed point in the real world.While in an immersive view, your app is also responsible for handling all input. Input in Windows Mixed Reality is made up of gaze, gesture, voice and motion controllers.

- 2D views
A 2D view appears in the shell as a virtual slate, rendered alongside the app launchers and other holograms the user has placed in their world. The user can adjust this slate to move and scale it, though it remains at a fixed resolution regardless of its size. 

### [App Model](https://developer.microsoft.com/en-us/windows/mixed-reality/app_model)
Windows Mixed Reality uses the app model provided by the Universal Windows Platform (UWP), a model and environment for modern Windows apps. The UWP app model defines how apps are installed, updated, versioned and removed safely and completely. It governs the application life cycle - how apps execute, sleep and terminate - and how they can preserve state. It also covers integration and interaction with the operating system, files and other apps.

The lifecycle of a mixed reality app involves standard app concepts such as placement. launch, termination and removal.

- App lifecycle
Placement is launch.
Every app starts in mixed reality by placing an app tile in the Hololens shell. These app tiles, on placement, will start running the app. Thess app tiles persist and stay at the location where they are placed, acting like launchers for anytime you want to get back to the app.

As soon as placement completes (unless the placement was started by an App 2 App launch), the app starts launching. Windows Mixed Reality can run a limited number of apps at one time. As soon as you place and launch an app, other active apps may suspend, leaving a screenshot of the app's last state on its app tile wherever you placed it.

Remove is close/terminate process
When you remove a placed app tile from the world, this closes the underlying processes. This can be useful for ensuring your app is terminated or restarting a problematic app.

- App Views
 Your app can create an additional 2D app view using technology like XAML, to use Shell features such as in-app purchase. 
 
 Mixed reality apps are those that create an immersive view, which is done by the HolographicSpace type.

- App size
2D app views always appear in a fixed virtual slate. This makes all 2D views show the exact same amount of content. Here are some further details about the size of your app's 2D view:
Aspect ratio of the app is preserved while resizing.
App resolution and scale factor are not changed by resizing.
Apps are not able to query their actual size in the world.

- App to app interactions
有很多Win10 功能在Holoens上还没有得到支持，比如Camera Settings, Alarm, Share contract

- App File Storage
All storage is through the Windows.Storage namespace, see the following for more details. HoloLens does not support App Storage sync/roaming.



### Win10 Holographic API
Hololens是一种MR设备，Windows 10 SDK提供了完整的API来支持MR应用的开发，主要包括立体渲染，空间理解及交互
- [Windows.Graphics.Holographic](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic)
包含如何创建，显示Hologram的类: HolographicSpace, HolographicCamera, HolographicFrame

https://developer.microsoft.com/en-us/windows/mixed-reality/getting_a_holographicspace

- [Windows.Perception.Spatial](https://docs.microsoft.com/en-us/uwp/api/Windows.Perception.Spatial)
处理spatial relationships的类：SpatialAnchor, SpatialCoordinateSystem, SpatialLocation

- [Windows.Perception.Spatial.Surfaces](https://docs.microsoft.com/en-us/uwp/api/Windows.Perception.Spatial.Surfaces)
Contains classes that describe the surfaces observed in the user's surroundings and their triangle meshes.
通过SLAM获取的3D表面网格信息: SpatialSurfaceMesh, SpatialSurfaceObserver

- [Windows.UI.Input.Spatial](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.input.spatial.aspx)
提供空间交互处理(GGV)的类: SpatialInteractionManager, SpatialGestureRecognizer, SpatialPointerPose


### [DirectX development overview](https://developer.microsoft.com/en-us/windows/mixed-reality/directx_development_overview)


- [Creating a holographic DirectX project](https://developer.microsoft.com/en-us/windows/mixed-reality/creating_a_holographic_directx_project)

- [Getting a HolographicSpace](https://developer.microsoft.com/en-us/windows/mixed-reality/getting_a_holographicspace)


### [Unity Development Overview](https://developer.microsoft.com/en-us/windows/mixed-reality/unity_development_overview)

https://docs.unity3d.com/Manual/windowsholographic.html  Unity上开发Holographic应用 相对于一般的3D应用开发，只需要做一些针对性的配置即可。

- Porting
The Windows platform APIs for mixed reality only work in the Universal Windows Platform (UWP) app model. So if your app is not already built for UWP, porting to UWP will be part of the porting experience.

- Congiguring for Windows Mixed Reality
对于一个新的MR应用，需要对Unity做一些配置，包括：
1. Per-project 配置(File->Build Settings): 
platform -> Windows Store
sdk -> Universal 10
Target device -> Hololens

2. Per-Scene Settings(Edit->Project Settings->Player):
Settings for Windows Store -> Other Settings -> Rendering -> Virtual Reality Supported -> Windows Mixed Reality
Once you enable the "Virtual Reality Supported" checkbox, the Unity Camera component handles head tracking and stereoscopic rendering. There is no need to replace it with a custom camera to do this.

For an app to take advantage of certain functionality, it must declare the appropriate capabilities in its manifest. The manifest declarations can be made in Unity so they are included in every subsequent project export. 

3. 如果目标设备是Hololens，则需要对MainCamera做一些配置(Hierarchy -> Main Camera)：
Position -> 0,0,0
Clear Flags -> Solid Color
Background -> RBGA(0,0,0,0)
在Holoens上，黑色是透明色，将背景设为透明，这样用户可以See-through物理世界
Clipping Planes. Near -> 0.85


除了 head tracking and stereoscopic rendering已经由Unity内置的Camera对象支持外，其他MR的主要特性: 
Coordinate systems, Gaze, Gestures and motion controllers, Voice input, Persistence, Spatial sound, Spatial mapping
Shared experiences, 以及Locatable camera, Focus point, Tracking loss, Keyboard，都有对应的Unity API/Component提供支持，后续的章节即按照上述features进一步的深入学习和实践。 


最快和方便的开发MR应用的方式，除了用DirectX来手工编写渲染过程，还可以基于Untiy的编辑器，游戏引擎(渲染，物理，动画，网络等...)快速开发

基于Unity，微软提供了[Holographic Academy tutorials](https://developer.microsoft.com/en-us/windows/mixed-reality/academy)导入AR相关知识及开发实践，源代码在https://github.com/Microsoft/HolographicAcademy

- [Holograms 100: Getting started with Unity](https://developer.microsoft.com/en-us/windows/mixed-reality/holograms_100) 
使用Unity开发MR应用的最基本的例子，主要是对per-Projct，per-Scene，MainCamera进行配置，具体参考上一节的内容。为简化开发，最好使用HoloTookit-Unity
The Unity Main Camera handles head tracking and stereoscopic rendering. There are a few changes to make to the Main Camera to use it with mixed reality.
Since maintaining high framerate on HoloLens is so important, we want the quality settings tuned for fastest performance. 
Creating a cube in your Unity project is just like creating any other object in Unity. Placing a cube in front of the user is easy because Unity's coordinate system is mapped to the real world - where one meter in Unity is approximately one meter in the real world.
可以使用[Holographic Remoting](https://developer.microsoft.com/en-us/windows/mixed-reality/holographic_remoting_player)方式在Hololens看到PC上的实时视频流，也就是在Unity上Play，然后在Hololens上看到效果，这个功能需要Windows build 14318，此种场景适用于直播应用。

使用Unity搭建3D场景和脚本后，最后还需要使用[VS build和deploy](https://developer.microsoft.com/en-us/windows/mixed-reality/using_visual_studio)到Hololens上。
既可以使用WIFI方式deploy到Remote Machine，也可以使用USB deploy到Device

在build的过程中，遇到“error MSB3774: Could not find SDK”的问题，主要是References的component(WindowsDesktop, WindowsIoT, WindowsMobile, WindowsTeam)不存在，通过查找Win10 SDK\Extension SDKs\WindowsTeam\10.0.15063.0\
没找到好的解决方法，只能先remove对应的Component先，麻烦的是每次Unity build的时候又会重新生成。
最后还是重装 VS2017/Win10 SDK到默认的C:\Program Files (x86)解决了。

目前VS和Unity的整合还在完善中，还没有稳定，导致总有些问题或者BUG，遇到问题，最好去https://forums.hololens.com/ 查询或者提问

默认VS安装的是本地语言包，要使用英文，先使用Visual Studio Installer安装英语语言包，然后在工具->选项->环境->区域设置->语言 选择 英语

每次在Unity中更新资产后，需要Build(修改脚本不需要)，然后再在VS中deploy到Hololens，参考这里的[最佳实践](https://developer.microsoft.com/en-us/windows/mixed-reality/best_practices_for_working_with_unity_and_visual_studio)

- [Holograms 101: Introduction with Device](https://developer.microsoft.com/en-us/windows/mixed-reality/holograms_101)
通过一个完整的例子介绍MR的主要特性：Gaze, Gesture, Voice, Spatial Sound and Spatial Mapping.

注意在Voice的例子里，除了添加脚本外，还需要将Edit -> Project Settings -> Player -> Windows Store -> Publishing Settings -> Capabilities -> Microphone勾选上，否则Voice input没有作用。
在Spatial Mapping的例子里，要将Edit -> Project Settings -> Player -> Windows Store -> Publishing Settings -> Capabilities -> SpatialPerception勾选上，否则看不到网格

让场景跟随头部移动，只需要根据Gaze碰撞到的位置来调整场景的Position即可。
最后的Underworld效果很好，可以看到纸鹤在飞，sphere掉下去后的滚动效果也符合物理规律。

## [Design](https://developer.microsoft.com/en-us/windows/mixed-reality/design)
Learn the fundamentals of designing mixed reality experiences. 相应的资产，例子存放在https://github.com/Microsoft/MRDesignLabs_Unity

### [Get started with design](https://developer.microsoft.com/en-us/windows/mixed-reality/category/get_started_with_design)
Read our high-level thoughts and understand the principles we follow.

- [About this design guidance](https://developer.microsoft.com/en-us/windows/mixed-reality/about_this_design_guidance)
这是一个全新的计算领域。所有人都在探索，那些事是好的经验，那些是错的教训。
We aim to deliver a comprehensive set of design guidance that covers mixed reality interaction, commanding, navigation, input, and style – all grounded in human behavior and scenarios.

One of the challenges of offering design guidance in this new 3D medium is that we don’t always have definitive guidance to offer. Just like you, we are learning, experimenting, prototyping, problem-solving, and adjusting as we hit obstacles.our end goal is to be definitive wherever we can, providing clear, flexible design guidance tied to open-source code, and actionable in Microsoft dev and design tools. But getting to that point takes many rounds of iteration and learning. We want to engage with you, and learn with you, along the way, so we will be doing the best we can to share as we go, even our stuff that is experimental.

We’ll offer two levels of design guidance: global and local：
- Fluent Design System
Fluent details how we think about fundamentals like light, depth, motion, material, and scale across all Microsoft design – our devices, products, tools, and services. 
- Local design guidance
covers topics unique to HMDs, for example 3D environments and objects; shared environments; the use of sensors, eye tracking and spatial mapping; and the opportunities of spatial audio.


- Case study - AfterNow's process - envisioning, prototyping, building
- Case study - My first year on the HoloLens design team
- Case study - The pursuit of More Personal Computing


### [Interaction design](https://developer.microsoft.com/en-us/windows/mixed-reality/category/interaction_design)
Learn about input, commanding, navigation, and other interaction basics for designing your apps.
关于Interaction Design的部分分散到具体的各个Feature的章节里: Gaze targeting, Gesture Design, Voice Design, Spatial Mapping Design
- [Interaction fundamentals](https://developer.microsoft.com/en-us/windows/mixed-reality/interaction_fundamentals)
The user is the camera

**Best practices**
1. The user is the camera and they control the movement. Let them drive.
2. If you need to virtually transport the user, be sensitive to issues around vestibular discomfort.

Users will react to large menus coming at them.
1. Use shorter animations
2. Animate from down/left/right or fade in instead of Z
3. Slow down timing
4. Allow user to see the world in the background

**What to avoid**
1. Don't shake the camera or purposely lock it to 3DOF (only orientation, no translation), it can make users feel uncomfortable.
2. No abrupt movement. If you need to bring content to or from the user, move it slowly and smoothly toward them for maximum comfort.
3. Users are sensitive to acceleration (both angular and translational). Do not accelerate or turn the user's camera.

In 2D development, frequently accessed content and settings may be placed in the corners of a screen to make them easily accessible. However, in holographic apps, the corners of the user's field of view may be uncomfortable to access. In this case, the center of the field of view is the prime location for content.

The user may need to be guided to help locate important events or objects outside their field of view. You can use arrows, light trails, character head movement, thought bubbles, pointers, spatial sound, and voice prompts to help guide the user to important content in your app.

On HoloLens, it's important to simplify your UI to fit within the user's field of view and keep your focus on the main action. 

To ensure maximum comfort on head-mounted displays, it’s important for designers and developers to create and present content in a way that mimics how humans interpret 3D shapes and the relative position of objects in the natural world. From a physical perspective, it is also important to design content that does not require fatiguing motions of the neck or arms.

Using [mixed reality capture](https://developer.microsoft.com/en-us/windows/mixed-reality/mixed_reality_capture), users can capture a photo or video of their experience at any time. Consider experiences in your app where you may want to encourage snapshots or videos.


- Comfort
用户体验的舒适性，涉及到很多人体生物特性。想设计优秀的体验，必须要花时间理解这些特性。

During natural viewing, the human visual system relies on multiple sources of information, or “cues,” to interpret 3D shapes and the relative position of objects. Some cues are monocular(单目), including linear perspective(线性透视), familiar size, occlusion(遮挡), depth-of-field blur(景深模糊), and accommodation(. Other cues are binocular, such as vergence(辐辏) (essentially the relative rotations of the eyes required to look at an object) and binocular disparity(双眼视差) (the pattern of differences between the projections of the scene on the back of the two eyes). To ensure maximum comfort on head-mounted displays, it’s important for designers and developers to create and present content in a way that mimics how these cues operate in the natural world. 

1. Vergence-accommodation conflict 视觉辐辏调节冲突
To view objects clearly, humans must accommodate, or adjust their eyes’ focus, to the distance of the object. At the same time, the two eyes must converge to the object’s distance to avoid seeing double images. In natural viewing, vergence and accommodation are linked. 

HoloLens displays are fixed at an optical distance approximately 2.0m away from the user. Thus, users must always accommodate near 2.0m to maintain a clear image in the device. App developers can guide where users' eyes converge by placing content and holograms at various depths. Discomfort from the vergence-accommodation conflict can be avoided or minimized by keeping content to which users converge to as close to 2.0m as possible 

For maximum comfort, **the optimal zone for hologram placement is between 1.25m and 5m.** In every case, designers should attempt to structure content scenes to encourage users to interact 1m or farther away from the content. When possible, we recommend starting to fade out content at 1m and placing a rendering clipping plane at 85cm to avoid any nearer objects.

2. Rendering rates(60FPS+)
与Oculus Rift采用的ATW一样，Hololens也是提前预测头部要移动的位置，并渲染
Since image rendering takes time, HoloLens and other Windows Mixed Reality devices predict where a user's head will be when the images are shown in the displays. This prediction algorithm is an approximation. Windows Mixed Reality algorithms and hardware adjust the rendered image to account for the discrepancy between the predicted head position and the actual head position. This process makes the image seen by the user appear as if it were rendered from the correct location, and holograms feel stable. 

By rendering at a minimum framerate of 60 FPS, you are doing two things to help make stable holograms:
Reducing the appearance of judder, which is characterized by uneven motion and double images. Faster hologram motion and lower render rates are associated with more pronounced judder. Therefore, striving to always maintain 60 FPS (or your device’s maximum render rate) will help avoid judder for moving holograms.
Minimizing the overall latency. In an engine with a game thread and a render thread running in lockstep, running at 30FPS can add 33.3ms of extra latency. By reducing latency, this decreases prediction error, and increases hologram stability.

There are a variety of tools that can be used to benchmark your application frame rate such as: GPUView, Visual Studio Graphics Debugger, Profilers built into 3D engines such as Unity

3. Self-motion and user locomotion
The only limitation is the size of your physical space; if you want to allow users to move farther in the virtual environment than they can in their real rooms, then a form of purely virtual motion must be implemented. 

4. Heads-up displays
In first-person-shooter videogames, heads-up displays (HUDs) persistently present information such as player health, mini-maps, and inventories directly on the screen. HUDs work well to keep the player informed without intruding on the gameplay experience. In mixed reality experiences, HUDs have the potential to cause significant discomfort and must be adapted to the more immersive context. Specifically, HUDs that are rigidly locked to the user’s head orientation are likely to produce discomfort. If an app requires a HUD, we recommend body locking rather than head locking. 

5. Gaze direction
To avoid eye and neck strain content should be designed so that excessive eye and neck movements are avoided.
Avoid gaze angles more than 10 degrees above the horizon (vertical movement)
Avoid gaze angles more than 60 degrees below the horizon (vertical movement)
Avoid neck rotations more than 45 degrees off-center (horizontal movement)

### [Style](https://developer.microsoft.com/en-us/windows/mixed-reality/category/style)
Style helps digital elements coexist within a physical environment, creating delight for users while enhancing the usability of interactions. From the legibility of type, to the placement of sounds, to the scale and lighting of objects, attention to style can both refine and enrich an experience.

- [Color design](https://developer.microsoft.com/en-us/windows/mixed-reality/color_design)

- [Typography](https://developer.microsoft.com/en-us/windows/mixed-reality/typography)


### [App patterns](https://developer.microsoft.com/en-us/windows/mixed-reality/category/app_patterns)
Create app experiences that span across the spectrum of mixed reality. From immersive apps that fully encompass the user's environment, to enhanced environment apps that add a digital layer onto the physical world. Learn how the Universal Windows Platform (UWP) provides the framework for all mixed reality experiences.

- Room scan visualization

- Gaze indicator

### Controls
Learn how to leverage these fundamental UI elements, including cursors, loading indicators, and text to create powerful mixed reality experiences.
- [Text in Unity](https://developer.microsoft.com/en-us/windows/mixed-reality/text_in_unity)

Text is one of the most important components in holographic apps. To display text in Unity, there are two types of text components you can use — UI Text and 3D Text Mesh. 
Unity assumes all new elements added to a scene are 1 Unity Unit in size, or 100% transform scale, which translates to about 1 meter on HoloLens.
Most visual designers use points to define font sizes in the real world. There are about 2835 (2,834.645666399962) points in 1 meter. Based on the point system conversion to 1 meter and Unity's default Text Mesh font size of 13, the simple math of 13 divided by 2835 equals 0.0046 (0.004586111116 to be exact) provides a good standard scale to start with (some may wish to round to 0.005).

如果是默认以13号Arial字体为基准，则需要将3D TextMesh Scale 到 0.005，也就是说在Unity的World Scene是以1米为基准单位，那么13号字，大概是0.005米
如果是基于Canvas的UI Text，则只有3D Text字体的1/10，也就是缩放比例为0.0005
为减少重复的设置，HoloTookit-Unity提供了对应的UI Text 和 3D Text Mesh的Perfab，同时因为Unity's default font material does not support occlusion. 所以提供了一个Shader支持Occlusion
对于字体的大小，根据与人眼的距离来调整，一般推荐使用Segoe UI字型，30Pt大小

- [Interactable Object](https://developer.microsoft.com/en-us/windows/mixed-reality/interactable_object)
A ‘button’ has long been a metaphor used for triggering an event in the 2D abstract world. In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore. Anything can be an Interactable object that triggers an event. An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.
using these standard interaction states: observation, observation targeted, ready and pressed. 

在交互元素上大量使用动画效果，Using 3D models imported from modeling software, we can create an Interactable object that resembles real life object. Since it's a digital object, we can add magical interactions to it.

- [Object Collection](https://developer.microsoft.com/en-us/windows/mixed-reality/object_collection)
Object collection is a script which helps you lay out an array of objects in a predefined three-dimensional shape. It supports four different surface styles - plane, cylinder, sphere and scatter. You can adjust the radius and size of the objects and the space between them. Object collection supports any object from Unity - both 2D and 3D.

https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable这个例子展现了Interactable Object和Object Collection两个设计理念。

- [Progress](https://developer.microsoft.com/en-us/windows/mixed-reality/progress)
A progress control provides feedback to the user that a long-running operation is underway. It can mean that the user cannot interact with the app when the progress indicator is visible, and can also indicate how long the wait time might be, depending on the indicator used.

There are two options to show the user that an operation is underway – a Progress bar or a Progress ring.

Best practices : 
1. Tightly couple billboarding or tag-along to the display of Progress since the user can easily move their head into empty space and lose context. Your app might look like it has crashed if the user is unable to see anything. Billboarding and tag-along is built into the Progress prefab.
2. If it takes more than few seconds to load your app data, it's always good to provide status information about what is happening to the user. The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status. You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.

- [App bar and bounding box](https://developer.microsoft.com/en-us/windows/mixed-reality/app_bar_and_bounding_box)
The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds. This pattern is commonly used to give users the ability to remove and adjust holograms.
Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user. 也就是物体能感知到用户的焦点发生改变，自动调整App bar的位置。
The App bar was designed primarily as a way to manage placed objects in a user's environment. Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality. 当要对物体做transform操作时，使用Bounding Box来做平移，缩放，旋转操作。

### Resource
- [HoloSketch](https://developer.microsoft.com/en-us/windows/mixed-reality/case_study_-_building_holosketch,_a_spatial_layout_and_ux_sketching_app_for_hololens)
HoloSketch is an on-device spatial layout and UX sketching tool for HoloLens to help build holographic experiences.
可以在Holoens里设计MR应用原型，可以快速原型设计，优化交互体验

- [Fluent Design System](http://fluent.microsoft.com/)
适用于所有微软产品的基础设计理念，是微软下一代Natual UI的设计，交互尝试：Light(高亮，阴影)，Depth(3D)，Motion(Animation, Physcial), Material, Scale
可以看到UI设计上增加了很多3D游戏相关的视觉感受，UI游戏化的趋势。

- [UWP app design and UI](https://developer.microsoft.com/en-us/windows/apps/design/)


## [Rendering](https://developer.microsoft.com/en-us/windows/mixed-reality/rendering)
Holographic rendering enables your app to draw a hologram in a precise location in the world around the user, whether it's precisely placed in the physical world or within a virtual realm you've created.

Mixed reality headsets (both HoloLens and immersive headsets) continually track the position and orientation of the user's head relative to their surroundings. As your app begins preparing its next frame, the system predicts where the user's head will be in the future at the exact moment that the frame will show up on the displays. Based on this prediction, the system calculates the view and projection transforms to use for that frame. 

Regardless of the viewport size, once the frame has been rendered by the application, the system will upscale the image to fill the entirety of the displays.

For any given frame, your app must render using the view transform, projection transform, and viewport resolution provided by the system. Additionally, your application must never assume that any rendering/view parameter remains fixed from frame-to-frame. Engines like Unity handle all these transforms for you in their own Camera objects, so that the physical movement of your users and the state of the system is always respected. 

Windows Mixed Reality introduces the concept of a holographic camera. Holographic cameras are similar to the traditional camera found in 3D graphics texts: they define both the extrinsic (position and orientation) and intrinsic camera properties (ex: field-of-view) used to view a virtual 3D scene. Unlike traditional 3D cameras, the application is not in control of the position, orientation, and intrinsic properties of the camera. Rather, the position and orientation of the holographic camera is implicitly controlled by the user's movement. The user's movement is relayed to the application on a frame-by-frame basis via a view transform. Likewise, the camera's intrinsic properties are defined by the device's calibrated optics and relayed frame-by-frame via the projection transform.

In general your app will be rendering for a single stereo camera. 

When rendering medical MRI or engineering volumes in 3D, [volume rendering](https://developer.microsoft.com/en-us/windows/mixed-reality/volume_rendering) techniques are often used. These techniques can be particularly interesting in mixed reality, where users can naturally view such a volume from key angles, simply by moving their head.
 

- [Windows Holographic Rendering: One SDK to Target VR and AR Ecosystems](https://channel9.msdn.com/events/GDC/GDC-2017/GDC2017-008)
本视频讨论了如下几个主题:
Positional tracking and rendering: latency, forward-prediction
Holographic rendering with DirectX: stereo rendering, frame timing, debugging tools, and best practices
Remote rendering from a PC to your HoloLens using remoting to increase scene complexity
Developing shared holographic experiences on HoloLens.


- [Rendering in DirectX](https://developer.microsoft.com/en-us/windows/mixed-reality/rendering_in_directx)

- [Camera in Unity](https://developer.microsoft.com/en-us/windows/mixed-reality/camera_in_unity)
在Unity中，Camera组件负责立体渲染(stereo rendering)和头部跟踪(head tracking)的处理

When you wear a mixed reality headset, it becomes the center of your holographic world. The Unity Camera component will automatically handle stereoscopic rendering and will follow your head movement and rotation when your project has "Virtual Reality Supported" selected with "Windows Mixed Reality" as the device (in the Other Settings section of the Windows Store Player Settings). 

有些配置需要根据不同情况手工配置，包括Mixed Reality Rendering(根据设备是VR，还是MR，选择Skybox或者透明背景色)，Positioning the Camera(对Hololens来说，用户就是Main Camera，用户的起点就是Camera的原点)，Clip planes(Holoens的near clip planes建议经验值是0.3 ~ 0.85，这样的距离会让看东西舒服一些)


## [Gaze](https://developer.microsoft.com/en-us/windows/mixed-reality/gaze)
Gaze is the first form of input and is a primary form of targeting within mixed reality. Gaze tells you where the user is looking in the world and lets you determine their intent. In the real world, you'll typically look at an object that you intend to interact with. This is the same with gaze.
Mixed reality headsets use the position and orientation of your user's head, not their eyes, to determine their gaze vector. You can think of this vector as a laser pointer straight ahead from directly between the user's eyes. As the user looks around the room, your application can intersect this ray, both with its own holograms and with the spatial mapping mesh to determine what virtual or real-world object your user may be looking at.

As a mixed reality developer, you can do a lot with gaze:
1. Your app can intersect gaze with the holograms in your scene to determine where the user's attention is.
2. Your app can target gestures and controller presses based on the user's gaze, letting the user select, activate, grab, scroll, or otherwise interact with their holograms.
3. Your app can let the user place holograms on real-world surfaces, by intersecting their gaze ray with the spatial mapping mesh.
4. Your app can know when the user is not looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.

Most apps should use a [cursor](https://developer.microsoft.com/en-us/windows/mixed-reality/cursors) (or other auditory/visual indication) to give the user confidence in what they're about to interact with. You typically position this cursor in the world where their gaze ray first interacts an object, which may be a hologram or a real-world surface.
Once the user has targeted a hologram or real-world object using their gaze, their next step is to take action on that object. The primary ways for a user to take action are through gestures, motion controllers and voice.

### [Cursors](https://developer.microsoft.com/en-us/windows/mixed-reality/cursors)
A gaze indicator, basically a cursor, provides continuous feedback for the user to understand what the HoloLens understands about their intentions.

Cursor Design Principles ：
1. The cursor is always present
2. The cursor should be no larger than the available targets, allowing users to easily interact with and view the content.
3. Avoid obstructing content
4. Although there is no one right cursor shape, we recommend that you use a directionless shape like a torus or something else. 一个例外是需要指示用户调整注意力到系统指定的位置
5. A donut or torus shaped cursor works for a lot of applications.

We could use the cursor to display the user's input state.We could also use the cursor to make the user aware that there is a voice command available. These different cursor states can be implemented in different ways. You might implement these different states by modeling the cursor like a state machine.

### [Gaze targeting](https://developer.microsoft.com/en-us/windows/mixed-reality/gaze_targeting)
**Optimal target size at 2 meter distance : 1.5-3 degree, 5-10cm height**

Users will often fail to find UI elements that are positioned very high or very low in their field of view, focusing most of their attention on areas around their main focus (usually roughly eye level). Placing most targets in some reasonable band around eye level can help. Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree that they're related conceptually can leverage attention-chaining behaviors from item to item as a user moves their gaze through an area. 

### [Gaze in Unity](https://developer.microsoft.com/en-us/windows/mixed-reality/gaze_in_unity)
Conceptually, gaze is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with. In Unity, the user's head position and direction are exposed through the Unity Main Camera.
Calling Physics.RayCast results in a RaycastHit structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the gaze ray collided with.

Cursor的管理，根据不同的状态，修改Cursor的位置，大小，形状。Cursor可以看做是一个一直存在的Mesh Object。那么在架构设计上是用一个CursorManager来管理场景中所有的Cursor的状态变化，还是每个Hologram自行处理各自的Cursor的状态变更？ 从文档上看，倾向于前者，原因没看懂？？？
While the example above demonstrates how to do a single raycast in an update loop to find the Gaze target, it is recommended to do this in a single object managing gaze instead of doing this in any object that is potentially interested in the object being gazed at. This lets your app save processing by doing just one gaze raycast each frame.

### [Holograms 210: Gaze](https://developer.microsoft.com/en-us/windows/mixed-reality/holograms_210)

从设计/用户体验的角度，使用好Gaze，包括Cursor的不同形态的变换来通知用户注意(一般形态，检测到手势时形态，通知用户要留意其他方向时形态)

这个例子主要实现Gaze相关的特性：
- making the cursor and our holograms gaze-aware: both will change based on where the user is looking - or where the user is not looking. This makes them context-aware. 
凝视感知，让用户感知到系统变化。头部也就是Main Camera即是Gaze的起点，Gaze到某个对象，主要是通过Physics.Raycast()函数来处理

- add feedback to our cursor and holograms to give the user more context on what is being targeted. This feedback can be audio and visual.
给Holograms增加Interactible能力，也就是在对象知道用户正在No-Gaze，Gaze，Select(GestureRecognizer)它，同时可以据此改变Cursor的形态，实现原理也是依靠Raycast()

- targeting techniques to help users hit smaller targets.
GazeStabilizer

- how to draw the user's attention to holograms with a directional indicator.
这个应用在RoboRaid里面感受很明显，当敌人随机出现在某个位置时，通过Cursor的方向提示通知用户。实现方式是计算当前Camera与目标对象的Direction 

看不懂DirectionIndicator.cs的计算方法，需要看 空间 算法相关的书了

- take your holograms with the user as she moves around in your world.
A tag-along object never fully leaves the user's view. You can think of the a tag-along as being an object attached to the user's head by rubber bands. As the user moves, the content will stay within an easy glance by sliding towards the edge of the view without completely leaving. When the user gazes towards the tag-along object, it comes more fully into view.
与Home类似，这个Tagalong Hologram会跟随用户的头部运动，一直保持在用户的视场内。 注意那个ChestButton_Center就是AstroMan胸口的倒三角标志。实现的原理是通过计算F

总结来说，就是如下几个功能：GazeManager，CursorManager，GestureManager，Interactible Object初探, directional indicator cursor(目标对象的方向指示)，billboarding(位置不变，总是面向用户而旋转), Tag-Along(总是显示在用户的视场范围内)

从ModelExplorer的目录结构，对我们项目Assets目录结构的定义也有借鉴意义：
Holograms       // 存放prefab相关内容
HoloToolkit     // HoloToolkit第三方库
Resources      // 存放资源文件，按照Materials, Modles, Shaders, Sounds, Textures 目录分类
Scripts        // 项目相关脚本

## [Gesture](https://developer.microsoft.com/en-us/windows/mixed-reality/gestures)
Hand gestures allow users take action in mixed reality.  While hand gestures do not provide a precise location in space, the simplicity of putting on a HoloLens and immediately interacting with content allows users to get to work without any accessories.

To take actions, hand gestures use gaze as targeting mechanism. The combination of gaze and the Select gesture results in a gaze-and-commit interaction. 

HoloLens recognizes hand gestures by tracking the position of either or both hands that are visible to the device. HoloLens sees hands when they are in either the **ready state** (back of the hand facing you with index finger up) or the **pressed state** (back of the hand facing you with the index finger down). When hands are in other poses, the HoloLens will ignore them. 也就是目前Holoens还只支持Tap，Bloom两种手势。但可以在此基础上扩展，比如2次Tap代表新的手势，2个手Tap，Hold，可以做Scale

HoloLens looks for hand input within a cone in front of the device, known as the gesture frame, which extends above, below, left and right of the display frame where holograms appear. This lets you keep your elbow comfortably at your side while providing hand input. 

For each hand that HoloLens detects, you can access its position (without orientation) and its pressed state. As the hand nears the edge of the gesture frame, you're also provided with a direction vector, which you can show to the user so they know how to move their hand to get it back where HoloLens can see it.

Interactions: Low-level spatial input
1. Select(known as air-tap) : ready state -> pressed state -> ready state
也可以使用"Select"命令达成同样的效果
Think of Select as the equivalent of a mouse click, a universal action that you learn once and then apply across all your apps, using either hands, motion controllers or voice.

2. Home(known as Bloom) is a special system action that is used to go back to the Start Menu.

Composite gestures: High-level spatial input
Your app can recognize more than just individual presses and releases. By combining presses and releases with movement of your hand, you can perform more complex composite gestures as well:
**Tap**: A Select press and release. 鼠标单击

**Hold**: Holding a Select press beyond the system's Hold threshold. 鼠标左键长按
Hold gestures are similar to a touch tap-and-hold and can be used to take a secondary action, such as picking up an object instead of activating it, or showing a context menu.

**Manipulation**: A Select press, followed by **absolute** movement of your hand through 3-dimensional world. 鼠标左键选中，可以大范围的移动
Manipulation gestures can be used to move, resize or rotate a hologram when you want the hologram to react 1:1 to the user's hand movements.

**Navigation**: A Select press, followed by relative movement of your hand or the controller within a 3-dimensional unit cube, potentially on axis-aligned rails. 鼠标左键选中，相对小范围的移动
Navigation gestures operate like a virtual joystick, and can be used to navigate UI widgets, such as radial menus. Navigation can be used to build velocity-based continuous scrolling or zooming gestures, similar to scrolling a 2D UI by clicking the middle mouse button and then moving the mouse up and down.

One benefit of using gesture recognition is that you can configure a gesture recognizer just for the gestures the currently targeted hologram can accept. 通过定制gestureRecoginzer的行为，可以让Hologram支持不同的手势事件。

### [Gesture design](https://developer.microsoft.com/en-us/windows/mixed-reality/gesture_design)
Interaction on HoloLens is built around Gaze, Gesture, and Voice. Interactions are built on gaze to target and gesture or voice to act upon whatever element has been targeted. 
The three key component gestures of HoloLens : Bloom, Air tap, Tap and hold

Hold is simply maintaining the downward finger position of the air tap. This allows "mouseup"/"mousedown" interactions, "click and drag" interactions, and more.

In general, gestures can be thought of as being discrete or continuous in nature, Discrete gestures are those in which there is a binary ‘completed’/’not completed’ state of the gesture. The air tap is the simplest of these

Continuous gestures are those in which the amount of action within the gesture matters to the output.  Movement is a key category of these continuous gestures.

For both discrete and continuous gestures on HoloLens, the hand must be within a “gesture frame”, in a range that the gesture-sensing cameras can see appropriately (very roughly from nose to waist, and between the shoulders).

In the case of continuous gestures in particular, there is some risk of users moving their hands outside of the gesture frame while in mid-gesture (while moving some holographic object, for example), and losing their intended outcome. 这个需要注意，当手势动作超出了识别范围，程序应该如何处理：
1. User education on the gesture frame's existence and approximate boundaries
2. Notifying users when their gestures are nearing/breaking the gesture frame boundaries within an application, to the degree that a lost gesture will lead to undesired outcomes. 
3. Consequences of breaking the gesture frame boundaries should be minimized. In general, this means that the outcome of a gesture should be stopped at the boundary, but not reversed. 

### [Gaze, gestures, and motion controllers in DirectX](https://developer.microsoft.com/en-us/windows/mixed-reality/gaze,_gestures,_and_motion_controllers_in_directx)

To access the user's gaze, you use the SpatialPointerPose type. 
There are two levels of API you can target when handling gestures or motion controllers in mixed reality:
- Interactions (SourcePressed, SourceReleased and SourceUpdated), accessed using a **SpatialInteractionManager**
可以处理Hand，MotionController，Voice三种SpatialInteractionSource
- Composite gestures (Tapped, Hold, Manipulation, Navigation), accessed using a **SpatialGestureRecognizer**

By routing interactions from the SpatialInteractionManager to a hologram's SpatialGestureRecognizer, apps can detect Tap, Hold, Manipulation, and Navigation events uniformly across hands, voice, and spatial input devices, without having to handle presses and releases manually.

### [Gestures and motion controllers in Unity](https://developer.microsoft.com/en-us/windows/mixed-reality/gestures_and_motion_controllers_in_unity)

Unity provides both low level access (raw position/orientation/velocity information) and a high level gesture recognizer that exposes more complex gesture events (for example: tap, double tap, hold, manipulation and navigation).

Unity提供的API基本是Win10 Holographic API的封装:
- Interactions: Low-level spatial input
Namespace: UnityEngine.VR.WSA.Input
Types: InteractionManager, InteractionSourceState, InteractionSource, InteractionSourceProperties, InteractionSourceKind, InteractionSourceLocation
Low-level spatial input allows you to get much more detailed information on interaction sources, such as the source's hand pose or pointing pose, or the state of a motion controller's touchpad or thumbstick.

- Gestures: High-level spatial input
Namespace: UnityEngine.VR.WSA.Input
Types: GestureRecognizer, GestureSettings, InteractionSourceKind

You can access the hand pose through either Unity's cross-vendor input API (VR.InputTracking.GetLocalPosition/Rotation) or through the Windows-specific API (sourceState.sourcePose.TryGetPosition/Rotation).

https://developer.microsoft.com/en-us/windows/mixed-reality/input_porting_guide_for_unity

### [Holograms 211: Gesture](https://developer.microsoft.com/en-us/windows/mixed-reality/holograms_211)
Hand detected, Navigation gesture, Manipulation gesture
本教程除了Holograms 101的air-tap外，还提供关于Gesture的如下特性：
- Detect when the user's hand is being tracked and provide feedback to the user.
跟踪手的状态，并通过Cursor可视化的方式反馈给用户
InteractionManager(SourceDetected, SourceLost, SourcePressed, SourceReleased)，通过这些事件可以感知到gesture frame的范围

- Use a **navigation** gesture to rotate our holograms.
介绍navigation手势的用途及实现： scrolling or zooming
GestureRecognizer.SetRecognizableGestures(GestureSettings.NavigationX)
1. Instantiate the NavigationRecognizer as a new GestureRecognizer.
2. Use SetRecognizableGestures to recognize NavigationX and Tap gestures.
3. Handle NavigationStarted, NavigationUpdated, NavigationCompleted, NavigationCanceled events，记录当前状态

- Provide feedback when the user's hand is about to go out of view.


- Use **manipulation** events to allow users to move holograms with their hands.
介绍manipulation手势的用途及实现： move, resize or rotate 
GestureRecognizer.SetRecognizableGestures(GestureSettings.ManipulationTranslate);

例子最后的模型expansion效果，值得借鉴

## [Voice input](https://developer.microsoft.com/en-us/windows/mixed-reality/voice_input)
Voice is one of the three key forms of input on HoloLens. You simply gaze at a hologram and speak your command.  Voice input can be a natural way to communicate your intent. Voice is especially good at traversing complex interfaces because it lets users cut through nested menus with one command.Voice input is powered by the same engine that supports speech in all other Universal Windows Apps.

- The "select" command
Even without specifically adding voice support to your app, your users can activate your holograms simply by saying "select". This behaves the same as a press and release with your hand. You will hear a sound and see a tooltip with "select" appear as confirmation.

也可以说出"Hey Cortana"来呼叫Cortana来做更多的语音命令工作。对于中文语音的支持，现在还不支持，要做的话，需要第三方的语音识别库。

- "See It, Say It"
HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well. For example, when looking at a 2D app, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world.

When apps follow this rule, users can easily understand what to say to control the system. To reinforce this, while gazing at a button, you will see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.

可以加一个麦克风的图标，然后在ICON旁边或上面显示语音命令。

There are also a number of voice commands you can say while gazing at a hologram to quickly perform manipulation tasks ： 
Face me， Bigger | Enhance，Smaller

- Dictation
Rather than typing with air-taps, voice dictation can be more efficient to enter text into an app. This can greatly accelerate input with less effort for the user.
这个就是Speech-To-Text功能，相比打字输入，的确是人性化很多，难点在于准确度和本地化的问题。在中国，科大讯飞应该会有优势。

At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.

### [Voice design](https://developer.microsoft.com/en-us/windows/mixed-reality/voice_design)

Because users speak with a variety of dialects and accents, proper choice of speech keywords will make sure that your users' commands are interpreted unambiguously.

- Bset Practices
**Use concise commands** - When possible, choose keywords of two or more syllables. One-syllable words tend to use different vowel sounds when spoken by persons of different accents. Example: "Play video" is better than "Play the currently selected video"
**Use simple vocabulary** - Example: "Show note" is better than "Show placard"
**Make sure commands are non destructive** - Make sure any action that can be taken by a speech command is non destructive and can easily be undone in case another person speaking near the user accidentally triggers a command.
**Avoid similar sounding commands** - Avoid registering multiple speech commands that sound very similar. Example: "Show more" and "Show store" can be very similar sounding.
**Unregister your app when not it use** - When your app is not in a state in which a particular speech command is valid, consider unregistering it so that other commands are not confused for that one.
**Test with different accents** - Test your app with users of different accents.
Maintain voice command consistency - If "Go back" goes to the previous page, maintain this behavior in your applications.
**Avoid using system commands** - The following voice commands are reserved for the system. These should not be used by applications.
"Hey Cortana"
"Select"

Voice strengths : 
1. Voice input is a natural way to communicate our intents. Voice is especially good at interface traversals because it can help users cut through multiple steps of an interface (a user might say "go back" while looking at Web page, instead of having to go up and hit the back button in the app). This small time savings has a powerful emotional effect on user’s perception of the experience and gives them a small amount superpower.

2.  Using voice is also a convenient input method when we have our arms full or are multi-tasking. On devices where typing on a keyboard is difficult, voice dictation can be an efficient alternative way to input. 

3. Lastly, in some cases when the range of accuracy for gaze and gesture are limited, Voice might be a user’s only trusted method input.

Voice's weaknesses :
1. Voice also has some weaknesses. Fine-grained control is one of them. (for example a user might say "louder," but can’t say how much. "A little" is hard to quantify. Moving or scaling things with voice is also difficult (voice does not offer the granularity of control).

2. Voice can also be imperfect. Sometimes a voice system incorrectly hears a command or fails to hear a command. Recovering from such an errors is a challenge in any interface. 

3. Lastly, voice may not be socially acceptable in public places. There are some things that users can’t or shouldn’t say. These cliffs allow speech to be used for what it is best at.


### [Voice input in DirectX](https://developer.microsoft.com/en-us/windows/mixed-reality/voice_input_in_directx)

- Use a SpeechRecognizer for continuous recognition of voice commands
1. create a new Windows::Media::SpeechRecognition::SpeechRecognizer instance
2. create a list of speech commands for the recognizer to listen for
3. The list of commands is loaded into the list of constraints for the speech recognizer. This is done by using a SpeechRecognitionListConstraint object.
4. Subscribe to the ResultGenerated event on the speech recognizer's SpeechContinuousRecognitionSession. This event notifies your app when one of your commands has been recognized.
5. Your OnResultGenerated event handler receives event data in a SpeechContinuousRecognitionResultGeneratedEventArgs instance. Save the event data so that you can make use of it in a subsequent update loop.
6. Make use of the data in Update() loop

- Use dictation for one-shot recognition of speech phrases and sentences

You can configure a speech recognizer to listen for phrases or sentences spoken by the user. In this case, we apply a SpeechRecognitionTopicConstraint that tells the speech recognizer what type of input to expect. 

通过识别一段语句中是否有需要的命令来执行动作。

Conditions in the environment can sometimes prevent speech recognition from working. For example, the room might be too noisy or the user might speak at too high a volume. The speech recognition API provides info, where possible, about conditions that have caused a degradation in quality.

- Use speech synthesis to provide audible voice prompts
也就是传统的TTS，将文本转换为语音。除了使用此种方案，根据不同的场景，也可以使用pre-recorded voice clip, a visual UI的方式达成 
The holographic speech samples use speech synthesis to provide audible instructions to the user. 
1. using Windows::Media::SpeechSynthesis::SpeechSynthesizer()创建SpeechSynthesizer对象，
2. 准备语音文本
3. 使用SynthesizeTextToStreamAsync开启异步合成任务，生成byte stream
4. 使用HRTF Audio effect，将byte stream播放出来

https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis

https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicVoiceInput


### [Voice input in Unity](https://developer.microsoft.com/en-us/windows/mixed-reality/voice_input_in_unity)
Unity提供了三种方法支持Voice Input，将SpeechRecognizer的应用场景更细化，这些类都在在UnityEngine.Windows.Speech namespace ： 
1. With the KeywordRecognizer (one of two types of PhraseRecognizers), your app can be given an array of string commands to listen for. 
2. With the GrammarRecognizer (the other type of PhraseRecognizer), your app can be given an SRGS file defining a specific grammar to listen for. 
3. With the DictationRecognizer, your app can listen for any word and provide the user with a note or other display of their speech.

要使用Voice Input，首先要开启Microphone能力:
Edit -> Project Settings -> Player -> Windows Store -> Publishing Settings -> Capabilities -> Microphone

- Phrase Recognition
To enable your app to listen for specific phrases spoken by the user then take some action, you need to:
1. Specify which phrases to listen for using a KeywordRecognizer or GrammarRecognizer
2. Handle the OnPhraseRecognized event and take action corresponding to the phrase recognized

-  Dictation
Use the DictationRecognizer to convert the user's speech to text. The DictationRecognizer exposes dictation functionality and supports registering and listening for hypothesis and phrase completed events, so you can give feedback to your user both while they speak and afterwards. 

1. Create a new DictationRecognizer
2. Handle Dictation events
3. Start the DictationRecognizer

除了开启 **Microphone** 能力外，还要开启 **Internet Client** 能力。


### [Holograms 212: Voice Input](https://developer.microsoft.com/en-us/windows/mixed-reality/holograms_212)
一些设计语音命令DO and Don't
**DO**
- Create concise commands; 
- Use a simple vocabulary; 
- Be consistent
**DON'T**
- Using single syllable commands
Use "Play Video", not "Play"
- Use system commands
Don't use : Select, Go Back, Scroll Tool, Zoom Tool, Drag Tool, Adjust, Remove
- Use similar Sounds

When using the Dictation Recognizer, keep in mind that:
- You must be connected to WiFi for the Dictation Recognizer to work.
- Timeouts occur after a set period of time. There are two timeouts to be aware of:
If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.
If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.
- Only one type of recognizer (Keyword or Dictation) can run at a time.

Grammar Recognizer to recognize the user's speech according to an SRGS(Speech Recognition Grammar Specification) file, 制定简单的规则，提供一定的弹性，减少硬编码

## [Spatial sound](https://developer.microsoft.com/en-us/windows/mixed-reality/spatial_sound)
In Windows Mixed Reality, the audio engine provides the aural component of the mixed-reality experience by simulating 3D sound using direction, distance, and environmental simulations. 
By analyzing how sound reaches both our ears, our brain determines the distance and direction of the object emitting the sound. An HRTF (or Head Related Transfer Function) simulates this interaction by modeling the spectral response that characterizes how an ear receives sound from a point in space. The spatial audio engine uses personalized HRTFs to expand the mixed reality experience, and simulate sounds that are coming from various directions and distances.

Because the general principle of mixed reality is to ground holograms in the user's physical world or virtual environment, most sounds from holograms should be spatialized. 
Recommended use for spatial sound voices include:
- Gaze Mixing
highlighting objects, particularly when out of view. When a hologram needs a user's attention, play a sound on that hologram (e.g. have a virtual dog bark). This helps the user to find the hologram when it is not in view.
- Audio Haptics
reactive audio for touchless interactions. For example, play a sound when the user's hand or motion controller enters and exits the gesture frame. Or play a sound when the user selects a hologram.
- Immersion
ambient sounds surrounding the user

Windows' spatial sound engine only supports a 48k sample rate for playback. Most middleware, such as Unity, will automatically convert sound files into the supported format, but when using Windows Audio APIs directly please match the format of the content to the format supported by the effect.

### [Spatial Sound design](https://developer.microsoft.com/en-us/windows/mixed-reality/spatial_sound_design)
Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications. We use sound cues in our daily lives to locate objects, get someone's attention, or get a better understanding of our environment. The more closely your app's sound behaves like it does in the real world, the more convincing and engaging your virtual world will be.

Spatial sound does four key things for mixed reality development: 
- Grounding
- User attention
- Immersion
- Interaction design

Best practices when using spatial sound:
- Real sounds work better than synthesized or unnatural sounds
- Expectation trumps simulation
- Most sounds should be spatialized
- Avoid invisible emitters
- Avoid spatial masking

General concepts to keep in mind when using spatial sound:
- Spatial sound is a simulation
- Normalize all sounds
- Object discovery and user interfaces
- Use spatial sound over standard 3D sound as much as possible

### [Spatial Sound in DirectX](https://developer.microsoft.com/en-us/windows/mixed-reality/spatial_sound_in_directx)
Add spatial sound to your Windows Mixed Reality apps based on DirectX by using the XAudio2 and xAPO audio libraries.

### [Spatial sound in Unity](https://developer.microsoft.com/en-us/windows/mixed-reality/spatial_sound_in_unity)
By default, Unity does not load a spatializer plugin. 
Spatial Sound, in Unity, is enabled using an audio spatializer plugin. The plugin files are bundled directly into Unity so enabling spatial sound is as easy as going to Edit > Audio > Spatializer and enabling the Microsoft HRTF extension. 

Spatial Sound is used in your Unity project by adjusting three settings on your Audio Source components. 
- In the Hierarchy panel, select the game object that has an attached Audio Source
- In the Inspector panel, under the Audio Source component
Check the Spatialize option.
Set Spatial Blend to 3D (numeric value 1).
For best results, expand 3D Sound Settings and set Volume Rolloff to Custom Rolloff.

### [Holograms 220: Spatial sound](https://developer.microsoft.com/en-us/windows/mixed-reality/holograms_220)
- Provide gesture feedback using sound.

- Sound, like light, can be occluded.
A classic example is a concert hall. When a listener is standing outside of the hall and the door is closed, the music sounds muffled. There is also typically a reduction in volume. When the door is opened, the full spectrum of the sound is heard at the actual volume.

Sound and Experience Design
- Normalize all sounds
- Design for an untethered experience
- Emit sound from logical locations on your holograms
- Familiar sounds are most localizable
- Be cognizant of user expectations
- Avoid hidden emitters

Sound Mixing
- Target your mix for 70% volume on the HoloLens
- HoloLens at 100% volume should drown out external sounds
- Use the Unity AudioMixer to adjust categories of sounds
- Mix sounds based on the user's gaze
- Building your mix


## [Spatial mapping](https://developer.microsoft.com/en-us/windows/mixed-reality/spatial_mapping)

// TODO : 泛泛而看，有空要回来再细读
Spatial mapping provides a detailed representation of real-world surfaces in the environment around the HoloLens, allowing developers to create a convincing mixed reality experience.By merging the real world with the virtual world, an application can make holograms seem real. 

The two primary object types used for spatial mapping are the 'Spatial Surface Observer' and the 'Spatial Surface'.
The application provides the Spatial Surface Observer with one or more bounding volumes, to define the regions of space in which the application wishes to receive spatial mapping data. For each of these volumes, spatial mapping will provide the application with a set of Spatial Surfaces. Each spatial surface describes real-world surfaces in a small volume of space, represented as a triangle mesh attached to a world-locked spatial coordinate system.

**Common Usage Scenarios**
- Occlusion
One of the primary uses of spatial mapping surfaces is simply to occlude holograms.This simple behavior has a huge impact on the perceived realism of holograms, helping to create a visceral sense that really inhabit the same physical space as the user.
Occlusion also provides information to the user; when a hologram appears to be occluded by a real-world surface, this provides additional visual feedback as to the spatial location of that hologram in the world. 

- Visualization
Most of the time it is appropriate for spatial surfaces to be invisible; to minimize visual clutter and let the real world speak for itself. However, sometimes it is useful to visualize spatial mapping surfaces directly, despite the fact that their real-world counterparts are already visible.

By visualizing surfaces, the application can share with the user its understanding of the environment.
The surface meshes provided by spatial mapping may not be particularly 'clean'. Thus it is important to visualize them appropriately. It is also possible to perform mesh processing to improve mesh properties, before the surfaces are rendered.

- Placement
Applications can also use the shape and direction of surfaces to guide hologram placement. 

At its extreme, user input can be simplified away entirely and spatial surfaces can be used to perform entirely automatic hologram placement. 
Note also that the ability of an application to use spatial surfaces for placement depends heavily on the application's scanning experience. If a surface has not been scanned, then it cannot be used for placement. It is up to the application to make this clear to the user, so that they can either help scan new surfaces or select a new location.

Visual feedback to the user is of paramount importance during placement. The user needs to know where the hologram is in relation to the nearest surface with grounding effects. They should understand why the movement of their hologram is being constrained (for example, due to collision with another nearby surface). If they cannot place a hologram in the current location, then visual feedback should make it clear why not. 

- Physics
The use of physics simulation is another way in which spatial mapping can be used to reinforce the presence of holograms in the user's physical space. When my holographic rubber ball rolls realistically off my desk, bounces across the floor and disappears under the couch, it might be hard for me to believe that it's not really there.
Physics simulation also provides the opportunity for an application to use natural and familiar physics-based interactions. 

In order to generate realistic physical behaviors, you will likely need to perform some mesh processing such as filling holes, removing floating hallucinations and smoothing rough surfaces.

You will also need to consider how your application's scanning experience influences its physics simulation.

- Navigation
Applications can use spatial mapping data to grant holographic characters (or agents) the ability to navigate the real world in the same way a real person would. This can help reinforce the presence of holographic characters by restricting them to the same set of natural, familiar behaviors as those of the user and their friends.
Navigation capabilities could be useful to users as well. Once a navigation map has been built in a given area, it could be shared to provide holographic directions for new users unfamiliar with that location. 

The key technical challenges involved in implementing navigation functionality will be reliable detection of walkable surfaces (humans don't walk on tables!) and graceful adaptation to changes in the environment (humans don't walk through closed doors!). The mesh may require some processing before it is usable for path-planning and navigation by a virtual character. Smoothing the mesh and removing hallucinations may help avoid characters becoming stuck. 

These challenges have received a great deal of attention in the development of videogame technology, and there is a wealth of available research literature on these topics.

Note that the built-in NavMesh functionality in Unity cannot be used with spatial mapping surfaces. This is because spatial mapping surfaces are not known until the application starts, whereas NavMesh data files need to be generated from source assets ahead of time. Also note that, the spatial mapping system will not provide information about surfaces very far away from the user's current location. So the application must 'remember' surfaces itself if it is to build a map of a very large area.


**Using The Surface Observer**
The starting point for spatial mapping is the surface observer. Program flow is as follows:
- Create a surface observer object
Provide one or more spatial volumes, to define the regions of interest in which the application wishes to receive spatial mapping data. A spatial volume is simply a shape defining a region of space, such as a sphere or a box.

- Use polling or notification to retrieve information about spatial surfaces
You may 'poll' the surface observer for spatial surface status at any time. Alternatively, you may register for the surface observer's 'surfaces changed' event, which will notify the application when spatial surfaces have changed.

- Process surfaces changes
- Process the asynchronous mesh request

**Mesh Caching**
Spatial surfaces are represented by dense triangle meshes. Storing, rendering and processing these meshes can consume significant computational and storage resources. As such, each application should adopt a mesh caching scheme appropriate to its needs, in order to minimize the resources used for mesh processing and storage. This scheme should determine which meshes to retain and which to discard, as well as when to update the mesh for each spatial surface.

**Rendering**
There are three primary ways in which spatial mapping meshes tend to be used for rendering:
- For surface visualization
- For occluding holograms behind real-world surfaces
- For modifying the appearance of holograms occluded by real-world surfaces

Performance is an important concern when rendering spatial mapping meshes. Here are some rendering performance techniques specific to rendering spatial mapping meshes:
- Adjust triangle density
- Perform frustum culling
- Adjust rendering order

**Mesh Processing**
An application may want to perform various operations on spatial surface meshes to suit its needs. The index and vertex data provided with each spatial surface mesh uses the same familiar layout as the vertex and index buffers that are used for rendering triangle meshes in all modern rendering APIs. However, one key fact to be aware of is that spatial mapping triangles have a front-clockwise winding order. 

**Raycasting and Collision**
In order for a physics API (such as Havok) to provide an application with raycasting and collision functionality for spatial surfaces, the application must provide spatial surface meshes to the physics API. 


### [Spatial mapping design](https://developer.microsoft.com/en-us/windows/mixed-reality/spatial_mapping_design)
In order to provide the best user experience, it is important to understand the factors that affect the quality of spatial mapping data gathered by HoloLens.
Errors in spatial mapping data fall into one of three categories:
- Holes: Real-world surfaces are missing from the spatial mapping data.
- Hallucinations: Surfaces exist in the spatial mapping data that do not exist in the real world.
- Bias: Surfaces in the spatial mapping data are imperfectly aligned with real-world surfaces, either pushed in or pulled out.

Several factors can affect the frequency and severity of these errors:
- User motion
The camera used for scanning provides data within a 70-degree cone, from a minimum of 0.8 meters to a maximum of 3.1 meters distance from the camera. Real-world surfaces will only be scanned within this field of view. Note that these values are subject to change in future versions.

- Surface materials
The materials found on real-world surfaces vary greatly. These impact the quality of spatial mapping data because they affect how infrared light is reflected.
Dark surfaces may not scan until they come closer to the camera, because they reflect less light.
Mirrors, because they create illusory reflections of real spaces and surfaces, can cause both hole errors and hallucination errors.

- Scene motion

- Lighting interference

**The environment scanning experience**
Each application that uses spatial mapping should consider providing a 'scanning experience'; the process through which the application guides the user to scan surfaces that are necessary for the application to function correctly.

Two principles:
clear communication with the user is the primary concern. 
applications should attempt to strike a balance between efficiency and reliability. 

To help design the right scanning experience, consider which of the following possibilities are applicable to your application:
- No scanning experience
- Find a suitable location
- Find a suitable configuration of surfaces
- Scan part of the environment
- Scan the whole room
- Take an initial snapshot of the environment
- Take use-initiated snapshots of the environment
- Allow the user to change the environment
- Guide the user to avoid errors in the spatial mapping data

**Mesh processing**
It may help to detect common types of errors in surfaces and to filter, remove or modify the spatial mapping data as appropriate.
- Hole filling
- Hallucination removal
- Smoothing
- Plane finding

Useful tools
- Hololens emulator can be used to provide reliable, repeatable input, which can be useful for debugging problems and evaluating changes to your code.
- To reproduce a scenarios, capture spatial mapping data over the network from a live HoloLens, then save it to disk and reuse it in subsequent debugging sessions.
- The Windows device portal 3D view provides a way to see all of the spatial surfaces currently available via the spatial mapping system. 

### [Room scan visualization](https://developer.microsoft.com/en-us/windows/mixed-reality/room_scan_visualization)

### [Spatial mapping in DirectX](https://developer.microsoft.com/en-us/windows/mixed-reality/spatial_mapping_in_directx)
https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping

### [Spatial mapping in Unity](https://developer.microsoft.com/en-us/windows/mixed-reality/spatial_mapping_in_unity)

SurfaceObserver
SpatialMapping prefab

Unity includes full support for spatial mapping, which is exposed to developers in the following ways:
Spatial mapping components available in the HoloToolkit, which provide a convenient and rapid path for getting started with spatial mapping
Lower-level spatial mapping APIs, which provide full control and enable more sophisticated application specific customization
To use spatial mapping in your app, the spatialPerception capability needs to be set in your AppxManifest.

- Getting started with Unity's built-in spatial mapping components
Unity offers 2 components for easily adding spatial mapping to your app, **Spatial Mapping Renderer** and **Spatial Mapping Collider**.

- Using the low-level Unity Spatial Mapping API
Unity封装Win10 API : Windows.Perception.Spatial.Surfaces，提供Low-level的Spatial Mapping API
Namespace: UnityEngine.VR.WSA
Types: SurfaceObserver, SurfaceChange, SurfaceData, SurfaceId

The following is an outline of the suggested flow for an application that uses the spatial mapping APIs :
1. Instantiate one SurfaceObserver object for each application-defined region of space that you need spatial mapping data for.
2. Specify the region of space that each SurfaceObserver object will provide data for by calling either SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox, or SetVolumeAsFrustum.
3. Handling Surface Changes OnSurfaceChanged
4. Handling data ready
The OnDataReady handler receives a SurfaceData object. The WorldAnchor, MeshFilter and (optionally) MeshCollider objects it contains reflect the latest state of the associated spatial surface. 
5. Start processing on updates
SurfaceObserver.Update() should be called on a delay, not every frame.
void Start () {
    ...
     StartCoroutine(UpdateLoop());
}

IEnumerator UpdateLoop()
{
    var wait = new WaitForSeconds(2.5f);
    while(true)
    {
        surfaceObserver.Update(OnSurfaceChanged);
        yield return wait;
    }
}

- Higher-level mesh analysis: SpatialUnderstanding
目前只能做简单的特征检测，比如floor, ceiling, and walls，如果使用Vuforia这样的recognition SDK，则遇到不通用的问题，这个还有很长的路要走。
When placing holograms in the physical world it is often desirable to go beyond spatial mapping’s mesh and surface planes. When placement is done procedurally, a higher level of environmental understanding is desirable. This usually requires making decisions about what is floor, ceiling, and walls. 
The HoloToolkit.SpatialUnderstanding library encapsulates this technology, allowing you to quickly find empty spaces on the walls, place objects on the ceiling, identify placed for character to sit, and a myriad of other spatial understanding queries.
The code for the C++ solver has been wrapped into a UWP dll and exposed to Unity with a drop in prefab contained within the HoloToolkit.

There are three primary interfaces exposed by the module: topology for simple surface and spatial queries, shape for object detection, and the object placement solver for constraint based placement of object sets.

The understanding dll internally stores the playspace as a grid of 8cm sized voxel cubes.


### [Holograms 230: Spatial mapping](https://developer.microsoft.com/en-us/windows/mixed-reality/holograms_230)
主要介绍几个场景，包括环境Scanning，将扫描结果Visualization，对mesh数据的处理，找到Planes(Walls，Ceilings，Floors)，然后placement Hologram到识别到的Plane上，最后Determine if a hologram is occluded by the spatial mapping mesh.Apply different occlusion techniques to achieve a fun effect.

Scanning, Visualization, Processing, Placement, Occlusion

- You know how to scan your environment and load spatial mapping data to Unity.
- You understand the basics of shaders and how materials can be used to re-visualize the world.
- You learned of new processing techniques for finding planes and removing triangles from a mesh.
- You were able to move and place holograms on surfaces that made sense.
- You experienced different occlusion techniques and harnessed the power of x-ray vision!


## [Shared experiences in mixed reality](https://developer.microsoft.com/en-us/windows/mixed-reality/shared_experiences_in_mixed_reality)
Holographic apps may share spatial anchors from one HoloLens to another, enabling users to render a hologram at the same place in the real world across multiple devices.

Before you begin designing for shared experiences, it’s important to define the target scenarios. These scenarios help clarify what you’re designing and establish a common vocabulary to help compare and contrast features required in your experience. Understanding the core problem, and the different avenues for solutions, is key to uncovering opportunities inherent in this new medium.

Through internal prototypes and explorations from our HoloLens partner agencies, we created six questions to help you define shared scenarios. These questions form a framework, not intended to be exhaustive, to help distill the important attributes of your scenarios.
1. How are they sharing?
There are many ways to share, but we’ve found that most of them fall into three categories: 
- Presentation
 When the same content is being shown to several users. \
- Collaboration
When people are working together to achieve some common goals.
- Guidance
When one person is helping someone to solve a problem in a more one-one style interaction. 

2. What is the group size?
We have found that the needs of groups can fall into three size categories:
1:1
Small < 7
Large >= 7

3. Where is everyone?
Following categories help convey where users are located:
Co-located: All your users will be in the same physical space.
Remote: All your users will be in separate physical spaces.
Both: Your users will be a mix of co-located and remote spaces.

4. When are they sharing?
Consider your experiences as one of these categories of time:
- Synchronously: Sharing the holographic experience at the same time.
- Asynchronously: Sharing the holographic experience at different times. 
- Both: Your users will sometimes be sharing synchronously but other times asynchronously.

5. How similar are their physical environments?
Consider your sharing experiences fitting into one of these two categories:
- Similar: Environments that tend to have similar furniture, ambient light and sound, physical room size. 
- Dissimilar: Environments that are quite different in furniture settings, room sizes, light and sound considerations.

It's important to think about the environment as it will influence:
How will people experience these objects. For example: If your experience works best on a table and the user has no table? Or on a flat floor surface but the user has a cluttered space.
Scale of the objects. For example: Placing a 6 feet human model on a table could be challenging but a heart model would work great.

6. What devices are they using?
immersive devices, holographic devices,  2D devices

The key to shared experiences is multiple users seeing the same holograms in the world on their own device. One of the most common methods to do this is to use spatial anchors in your app. 

### [Coordinate Systems](https://developer.microsoft.com/en-us/windows/mixed-reality/coordinate_systems)

Mixed reality experience scales : Orientation-only, Setaed-scale, Standing-scale, Room-scale, World-scale
根据不同的设备的能力，提供不同的experienc scale. These experience scales follow a "nesting dolls" model. The key design principle here for Windows Mixed Reality is that a given headset supports apps built for a target experience scale, as well as all lesser scales
Orientation-only : 传统的
Seated-scale : 6DOF tracking
Standing-scale : 6DOF tracking, Floor defined, 360 tracking
Room-scale : 6DOF tracking, Floor defined, 360 tracking, Bounds defined
World-scale: 6DOF tracking, Floor defined, 360 tracking, Bounds defined, Spatial anchors

- Spatial coordinate systems

All 3D graphics applications use Cartesian coordinate systems(笛卡尔坐标系) to reason about the positions and orientations of objects in the virtual worlds they render. Such coordinate systems establish 3 perpendicular axes along which to position objects: an X, Y, and Z axis.
In mixed reality, your apps will reason about both virtual and physical coordinate systems. Windows calls a coordinate system that has real meaning in the physical world a spatial coordinate system.
Spatial coordinate systems express their coordinate values in meters. This means that objects placed 2 units apart in either the X, Y or Z axis will appear 2 meters apart from one another when rendered in mixed reality. This lets you easily render objects and environments at real-world scale.

Spatial coordinate systems on Windows are always right-handed, which means that the positive X-axis points right, the positive Y-axis points up (aligned to gravity) and the positive Z-axis points towards you.

- Building an orientation-only or seated-scale experience

The key to holographic rendering is changing your app's view of its holograms each frame as the user moves around, to match their predicted head motion.  You can build seated-scale experiences that respect changes to the user's head position and head orientation using a stationary frame of reference(静止参照系).

For seated-scale experiences in a game engine such as Unity, a stationary frame of reference is what defines the engine's "world origin". Objects that are placed at a specific world coordinate use the stationary frame of reference to define their position in the real-world using those same coordinates. Content that stays put in the world, even as the user walks around, is known as world-locked content.

对于坐标系统的理解还需要结合世界的代码

An attached frame of reference moves with the user as they walk around, with a fixed heading defined when the app first creates the frame. 
When the headset can't figure out where it is in the world, an attached frame of reference provides the only coordinate system which can be used to render holograms. 

- Building a standing-scale or room-scale experience
To go beyond seated-scale on an immersive headset to build a standing-scale experience, you can use the stage frame of reference.
To provide a room-scale experience, letting users walk around within the 5-meter boundary they pre-defined, you can check for stage bounds as well.

- Building a world-scale experience

HoloLens allows for true world-scale experiences that let users wander beyond 5 meters. To build a world-scale app, you'll need new techniques beyond those used for room-scale experiences.

Today, when writing games, data visualization apps, or virtual reality apps, the typical approach is to establish one absolute world coordinate system that all other coordinates can reliably map back to. In that environment, you can always find a stable transform that defines a relationship between any two objects in that world. 

By placing a spatial anchor at the location where the user places a hologram and then positioning that hologram relative to its spatial anchor, you can ensure that the hologram maintains optimal stability, even as the user roams across tens of meters.

- Spatial anchors
A spatial anchor represents an important point in the world that the system should keep track of over time.  As the device learns about the world, these spatial anchors can adjust their position relative to one another as needed to ensure that each anchor stays precisely where it was placed relative to the real-world. 


- Spatial anchor persistence

Spatial anchors can also allow your app to remember an important location even after your app suspends or the device is shut down.
You can save to disk the spatial anchors your app creates, and then load them back again later, by persisting them to your app's spatial anchor store. When saving or loading an anchor, you provide a string key that is meaningful to your app, in order to identify the anchor later. Think of this key as the filename for your anchor. If you want to associate other data with that anchor, such as a 3D model that the user placed at that location, save that to your app's local storage and associate it with the key you chose.
By persisting anchors to the store, your users can place individual holograms or place a workspace around which an app will place its various holograms, and then find those holograms later where they expect them, over many uses of your app.

https://developer.microsoft.com/en-us/windows/mixed-reality/persistence_in_unity

- Spatial anchor sharing

Your app can also share spatial anchors with other devices. By transferring a spatial anchor along with its supporting understanding of the environment and sensor data around it to a second HoloLens, both devices can then reason about the same location. By having each device render a hologram using that shared spatial anchor, both users will see the hologram appear at the same place in the real world.

- Avoid Head-locked content

We strongly discourage rendering head-locked content, which stays at a fixed spot in the display (such as a HUD). In general, head-locked content is uncomfortable for users and does not feel like a natural part of their world.
Head-locked content should usually be replaced with holograms that are attached to the user or placed in the world itself. For example, cursors should generally be pushed out into the world, scaling naturally to reflect the position and distance of the object under the user's gaze.


- Handling tracking errors

In some environments such as dark hallways, it may not be possible for a headset using inside-out tracking to locate itself correctly in the world. This can lead holograms to either not show up or appear at incorrect places if handled incorrectly. 

1. Headset cannot track due to insufficient sensor data

Sometimes, the device's sensors are not able to figure out where the device is. This can happen if the room is dark, or if the sensors are covered by hair or hands, or if the surroundings do not have enough texture. Your app should tell the user how to get positional tracking back, rendering some fallback body-locked content that describes some tips, such as uncovering the sensors and turning on more lights.
环境太暗，或者被手，头发遮挡，导致定位失效，需要通知用户调整环境

2. Headset tracks incorrectly due to dynamic changes in the environment

Sometimes, the device cannot track properly if there are lot of dynamic changes in the environment. For example, many people walking around in the room. In this case, the holograms may seem to jump or drift as the device tries to track itself in this dynamic environment. We recommend using the device in a less dynamic environment if you hit this scenario.
环境太多动态内容，比如人来人往，太复杂的环境导致识别不稳定。

3. Headset tracks incorrectly because the environment has changed significantly over time

Sometimes, when you start using a device in an environment which has undergone lot of changes (e.g. significant movement of furniture, wall hangings etc.), it is possible that some holograms may appear shifted from their original locations. If the newly placed holograms also seem to shift and jump, please ask the user to remove the current space on the device by going to Settings > System > Spaces. Please note that removing a space leads to loss of all the holograms.
环境变化太大，系统已经混乱，无法恢复，建议移除

4. Headset tracks incorrectly due to identical spaces in an environment

Sometimes, a home/space may have two identical portions. For example, two identical rooms in a home, two identical corner areas, two large identical posters that cover the device's field of view. In such scenarios, the device may, at times, get confused between the identical parts and mark them as the same in its internal representation. This may cause the holograms from some areas to appear in other locations. 
相同的背景导致无法区分，可能出现一个hologram出现在另一个地方的情况

从上面说明来看，Hololens不但只能用在受限的环境，而且还有诸多要求，要变成随身携带，随时可用还有漫漫长路。

- [Coordinate systems in DirectX](https://developer.microsoft.com/en-us/windows/mixed-reality/coordinate_systems_in_directx)

从原生API应用的角度来理解坐标系统，理解会更深入。
Handling tracking loss :  https://developer.microsoft.com/en-us/windows/mixed-reality/tracking_loss_in_unity


- [Coordinate systems in Unity](https://developer.microsoft.com/en-us/windows/mixed-reality/coordinate_systems_in_unity)
Windows Mixed Reality supports apps across a wide range of experience scales, from orientation-only and seated-scale apps up through room-scale apps. On HoloLens, you can go further and build world-scale apps that let users walk beyond 5 meters, exploring an entire floor of a building and beyond.

Your first step in building a mixed reality experience in Unity is to determine which experience scale your app will target.

### [Spatial anchors](https://developer.microsoft.com/en-us/windows/holographic/spatial_anchors)
A spatial anchor represents an important point in the world that the system should keep track of over time. Each anchor has a coordinate system that adjusts as needed, relative to other anchors or frames of reference, in order to ensure that anchored holograms stay precisely in place. By saving spatial anchors to disk and loading them back later, your app can reason about the same location in the real-world across multiple app sessions.

Rendering a hologram in an anchor's coordinate system gives you the most accurate positioning for that hologram at any given time. This comes at the cost of small adjustments over time to the hologram's position, as the system continually moves it back into place relative to the real world.

or standing-scale or room-scale experiences for tethered desktop headsets that will stay within a 5-meter diameter, you can usually just use the stage frame of reference instead of spatial anchors, providing you a single coordinate system in which to render all content. However, if your app intends to let users wander beyond 5 meters on HoloLens, perhaps operating throughout an entire floor of a building, you'll need spatial anchors to keep content stable.

**Best practices**
- Create spatial anchors where users place them
- Always render anchored holograms within 3 meters of their anchor
- Group holograms that should form a rigid cluster
- Render highly dynamic holograms using the stationary frame of reference instead of a spatial anchor
- Avoid creating a grid of spatial anchors
- Release spatial anchors you no longer need

### [Shared spatial anchors in DirectX](https://developer.microsoft.com/en-us/windows/mixed-reality/shared_spatial_anchors_in_directx)

https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicTagAlong

### [Shared experiences in Unity](https://developer.microsoft.com/en-us/windows/mixed-reality/shared_experiences_in_unity)
https://developer.microsoft.com/en-us/windows/mixed-reality/persistence_in_unity

To share a WorldAnchor, one must establish the anchor to be shared. The user of one HoloLens scans their environment and either manually or programmatically chooses a point in space to be the Anchor for the shared experience. The data that represents this point can then be serialized and transmitted to the other devices that are sharing in the experience. Each device then de-serializes the anchor data and attempts to locate that point in space. In order for Anchor Sharing to work, each device must have scanned in enough of the environment such that the point represented by the anchor can be identified.

Namespace: UnityEngine.VR.WSA.Sharing
Type: WorldAnchorTransferBatch

UnityEngine.VR.WSA.WorldAnchor

You can use the Sharing prefab from the HoloToolkit-Unity to implement shared experiences in your applications.

### [Holograms 240: Sharing holograms](https://developer.microsoft.com/en-us/windows/mixed-reality/holograms_240)
Holograms are given presence in our world by remaining in place as we move about in space. HoloLens keeps holograms in place by using various coordinate systems to keep track of the location and orientation of objects. When we share these coordinate systems between devices, we can create a shared experience that allows us to take part in a shared holographic world.

, Placement, Real-World Physics, Grand Finale

- Shared Coordinates
Setup a network for a shared experience.
Establish a common reference point.
Share coordinate systems across devices.
Everyone sees the same hologram!

The InternetClientServer and PrivateNetworkClientServer capabilities must be declared for an app to connect to the sharing server. 

- Discovery
Discover each other in our shared experience.
Choose and share a player avatar.
Attach the player avatar next to everyone's heads.

- Placement
Place holograms on the spatial map based on players’ head position.

- Real-World Physics
Launch projectiles that bounce off real-world surfaces.
Share the projectiles so other players can see them.


### [Spectator view](https://developer.microsoft.com/en-us/windows/mixed-reality/spectator_view)

https://blogs.windows.com/devices/2017/02/13/spectator-view-new-tool-help-others-see-see-hololens

Spectator view allows others to see on a 2D screen what a HoloLens user sees in their world. 


使用MRC，可以用于将MR场景直播。


## [Locatable Camera](https://developer.microsoft.com/en-us/windows/mixed-reality/locatable_camera)
HoloLens includes a world-facing camera mounted on the front of the device which enables apps to see what the user sees. Developers have access to and control of the camera just as they would for color cameras on smartphones, portables, or desktops. The same universal windows media capture and windows media foundation APIs that work on mobile and desktop work on HoloLens. Unity has also wrapped these windows APIs to abstract simple usage of the camera on HoloLens for tasks such as taking regular photos and videos (with or without holograms) and locating the camera's position in and perspective on the scene.

### [Locatable camera in DirectX](https://developer.microsoft.com/en-us/windows/mixed-reality/locatable_camera_in_directx)
### [Locatable camera in Unity](https://developer.microsoft.com/en-us/windows/mixed-reality/locatable_camera_in_unity)

### [Mixed reality capture](https://developer.microsoft.com/en-us/windows/mixed-reality/mixed_reality_capture)

### [Mixed reality capture for developers](https://developer.microsoft.com/en-us/windows/mixed-reality/mixed_reality_capture_for_developers)

https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicMixedRealityCapture


# [Open Source Projects](https://developer.microsoft.com/en-us/windows/mixed-reality/Community.html#open_source_projects):

## [HoloToolkit](https://github.com/microsoft/HoloToolkit)
在Windows Holographic API的基础上，封装一些通用功能，主要提供Spatial Mapping, Spatial Understanding, Sharing的C++ dll及Unity Plugin实现。


## [HoloToolkit-Unity](https://github.com/microsoft/HoloToolkit-Unity)
可以看到在开发Holograms tutorials的过程中，逐步积累了一些通用的prefab，script，再加上HoloToolkit dll ，对这些内容的封装就构成了HoloToolkit-Unity，也为开发其他应用提供了基础。

在使用Unity开发Hololens应用前，需要对Unity做一些配置，包括project，Camera的配置，这些都可以预先设置，避免重复劳动，这个库可以作为开发自己应用的起点，值得深入学习。特别是HoloToolkit-Tests可以理解如何使用。

HoloToolkit-Unity的Example里，提供一些有价值的想法
https://github.com/Microsoft/HoloToolkit-Unity/tree/master/Assets/HoloToolkit-Examples/InteractiveElements 封装了如下的UI controls：Button, Toggle Button, RadialButton, CheckBox, Toggle, Progress, Slider

## [MRDesignLabs](https://github.com/Microsoft/MRDesignLabs)
This repo is where Microsoft's Windows Mixed Reality Design team publishes examples and explorations. The goal is to inspire creators and help them to build Mixed Reality experiences.
提供了一些通用Controls的代码和例子 ： 
- Interactable Object
Mesh button : using primitives and imported 3D meshes as Interactable Objects
Holographic button : 
Toolbar : Toolbar is a widely used pattern in mixed reality experiences. It is a simple collection of buttons with additional behavior such as Billboarding and tag-a-long. 
Traditional button :  traditional 2D style button with some dimension. Each input state has a slightly different depth and animation properties.  

- App Bar and Bounding Box

- Object Collection
Object collection is a script which helps you lay out an array of objects in predefined three-dimensional shapes. It supports four different surface styles - plane, cylinder, sphere and scatter. 

- Dialog
Dialog is a transient UI element which appears when something happens that requires notification, approval, or additional information from the user. 

- Progress


### Periodic Table of the Elements
包含MRDesignLab提供的一些通用组件(Button，Cursor，Dialog，Keyboard)的例子，这里的问题是这些模块都是采用源代码级的复用方式，那就是要各自维护自己的版本，导致复用程度比较低。


## [Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer)
一个完整的开源的Holographic应用，https://developer.microsoft.com/en-us/windows/mixed-reality/galaxy_explorer对开发过程做了描述.12个人，8周的时间设计，编码，完善。


## [HoloLens Companion Kit](https://github.com/Microsoft/HoloLensCompanionKit)
提供与Hololens配对的应用开发的toolkit,辅助Hololens开发的其他平台代码组件
- Holographic Remoting Host
https://developer.microsoft.com/en-us/windows/mixed-reality/add_holographic_remoting

- KinectIPD

- MixedRemoteViewCompositor

- SpectatorView

- Windows Mixed Reality Commander


# [Case Study](https://developer.microsoft.com/en-us/windows/mixed-reality/category/case_studies)
对MR设计，开发的基本概念，原理，实现有一定的理解之后，可以更广泛的了解和思考不同的MR应用是如何设计和实现的，对于实现自己的MR应用有借鉴和启发作用。

https://developer.microsoft.com/en-us/windows/mixed-reality/case_study_-_3_holostudio_ui_and_interaction_design_learnings

https://developer.microsoft.com/en-us/windows/mixed-reality/case_study_-_expanding_the_spatial_mapping_capabilities_of_hololens

Case study - 3 HoloStudio UI and interaction design learnings
Case study - AfterNow's process - envisioning, prototyping, building
Case study - Building HoloSketch, a spatial layout and UX sketching app for HoloLens
Case study - Capturing and creating content for HoloTour
Case study - Creating a galaxy in mixed reality
Case study - Creating an immersive experience in Fragments
Case study - Creating impossible perspectives for HoloTour
Case study - Expanding the spatial mapping capabilities of HoloLens
[Case study - Looking through holes in your reality](https://developer.microsoft.com/en-us/windows/mixed-reality/case_study_-_looking_through_holes_in_your_reality)
Case study - My first year on the HoloLens design team

[Case study - Spatial sound design for HoloTour](https://developer.microsoft.com/en-us/windows/mixed-reality/case_study_-_spatial_sound_design_for_holotour)
Case study - The pursuit of More Personal Computing
Case study - Using spatial sound in RoboRaid
Case study - Using the stabilization plane to reduce holographic turbulence

[Case study - Representing humans in mixed reality](https://developer.microsoft.com/en-us/windows/mixed-reality/case_study_-_representing_humans_in_mixed_reality)


# Others
Hololens提供了环境感知的能力(基于SLAM)，如果需要提供AR那样的识别物体，然后交互的能力，则需要像Vuforia这样的SDK。从2012年Deep Learning在Computer Vision领域的应用，证明了其在物体识别精度上的有效性后，对物体识别的技术都转移到使用Deep Learning上。

- [Using the Windows Device Portal](https://developer.microsoft.com/en-us/windows/mixed-reality/using_the_windows_device_portal)
The Device Portal is a web server on your HoloLens that you can connect to from a web browser on your PC. The Device Portal includes many tools that will help you manage your HoloLens and debug and optimize your apps.
Everything in the device portal is built on top of REST API's that you can optionally use to access the data and control your device programmatically.

这个Developer辅助功能非常好用，提供非常多可视化功能，可以用来管理Hololens，调试，优化应用。
通过浏览器，可以查看，控制Hololens设备；提供3D View管理；提供MRC，实时查看，录像，拍照功能；性能常看，分析等

而且微软还开源了一个[Windows Device Portal Wrapper](https://github.com/Microsoft/WindowsDevicePortalWrapper)的库，用来开发MR直播很有用，获取MRC视频后转发出去。

- [Hologram stability](https://developer.microsoft.com/en-us/windows/mixed-reality/Hologram_stability.html)


Stabilization plane : https://developer.microsoft.com/en-us/windows/mixed-reality/focus_point_in_unity

- [Keyboard input in Unity](https://developer.microsoft.com/en-us/windows/mixed-reality/keyboard_input_in_unity)


- FAQ
https://support.microsoft.com/en-us/help/13456/hololens-and-holograms-faq
Hololens使用Fly on Light 传感器在感知周围环境，当出现环境太暗，有遮挡等导致SLAM失效

要生成Windows Store 离线安装文件(.appx)或部署文件(.appxbundle)，在VS的Project -> Store -> Create App Packages...即可

- Performance recommendations for HoloLens apps
https://developer.microsoft.com/en-us/windows/mixed-reality/performance_recommendations_for_hololens_apps

- Current limitations for apps using APIs from the shell
https://developer.microsoft.com/en-us/windows/mixed-reality/current_limitations_for_apps_using_apis_from_the_shell

- [Health & Safety](https://www.microsoft.com/en-us/hololens/legal/health-and-safety-information)
An interpupillary distance (an eye measurement of the distance between your two pupils) between 51 and 74 is needed to correctly and comfortably view Holograms with HoloLens. This range accommodates most adults and children age 13 and older. 

和Oculus Rift等一样，未来避免法律问题，不许13岁以下未成年人使用。对于教育领域的应用来说，初2以上的学生才能使用。
可能出现的不适症状：nausea(恶心), motion sickness(晕动症), dizziness(头晕), disorientation(迷失方向), headache(头痛), fatigue(疲劳), eye strain(眼睛疲劳), dry eye(眼睛干涩)


# My Practices
上述主要是文字笔记，实践经验参见 https://wangwh0204.github.io/2017/09/01/porting-to-hololens/

