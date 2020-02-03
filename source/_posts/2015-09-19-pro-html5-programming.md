title: HTML5 高级程序设计
date: 2015-09-19
updated: 2015-09-28
categories: 
- [technology]
tags: 
- HTML5
---

&lt;&lt;Pro HTML5 Programming&gt;&gt;的中文版&lt;&lt;HTML5 高级程序设计&gt;&gt;读书笔记, 本书适合对HTML5相关概念快速了解，用1周时间看完<!--more-->


# 01 HTML5概述

HTML5是基于各种各样的理念进行设计：
- 兼容性 ：存在即合理
- 实用性 ：效率和用户优先
  表现和内容分离
  化繁为简
- 互通性 ：
- 通用访问性 ： 


HTML5 :
- Canvas : 2D & 3D(WebGL)
- Cross-document 消息传送
- Geolocation
- Media : audio & video
- Forms
- MathML
- Microdata
- Server-Sent Event
- Scalable Vector Graphics(SVG)
- WebSocket
- Web Origin Concept
- Web Storage
- IndexedDB
- Application Cache
- Web Workers
- Drag & Drop
- XMLHttpRequest
- WebRTC

www.caniuse.com网站按照浏览器的版本提供了详尽的HTML5功能支持情况。若用户通过浏览器访问www.html5test.com的话，该网站会直接显示用户浏览器对HTML5规范的支持情况。

- semantics
    - SVG
    - MathML
    - Microdata
- multimedia
    - video
    - audio
- graphics
    - 2D
    - WebGL
- device access
    - Geolocation
- offline
    - Application Cache
    - IndexedDB
- connectivity
    - Server-Sent Events
    - WebSocket
    - WebRTC
- performance
    - Web Workers
- Web Components
    - Custom elements
    - Shadow DOM
    - HTML templates
    - HTML imports

主流的浏览器：
Apple Safari, Google Chrome, Microsoft IE, Mozilla Firefox, Opera

和windows，Android，iOS一样，WEB也自成一个平台。HTML5涵盖了UI，grpahics，multimeida，network各个技术方向。


我们强烈推荐使用Modernizr，因为它是检测浏览器是否支持某些特性的最佳工具。

<!DOCTYPE html>
<meta charset="utf-8">

新的片段类元素 
header 头部区域
footer	脚部区域
section 一块区域
article 独立文章内容
aside 	相关内容或者引文
nav	导航类辅助内容

在HTML5的实际编程中，开发人员必须使用CSS来定义样式。

margin padding

使用Selectors API简化选取操作

很多调试工具(chrome Developer Tools : Ctrl + Shitf + J)支持设置断点来暂停代码执行，分析程序状态以及查看变量的当前值。console.log 已经成为JavaScript开发人员记录日志的事实标准。

# 02 Canvas API

Canvas本质上是一个位图画图，在其上绘制的图形是不可缩放的，不能像SVG图像那样可以放大缩小。
transformation : 缩放，平移，旋转

在HTML5 Canvas API中，canvas的清除矩形功能是创建动画和游戏的核心功能。如果需要创建流畅的动画，需要使用裁剪(clipping)功能。

阴影，渐变色

canvas可以用于整个浏览器窗口或者其中的一部分之上--这种技术通常被称作“glass pane”玻璃窗。可以应用在：获取页面的DOM元素的绝对位置，然后创建循序渐进的帮助功能，引导用户；还可以用来在页面上绘制反馈。

目前许多浏览器为windows对象提供了requestAnimatonFrame函数，该函数以一个回调函数为参数，在浏览器认为更新动画时机已到时，回调函数就会被调用。

HTML5 Canvas API可以通过自由组合图像，渐变和复杂path等方式来创建能想到的几乎所有效果。需要注意的是，绘制工作通常应以原点为起点，在展现图像之前要先完成加载，而在使用外部来源的图片时则要留心。如果能学会驾驭canvas，那么就能在网页上创建出前所未见的应用。

# 03 SVG
SVG : Scalable Vector Graphics
SVG的本质特征是它基于XML. 在HTML5出现之前，可以在HTML页面上的<img>元素中嵌入SVG或者链接到自包含的.svg文档。借助SVG，可以实现很多同canvas API类似的绘制操作。
但存在一些重要且不可见的差异。首先，SVG绘制的文本可选，而利用canvas则做不到。在Canvas元素上绘制文本时，字符会以像素方式固定到上面。文本成为图像的一部分。因此，canvas上的文本无法被搜索引擎获取，而SVG上的文本是可搜索的。

SVG同HTML密切相关。可以使用标记来定义SVG文档的内容。通过DOM API，可以与SVG和HTML进行交互。SVG文档是元素构成的树状结构，同HTML一样，它支持脚本操作和样式。还可以向SVG元素添加事件处理函数。、此外，在浏览器的开发工具中能够查看和编辑SVG结构。在开发环境中，可以添加，删除以及编辑SVG元素，修改的结果会立即显示在页面上，非常便于调试和测试。

放大，旋转或者用其他手段变换SVG内容的时后，渲染程序会立即重绘所有构成图像的线条。缩放SVG不会导致其质量下降。SVG文档在呈现时会保留构成它的矢量信息。

SVG 绘制形状对象时是按照对象在文档中出现的顺序进行的。

SVG中有些组织元素，可用于将多个元素组合起来，使它们作为一个整体进行变换或链接。<g>表示group，可以用来组合多个相关的元素。组可以作为一个整体进行变换，变换属性包含旋转，变形，缩放和斜切。

SVG的path元素有一个d属性，d代表数据。在d属性的值中，能够指定一系列路径绘制命令。每条命令都可能带有坐标参数。M代表moveto, L代表Lineto，Q代表二次曲线，Z代表闭合路径。

# 04 音频和视频
不论是音频文件还是视频文件，实际上都只是一个container文件，包含了音频轨道，视频轨道和其他一些元数据。
主流视频容器：
- Audio Video Interleave(.avi)
- Flash Video(.flv)
- MPEG 4(.mp4)
- Matroska(.mkv)
- Ogg(.ogv)

音频编解码器：
- AAC
- MPEG-3
- Ogg Vorbis

视频编解码器:
- H.264
- VP8
- Ogg Theora

2010年5月，google发布了WebM视频格式。WebM后缀名是.webm，是基于Matroska修改的封装格式，视频使用VP8编码，音频使用Ogg Vorbis编码.

鉴于浏览器对编解码器的支持并不统一，仅仅知道哪些浏览器支持新的audio元素和video元素是不够的，还要知道浏览器支持那种编解码器。

检测浏览器是否支持audio或video元素最简单的方式是用脚本动态创建它，然后检测特定函数是否存在：
var hasVideo = !!(document.createElement('video').canPlayType);

video元素有一个关键特性：可被HTML5 Canvas的函数调用:drawImage(video...)

对象，属性，事件

# 05 Geolocation API
HTML5 Geolocation API允许用户在Web应用程序中共享他们的位置，使其能够享受位置感知服务。

HTML5 Geolocation API的使用方法相当简单。请求一个位置信息，如果用户同意，浏览器就会返回位置信息，该位置信息是通过支持HTML5地理定位功能的底层设备提供给浏览器的。位置信息由纬度，经度坐标和一些其他元数据组成。

经纬度坐标可以使用以下两种方式表示：
- 十进制格式(例如, 39.17222)
- DMS(Degree Minute Second,角度)格式(例如, 39 10'20')
HTML5 Geolocation API返回坐标的格式是 十进制 格式

设备可以使用下列数据源：
- IP地址
- 三维坐标
    - GPS
    - 从RFID, WIFI和蓝牙的MAC地址
    - GSM或CDMA手机的ID
- 用户自定义数据

距离计算使用众所周知的Haversine公式实现，这个公式能够根据经纬度来计算地球上两点间的距离。 


# 06 Communication API
本章将讨论用于构建实时(real-time)跨源(cross-origin)通信的两个重要模块：跨文档消息通信(Cross Document Message)和XMLHttpRequest Level 2.

跨文档消息通信可以确保iframe，标签页，窗口间安全地进行跨源通信。它把postMessage API定义为发送消息的标准方式.

HTML5通过引入源(origin)的概念对域安全进行了阐明和改进。源是在网络上建立信任关系的地址的子集。源由规则(scheme), 主机(host)，端口(port)组成。

XMLHttpRequest API使得Ajax技术的实现成为可能。

# 07 WebSockets API
HTML5 WebSockets是HTML5中最强大的通信功能，它定义了一个全双工通信信道，仅通过Web上的一个Socket即可进行通信。
WebSockets淘汰传统的Comet和Ajax轮询(polling)，长轮询(long-polling)以及流(streaming)解决方案。

目前实时Web应用的实现方式，大部分是围绕轮询和其他服务器端推送技术展开的，其中最著名的是Comet.Comet技术可以让服务器端主动以异步方式向客户端推送数据，它会使针对传输消息到客户端的响应延迟完成。

所有这些提供实时数据的方式都会涉及HTTP请求和响应报头，其中包含由大量的额外的不必要的报头数据，会造成传输延迟。

Websocket是Web应用程序的传输协议，类似于TCP，它提供了双向的，按序到达的数据流。和TCP协议一样，高层协议能够在WebSocket上运行。作为WEB的一部分，Websocket连接的是URL，而非因特网上 的主机和端口。

为了建立WebSocket通信，客户端和服务器在初始握手时，将HTTP协议升级到了WebSocket协议。一旦连接建立成功，就可以在全双工模式下在客户端和服务器端之间来回传送websocket消息。
每个消息以0x00开头，以0xFF结尾，中间数据采用UTF-8编码格式。

基于同一底层TCP/IP连接，在客户端和服务器之间的初始握手阶段，将HTTP协议升级至WebSocket协议，WebSocket连接就建立完成了。连接一旦建立，WebSocket数据帧就可以以全双工模式在客户端和服务器之间进行双向传送。连接本身是通过WebSocket接口定义的message事件和send函数来运作的。

在使用WebSockets API之前，开发人员还需要一个支持WebSocket的服务器。下面是几种现有的WebSocket服务器：
- Kaazing WebSocket Gateway : 一种基于Java的WebSocket网关
- mod_pywebsocket : 一种基于python的Apache HTTP服务器扩展
- Netty : 一种包含WebSocket的JAVA框架
- node.js : 一种驱动多个WebSocket服务器的服务器端JavaScript框架

WebSocket接口的使用非常简单，要连接通信端点，只需要创建一个新的WebSocket实例，并提供希望连接的对端URL。
建立WebSocket连接时，可以列出Web应用能够使用的协议。可使用的协议包括XMPP，AMQP，RFB(Remote Frame Buffer, 或VNC）和STOMP
使用标准化的协议能够确保来自不同机构的Web应用和服务器的互操作性。

WebSocket编程遵循异步编程模型：打开socket后，只需等待事件发生，而不需要主动向服务器轮询，所以需要在websocket对象中添加回调函数来监听事件。
WebSocket对象有三个事件:open, close和message. 同大多数Javascript API一样，事件处理时会调用相应的onopen, onmessage, onclose, onerror回调函数。
当socket处于打开状态，可以采用send方法发送消息。

# 08 Forms API
一定要领会HTML5 Forms的核心设计理念：规范的核心是功能性动作和语义，而非外观和显示效果。
规范虽然详细描述了相关功能性API的使用方法，如颜色，日历，数值选择器，邮件地址等，但是它没有规定浏览器应该以何种方式将这些元素呈现给用户。

新的输入控件：
- tel
- email
- url
- search
- range
- number
将输入控件指定为特殊的类型的好处是，可以让浏览器在支持控件的情况下，为用户呈现不同的输入方式或用户界面，而且浏览器还可以在表单提交前对其做进一步的验证。
移动设备浏览器向来是最先支持这些表单控件类型的浏览器。在手机上，每按下或单击一个键对于没有全键盘的用户来说，都是较大的负担。通过声明不同的类型，浏览器会显示不同的输入界面。

新的表单特性和函数
1. placeholder
当用户还没有输入值的时候，输入型控件可以通过placeholder特性向用户显示描述型说明或者提示信息。
2. autocomplete
浏览器通过autocomplete特性能够知晓是否应该保存输入值以备将来使用。
3. autofocus
页面载入时，开发人员通过autofocus特性可以指定某个表单元素获得输入焦点。与其他布尔类型特性一样，使autofocus特性生效不需要专门将其值设为true。
4. spellcheck
可对带有文本内容的输入控件和textarea控件设置spellcheck属性。设置完成后，它会询问浏览器是否应该给出拼写检查结果反馈。
5. list特性和datalist元素 
通过组合使用list特性和datalist元素，开发人员能够为某个输入型控件构造一张选值列表。
6. min和max
通过设置min和max特性，可以将range输入框的数值输入范围设定在最低值和最高值之间。
7. step
对于输入型控件，设置其step特性能够指定输入值递增或递减的粒度。
8. valueAsNumber函数
valueAsNumber函数的作用是完成控件值类型在文本和数值间的相互转换。
9. required
一旦为某输入型控件设置了required特性，那么此项必填，否则无法提交表单。

- 表单验证
就其核心而言，表单验证是一套系统，它为终端用户检测无效的控件数据并标记这些错误。换言之，表单验证就是在表单提交服务器前对其进行一系列的检查并通知用户纠正错误。

HTML5的表单验证可让用户快速获得重要反馈，但正确性方面绝对不应依赖于它。

HTML5引入了八种用于验证表单控件的数据正确性的方法。


# 09 拖放
拖放被用于文件管理，数据传输，图表绘制和其他许多操作。

# 10 Web Workers API
JavaScript是单线程的。HTML5 Web Workers可以让Web应用程序具备后台处理能力。Web Workers不能直接访问Web页面和DOM API。虽然Web Workers不会导致浏览器UI停止响应，但是仍然会消耗CPU周期，导致系统反应速度变慢。
Web Workers的使用方法非常简单，只需创建一个Web Workers对象，并传入希望执行的JavaScript文件即可。另外，在页面中设置一个事件监听器，用来监听由Web Worker发送来的消息和错误消息。如果想要在页面与Web Workers之间建立通信，数据需要通过postMessage函数传递。

# 11 Web Storage API
在Web Storage API出现之前，远程Web服务器需要存储客户端和服务器间交互使用的所有相关数据。随着Web Storage API的出现，开发者可以将需要跨请求重复访问的数据直接存储在客户端的浏览器中，还可以在关闭浏览器很久后再次打开时恢复数据，以减小网络流量。

为了解释Web Storage API，最好先回顾其前身。也就是Cookie。Cookie很神奇，它是一个在服务器和客户端之间来回传送文本值的内置机制。服务器可以基于其放在cookie中的数据在不同Web页面间追踪用户的信息。用户每次访问某个域时，cookie数据都会被来回传送。cookie有一些众所周知的缺点：
- cookie只能设置大约4KB的数据
- 只要有请求涉及cookie，cookie就要在服务器和浏览器间来回传送
Web Storage适用于存储超过cookie大小限制的文档和文件数据。

sessionstorage, localstorage
key/value 对

Web SQL Database期望将已建立的SQL语言引入浏览器，而Indexed Database旨在引入底层索引存储功能，并希望更多易于开发者使用的库能够基于索引核心被构建出来。

对比二者，Web SQL API支持使用查询语言编写SQL语句来检索数据表，索引数据库API则通过直接执行同步或异步的函数调用来检索树状的对象存储引擎。与Web SQL不同，索引数据库不会用到表和列。

# 12 构建离线Web应用
HTML5中引入了离线应用缓存，有了它Web应用程序就可以在没有网络连接的情况下运行。从缓存中加载资源可节省带宽，这对于移动Web应用是至关重要的。
缓存清单文件 中标识的资源构成了应用缓存(application cache)，它是浏览器持久性存储资源的地方。离线应用包含一个manifest文件，此文件中列出了浏览器为离线应用缓存的所有资源。
manifset文件的MIME类型是text/cache-manifest 


# 13 HTML5未来展望
- WebGL
WebGL版本的canvas上下文管理的是纹理和顶点缓冲区，而不是调用函数来绘制线条和填充形状。
现有的Web网络架构也为WebGL的开发提供了便利。WebGL应用程序可以通过URL加载纹理，模型等资源。多人游戏可以基于WebSocket进行通信。例如Google使用HTML5 WebSocket， Audio， WebGL
等技术将经典的3D游戏QuakgeII移植到了Web上，并加入了多人竞争机制。游戏逻辑和图形使用JavaScript实现，页面呈现通过调用WebGL canvas完成。游戏使用持久化的WebSocket连接来保持和服务器间的通信，从而实现对不同玩家位置的调整。

WebGL是OpenGL ES 2与JavaScript的结合。HTML5的WebGL应用程序时以哦嗯HTML搭建框架，用CSS控制样式，用JavaScript处理逻辑，用GLSL进行着色。开发人员可以借鉴在OpengGL着色器方面的开发经验，按照类似的方式使用WebGL API。

- webRTC
