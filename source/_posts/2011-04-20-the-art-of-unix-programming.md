title: The Art of UNIX Programming
date: 2011-04-20
updated: 2011-04-20
categories: 
- [reading]
- [technology]
tags: 
- OS
- UNIX
---

&lt;&lt;The Art of UNIX Programming&gt;&gt;的中文版&lt;&lt;UNIX编程艺术&gt;&gt;读书笔记。<!--more-->

# 01 哲学 Philosopy

Unix哲学是自下向上的，而不是自上而下的。Unix哲学注重实效，立足于丰富的经验。它鼓励那种分清轻重缓急的感觉，以及怀疑一切的态度，并鼓励你以幽默达观的态度对待这些。

Unix哲学是这样的：一个程序只做一件事，并做好。

Rob Pike在&lt;&lt;Notes on C Programming&gt;&gt;中从不同角度表述了Unix的哲学:
1. 你无法断定程序会在什么地方消耗运行时间。瓶颈经常出现在想不到的地方，所以别急于胡乱找个地方改代码，除非你已经证实那儿就是瓶颈所在。
2. 估量。在你没对代码进行估量，特别是没找到最耗时的那部分之前，别去优化速度。
3. 花哨的算法再n很小时通常很慢，而n通常很小。花哨算法的常熟复杂度很大。除非你确定n总是很大，否则不要使用花哨算法(即使n很大，也优先考虑原则2)
4. 花哨的算法比简单算法更容易出BUG，更难实现。尽量使用简单的算法配合简单的数据结构。(拿不准就穷举)
5. 数据压倒一起。如果已经选择了正确的数据结构并且把一切都组织的井井有条，正确的算法也就不言自明。编程的核心是数据结构，而不是算法。

Unix哲学：
- 模块原则：使用简洁的接口拼合简单的部件
- 清晰原则：清晰胜于技巧
- 组合原则：设计时考虑拼接组合
在输入输出方面，Unix传统极力提倡采用简单，文本化，面向流，设备无关的格式。
- 分离原则：策略同机制分离，接口同引擎分离
- 简洁原则：设计要简洁，复杂度能低则低
- 吝啬原则：除非确无它法，不要编写庞大的程序。
- 透明性原则： 设计要可见，以便审查和调试

- 健壮原则：健壮源于透明和简洁
- 表示原则：把知识叠入数据以求逻辑质朴而健壮
- 通俗原则：接口设计避免标新立异
- 缄默原则：如果一个程序没什么好说的，就沉默。
- 补救原则：出现异常时，马上退出并给出足够错误信息。
软件要尽可能从容地应付各种错误输入和自身的运行错误。但是，如果做不到这一点，就让程序尽可能以一种容易诊断错误的方式终止。
- 经济原则，宁花机器一分，不花程序员一秒
- 生成原则：避免手工hack，尽量编写程序去生成程序。
- 优化原则：雕琢前先要有原型，跑之前先学会走
还不知道瓶颈所在就匆忙进行优化，这可能是唯一一个比乱加功能更损害设计的错误。
先制作原型，再精雕细琢。优化之前先确保能用。
Kent Beck : Make it work, Make it right, make it fast
- 多样原则：决不相信所谓“不二法门”的断言
- 扩展原则：设计着眼未来，未来总比预想来的快

所有的Unix哲学浓缩为一条铁律，那就是各地编程大师们分为圭臬的：Keep It Simple, Stupid(KISS)

只要可行，一切都应该做成与来源和目标无关的过滤器
数据流应尽可能文本化(这样可以使用标准工具来查看和过滤)
数据库部署和应用协议尽可能文本化(让人可以阅读和编辑)
复杂的前端(用户界面)和后端应该泾渭分明。
如果可能，用C编写前，先用解释性语言搭建原型。
当且仅当只用一门语言编程会提高程序复杂度时，混用语言编程才比单一语言编程来的好。
宽收严发。
小就是美。在确保完成任务的基础上，程序功能尽可能少。

要良好的运用Unix哲学，你就应该不断追求卓越。你必须相信，软件设计是一门技艺，值得你付出所有的智慧，创造力和激情。注意重用，善用工具，尽可能将一切都自动化。

Unix有几个统一性的理念或象征，并塑造了它的API及由此形成的开发风格。其中最重要的一点应当是“一切皆文件”模型及在此基础上建立的管道概念。

# 04 模块性
There are two ways of constructing a software design. One is to make it so simple that there are obviously no deficiencies; the other is to make it so complicated that there are no obvious deficiencies. The first method is far more difficult.

模块化代码的首要特质就是封装。封装良好的模块不会过多向外部披露自身的细节，不会直接调用其他模块的实现码，也不会胡乱共享全局数据。模块之间通过应用程序编程接口(API)--一组严密，定义良好的程序调用和数据结构来通信。这就是模块化原则的内容。

紧凑性 及 正交性
The Magical Number Seven, Plus or Minus Two : Some Limits on Our Capacity for Processing Information 是认知心理学的基础性文章之一。这篇文章表明，人类短期记忆能够容纳的不连续信息数是七，加二或减二。这给我们一个评测API紧凑性的很好的经验法则：编程者需要记忆的条目数大于七吗？如果大于七，则这个API不太可能算是严格紧凑的。

正交性是有助于使复杂设计也能紧凑的最重要特性之一。在纯粹的正交设计中，任何操作均无副作用。每一个动作只改变一件事，不会影响其它。无论你控制的是什么系统，改变每个属性的方法有且只有一个。

4.2.3 SPOT原则
The Pragmatic Programmer针对一类特别重要的正交性明确提出了一条原则 --- Don't Repeat Yourself，意思是说：任何一个知识点在系统内部都应当有一个唯一，明确，权威的表述。Single Point of Truth

重复会导致前后矛盾，产生隐微问题的代码，原因是当你修改重复点时，往往只改变了一部分而并非全部。通常，这也意味着你对代码的组织没有想清楚。

完美之道，不在无可增加，而在无可删减。

# 05 Textuality: Good protocols Make Good Practice
互用性，透明性，可扩展性和存储/事务处理的经济性--这些都是设计文件格式和应用协议时需要考虑的重要方面。互用性和透明性要求我们在此类设计中要重点考虑数据表达的清晰问题，而不是首先考虑实现的方便性和可能达到的最高性能。既然二进制协议很难扩展和干净地抽取子集，可扩展性当然青睐文本化协议。事务处理的经济性则会提出相反的要求--但我们应看到，首先考虑这个标准就是一种过早优化，不这么做往往是明智选择。

使用二进制协议的唯一正当理由是：如果要处理大批量的数据集，因而确实关注能否在介质上获得最大位密度，或是非常关心将数据转化为芯片核心结构所必须的时间或指令开销。 大图像和多媒体数据的格式有时可以算是前者的例子，对延时有严格要求的网络协议有时则可以算是后者的例子。

PNG格式是二进制文件格式中一个经过周密设计的优秀例子。PNG标准精确全面，编写得非常好，可以作为如何撰写文件格式标准的范例来使用。

Marshall Rose的RFC 3117 (On the Design of Application Procotol)很好概况了互联网应用协议设计中的种种问题。

# 06 Transparency: Let There Be Light
Beauty is more important in computing than anywhere else in technology because software is so complicated. Beauty is the ultimate defense against complexity.
Machine Beauty : Elegance and the Heart of Technology 1998
  --- David Gelernter

# 07 Multiprogramming: Separating Process to separate Function
Unix最具特点的程序模块化技法就是将大型程序分解成多个协作进程。

总的来说，线程不是降低而是提高了全局复杂度，因此，除非万不得已，尽量避免使用线程。

另一个把程序划分成多个协作进程的重要原因是为了更强的安全性。

Unix IPC方法的分类
廉价的进程生成使得程序间的协作变为可能，其中最简单的形式就是一个程序调用另一个程序来完成专门任务。

继Ken Thompson和Dennis Ritchie之后，对早期Unix影响最重要的人大概非Doug McIIroy莫属。他发明的 *管道* 结构始终闪现在Unix设计中，促进了"做单件事并做好"哲学的萌发，并且引发了Unix设计中绝大多数后续IPC方法的诞生(尤其是用于网络的socket抽象概念)。

Andrew S.Tanenbaum 和 Robbert van Renesse在&lt;&lt;A Critique of the Remote Procedure Call Paradigm&gt;&gt;中对RPC的一般问题作了详细分析，这篇文章应该是对考虑将其作为基础架构的人们的当头棒喝。

Unix传统强烈赞成使用透明，可显的接口。这是UNIX文化不断坚持文本协议IPC的动力。

# 10 Configuration: Starting on the Right Foot

