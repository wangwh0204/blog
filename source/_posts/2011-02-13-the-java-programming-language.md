title: The Java Programming Language 3rd
date: 2011-02-13
updated: 2011-04-03
categories: 
- [technology]
tags: 
- Java
---

&lt;&lt;The Java Programming Language 3rd&gt;&gt;的中文版&lt;&lt;Java编程语言&gt;&gt;读书笔记。<!--more-->

# 01 概述
类包括成员，field和method
method名字和parameter列表一起组成method的签名(signature)。
parameter
argument

Java基本类型包括布尔型, 字符型, 整型，浮点类型			初始值
boolearn	true/false							false

char		16b unicode 2.1字符					'\u0000'

byte		8b integer(signed)					0
short		16b integer(signed)					0
int 		32b integer(signed)					0
long		64b integer(signed)					0

float		32b float(IEEE 754-1985)				+0.0f
double	64b float(IEEE 754-1985)				+0.0

对象										null
named constant是通过名字应用的常量值。

static 
final 声明为常量


JAVA使用Unicode字符集

控制流
while, for, if-else, switch, do-while


数组:
类型[] 变量;

对象通过含有new关键字的表达式创建。从类定义创建对象也叫实例化(instantiation)
在JAVA中，新创建的对象分配在heap中，JAVA中的所有对象都通过对象引用进行访问。

String对象的值是只读的：String对象的内容永远不变。每次执行一个看上去好像修改String对象的操作，实际上是产生另一个只读的String对象，并将新对象的引用传递给被修改的对象。

equals方法是比较两个String对象是否相等的最简单方法，如果用==来比较字符串对象，实际上是比较两个对象是不是同一个对象的引用，而不是比较其字符串是否具有相同的内容。

subclass, superclass

polymorphism

super, this
当调用super.method()时，运行时系统从下到上检查继承层次，直到找到第一个含有method方法的superclass

Object类
没有显式继承其他类的类隐式继承了Object类。

interface
接口的所有成员都隐式或显式的是public的。

implements
extends


异常，Throwable <--- Exception
try-catch-finally

异常是一个具有类型，数据和方法的对象。异常对象一般从Exception类中派生，这个类有一个描述错误的字符串域。所有的异常都必须是Throwable类的子类，Throwable类是Exception类的超类。

异常的一般范式是try-catch-finally: 首先尝试(try)什么；如果它抛出异常，你可以捕获(catch)它；最后(finally)，不管发生了什么，由正常的代码路径或异常代码路径进行清理工作。



import 	package


# 02 类和对象
类成员
- field : 与类及其对象相关联的数据变量，其中保存着类或对象的状态。
- method : 包含类的可执行代码并定义了对象的行为。
- nested class/interface :

类 修饰符
- public : 
- abstract : 不能实例化
- final : 不能子类化
- strict floating point : 要求类中定义的浮点算法都进行精确运算。

field 修饰符
- 访问修饰符
- static
- final
- transient
- volatile
如果域没有初始化，就根据其类型赋予默认的初始值，特别的对象被赋予null值。

如果类中没有任何类型的构造函数，Java提供一个什么也不做的无参数no-arg构造函数(默认构造函数)。

类成员具有四种可能的控制修饰符:
private	package	protected	public

method 
method header + method body
- access modifier
- abstract
- static 
- final
- synchronized
- native

Java 中，方法的所有参数都是"by value"的。当参数是对象引用时，"传值"传递的是对象引用而不是对象本身。

一般来说，我们只在需要的时候使用this，这是指当要访问的域名被本地变量或参数声明隐藏的时候。

在JAVA中，每个方法都有签名(signature)，就是方法名以及参数的个数和类型。如果两个方法参数的个数和类型不同，它们可以具有相同的名字，这种现象叫做重载(overloading)。签名并不包括返回类型或者抛出异常的列表，所以不能通过这些来重载方法。

natvie方法不能声明为abstract或者strictfp类型。

# 03 继承类

继承类叫做它所继承的类的子类(subclass)或继承类(extended class)，被继承的类叫做超类(superclass)。

Object类位于所有类层次的根部。
创建对象时，将会对它所有的域分配内存，包括从超类继承来的并且这些域会被设置为相应类型的默认初始值，然后调用构造函数。每个构造函数的执行有三个阶段：
1) 调用超类的构造函数
2) 利用初始器或任何初始化语句块对域进行初始化
3) 执行构造函数体。

构造函数应该避免调用可覆盖(override)的方法----既不是private, static也不是final的方法。

overload方法提供同名的多个方法，但是它们具有不同的参数
override方法使用同样的签名方法替换超类的实现

子类可以改变超类方法的访问权限，但只能提供更多的权限。

field不能被覆盖，它们只可以被隐藏(hidden)。如果在类中声明与超类同名的域，超类中的那个域仍然存在，但是再也不能仅仅通过名字去直接访问它了，而是必须使用super或超类类型的另一个引用去访问。

如果某方法要访问子类中override的对象成员，那么该方法会引用哪个成员---超类还是子类成员？问题的答案取决于成员的类型，访问权限以及引用的方式。

当通过对象引用来调用method时，对象的实际类将决定使用哪种实现。当访问field时，所用的是引用的声明类型(declared type of the reference)

基于用来访问field的引用类型，哪个field会被访问将在编译时进行确定。

只有可访问的方法才可以被重载。如果某方法是不可访问的，那么它并未被继承，如果它并未被继承，那么它就是不可被重载的。

类的所有非静态方法中都可以使用关键字 super.在field访问和method调用中，super实际是作为对超类实例当前对象的一个引用。

super.method调用总是使用超类的method实现，而不是位于类层次下层的其他override实现。

通过使用instanceof运算符可以检查对象的类，如果其左边的表达式与右边的类型名是赋值兼容的，那么将返回true，否则返回false.尽管null并不是任何类型的实例，对null进行instanceof检查将会返回false.使用instanceof可以安全地对引用进行向下强制转换，而不会抛出任何异常。
if (list instanceof SortedList)

protected

把method标记为final意味着继承类不能通过override该方法来改变行为；同样的标记为final的类不能由其他类继承，且该类的所有方法都是final.

abstarct class 可以声明仅定义了部分实现的类，让继承类提供某些或全部方法的具体实现。

所有带abstract方法的类都要被声明为abstract.不能创建abstract类的对象，因为有些可能要调用的方法还没有合法的实现。

Object类是类层次的根。所有类都直接或间接地继承Object类，主要method如下：
public boolean equals(Object obj);
public int hashCode();	// 返回对象的hashcode,每个对象都有一个用于hash table的hash code
protected Object clone() throws CloneNotSupportedException
public final Class getClass(); // 返回表示该对象的Class类型的特定对象，Class类的对象是类的运行时表示
protected void finalize() throw Throwable
public String toString();

IsA  VS HasA
继承 VS 组合

JAVA使用了面向对象程序设计的多重继承模型而没有使用多重继承。通过使用 接口继承 达到多重继承的优点并且没有多重继承的问题，比如菱形问题。

# 04 接口
interface没有任何实现，也就不可以创建接口的实例。
JAVA允许对接口进行多重继承，但是只支持实现的单重继承。

Cloneable, Comparable, Runnable, Serializable

interface 

接口中可以声明named constant，这些常量均被定义为field，但都为隐式的public, static和final.

接口也可以利用关键字extends继承，与类不同，接口可以继承多个接口。


# 05 嵌套类和接口

nested type被认为是其包装类型(enclosing type)的一部分，它们互相信任，能够访问对方的所有成员。

静态嵌套类是类的成员，我们可以将它声明为任何方式访问。

非静态嵌套类被称为内部类(inner class)

在内部类中，所有在其包装类中声明的名字都被称为in scope---它们可以直接被使用，就像该内部类代码是在其外部类中声明的一样。inner class自己的域和方法则能够隐藏包装对象中的域和方法。 

我们可以在代码块中定义内部类，这些局部内部类(local inner class)布什代码所在类的成员，但对本代码块是局部的，就像局部变量那样。这样的类在定义它们的块外是完全不能访问的。

# 06 语言符号，运算符和表达式

JAVA有三种形式的注释:
// comment
/* comment */
/** comment */

JAVA语言的关键字不能用作标识符，清单如下:
abstract	default  	if  		private  	this
boolean   	do       	implements  protected  	throw
break    	double 	import  	public 	throws
byte 		else 		instanceof 	return 	transient
case 		extends 	int 		short 	try
catch 	final 	interface 	static 	void
char  	finally 	long 		strictfp 	volatile
class 	float 	native 	super 	while 
const 	for 		new 		switch
continue 	goto 		package 	synchronized

JAVA数组(array)提供有序的元素集合。数组元素可以是基本类型，也可以是对对象引用。
int[] ia = new int[3];
和
int ia[] = new int[3]
两种定义是相同的。

数组元素的个数是new创建时而不在声明时决定的。数组对象的长度在创建时限定并且不能再改变。


 <<  向左移位，右边用零填充
 >>  向右移位，左边用最高位(符号位)填充   算术移位
 >>> 向右移位，左边用零填充		     逻辑移位

移位运算符只能用在整型值上。移位运算中实际的移动的位数等于类型长度减1所得的值对所提供的移位数做掩码得到的结果。对一个int整数来说，所用的掩码是0x1f(31)，所以n << 35 和 n <<< -29 等价于 n << 3

当从double强制转换到float时，有三种可能：丢失精度，得到零或者在原先有穷值超过float的范围时得到无穷大。

整型是通过去掉高位进行转换的。

# 07 控制流 

if () { } else { }

switch (expression) {
    case n: statements;
    case m: statements
    default: statements
}

switch表达式必须是char, byte, short或者int。所有的case标号都必须是常量表达式。

break语句用于从任意语句块中退出，而不仅仅从switch中退出。break语句有两种形式。
无标号的break : break;(用于终止最内层的switch ,for ,while语句)
和有标号的break : break label;(中止任何被标注的语句)


continue语句只能在循环中使用(for, while或者do)，它把控制体转移到循环体的结尾。
与break语句类似，continue语句也分为两类:
无标号的continue : continue;(转移控制权到最内层循环体的结尾。)
和有标号的continue : continue label;(转移控制权到标号指定循环的结尾，它的标号必须属于某个循环语句)

# 08 异常
Java中的异常是对象。所有的异常类型，即所有为throwable对象设计的类，必须继承JAVA中的Throwable类或其子类。

``` java
try {
    statments
} catch(exception_type identifier) {
    statments
} finally {
    statements
}
```
每个错误都有借口，但不管如何辩解，错误终究还是错误。
					------G.K.Cheserton 英国作家

# 09 字符串
字符串是具有bulit-in语言支持的标准对象。String对象是不可改变(read-only)的，因此JAVA还为可变的字符串提供了StringBuffer类。

在对象上使用==运算符只是测试两个引用是否指向同一个对象，而不是测试他们是否是相同的对象。

# 10 线程

``` java
public class Thread {

public void run();
}
```

Runnable接口只声明了一个方法: public void run();

把Runnable对象传递给Thread构造函数，它就可在它本身的线程内执行。Thread.run的实现会调用Runnable继承类的run方法。

