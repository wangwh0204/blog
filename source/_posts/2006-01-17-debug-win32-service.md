title: 调试Win32 Service
date: 2006-01-17
updated: 2015-12-10
categories: technology
tags: 
- Win32
---

关于如何对win32 service程序进行调试的总结。<!--more-->

# 合适的读者:
本文章主要针对对Win32 Service有所了解和熟悉的程序员.

# 目的:
写这篇文章的目的是实践和总结，巩固Service相关的知识。同时为我们项目中B(WEB)/S(Service)的Service端调试寻找一种简单，方便的调试手段。

# 正文:
半年前就已经抱着[Richter2000]及MSDN看有关Service相关的文章,总体有个了解,但因为缺乏实际项目锻炼的原因(懒惰的借口:))并没有实际的动手去编写和调试一个Service程序.近来因为要协助解决一个系统的Memory Leak,该系统是Component & Service的exe程序,才用心的去看相关的知识。当时同事说Service不能在运行时调试，我也相信了，后来自己调试的时候感觉很麻烦，总是使用第5招，麻烦死了。然后就去找[Richter2000]看，自己也实际动手试验了各种方法。

对于要编写Service的同志，建议使用ATL Wizard生成的Service Framework，然后再根据自己的需要进行适当的修改。当然Service的实际运行原理也最好要了解一些。主要是四个函数StartServiceCtrlDispatcher, ServiceMain(或其他名字),RegisterServiceCtrlHandlerEx，Handler(或其他名字)，具体的详细信息请参看[Ricthter2000] Chapter 3.

## 为什么调试Win32 Service比普通Win32程序要麻烦?
Win32 Service程序相对普通程序而言，增加一种机制，可以由SCM来统一管理。Win32 Service有以下几个特点：
1. 可以随系统一起自动启动，而不管是否有用户登陆到系统；
2. 不提供UI交互；
调试Sevice程序比普通WIN32程序麻烦的根本原因在于Service只能依赖SCM来启动，而不能由Debugger来启动。具体的可以看[Richter2000]Chap3关于Service Application Architecture。

调试方法:
下面的调试方法主要参考[Ritchter2000] chap3，加上我自己的一些实践心得。
- 将Service变成普通的WIN32程序
具体的做法是去掉调用StartServiceCtrlDispatcher函数的代码。在ATL Framework的代码中可以直接的按F5调试Initialization Code,等到进入消息循环之后在欲调试的代码行设置断点，等待外部Client请求即可。其原理是因为该Framework 自动做了处理，如果进程作为Service启动失败时，会被自动当作WIN32程序来执行。大部分Service Start失败的情况都是因为Initialization Code出错导致的，这时可以通过此方法来调试。
这是通常的做法，该方法的缺点是：
1).这样启动的进程不是实际的Service，不能接受SCM的管理，因此也不能接受SCP发送的Notification消息,也就是说在处理Notification出错时这种方法不可行。
2). 有可能需要编写额外的Client测试代码。以我们的系统为例子，使用WEB/SERVICE为架构，WEB能访问SERVICE的前提条件是Service必须启动,因此这种方法对我们的调试是无效的，我们的做法是用VB写一个测试程序来调用Service的接口来调试。可以想象，测试程序不可能完全模拟真实的系统，因此我们需要更好的调试方法。

以下三种方法都是通过激活JIT Debugger来调试Service代码，如果系统中有多个Debugger，可以在注册表里/HKEY_LOCAL_MACHINE/SOFTWARE/Microsoft/Windows NT/CurrentVersion/ AeDebug的Debugger 键值里设置想要的Debugger。

- 通过在Main/WinMain函数中使用DebugBreak函数，在Service Snap-in 里Start Service时会激活Jit Debugger，这时通常会弹出一个异常对话框，选择Debug即可。使用此种方法可以启动Service，调试其Entry Point函数及对SCP的Notification的处理代码，也可以调试实际的功能代码(将欲调试代码的.CPP文件拖到Debugger IDE里，在需要调试的代码行设置断点即可)，这种方法适用的范围最广，推荐使用。

- 当Service启动之后，可以在任务管理器里找到对应的进程，然后点击右键, 选择Debug ,会启动预先设置的Debugger。然后打开代码文件，设置断点即可。缺点是不能调试Initialization Code.

- 通过启动进程时启动JIT Debugger
具体做法是在注册表里HKEY_LOCAL_MACHINE/SOFTWARE/Microsoft/Windows NT/CurrentVersion/Image File Execution Options下建立子键，子键名为要调试的Service对应的进程名(不包括路径，但需要后缀名.exe)，在该子键下创建字符值为Debugger的键值，设置该值为指定的JIT  Dubugger的完整路径。设置完成后，Start Service，按F5进入调试即可。
注：此种方法在我自己的机子VC6上可以，在公司的机子VC6(＋SP6)不行，原因不明。

- 打log，对于输出信息很频繁及随机出现BUG的情况，最好通过在出错点的上下文输出运行时信息来观察判断导致BUG的根源。

使用ATL生成的Win32 Service,如果是使用WIN32 Release Min Size 编译选项，可能导致注册时失败，改为WIN32 Release Min Dependency编译选项即可解决。


# 参考资料:
1. [Richter2000]“Programming Server-Side Applications for Microsoft windows 2000” by Jeffrey Richter & Jason D.Clark
2. http://msdn.microsoft.com/library/default.asp?url=/library/en-us/dndllpro/html/msdn_ntservic.asp

