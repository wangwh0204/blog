title: Go语言编程
date: 2015-09-01
updated: 2015-09-11
categories: 
- [reading]
- [technology]
tags: 
- Go
---

&lt;&lt;Go语言编程&gt;&gt;读书笔记，内容泛泛而谈，简单而不深入，更像个人的BLOG文章，而不是书籍。花了2周时间看完.<!--more-->

# 01 初识Go语言
Go语言的第一个版本在2009年11月正式对外发布。第一个正式版本的Go语言于2012年3月28日正式发布。
Go语言的主要作者：Ken Thompson， Rob Pike, Robert Griesemer, Russ Cox, Ian Lance Taylor, Brad Fitzpatrick

Go 语言最主要的特性：
- 自动垃圾回收
- 更丰富的内置类型
- 函数多返回值
- 错误处理
Go语言引入3个关键字用于标准的错误处理流程：defer, panic, recover
- 匿名函数和闭包
在Go语言中，所有的函数也是值类型，可以作为参数传递。
- 类型和接口
- 并发编程
Go语言引入了goroutine概念，它使得并发编程变得非常简单。通过在函数调用前使用关键字go，即可让该函数以goroutine方式执行。
- 反射
- 语言交互性
在Go代码中，可以按Cgo的特定语法混合编写C语言代码，然后Cgo工具可以将这些混合的C代码提取并生成对于C功能的调用包装代码。开发者基本上
可以完全忽略Go语言和C语言的边界是如何跨越的。

``` go
package main
import "fmt"
func main() {
  fmt.Println("Hello, world. 你好，世界!")
}
```
每个Go源代码文件的开头都是一个package声明，表示该Go代码所属的包。包是Go语言里的最基本的分发单位，也是工程管理中依赖关系的体现。

有一点需要注意，不得包含在源代码文件中没有用到的包，否则Go编译器会报编译错误。这与下面提到的强制左花括号{的放置位置以及之后提到的函数名大小写
规则，均体现了Go语言在语言层面解决软件工程问题的设计哲学。


func 函数名(参数列表)(返回值列表) {
}

func Compute(value1 int, value2 float64)(result float64, err error) {
}

Go命令行工具的革命性之处在于彻底消除了工程文件的概念，完全用目录结构和包名来推导工程结构和构建顺序。

# 02 顺序编程

对于纯粹的变量声明，Go语言引入了关键字var,而类型信息放在变量名之后，示例如下：
``` go
var v1 int
var v2 string
var v3 [10]int
var v4 []int
var v5 struct {
   f int
}
var v6 *int
var v7 map[string] int
var v8 func(a int) int
```

通过const关键字，可以给字面常量指定一个友好的名字：
const zero = 0.0

Go语言预定义了这些常量：true, false和iota
itoa比较特殊，可以被认为是一个可被编译器修改的常量，在每一个const关键字出现时被重置为0，然后在下一个const出现之前，每出现一次iota，其所代表的数字自动增1.

Go语言并不支持enum关键字，而是使用const后跟一对圆括号的方式定义一组常量来定义：
const (
  Sunday = iota
  Monday
  Tuesday
  Wednesday
  Thursday
  Friday
  Saturday
  numberofDays
)

Go语言内置以下基础类型：
- 布尔类型: bool
- 整形: int8, byte, int16, int, uint, uintptr
- 浮点类型：float32, float64
- 复数类型： complex64, complex128
- 字符串：string
- 字符类型：rune
- 错误类型：error

此外，Go语言也支持以下复合类型：
- 指针(pointer)
- 数组(array)
- 切片(slice)
- 字典(map)
- 通道(chan)
- 结构体(struct)
- 接口(interface)

数组的长度在定义之后无法再次修改，数组是值类型，每次传递都将产生一份副本。Go语言提供了slice来弥补数组的不足。

数组切片可以基于一个已经存在的数组创建:
var myArray [10]int = [10]int {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}
var mySlice []int = myArray[:5]

也可以通过make函数直接创建:
mySlice1 := make([]int, 5)

既可以使用下标来遍历元素：
for i := 0; i < len(mySlice); i++ {
  fmt.Println("mySlice[", i, "] =", mySlice[i])
}
也可以使用range关键字：
for i, v : range mySlice {
  fmt.Println("mySlice[", i, "] =", v)
}

Go语言支持如下的几种流程控制语句：
- 条件语句 : if, else, else if
if a < 5 {
  return 0
} else {
  return 1
}
    - 条件语句不需要使用括号将条件包含起来;
    - 无论语句体内有几条语句，花括号{}都是必须存在的；
    - 左花括号{必须与if或者else处于同一行；
    - 在if之后，条件语句之前，可以添加变量初始化语句，使用;间隔；
    - 在有返回值的函数中，不允许将最终的return语句包含在if...else...结构中，否则会编译失败
- 选择语句 : switch, case, select
switch i {
  case 0:
   fmt.Printf("0")
  case 1:
   fmt.Printf("1")
  case 2:
   fallthrough
  case 3:
   fmt.Printf("3")
  case 4, 5, 6:
   fmt.Printf("4, 5, 6")
  default:
   fmt.Printf("Default")
}

    - 左花括号{必须与switch处于同一行；
    - 条件表达式不限制为常量或者整数；
    - 单个case中，可以出现多个结果选项；
    - 与C语言等规则相反，Go语言不需要用break来明确退出一个case；
    - 只有在case中明确添加fallthrough关键字，才会继续执行紧跟的下一个case；
    - 可以不设定switch之后的条件表达式，在此种情况下，整个switch结构与多个if...else...的逻辑作用等同

- 循环语句 : for, range
Go语言中的循环语句只支持for关键字，而不支持while和do-while结构。
``` go
sum := 0
for i := 0; i < 10; i++ {
  sum += i
}
```
无限循环:
``` go
sum := 0
for {
  sum++
  if sum > 100 {
   break
  }
}
```
多重赋值：
a := []int {1, 2, 3, 4, 5, 6}
for i, j := 0, len(a) - 1; i < j; i, j = i + 1, j - 1 {
  a[i], a[j] = a[j], a[i]
}

    - 左花括号{必须与for处于同一行
    - Go语言中的for循环与C语言一样，都允许在循环条件种定义和初始化变量，唯一的区别是，Go语言不支持以逗号
    为间隔的多个赋值语句，必须使用平行赋值的方式来初始化多个变量
    - Go语言的for循环同样支持coutinue和break来控制循环，但是它提供了一个更高级的break，可以选择中断哪一个循环

- 跳转语句 : goto 

与C，C++和JAVA等开发语言的一个极大不同在于，Go语言的函数或者成员的方法可以有多个返回值。比如File.Read()函数
可以同时返回读取的字节数和错误信息：
func (file *File) Read(b []byte) (n int, err Error)
我们可以给返回值命名，它们的值在函数开始的时候被自动初始化为空，在函数中执行不带任何参数的return语句时，会返回对应的返回值汴梁的值。

如果调用方调用了一个具有多返回值的方法，但却不关心某个返回值，可以使用下划线_来跳过此返回值：
n, _ := f.Read(buf)

## 匿名函数和闭包

匿名函数由一个不带函数名的函数声明和函数体组成：
func(a, b int, z float64) bool {
  return a*b < int(z)
}
匿名函数可以直接赋值给一个变量
f := func(x, y int) int {
  return x + y
}
或者 直接执行
func(ch chan int) {
  ch <- ACK
} (replay_chan) // 花括号后直接跟参数列表表示函数调用

Go的匿名函数是一个闭包(closure)。
闭包是可以包含自由变量的代码块，这些变量不在此代码块内或者任何全局上下文中定义，而是在定义代码块的环境中定义。

闭包的价值在于可以作为函数对象或者匿名函数。

## 错误处理
Go语言引入了一个关于错误处理的标准模式，即error接口:
type error interface {
  Error() string
}

defer 关键字

Go语言引入了两个内置函数panic()和recover()以报告和处理运行时错误和程序中的错误场景。


# 03 面向对象编程
对于面向对象编程的支持，Go语言设计的非常简洁而优雅。Go语言并没有沿袭传统面向对象编程中的诸多概念，比如继承，虚函数，构造函数和析构函数，隐藏的this指针等。


func (a Integer) Less(b Integer) bool {
  return a < b
}

func (a *Integer) Add(b Integer) {
  return *a += b
}

Go语言的结构体(struct)和其他语言的类(class)有同等的地位，但Go语言放弃了包括继承在内的大量面向对象特性，只保留了组合(composition)这个最基础的特性。

所有的Go语言类型(指针类型除外)都可以有自己的方法。例如，定义一个矩形类型：

type Rect struct {
  x, y float64
  width, height float64
}

定义成员方法Area()来计算矩形的面积：
func (r *Rect) Area() float64 {
  return r.width * r.height
}

在定义了Rect类型后，可以通过如下几种方法创建并初始化Rect类型的对象实例：
rect1 := new(Rect)
rect2 := &Rect{}
rect3 := &Rect{0, 0, 100, 200}
rect4 := &Rect{width:100, height: 200}

在Go语言中，未进行显式初始化的变量都会被初始化为该类型的零值，例如bool类型的零值为false，int类型的零值为0，string类型的零值为空字符串。

在Go语言中没有构造函数的概念，对象的创建通常交由一个全局的创建函数来完成，以NewXXX来命名，表示"构造函数":

func NewRect(x, y, width, height float64) *Rect {
  return &Rect{x, y, width, height}
}

- 匿名组合
确切的说，Go语言也提供了继承，但是采用了组合的文法。
type Base struct [
  Name string
}

func (base *Base) Foo() { ... }
func (base *Base) Bar() { ... }

type Foo struct {
  Base
  ...
}

func (foo *Foo) Bar() {
  foo.Base.Bar()
  ...
}

Go语言对关键字的增加非常吝啬，没有private, protected, public这样的关键字。要使某个符号对其他包可见，需要将该符号定义为以大写字母开头。

需要注意的一点是，Go语言中符号的可访问性是包一级而不是类型一级。也就是类的内部方法，在同一个包中的其他类型也都可以访问它。

## 接口
接口在Go语言有着至关重要的地位。如果说goroutine和channel是支撑起Go语言的并发模型的基石，让Go语言在如今集群化与多核化的时代成为一道极为亮丽的风景，那么接口是Go语言整个类型系统的基石，让Go语言在基础编程哲学的探索上达到了前所未有的高度。

在Go语言中，一个类只需要实现了接口要求的所有函数，我们就说这个类实现了该接口。

由于Go语言中任何对象实例都满足空接口interface{}, 所以interface{}看起来像是可以指向任何对象的Any类型.
相比而言，使用Go语言可以大幅降低代码量，从软件工程的角度而言，降低代码量不仅仅意味着工作量的降低，更重要的是产品质量更容易得到保障。


# 04 并发编程

就目前而言，并发包含以下几种主流的实现模型：
- 多进程
- 多线程
- 异步IO
- 协程(Coroutine) 
本质上是一种用户态线程，不需要操作系统进行抢占式调度，且在真正的实现中寄存于线程中，因此系统开销极小，可以有效提高线程的任务并发性，而避免多线程的缺点。

线程之间通信采用共享内存的方式，为了保证共享内存的有效性，采用加锁方式，避免死锁或资源竞争。

Go语言在语言级别支持轻量级线程，叫goroutine。goroutine是Go语言中的轻量级线程实现，由Go runtime管理。

在一个函数调用前加go关键字，这次调用就会在一个新的goroutine中并发执行。当被调用的函数返回时，这个goroutine也自动结束。

工程上，有两种最常见的并发通信模型：共享数据和消息
Go语言提供的消息通信机制被称为channel

``` go
package main

import "fmt"

func Count(ch chan int) {
  ch <- 1
  fmt.Println("Counting")
}

func main() {
  chs := make([]chan int, 10)
  for i := 0; i < 10; i++ {
   chs[i] = make(chan int)
   go Count(chs[i])
  }
  
  for _, ch := range(chs) {
   <-ch
  }
}
```

Go语言在语言级别支持select关键字，用于处理异步IO问题
Go语言没有提供直接的超时处理机制，但可以利用select机制：

// 首先，我们实现并执行一个匿名的超时等待函数
timeout := make(chan bool, 1)
go func() {
  time.Sleep(1e9) // 等待1秒钟
  timeout <- true
}()

// 然后我们把timeout这个channel利用起来
select {
  case <-ch:
   // 从ch中读取数据
  case <-timeout:
   // 一直没有从ch读取到数据，但从timeout中读取到了数据
}

这种写法看起来是一个小技巧，但却是在Go语言开发中避免channel通信超时的最有效方法。
需要注意的是，在Go语言中channel本身也是一个原生类型，与map之类的类型地位一样，因此channel本身在定义后也可以通过channel来传递. 我们可以使用这个特性来实现*nix上非常常见的管道特性。

使用close()函数关闭channel

使用runtime.Gosched()函数可以主动出让时间片给其他goroutine

go语言包中的sync包提供两种锁类型：sync.Mutex和sync.RWMutex


# 05 网络编程
Go语言标准库里提供的net包，支持基于IP层，TCP/UDP层及更高层面(HTTP, FTP, SMTP)的网络操作，其中用于IP层的称为Raw Socket

Go语言标准库对传统的网络编程的过程(socket, bind, listen/connect, accept, send/receive)进行了
抽象和封装。无论我们期望使用什么协议建立什么形式的连接，都只需要调用net.Dial()即可.

func Dial(net, addr string) (Conn, error)

例子：
conn, err : = net.Dial("tcp", "192.168.0.10:2100")

conn, err : = net.Dial("udp", "192.168.0.12:975")

conn, err : = net.Dial("ip4:icmp", "www.baidu.com")

目前，Dial()函数支持如下协议："tcp", "tcp4"(仅限ipv4), "tcp6", "udp", "udp4", "udp6", "ip", "ip4", "ip6"

在成功建立连接后，我们就可以进行数据的发送和接收。发送数据时，使用conn的Write()方法，接收数据使用Read()方法

Go语言标准库内建提供了net/http包，涵盖了HTTP客户端和服务端的具体实现。

- http客户端

1. net/http包的client类型提供了如下几个方法：

func (c *Client) Get(url string) (r *Response, err error)
func (c *Client) Post(url string, bodyType string, body io.Reader) (r *Response, err
error)
func (c *Client) PostForm(url string, data url.Values) (r *Response, err error)
func (c *Client) Head(url string) (r *Response, err error)

func (c *Client) Do(req *Request) (resp *Response, err error)

2. 自定义http.Client

- http服务端
使用net/http包提供的http.ListenAndServe()方法，可以在指定的地址监听：
func ListenAndServe(addr string, handler Handler) error

如果想更多地控制服务端的行为，可以自定义http.Server : 
s := &http.Server {
  Addr: ":8080",
  Handler: myHandler,
  ReadTimeout: 10 * time.Second,
  WriteTimeout: 10 * time.Second,
  MaxHeaderBytes: 1 << 20,
}
s.ListenAndServe()

在Go中，标准库提供的net/rpc包实现了RPC协议需要的相关细节，开发者可以很方便地使用该包编写RPC的服务端和客户端程序，这使得用Go语言开发的多个进程之间的通信变得非常简单。

net/rpc包允许RPC客户端程序通过网络或是其他I/O调用一个远端对象的公开方法。

一个对象中只有满足如下这些条件的方法,才能被 RPC 服务端设置为可供远程访问:
- 必须是在对象外部可公开调用的方法(首字母大写);
- 必须有两个参数,且参数的类型都必须是包外部可以访问的类型或者是Go内建支持的类型;
- 第二个参数必须是一个指针;
- 方法必须返回一个error类型的值。
以上4个条件,可以简单地用如下一行代码表示:
func (t *T) MethodName(argType T1, replyType *T2) error
在上面这行代码中,类型T、T1 和 T2 默认会使用 Go 内置的 encoding/gob 包进行编码解码。

RPC 服务端可以通过调用 rpc.ServeConn 处理单个连接请求。多数情况下,通过 TCP 或
是 HTTP 在某个网络地址上进行监听来创建该服务是个不错的选择。

在 RPC 客户端,Go 的 net/rpc 包提供了便利的 rpc.Dial() 和 rpc.DialHTTP() 方法来与指定的 RPC 服务端建立连接。在建立连接之后,Go 的 net/rpc 包允许我们使用同步或者异步的方式接收 RPC 服务端的处理结果。调用 RPC 客户端的 Call() 方法则进行同步处理,这时候客户端程序按顺序执行,只有接收完 RPC 服务端的处理结果之后才可以继续执行后面的程序。当调用 RPC 客户端的Go() 方法时,则可以进行异步处理,RPC 客户端程序无需等待服务端的结果即可执行后面的程序,而当接收到 RPC 服务端的处理结果时,再对其进行相应的处理。无论是调用 RPC 客户端的 Call() 或者是 Go() 方法,都必须指定要调用的服务及其方法名称,以及一个客户端传入参数的引用,还有一个用于接收处理结果参数的指针。

``` go
packageserver
type Args struct {
  A, B int
}

type Quotient struct {
  Quo, Rem int
}
type Arith int
func (t *Arith) Multiply(args *Args, reply *int) error {
  *reply = args.A * args.B
  return nil
}

func (t *Arith) Divide(args *Args, quo *Quotient) error {
  if args.B == 0 {
   return errors.New("divide by zero")
  }
  quo.Quo = args.A / args.B
  quo.Rem = args.A % args.B
  return nil
}
```

注册服务对象并开启该 RPC 服务的代码如下:
arith := new(Arith)
rpc.Register(arith)
rpc.HandleHTTP()
l, e := net.Listen("tcp", ":1234")
if e != nil {
log.Fatal("listen error:", e)
}
go http.Serve(l, nil)

此时,RPC 服务端注册了一个 Arith 类型的对象及其公开方法 Arith.Multiply() 和 rith.Divide()供 RPC 客户端调用。RPC 在调用服务端提供的方法之前,必须先与 RPC 服务端建立连接,如下列代码所示:
client, err := rpc.DialHTTP("tcp", serverAddress + ":1234")
if err != nil {
log.Fatal("dialing:", err)
}

在建立连接之后,RPC 客户端可以调用服务端提供的方法。首先,我们来看同步调用程序顺序执行的方式:
args := &server.Args{7,8}
var reply int
err = client.Call("Arith.Multiply", args, &reply)
if err != nil {
  log.Fatal("arith error:", err)
}
fmt.Printf("Arith: %d*%d=%d", args.A, args.B, reply)

此外,还可以以异步方式进行调用,具体代码如下:
quotient := new(Quotient)
divCall := client.Go("Arith.Divide", args, &quotient, nil)
replyCall := <-divCall.Done



Gob 是 Go 的一个序列化数据结构的编码解码工具,在 Go 标准库中内置encoding/gob包以供使用。一个数据结构使用 Gob 进行序列化之后,能够用于网络传输。与 JSON 或 XML 这种基于文本描述的数据交换语言不同,Gob 是二进制编码的数据流,并且 Gob 流是可以自解释的,它在保证高效率的同时,也具备完整的表达能力。

作为针对 Go 的数据结构进行编码和解码的专用序列化方法,这意味着 Gob 无法跨语言使用。在 Go 的net/rpc包中,传输数据所需要用到的编码解码器,默认就是 Gob。由于 Gob 仅局限于使用 Go 语言开发的程序,这意味着我们只能用 Go 的 RPC 实现进程间通信。

Go 的net/rpc很灵活,它在数据传输前后实现了编码解码器的接口定义。这意味着,开发者可以自定义数据的传输方式以及 RPC 服务端和客户端之间的交互行为。

实际上,Go 标准库提供的net/rpc/json包,就是一套实现了rpc.ClientCodec和rpc.ServerCodec接口的 JSON-RPC 模块。


关于JSON的更多信息,请访问JSON官方网站 http://json.org/ 查阅。Go语言内建对JSON的支持。使用Go语言内置的encoding/json 标准库,开发者可以轻松使用Go程序生成和解析JSON格式的数据。在Go语言实现JSON的编码和解码时,遵循RFC4627协议标准。


使用 json.Marshal()函数可以对一组数据进行JSON格式的编码。 json.Marshal()函数的声明如下:
func Marshal(v interface{}) ([]byte, error)

可以使用 json.Unmarshal() 函数将JSON格式的文本解码为Go里边预期的数据结构。json.Unmarshal()函数的原型如下:
func Unmarshal(data []byte, v interface{}) error
该函数的第一个参数是输入,即JSON格式的文本(比特序列),第二个参数表示目标输出容器,用于存放解码后的值。要解码一段JSON数据,首先需要在Go中创建一个目标类型的实例对象,用于存放解码后
的值:
var book Book
然后调用 json.Unmarshal() 函数,将 []byte 类型的JSON数据作为第一个参数传入,将 book实例变量的指针作为第二个参数传入:
err := json.Unmarshal(b, &book)


3. 渲染网页模板
使用Go标准库提供的html/template包,可以让我们将 HTML 从业务逻辑程序中抽离出来形成独立的模板文件,这样业务逻辑程序只负责处理业务逻辑部分和提供模板需要的数据,模板文件负责数据要表现的具体形式。然后模板解析器将这些数据以定义好的模板规则结合模板文件进行渲染,最终将渲染后的结果一并输出,构成一个完整的网页。


# 06 安全编程
Go提供了MD5，SHA-A等几种hash函数crypto/

# 07 工程管理
Go语言在设计之初就考虑了在语言层面如何更好地解决当前工程管理中的一些常见问题。
本章我们将从以下方面介绍Go语言所引入的工程管理思想，工具和规范：
- 代码风格
- 文档风格和管理
- 单元测试与性能测试方法
- 项目工程结构
- 跨平台开发
- 打包分发

go 命令行工具可以完成以下几类工作：
- 代码格式化
- 代码质量分析和修复
- 单元测试与性能测试
- 工程构建
- 代码文档的提取和展示
- 依赖包管理

- 代码风格
“代码必须是本着写给人阅读的原则来编写,只不过顺便给机器执行而已。”这段话来自&lt;&lt;计算机程序设计与解释&gt;&gt;,很精练地说明了代码风格的作用。代码风格,是一个与人相关、与机器无关的问题。代码风格的好坏,不影响编译器的工作,但是影响团队协同,影响代码的复用、演进以及缺陷修复。

Go语言很可能是第一个将代码风格强制统一的语言。

> 深得我心，个人对代码风格并没有特别得偏好，但在一个团队里面一定要有编码规范，且强制执行。问题是通常没有办法依靠人自己编码时自动执行，使用工具来达成是最好的办法，比如预先在IDE里面设定好编码规范，然后设置save时自动format。
> go语言将代码规范作为语法层面来对待，减少了团队间不必要的沟通成本

> 无处不透露着实用主义，KISS的设计理念。将注意力放在要解决的问题本身，而不是语言本身。当一个语言本身的复杂性甚至超过了要解决的问题本身，语言变成了智力题

命名规则涉及变量、常量、全局函数、结构、接口、方法等的命名。Go语言从语法层面进行了以下限定:任何需要对外暴露的名字必须以大写字母开头,不需要对外暴露的则应该以小写字母开头。

使用go fmt 自动格式化

-  远程import支持
支持在语言级别调用远程的包。假如,我们有一个用于计算CRC32的包托管于Github,那么可以这样写:
package main
import (
  "fmt"
  "github.com/myteam/exp/crc32"
)
然后,在执行go build或者go install之前,只需要加这么一句:
go get github.com/myteam/exp/crc32

- 工程组织
GOPATH 这个环境变量是在讨论工程组织之前必须提到的内容。Gotool的大部分功能其实
已经不再针对当前目录,而是针对包名,于是如何才能定位到对应的源代码就落到了GOPATH
身上。


一个标准的Go语言工程包含以下几个目录:src、pkg和bin。目录src用于包含所有的源代码,
是Gotool一个强制的规则,而pkg和bin则无需手动创建,如果必要Gotool在构建过程中会自动创
建这些目录。

构建过程中Gotool对包结构的理解完全依赖于src下面的目录结构,

- 文档管理

在传统开发中，同步设计文档和代码是一件非常困难的事情。一旦开始有一些细微的不一致，之后这个鸿沟将会越来越大，并最终导致文档完全废弃。Javadoc工具的出现开始逐步缓解文档和代码一致性的难题。Javadoc工具可以直接将注释提取并生成HTML格式的文档。

使用go doc 生成代码文档 

- 跨平台开发
可以通过设置GOOS和GOARCH两个环境变量来指定交叉编译的目标格式。
$GOOS : darwin, freebsd, linux, windows
$GOARCH : 386, amd64, arm

$ GOOS=windows GOARCH=386 go build -o hello.exe hello.go

- 单元测试
Go本身提供了一套轻量级的测试框架。符合规则的测试代码会在运行测试时被自动识别并
执行。单元测试源文件的命名规则如下:在需要测试的包下面创建以“_test”结尾的go文件,形
如[^.]*_test.go。

Go的单元测试函数分为两类:功能测试函数和性能测试函数,分别为以Test和Benchmark
为函数名前缀并以*testing.T为单一参数的函数。下面是测试函数声明的例子:
func TestAdd1(t *testing.T)
func BenchmarkAdd1(t *testing.T)

# 08 开发工具 
goclipse : http://goclipse.github.io/releases/
eclipse的go语言插件

# 09 进阶话题
- 反射
- 语言交互性
package main

import "fmt"
/*
#include <stdlib.h>
*/
import "C"

func Random() int {
  return int(C.random())
}
func Seed(i int) {
  C.srandom(C.uint(i))
}

func main() {
  Seed(100)
  fmt.Println("Random:", Random())
}

- goroutine机理
- interface机理
