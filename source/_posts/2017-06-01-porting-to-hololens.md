title: Porting UWP APP to Hololens
date: 2017-06-01
updated: 2019-02-15
categories: 
- [technology]
tags: 
- Hololens
- Unity3D
- MR
---

移植UWP应用到Hololens遇到的问题及解决方法。<!--more-->

Hololens MR开发还处于早期，持续迭代阶段，所以很多问题可能都已经解决或改变，这也就是软件开发的特点所在，应用层技术变化太快。

在Microsoft和Unity的支持下，开发MR应用还是比较容易的，尤其是使用Holotoolkit-Unity情况下，与一般的3D手游开发类似；我觉得难点在于满足目标应用场景需求的 设计 以及 图形rendering/动画的优化上。

对于Hololens/MR应用的开发，我的观点 ： MR是一种不同的重点是找到应用的场景，以及 设计 出更好的体验，在 编程 实现上，Unity和Holotoolkit提供了很多帮助。
1. 从实际的体验，商业场景，VR/MR的状况等不同角度来看，我觉得在当前时机上，Hololens(MR)在现有体验上，做DEMO还可以，实际应用则还不成熟，性价比很低(除非客户很有钱或者设备可以共享使用)。也许要到2019年的下一代Hololens，在价格大幅降低和体验提升后，或者在商业模式上找到了Kill Application后才会有更多的机会。
 
2. 从具体的Hololens应用的开发上，Microsoft和Unity已经提供了很好的支持，更多的工作应该是结合实际应用 设计 更友好的体验，构建更真实的 模型 ，在编程方面与一般的Unity应用差别不大。我觉得自己在这里面的贡献不大。
游戏，行业应用，对于 平台 厂商 而言，当然可以持续的研发，但是对于 应用开发者而言，没有很长久的持续性，做做项目可以。对于其他的行业而言，这些只是 锦上添花 的工具而已。


将已有的应用移植到Hololens，分两种情况：
1. 一种是一般的UWP 2D应用移植到Hololens上，参见 https://developer.microsoft.com/en-us/windows/mixed-reality/building_2d_apps
主要需要注意的是UI和Input方式的处理，虽然Windows takes care of all of this complexity for UWP apps, translating your gaze, gestures, voice and motion controller input to pointer events that abstract away the input mechanism. 
但如果想要更友好自然的交互，还是需要使用Holotoolkit来增强用户体验，比如Cursor，Voice Input

一般的2D 应用部署到Hololens上会被装饰一个Appbar，根据情况会有Back Button, Title, Scroll Tool, Drag Tool, Zoom Tool, Adjust, Remove等条目，参见 https://developer.microsoft.com/en-us/windows/mixed-reality/updating_your_existing_universal_app_for_hololens

2. 第二种是一般的Unity 3D应用移植到Hololens，参见 https://developer.microsoft.com/en-us/windows/mixed-reality/porting_guides
为其他平台(Android，iOS)开发的Unity应用，要porting到UWP平台，参考https://unity3d.com/partners/microsoft/porting-guides

需要注意的是在Unity3D的Hololens Build选项中XAML和D3D的差别是The HoloLens system keyboard is only available to Unity applications that are exported with the "UWP Build Type" set to "XAML". There are tradeoffs you make when you choose "XAML" as the "UWP Build Type" over "D3D". 具体参见https://developer.microsoft.com/en-us/windows/mixed-reality/keyboard_input_in_unity

移植主要包括如下几个方面：UI适配，保证可以在Hololens中可以正确的显示GUI；第三库的移植，保证业务正常；交互输入，保证用户体验，应用Hololens的特性。

# UI适配
对于有Canvas的Unity UI项目，参见: https://forum.unity3d.com/threads/unity-ui-on-the-hololens.394629/，主要是：
- Select EventSystem object, add "Hololens Input Module" component
- Select Canvas object, Change "Render Mode" to "World Space", Drag MainCamera object to "Event Camera"
- Set MainCamera's position to origin
- 建议Canvas的W/H是100 x 100，Scale是1/16或者1/32

# 第三方库的兼容性
在移植到UWP时，当涉及第三方库时，有两种方案：
- 一种是使用IL2CPP做script backend，也就是将Player Settings -> Scripting Backend设置为IL2CPP，那么最后部署到Hololens的.NET 环境与Unity Editor是一样的，使用.NET Framework 3.5，这样第三方的DLL就不需要做UWP的适配。 通过mono.net CLR来达到跨平台的目的，而不是使用目标平台的Native .NET API
- 另外一种是使用.NET做script backend，那么这些DLL就需要做相应的修改以适配UWP

通过设置Play Settings -> Other Settings -> Scripting Backend -> IL2CPP/.NET，即可在两种方式中切换。

使用两种script backend，最终部署的文件相差很大，.NET backend会将.Net Core dlls(很多独立的DLL)，IL2CPP使用mscorlib.dll(.NET Framework 3.5)，经过实践，最终选择使用 .NET Backend，具体对2种方案详细说明：

## IL2CPP backend
只要第三方DLL在Unity Editor能编译通过，那跨平台就没有问题。而不像.NET Backend，需要第三方DLL也要对相应的移植，从实践来看，工作量小很多。这也是为什么Unity想要用IL2CPP 替代Mono CLR的原因之一。
但需要注意的是，For Hololens的库，比如HoloToolkit又不一样，它主要是用.NET Core API，比如System.Threading.Tasks，System.Reflection.TypeInfo等类，所以反而使用IL2CPP编译的时候遇到问题。

比如编译HoloToolkit 1.6.8的时候遇到很多问题，将Api Compatibility Level 改为.NET 4.6，错误减少很多，只剩下：
Assets\HoloToolkit\SpatialMapping\Scripts\RemoteMapping\MeshSaver.cs(162,53): error CS1061: 'StorageFile' does not contain a definition for 'OpenStreamForReadAsync' and no extension method 'OpenStreamForReadAsync' accepting a first argument of type 'StorageFile' could be found (are you missing a using directive or an assembly reference?)
该问题现在没有解决方法，参见 : https://github.com/Microsoft/MixedRealityToolkit-Unity/issues/265
考虑到此种方法还有问题要解决，同时无法直接使用.CS 脚本调试，且编译时间较长的缺点，放弃此种方案。

## .NET backend
先解决一些通用的问题，然后再针对具体的第三方库总结遇到的问题及解决方法。先理解一些.NET相关术语和概念, 详细参考 https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/

.NET Framwork 2.0 3.5 4.5  .NET Framework的一个特点是很多类都放在mscorlib.dll，而.NET Core则分散在各个Dll
.Net Core是.Net Framework的新一代版本，开源并跨OS(Windows, MacOS, Linux)，不完全兼容.Net Framework(不包含WPF, WINForm等GUI部分)，UWP基于此框架库构建。https://github.com/dotnet/corefx
.Net Standard 是一套API规范，目前的各种实现(.net famework，Xamarin，Mono，.net Core),  https://github.com/dotnet/standard

.NET Framwork 4.6实现.NET Standard 1.3，而.NET Core 1.0框架实现1.6, UWP 10.0 实现.NET Standard 1.4 ，在未来都支持Standard 2.0来统一Standard Library

Unity 5.6使用的.NET Framework 3.5，而Hololens使用的UWP是.Net Core，未来可能会统一。

1. 一些语法问题(StreamReader, Thread)：
出现编译问题主要是因为：In the Unity IDE, scripts using .NET are referencing .NET version 3.5. When your game is exported to Visual Studio, however, all your C# code is compiled against .NET Core, which is a subset of .NET version 4.5. ( Note: If you use IL2CPP as the scripting backend, however, your Windows Store app will continue to use .NET 3.5.) 
The .NET scripting backend that is used on Universal Windows Apps is a special .NET version for this platform, which is not entirely compatible with Mono. In particular some data types are missing and some other classes don’t have certain methods, that the same classes do have in Mono.

To make porting existing games to Universal Windows Platform easier, some of the missing .NET types are provided by Unity. In addition some extension methods and replacement types were added to make migration easier. These types are placed in Editor\Data\PlaybackEngines\MetroSupport\Managed\UAP\WinRTLegacy.dll.

WinRTLegacy可以修补部分.net core缺乏的方法，成员，这时候sealed关键字的作用就体现出来了，可以跨DLL，跨文件，增加一个类的成员和方法，这个可以用来做热更新？ 

System.Threading.Thread类则只支持Desktop开发，在UWP中已经没有这个类了。https://github.com/dotnet/corefx/issues/2576
要使用System.Threading.Tasks.Task类代替，使用NETFX_CORE区分

所以出现script编译的问题之后，使用宏来隔离代码，同时引用WinRTLegacy来补缺少的类， 方法等，更具体参考https://docs.unity3d.com/Manual/windowsstore-missingtypes.html

2. link问题
在解决语法问题，编译通过后，会遇到link的问题，主要是第三方插件NDatabase, Zxing，LitJson，SharpZipLib没有提供相应平台的DLL导致(Reference rewriter : Error : type 'xxx' doesn't exist in target framework. It is referenced from xxx)

解决方案是：像Vuforia那样，基于同一份代码根据不同的平台(Android, iOS, Windows, UWP)，build出不同的Dll供应用程序调用。

因为对于要支持UWP的DLL，无法只是用一个DLL就兼容Unity Editor和UWP平台，因为Unity Editor是用.NET Framework 3.5，而UWP是用.NET CORE 1.3 +，这个问题可能要到统一都使用.NET Core 2.0之后得到解决。

**通过在dll的Inspector中将Platform Setting中选择"Don't process"，可以规避Link错误，但问题并没有解决，只是延迟到Runtime时变成Exception，程序跑起来问题就暴露出来，还是需要修改源代码用 宏 来做适配。**

开发Hololens应用，比较耗时的地方时编辑使用Unity，构建(Build)/调试(Debug)/部署(Depoly)使用Visual Studio，需要在两者间不断的切换。具体 参见 https://developer.microsoft.com/en-us/windows/mixed-reality/exporting_and_building_a_unity_visual_studio_solution
有个技巧是：Export from Unity only when the scene is changed in the Unity Editor; changing the contents of scripts can be done in Visual Studio without re-exporting.

Unity的Debug.Log()在使用VS调试时，信息将显示在VS的Output窗口，如果想将Log显示在Hololens中，参考： https://forums.hololens.com/discussion/708/how-can-i-see-the-unity-debug-log-output-from-a-running-app-on-the-device

有时 Using the Windows Device Portal
https://developer.microsoft.com/en-us/windows/mixed-reality/using_the_windows_device_portal

## 3rd libs
项目中使用了Vuforia, Zxing.net, LitJson, NDatabase, SharpZiplib, HoloTookit-Unity等第三方库，对于Litjson, NDatabase, SharpZiplib这样已经没有维护的类库，要移植到UWP，一种是自己改写For UWP的版本，如同Vuforia所做的那样，将不同平台的Dll导入Unity，然后在Inspector中进行平台设置；还有一种方法是寻找已经支持UWP的可以替代的库。

主要解决方法是通过 宏定义 区分代码，主要的平台相关的宏参见：https://docs.unity3d.com/Manual/PlatformDependentCompilation.html
也就是第三方的DLL需要特别for Unity，For .Net Core API/.Net backend(NETFX_CORE)， for UWP(UNITY_WSA)

### Vuforia
参考 https://developer.microsoft.com/en-us/windows/mixed-reality/vuforia_development_overview
Vuforia提供了物体识别能力，可以将现实世界的物体与虚拟世界的数字体验关联起来。

Vuforia也提供了一个for Hololens的例子，参见 : https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity

在使用Vuforia的过程中，出现如下问题以及对应的解决方法。

1. 配置Vuforia的时候，出现：
XmlException: invalid data.
System.Xml.XmlStreamReader.Read(System.Char[] dest_buffer, Int32 index, Int32 count)
Mono.Xml2.XmlTextReader.ReadTextReader (Int32 remained)
Mono.Xml2.XmlTextReader.PeekChar()
Mono.Xml2.XmlTextReader.ReadContent()
Mono.Xml2.XmlTextReader.Read()
System.Xml.XmlTextReader.Read()
Vuforia.EditorClasses.ConfigParser.fileToStruct (System.String configXMLPath, System.String authoringInfoXMLPath, Vuforia.EditorClasses.ConfigData configData)
Vuforia.EditorClasses.ConfigDataManager.ReadConfigData (System.String dataSetFilePath)
Vuforia.EditorClasses.ConfigDataManager.DoRead()
Vuforia.EditorClasses.SceneManager.InitScene()
Vuforia.EditorClasses.DatabaseLoadEditor.FindSerializedProperties(UnityEditor.SerializedObject serializedObject)
Vuforia.EditorClasses.VuforiaAbstractConfigurationEditor.OnEnable()

找了2天，结果发现是因为Assets\StreamingAssets\Vuforia目录下除了xx.dat和xx.xml，还多了.xx.xml和.xx.dat文件，删除这两个文件即解决此问题。 深层原因尚不知。

2. 将项目另存之后，出现
NullReferenceException: Object reference not set to an instance of an object
Vuforia.VuforiaAbstractConfiguration.CreateInstance ()
Vuforia.EditorClasses.VuforiaAbstractConfigurationEditor.LoadConfigurationObject ()
Vuforia.EditorClasses.DatabaseLoadEditor.OnConfigDataChanged ()
Vuforia.EditorClasses.SceneManager.EditorUpdate ()
UnityEditor.EditorApplication.Internal_CallUpdateFunctions () (at C:/buildslave/unity/build/artifacts/generated/common/editor/EditorApplicationBindings.gen.cs:249)

点击 Vuforia -> Configuration 没有反应，解决方法是将 Assets目录下的Vuforia删除，重新导入vuforia-unity-6-2-10.unitypackage

3. Vuforia initialization failed, 在Vuforia Configuration Inspector 中的App Licence Key不正确

4. 通过Vuforia OnTrackablesUpdated 来定时抓Camera 图片分析 QRCode，使用单线程/定时器 机制即可

5. 其他Vuforia相关的问题
遇到莫名其妙的Unity Build问题时，删除Assets下的Vuforia目录，重新导入vuforia-unity-6-2-10.unitypackage


### ZXing.net
Zxing.Net，https://github.com/micjahn/ZXing.Net 已经支持UWP，所以只需将对应的DLL放在Plugins目录，然后在Inspector中设置即可。
在项目中，需要基于Camera扫描二维码，也就是获取一帧当前Camera的图像，然后使用ZXing做解码，在Hololens中有几种做法：

1. 使用UnityEngine.VR.WSA.WebCam 参考https://forums.hololens.com/discussion/1482/barcode-qr-code-detection

2. 使用Windows.Media.MediaCaputre 参考https://mtaulty.com/2016/12/28/windows-10-uwp-qr-code-scanning-with-zxing-and-hololens/

3. 利用Vuforia的OnTrackablesUpdated回调获取一帧Camera图像，然后使用Zxing解码；遇到的问题是:
Exception thrown: 'System.IO.FileLoadException' in Assembly-CSharp.dll
Exception thrown: 'System.Reflection.TargetInvocationException' in System.Private.CoreLib.ni.dll
Exception in callback: System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.IO.FileLoadException: Could not load file or assembly 'System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)
   at ZXing.BarcodeReader..ctor()
   at CodeDecode.DecodeImg(HandleDecodeResult handle, Image i)
   at CameraAccess.GetCameraImg()
   at CameraAccess.OnTrackablesUpdated()
   --- End of inner exception stack trace ---
   at System.RuntimeMethodHandle.InvokeMethod(Object target, Object[] arguments, Signature sig, Boolean constructor)
   at System.Reflection.RuntimeMethodInfo.UnsafeInvokeInternal(Object obj, Object[] parameters, Object[] arguments)
   at System.Delegate.DynamicInvokeImpl(Object[] args)
   at Vuforia.DelegateHelper.InvokeDelegate(Delegate action, Object[] args)

参考 https://forums.hololens.com/discussion/3263/zxing-unity-barcode-dll-issue的做法将zxing.unity.dll拷贝一份放在另一个文件夹WSAPlayer分别设置不同的Platform Settings，出现的问题依然一样。

解决方法：针对Hololens使用Zxing.net for UWP的Zxing.dll即可。ZXing.net既提供了For Unity的zxing.unity.dll也提供了for UWP的zxing.dll，一种方法是针对不同的平台使用不同的dll，代码上就需要使用宏做一个区分，因为for Unity的版本提供了的BarcodeReader是针对Unity的BarcodeReaderGeneric<Color32[]>.Decode版本，其他平台没有Color32类型，如果想使用Color32类型则需要用宏来区分，使用BarcodeReader.Decode(byte[], width, height, bitmapformat)

### Json
项目中使用的是Litjson，https://github.com/lbv/litjson，该代码库2014年之后就不更新，为避免修改Unity的代码，决定先尝试将Litjson 移植到UWP 平台。如果不做移植，可以选择其他的解决方法：
1. 使用Unity自带JsonUtility用于JSON的解析，抛开特定的功能需求，这是最简单快速的方案
2. 使用Json.net https://github.com/JamesNK/Newtonsoft.Json 对应的Unity 3D版本 https://github.com/SaladLab/Json.Net.Unity3D

如果直接使用项目中的LitJson.dll，在Unity for Hololens build时会出现如下问题：
Error: type `System.Collections.Specialized.IOrderedDictionary` doesn't exist in target framework. It is referenced from LitJson.dll at LitJson.IJsonWrapper.
Error: type `System.Collections.Specialized.IOrderedDictionary` doesn't exist in target framework. It is referenced from LitJson.dll at LitJson.JsonMockWrapper.
Error: type `System.Collections.Specialized.IOrderedDictionary` doesn't exist in target framework. It is referenced from LitJson.dll at System.Object

如果在LitJson.dll的Inspector对应的UWP中选择"Don't Process"，build不会有问题，但是runtime则会抛出异常：
Exception thrown: 'System.TypeLoadException' in Assembly-CSharp.dll
TypeLoadException: Could not load type 'System.Collections.Specialized.IOrderedDictionary' from assembly 'System, Version=2.0.5.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e, Retargetable=Yes'.

解决方法 : 基于现有LitJson代码，移植到UWP平台：
在VS2017中建立一个新的UWP Class Library项目，将LitJson代码导入，编译，遇到的几个问题：

1. 一个是System.Type的IsClass IsEnum 属性都不见了，转移到了System.Reflection.TypeInfo， 用Type调用的方法改为使用type.GetTypeInfo().调用，参考 https://blogs.msdn.microsoft.com/dotnet/2012/08/28/evolving-the-reflection-api/

2. 另一个是GetInterface也不见，使用typeof(IMyInterface).IsAssignableFrom(typeof(MyType))代替，参考 https://stackoverflow.com/questions/4963160/how-to-determine-if-a-type-implements-an-interface-with-c-sharp-reflection

将编译好的DLL放到Unity的Assets/Plugins/目录，遇到如下问题：
error CS1705: Assembly 'LitJsonUWP' with identity 'LitJsonUWP, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null' uses 'System.Collections.Specialized, Version=4.0.1.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' which has a higher version than referenced assembly 'System.Collections.Specialized' with identity 'System.Collections.Specialized, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'

也就是VS2017编译LitJson引用的System.Collections.Specialized版本比Unity使用的版本要高，通过验证发现将VS中NuGet Package Manager的"Allow NuGet to download missing package"取消，然后点击 Clear All NuGet Cache，C:\Users\xxx\.nuget\packages\的内容会被清空，重新Build Unity Hololens项目，Unity将使用NuGet重新下载相应的dll，比如下载的Microsoft.CSharp的目录是4.0.0，而VS2017需要的的是4.0.1

解决方法：参考https://forum.unity3d.com/threads/suggestion-choose-microsoft-netcore-universalwindowsplatform-version-when-building.469922/ 得知：

VS2017默认的项目引用的“Microsoft.NETCore.UniversalWindowsPlatform”版本是5.2.3，而Unity 5.6.2默认引用的版本是5.0.0，参见Unity\Editor\Data\PlaybackEngines\MetroSupport\Tools\project.json文件。

考虑到最新的版本有更多的功能，尤其是向.NET Core/Standard 2.0靠近，这样功能日趋成熟和完善，减少不必要的工作；5.2.3与5.0.0相差较大，一些三方库，比如Sharpzip，LitDB都依赖System.Security.Cryptography.Primitives.dll，但是5.0.0没有该DLL。因此将Unity引用的Microsoft.NETCore.UniversalWindowsPlatform的版本改为与VS2017保持一致，也就是使用5.2.3：

修改Unity\Editor\Data\PlaybackEngines\MetroSupport\Tools\project.json及Unity\Editor\Data\PlaybackEngines\MetroSupport\Templates\UAP\CSharp\project.json

"dependencies": {
    "Microsoft.NETCore.UniversalWindowsPlatform": "5.2.3"
},

同时所有的第三方库使用5.2.3版本编译，然后一个一个的替换，测试，验证即可。


在这个过程中遇到如下问题：
1>------ Build started: Project: Assembly-CSharp-firstpass, Configuration: Release x86 ------
1>  Running SerializationWeaver...
1>  System.Collections.Generic.KeyNotFoundException: 给定关键字不在字典中。
1>     在 System.Collections.Generic.Dictionary`2.get_Item(TKey key)
1>     在 UnityEditor.Scripting.Compilers.NuGetPackageResolver.Resolve()
1>     在 Unity.NuGetAssemblyResolver..ctor(String projectLockFile)
1>     在 usw.Weaver.ReaderParameters(String assemblyPath, ConversionOptions options)
1>     在 usw.Weaver.Weave()
1>     在 usw.Program.RunProgram(ConversionOptions options)
1>     在 usw.Program.Main(String[] args)

原因是升级到VS2017 15.3之后Unity 5.6出现了不兼容的问题，参见https://forum.unity3d.com/threads/net-scripting-backend-and-visual-studio-2017-3-incompatibility.487833/
要么重装VS2017 15.2要么使用Unity 2017.2.0b7，考虑到Unity2017的稳定性，还是只能重装VS 2017 15.2版本。所以目前的版本最好保持VS2017 15.2，Unity 5.6.2，先不要升级等稳定后再升级。
**2017.9.2 有了Unity5.6.3p2的补丁**

如果遇到如下问题：
PlayerInitEngineNoGraphics settings: Failed to load PlayerSettings (internal index #0).
Most likely data file is corrupted, or built with mismatching
editor and platform support versions.

metro::Initialize() failed

解决方法：重新用Unity build出VS Solution，因为要保证Unity使用的VS版本和deploy使用的VS版本要一致。

### ORM/NoSQL
对于数据存储的方案，一种是基于SQLite，并提供ORM库；还有一种是直接使用NoSQL库。

如果是选择ORM库，可以选择：
1. Entity Framework，https://docs.microsoft.com/en-us/ef/
Entity Framework (EF) is an object-relational mapper(ORM)that enables .NET developers to work with relational data using domain-specific objects.
EntityFrameworkCore要求UniversalWindowsPlatform的版本在5.2.2

2. sqlite-net，https://github.com/praeclarum/sqlite-net
轻量的SQlite的ORM库(源代码只有一个SQLite.cs文件)，支持UWP
https://github.com/codecoding/SQLite4Unity3d在此库基础上提供了Unity Plugin

3. Dapper，https://github.com/StackExchange/Dapper
目前还不支持UWP，参见https://github.com/StackExchange/Dapper/issues/673

但在项目中使用的是NDatabase, https://ndatabase.codeplex.com/, 是一个NoSQL数据库。其最新版本是3.8.0，2013.5.12发布，只支持.NET 3.5, 4.0, 4.5。经过实践，移植到UWP时问题很多，要移植就要完全理解System.Reflection的机制，要花较长时间，不值得，所以决定使用 LiteDB，https://github.com/mbdavid/LiteDB 替代

使用LiteDB过程中遇到如下问题：
Exception thrown: 'LiteDB.LiteException' in LiteDBUWP.dll
Exception thrown: 'LiteDB.LiteException' in LiteDBUWP.dll
LiteException: Invalid BSON data type 'Null' on field '_id'.
   at LiteDB.LiteEngine.InsertDocument(CollectionPage col, BsonDocument doc, BsonType autoId)
   at LiteDB.LiteEngine.<>c__DisplayClass20_0.<Insert>b__0(CollectionPage col)
   at LiteDB.LiteEngine.Transaction[T](String collection, Boolean addIfNotExists, Func`2 action)
   at LiteDB.LiteEngine.Insert(String collection, IEnumerable`1 docs, BsonType autoId)
   at LiteDB.LiteCollection`1.Insert(T document)

解决方法：在目标Document里加入 public int Id { get; set; }，具体参考https://stackoverflow.com/questions/38341076/litedb-invalid-bson-data-type-null-on-field-id

### zip
项目使用的是SharpZipLib，https://github.com/icsharpcode/SharpZipLib，最新的代码支持.NET Standard 1.3/2.0，但还未Release。
在项目中主要的目的是解压zip文件到目录，因此决定使用.net core提供的System.IO.Compression.ZipFile替代。

如果遇到问题：
Exception thrown: 'System.Exception' in Assembly-CSharp.dll
Exception: Unsupported protocol
   at XmlLoader.<LoadMaintenanceData>d__0.MoveNext()
   at UnityEngine.SetupCoroutine.InvokeMoveNext(IEnumerator enumerator, IntPtr returnValueAddress)
   at UnityEngine.SetupCoroutine.$Invoke1(Int64 instance, Int64* args)
   at UnityEngine.Internal.$MethodUtility.InvokeMethod(Int64 instance, Int64* args, IntPtr method) 
(Filename: <Unknown> Line: 0)

解决方案：这个异常是www抛出的，是因为没有使用在C:/Data/路径前面加file://前缀导致。

工具选择：
在目前状况下，因为Hololens，UWP等都属于比较前沿的技术，并没有稳定，为避免一些工具版本差异导致的不稳定性，出现不可预料的问题，建议：
Unity的版本：5.6.2，VS的版本 ： VS2017 15.2，Holotoolkit-Unity的版本 ： 1.5.8，Unity script backend ： 选择.NET而不是IL2CPP

Unity和VS2017项目设置 :
"Microsoft.NETCore.UniversalWindowsPlatform": "5.2.3"
<TargetPlatformVersion>10.0.15063.0</TargetPlatformVersion>

# 交互，Hololens特性
将一般的Unity 3D应用移植到Hololens上时，根据具体的应用场景及业务需要，可以发挥Hololens独特的特性：GGV, Sptaial Sound， Spatial Mapping， Spatial Understanding，Hologram Sharing
这些功能在Holotoolkit-Unity(最近改名MixedRealityToolkit-Unity)，https://github.com/Microsoft/MixedRealityToolkit-Unity 里都提供了易用的支持。 
除此外，还可以参考 https://github.com/Microsoft/MRDesignLabs，探索MR的设计，UI，交互。

从这次移植经验看，在所有的场景中加入 HoloToolkit 的InputManager，InteractiveMeshCursor prefab，这样才能看到Cursor，并能处理Gesure动作。没有Cursor指示，很难做精细的操作；根据需要使用Tag-Along， billboarding，这些Unity Component很通用，易用

# 寻找解决方法
如之前所说，Hololens/MR的开发还处于比较前沿阶段，并不成熟，所以遇到的问题一般并没有直接的答案，需要自己去探索，尝试。重点搜索/问询如下两个论坛：
https://forums.hololens.com/
https://forum.unity3d.com/forums/hololens.102/



