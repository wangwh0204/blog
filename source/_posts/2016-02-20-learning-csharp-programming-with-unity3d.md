title: Learning C# Programming with Unity3D
date: 2016-02-20
updated: 2016-05-27
categories:
- [reading]
- [technology]
tags: 
- C#
- Unity
---

&lt;&lt;Learning C# Programming with Unity3D&gt;&gt;读书笔记，书的内容写的非常基础，也非常细致，主要写给Artist作为编程入门看的，最大的优点是结合Unity来实践，可以即时看到程序运行效果。即便如此，因为英语阅读速度的关系，断断续续也花了3个月时间才看完.<!--more-->

内容主要关于Unity3D的用法，以及C#的语法，都很基础，书里一些作者的软件开发经验之谈值得品味。

# chapter 1 Introduction : What This Book Is About
Unity 3D uses Mono, as it is a compiler to generate the bytecode, but Unity 3D does this automatically. 
When writing C# for games using Unity 3D, your code is compiled by Mono. Unity 3D then takes the bytecode from Mono and compiles for a target platform into a native machine code. 

https://github.com/badkangaroo/UnityProjects

# chapter 2 Before You Begin
using UnityEngine;
using System.Collections;

public class Example : MonoBehaviour {
  void Start() {
  }
  
  void Update() {
  }
}

In a new scene, you'll only have a Main Camera. The Hierarchy panel shows you all of the different objects that are going to make your game scene. The scene is more like a construction view of the game. The Game panel is the view of the game through the Main Camera.


You will find that four different directories -- Assets, Library, ProjectSettings, and Temp -- and several support files may occupy an active Unity 3D project directory.

- Assets Directory
The primary location for all your C# files and any other game objects such as 3D models, 2D textures, and sounds will be somewhere in this directory.

You might be inclined to put all asset resoureces together in one place. For instance, a hero might have a Hero directory with his sounds, models, textures, and scripts grouped together. This does make things more difficult to share. A weapon or sound effect might have to be shared by more than one character, so it makes more sense assuming that every resource can be shared.
Effects, Meshes, Scenes, Scripts, Sounds

- Library Directory
This contains the glue which Unity 3D uses to tie assets and logic together behind the scenes. Your editor preferences, platform settings, and many other bits that game engines need are placed here. It is very rare that any user will ever need to go in here to make any modifications, so it is best to avoid messing with the contents of this directory.

- ProjectSettings Directory
When any asset is imported into Unity 3D, it goes through a sort of filter and setup. Mostly, with things such as 3D models and textures, a lot of mashing of the bits must take place before they're game ready. Unity 3D does nearly all of this automatically.

- Temp Directory
Data caches, writing temp files, and other operating system maintenance-related stuff get thrown into the Temp directory.

It is best for you to look around online for some additional information on the editor itself. (unity manual, unity tutorial)
This is often why programmers like having multiple monitors. One monitor with their code and the other monitor with an editor open showing them the resulting behaviors.


Just to make sure we're off to a good start, the name of the C# file should match the name of the class.
To assign the C# file to an object in the scene, you can drag it from the Project panel onto an object in the scene.
You can also drop it on a object in the Hierarchy panel. 
Dropping the script file anywhere under the other properties in the Inspector panel will also add it to the selected object.
If that's not enough, then you can press the Add Component button on a selected object in the scene and pick Scripts to select any scripts available in your project.
Using the Add Component button, you can even create, name, and add a script all at once! It does everything all at once. After this it is just a mater of moving the script from the root of the Assets directory into a more organized directory.
The end result is that our script will be attached to an object in the scene.

> View, Transform, Rotate, Scale to a object

The Transform tool allows you to pick and drag the object around in the scene.

All of the changes we've been doing have been created and applied to objects in a scene.

# chapter 3 First Steps

C# is an English-based programming language; like any other C-like programming language it can be broken into tokens.
Tokens can be categorized as a *keyword, identifier, literal, operator, separator, * and *white space*.

Programmers are often a group of literal thinkers. In terms of order of operation, programmers take things one step at a time. This process in programming terms is an imperative procedure, a step-by-step process in which operations are carried out in a linear fashion.

To learn how to write code is to learn how to think like a programmer.

Between programmers there's often a discussion of code style.
> 这个根本不是重点，只要团队统一就好，问题是很难协调，所以Go就很好，直接官方定义死了，避免无畏的争吵，浪费时间，精力。采用业界的一些通用标准会有利于沟通，比如google C++/JAVA/Python programming style

The keyword *int* is short for integer. Other C# built-in types include : float, double, string, bool, object, char, short, byte. Altogether, there are 15 different built-in types. All of these, except object and string, are value types.

Every type of data you're able to build must be based on all of these built-in types.

In Unity3D, a commonly used type is the Vector3. Vectors, in the math world, are directions in x, y, and z with a lengh. Unity3D uses vectors to keep track of a position in 3D space. The Vector3 type is a composite of there float variables.

C# is a *strongly* typed programming language.

great deal of information to be inferred by the programmer reading the code. In Unity 3D a Vector3 vec = new Vector3(1.0, 1.0, 1.0); will throw an error. The number 1.0 is called a double, which uses 64 bits, whereas 1.0f, which is a float, uses 32 bits. The difference means float 1.0f is half the size of the double 1.0 in memory. A Vector3 is made up of three float values, not three doubles.

Not all programming languages are so strict with types, but it’s a good to get used to working with strict types before learning a more lazily typed programming languages, like Lua (http://www.lua.org/ ).

in general, we need to be very careful when converting from one type into another.

# chapter 4 Basics: The Building Blocks of Code
Building up a game idea : working with what you know.
Often, when you come up with a game idea it's usually something that sounds familiar yet it's never been done before. The best games are finished games.
Where you begin your code and what you decide to tackle first is determined by what the player does the most often in your game.
It's an incremental process; layer one activity onto the next. When the game begins to be playable, you've reached a point where you can begin to add on more interesting behaviors. This process of adding features comes only after the core activity has been achieved.

Deciding what it is that you do most of the time in building a game is usually based on the type of game you're aiming to build.
The players' primary activity should be the focus of your game code.

At the beginning of almost every game development project, the player controls are usually the first focus of the game.

Input management is our first goal. You should decide if you're dealing with either keyboard and mouse or touch screen taps and gestures. Testing and iteration on a good input management system takes time and effort.

The programmers at Unity 3D have taken on the bulk of these complex tasks for you, so you don't have to deal with all of the physics and PhD-level science of rendering 3D graphics. The keyword using is how we tell C# that we're going to ask for a specific library to access.

In addition, it's also possible to write your own DLLs creating libraries for your game. This might allow you to add in platform-specific functions to accelerate various aspects of the game outside of the abilities of the built-in Unity 3D tools or engine.

The Unity 3D developers provided us with *MonoBehaviour* which is a class that allows our c# classes to have direct access to the inner workings of the Unity 3D game scene.

When dealing with most other C# applications, you'll need to use *Main* as the starting point for your C# application.
When the class we asked Unity 3D to create was made, Unity3D automatically added in *void Start()* and *void Update* to the class. These two functions are called *entry points*.

In a classic FPS the camera is always under control by the mouse.
We will learn what all of that means, but one thing at a time.

Specifically, in code, the C# file you attach is instanced by the GameObject when the game starts. As a matter of fact, practically every object in a Unity 3D Scene is a GameObject. The camera, lights, boxes, and so forth, everything you see in the scene, is a different instance of the GameObject class, each one with different attachments.

Everything you see in the Hierarchy panel is a GameObject. They are all instances of the GameObject class found in the *UnityEngine* library.
Every time we add our code as a component, we're telling GameObject to instantiate our class. Once instantiated, our code has become a part of the Unity 3D Scene and can both read and write data to the scene it's in.

C# does a pretty good job of automatically initializeing many of its built-in types. Number values are always initialized to 0 when they are not given a value. Bools are initialized as false when not given a value. This is handy to know since not all languages do this.

Using a flowchart as a guide, you can have a better idea what your code must accomplish when you start writing.
Game designers should also be able to explain a specific design decision in terms of a flowchart. When a monster shows up the game designer must be able to explain with simple logic what happens next. User interfaces and even the computer’s AI behavior. All of these game events can benefit from having a flowchart as a basis for design decisions.

Normally, variables and class definitions are considered to be private. This is usually implied and if you don’t tell C# otherwise, it will assume you mean every variable to be private information.
private
public
protected
internal
There are only four keywords used to change the accessibility of a variable.

When each class is created in Unity 3D, C# is used to make additions to the global scope of the project. This means that throughout the project, each class will be able to see every other class. As each new file is created, they're added to the global namespace.

# chapter 5 Fundamentals
We've gotten to a point where we'd like to search the entire scene for a specific object. We can find an object using its name or tag.
With Unity 3D, we have plenty of functions available which make find objects in a scene quite easy. eg. GameObject.FindObjectsOfType(typeof(GameObject). When monsters go chasing after players, we need to have a simple system for allowing them to find one another.

foreach

Multidimensional Arrays
GameObject[,] twoDimension = new GameObject[2, 3];

An *ArrayList* is a C# class that has special functions for building lists that allow for changes in the number of values stored. An array like int[] numbers can store only a bunch of ints. An ArrayList can store any variety of object types. Another feature which we’ll find out later is that an array, not an ArrayList, can have multiple dimensions, for instance, int[,] grid = new int[8,8];, which creates an 8 by 8 array. An ArrayList cannot be used like this.

In some cases, it's useful to use the @ operator before a string. This tells C# that we're really not interested in formatting or not being able to make modifications to our string, like string s = "this \nthat", which would result in the following:
this
that
The verbatim operator when used with strings—string s = @"this \nthat";—actually just
prints out like the following:
this \nthat

The best concept for working with a team of programmers is source control. Sometiems called revision or version control, the concept is basically being able to keep of code changes and keeping a history of all of your source files.

Unity 3D needs to be informed that the files it’s generating are to be controlled by some sort of source control. To make this change, select Edit → Project Settings → Editor. The Inspector panel will now display the options for Version Control; select Meta Files to ensure that your Unity 3D project can be managed by Git.

Unity 3D project's *.gitignore* : 
Library/
Temp/
*.csproj
*.sln
*.userprefs

These meta files are required for these magic data connections between objects in a Unity 3D Scene file. Of course, other file settings and project settings are also stored in these meta files. If you open one, you’ll find many things called GUIDs, which stands for globally unique identifiers, and they’re used in meta files to find a specific object in the scene and apply settings to them. 


# chapter 6 Intermediate
Don't worry about not making rapid progress; learning is more about the journey than it is about the goal.

Mathf is a class filled with specific math function, which we'll need to use fairly often. Mathf contains many functions such as abs for absolute value, and Sin and Cos for sine and cosine.
There’s more to these functions than just knowing the mathematics behind the simple concept of something like Sin. There’s also a great deal of optimization that went into making the function work. This sort of optimization comes only from years of computer science experience and lots of know-how and practice.

It's important to understand that *AddComponent()* is a function specific to Unity 3D's GameObject class.

C# has the keyword *as* for some basic type casting.

Prototyping game play using primitive shapes is a regular part of game development. This is somewhat related to what has become to be known as "programmer art". Changes to code often mean changes to art. It's difficult to build a game keeping art and code parallel.Often a simple change in code means days of changes to art. It's quite often easier to prototype a game making no requests of an artist. Most of the time, the programmer doesn't even know himself what to ask of an artist.

A *switch* is allowed to use only "integral, bool, char, string, enum, or nullable" types of data.

The principal differences between the struct and the class is where in the computer's memory they live and how they are created.
This system of using a struct as data means that a struct is a value type, whereas a class is a reference type.
When a class is assigned to a variable, only a reference to the calss is assigned. A new copy is not made and assigned to the variable.

In practice, it's a good idea to have a more central location for your globally accessible structs and enums.

In a simple function call, the variables that appear in it are all pushed into the stack. As soon as the function is complete, any of the temporary values created and used inside of the function are immediately destroyed once the function is done executing.

The primary advantage a class has over a struct is the addition of a constructor and class inheritance. Aside from that, you're able to add assignments to each variable in a class as it's created.

The *const* keyword is used to tell anyone reading the class that the value assigned cannot change during the game.
The *readonly* declaration allows you to change the variable only when a class is declared or as it's written when it was initialized.
This means that a *readonly* variable can only be set in a variable, an initializer, or a constructor.

A namespace is a system used to sort classes and their contained functioins into named groups.

The Rule of Three is a simple idea that any time you need to do any given task more than threee times it would be better served by creating a new single procedure to accomplish the task that has been done manually. This reduces the chance of error in writing the same code more than three times. 

A total of eight functions which Unity 3D calls are as follows:
Awake()
OnEnable()
Start()
FixedUpdate()
Update()
LateUpdate()
OnDisable()
OnDestroy()

The execution of classes becomes a bit more confusing when they're attached to a gameObject as a prefab. There's no specific order in which the objects are created and how they are ordered in the gameObject's components list. However, there is a simple system in which we can change the execution order manually.In Unity 3D under the Edit -> Preferences -> Script Execution Order, we can open a panel that tells Unity 3D how to prioritize when a class is called. By clicking on the + icon on the lower right of the panel, we can add our classes to an ordered list.

The *override* keyword following the *public* keyword in a function declaration tells the child version of the function to clear out the old behavior and implement a new version.

Adding the *virtual* keyword after the *public* declaration and before the return data type, we can tell the function it'a allowed to be overridden by any class inheriting its functions.

Games use "mechanics" as a generalized term for game rules. Often used like "this game's mechanics are fun."

The base class from which all classes in Unity3D inherit is *Object*.

(<Type>) versus "as", the two different methods we can use are called *prefix-casting* and *as-casting*. Prefix casting is what the (int) is called; this is also referred to as an explicit cast operator.

While stepping through code helps a great deal with understanding how our code is being executed, visualizing things as they move can be more helpful.That's where Unity 3D has provided us with a great deal of tools for doing just that. Unity3D calls its helper objects "Gizmos". Visualing data is carried out by using Gizmos to draw lines and shapes in the scene.

It's expecting the Gizmos drawing function to be used in an OnDrawGizmos or OnDrawGizmosSelected function.

Drag object from the Hierarchy to the Project panel, this created a Unity 3D prefab object. A prefab is a nicely packaged object that is an aggregation of different objects. This saves us some time if we need to make changes to multiple instances of the guy in the scene. We just make a modification to one; then we can press the Apply Changes to Prefab button in the Inspector panel, and the changes propagate to the rest of the objects that are from the same prefab.

A distance in math is called a magnitude. To get a magnitude, we need to provide a Vector3() and use the .magnitude property of the Vector3() class.

Another method to get more than one value from a function is to use the *out* keyword in the parameters.

sorting is a very deep topic that leads into the very messy guts of computer science.
For games such as tower defense, or anything where a character needs to shoot at the closest target and then move on to the next closest, we can use sorting to help provide the character with some more interesting behaviors.

The *ref* keyword, which is short for *reference*. If we use a statement like x = 1; y = x; we aren't actually taking x and putting it into y. In memor, y is storing a 1 and x is storing a different 1. The statement x = 1; ref y = x; would actually mean that y is now looking at the identifier, not the value being stored at the location of x. If ref y is looking at the idendifier and not the value, were we to modify y, the action is going to take place in the contents of x.
> 指针？
In many cases, a function is best when there are no side effects.

The expressivity of C# is fairly high, allowing you to try out many different methods to do the same thing. 

A *sealed* class is meant to prevent any further modifications from the point where it has been sealed.
The *abstract* keyword is used to tell inheriting classes that there's a function they need to implement.
When a function is preceded by the *abstract* keyword, the function cannot have a body.

C# is informing us that it cannnot create an instance of the *abstract* class or interface. An interface works in a similar way to an abstract class, but with a few more restrictions.


# chapter 7 Advanced

- 7.5 Accessors(or Properties)

class GetSet
{
  private int myInt;
  public int MyInt {get{return myInt;} set{myInt = value;}}
}
The above code has a private int myInt and a public in MyInt with an accessor. This is a standard notation that should be used to define a variable for a cleanly encapsulated class. This too operates the same as the previous {get;set;}, only with the idea that it’s redirecting an incoming data value from a public variable to a private variable hidden inside of the class.

One of the advantages of an accessor is the ability to add logic to how a number is set. In addition to logic is the ability to raise an event.

The *base* keyword tells C# to execute the parent classes' version of the function after the dot operator.

## 7.7 Optional Parameters

Naming the arguments can be an easy way to make the parameters easier to read.

Even in bug fixing, we learn how to write better code. Often having others check your work is a good practice to keep you in line with the rest of the team. Code reviews are a common practice among large companies, especially on high-profile projects in which a small bug can cause big problems.

## 7.8 Delegate Functions
A delegate acts like a data type; just like how both int and double are number types, a delegate is a type of function.
A delegate allows us to use function in a variable. If you're able to assign a variable to a function, you can use it like data. This means passing it between functions, structs, or classes through a parameter or assignment.

Once we get into events and event management, we'll get a clearer picture of what delegate functions are really used for, but it's important to understand how to create and assign delegates before we get ot events. Events are basically functions that call other functions when something specific is triggered.

In Unity 3D, delegates are often used to update the state of an object that has been createed in the scene. This is best done via events. 

## 7.9 Interface
An interface provides a framework that all of the child classes based on it will derive from.
Using an interface should be considered early on. Adding them after many classes have already been written can turn into a nightmare if your different monsters took on a wide variety of implementations, but therein lies the strength of the interface.

It's very common to add a feature to an interface or a base class, and then need to do many code updates. when you add a small bit of code to an interface, you'll need to find everything that uses the interface and add the new changes to them. This can be time consuming, but if the feature is important, it's worth the effort.

> 这里存在一个悖论，interface的完整抽象需要对所做的业务有足够的认知才能达成，而且要足够的稳定来抵抗需求的变化导致的变化，所以其实一开始是无法定义完整的interface的，这就意味着一开始就做出的抽象其实并不稳固，而这违反了interface被设计出来的初衷。 也许go提出的动态interface的概念才是真正合理的解决之道。

In C# we do not have the ability to inhert from multiple classes. However, we can implement both interfaces.

Practice is the only way we will get better at the craft of code. With each new tool we learn we should use it.

## 7.11 Preprocessor Directives
The system in place to enable or disable blocks of code is called a preprocessor directive, which acts somewhat like a comment that can use logic to bypass or enable blocks of code.
#define TESTING

#if TESTING
#elif 
#endif

#region NAME is a useful directive that is used to help keep your development environment sane.

#region NAME
#endregion

Directives are used for many different things: One of the most common is to mangage work with multiple platforms.

## 7.12 Exceptions
try {} 
catch(Exception e) {}
finally {}

## 7.13 IEnumerator
Enumerations are systems in which you might get data from something but it's presented to you only through specific methods.
The IEnumerator is an interface with one property and two methods. The only property is called Current, and the two methods we can use are callsed Rest and MoveNext.

## 7.14 Generics
- Generic Functions
public void log<T>(T thing) {
  string s = thing.ToString();
  Debug.Log(s);
}

log(9);

- Generic Types
public class ThreeThings<T>
{
  private T first;
  private T second;
  private T third;
}
new ThreeThings<zombie>();
> 相比C++的模板，在声明和调用上做了语法上的简化

The *var* keyword means to implicitly get a type once it's been assigned. Only after the actual object is created and assigned to the identifier that was created with *var* will the identifier turn into a type.

Debugging code with many generic classes and methods is difficult and can lead to a great deal of wasted time.In short, use them only when you have to.

## 7.15 Events
Delegates with generic types allow for even more cool things, mostly notably, the event. An event acts as a container or a handy place to put any number of functions. When the event is called, all of the functions assigned to it are then called.It's a great system to notify another function that something has occurred that you were waiting for.
> Observer 模式

## 7.16 Unity-Friendly Classes
When we're working with the built-in Unity 3D types such as GameObject, we're unable to extend those classes. However, it doesn't mean that we can't give the GameObject new functions. For instance, if we wanted gameObject.NewTrick(); we're able to do this through *Extensions* methods.

public static class GameObjectExtensions {
  public static void NewTrick(this GameObject go)
  {
    Debug.Log(go.name);
  }
}
The public static void NewTrick() is our extension function. To extend the GameObject, we use the argument *this GameObject go* where the this keyword informs C# that we're writing an extension method.
The Extension functions can be applied to any sealed class. When working with third-party libraries, it's often useful to add your own functions to classes which you don't have source code for.

After your scripts begin to deal with a great number of different variables, garbage collection(GC) begins to be an issue that also bogs down the game's performance.

## 7.17 Destructors
Unity 3D provides the onDestroy() event after any object based on MonnoBehaviour has been destroyed.
The destructor can be identified by the ~, or tilde, preceding the class identifier. Somewhat like a very simple-looking constructor, the destructor is called any time the object is garbage collected. There are serveral ways we can force the object to be cleaned out of memory.

> 1. 将对象赋null值
Setting the variable to null releases the reference in this class to the object. Once C# see that there is nothing referencing the object, it's cleaned out of memory and its destructor is called.

The automatic GC is done in random intervals. On a mobile device, the GC can lead to a sudden loss in frame rate once every few seconds. The interval between GC cycles can be longer or shorter depending on how often objects are created. Because of this, it's important to build some sort of scheme to track and destroy objects on your own.
> 2. 显式调用GC.Collect()强制GC

Destructors are used when manual clean up of a class is needed. When using classes based on any of the
Unity 3D class objects, it’s recommended you use the OnDetroy() function to clear any extra data created
by the class. It’s recommended that any class not based on a Unity 3D class use a destructor, though it’s
not a common practice to create classes not based on Unity 3D.

## 7.18 Concurrency or Coroutines
For instance, if we had a task that might take more than a single update frame to complete, we could use a function with a *yield*; this works only with a function that is an IEnumerator. This means that the function starts when it's called, but then allows us to come back to it again and check on how it's doing.

using UnityEngine;
using System.Collections;
public class Concurrent : MonoBehaviour
{
  void start()
  {
    StartCoroutine(DelayStatement());
  }
  
  IEnumerator DelayStatement()
  {
    Debug.Log("Started at: " + Time.fixedTime);
    yield return new WaitForSeconds(3.0f);
    Debug.Log("Ended at: " + Time.fixedTime);
  }
}

The *yield statement * create a concurrent task that then pauses the *DelayStatement* code block at the yield. Once the yield is done, it release the function's operation and allows it to move to the next statement.


## 7.19 Dictionary, Stacks, and Queues
Dictionary<string, int> MyDictionary = new Dictionary<string, int>();
MyDictionary.Add("Zombies", 10);
Debug.Log(MyDictionary["Zombies"]);

The structure of the declaration of a Dictionary is <first type, second type>, where the first type you use is called a key and the second type is the value that is associated with that key.

The queue works in a similar fashion to the stack, but with a few handy modifications. The difference between a queue and a stack is the order in which new objects are added. When we add a new object to a stack, we add it to the top of the list. With a queue we're making a waiting list where the first object added to the queue will also be the first removed out of the list.

## 7.20 Callbacks
To overly simplify, a callback is a function that is executed when some other function is done with its work.
The WWW class in Unity 3D provies a multitude of functions that allow us to obtain various assets from the Web.

## 7.21 Lambda Expressions
Lambda expressions were an upgrade from what is called an anonymous function. Anonymous functions were basically clips of code that could be stored as a variable.

Anonymous expressions are basically short functions that can appear in the middle of a function.



 //declare a delegate like before
 delegate void AnonExpression(string s);
 //Use this for initialization
 void Start ()
{
 //create and assign the delegate here
 AnonExpression delAnonExpression = delegate(string s)
 {
   Debug.Log(s);
 }; //observe the ; after the}
 
 //delegates content has been assigned
 //after it's been assigned, we can use it.
 delAnonExpression("weird");
}

Lambda expressions are best recognized by the => operator. This is sometimes called either the becomes or the points to operator.

 //create a delegate signature like before
 delegate void MyDelegate();

 //Use this for initialization
 void Start ()
 {
 //assign a new delegate and assign the expression at the same
time
 MyDelegate myDelegatedTask = () = > Debug.Log("Hello from
lambda.");
 //call the new delegated task
myDelegatedTask();
 }

brief is the main goal of the lambda. A lambda is basically a function written inside of a function.

 
# chapter 8 Extended
## 8.8 LINQ
LINQ stands for Language-INtegrated Qery.

void Start ()
{
int[] numbers = {0,1,2,3,4,5,6,7,8,9,10};//declare an array

var divisibleByThree = from n in numbers where (n% 3) == 0 select n;

foreach (int i in divisibleByThree)
{
  Debug.Log(i);
}
When a LINQ query is created, it's not immediately executed. It's only when the *foreach* statement uses the var from the linq statement the actual query is made. It's important to keep this in mind when using LINQ; this can lead to strange bugs if you're not aware of what's going on here.

The LINQ library is a power tool made available through System.Linq. For sorting through and finding bits of information, we are able to use LINQ to find and use data quickly and easily. Rather than using for loops and complex foreach loops for inspecting each object in an array, we’re better able to use LINQ to find what we’re looking for.

## 8.9 Bitwise Operators
The bitwise operators |, &, ^, and ~ are used to manipulate numbers on the bit level rather than on the math level where we assume 1 + 2 = 3.

The computer’s CPU actually has no + and − circuits built into it. It’s actually a collection of these bitwise operators.

## 8.11 Attributes
Attributes in some ways look out of place; like preprocessor directives, they have their own set of rules and uses. They use the square brackets [] to indicate their use and function. Attributes allow your code to read additional information about your code. Reflection occurs when your code is able to look up additional information on a function or type. This includes any field in a class as well as any function or the class itself.

Attributes need to be prepared before they are used. A custom attribute is a class that inherits from the System.Attributes class. The class itself is also labeled as a special class that is used to define custom attributes.

The concept of a class being able to collect information on another object is called reflection. When using the System.Reflection class, an object is allowed to inspect another class or struct in depth. When you write code, you’re able to actually look at and see another object before using it.

## 8.12 Architectures and Organization
When you’re building a structure for your game, it’s important to keep C# files separated by task. Tasks can be added or merged as needed far more easy when separated into different files. The more separation you keep, the less often files will have to be merged when working in a team of engineers. If each class is limited in scope to just a few related tasks, you also decrease the number of places you need to look to fix bugs. This also helps when using the debugger; if the file isn’t long and the scope is limited, you only have to find a problem and fix it in a smaller file.

Directories for your classes add to the structure of the project. It's a good practice to keep the names of the directories matching the names of the classes and namespaces.

A simple layout can end up being many different folders, each one containing any number of related classes and partial classes designed to work together. It’s also important to keep your C# script files separated from your game assets.

You should be managing these files in some form of source control. This allows your heavy assets like art and audio to run on a different version control system from your code. Combining binary files like an image with text makes for a messy version control system. Art files also tend to take up a lot more space than text files. Large files that make pulling an update from a server take a long time. In the interest of keeping code versioning quick, it’s best to keep the two under different revision control servers.

Modify Zombie.cs to public partial class Zombie : Behavior and then create a new C# script file called InitZombie.cs, which could contain one function. The partial keyword will allow us to break apart a single class across multiple different files. The reason for this is to allow you to
spread your work across multiple files.

Creating and using a structure for your game takes a lot of experience and practice. Coming to a final decision on structure before you’ve started writing the code for your game is unlikely. By creating namespaces and writing small classes in each one, you’re also giving yourself a much easier way to reorganize the files into new namespaces and new directories.

## 8.13 Design Patterns
we’ve studied something called a design pattern. Computer programmers have been solving the same problems time and again, so it should come as no surprise that some common solutions for similar prob lems have been discovered and shared. The solutions to these reoccurring problems became to be known as design patterns. With the long history of programming, many complex problems are solved with known patterns. The more common the problem, the more likely there’s already a known pattern. These solutions are described by how the problem has been solved. Design patterns are reusable solutions. The patterns become established when they are reusable, and they are proven to work. They are also general enough to be modified to suit the situation you need it for.

main points behind why the design patterns matter. There are three categories of design patterns in computing: creational, structural, and behavioral. When writing software for the first time, you’re going to be coming across tasks thinking that they’re all new. In fact, they’re the same problems which everyone has had to solve many times before you.

The Singleton pattern is useful to ensure that a game only has a single game state controller. If you want to keep track of the player’s navigation through your menus and into your game, it’s better to have a single class instructing the rest of your game to start, stop, and post results through one class.

Structural design patterns help consolidate how data and functions are organized and arranged in a class. In this category, we’ve got the Decorator, Facade, Flyweight, Adapter, and Proxy. Of these the Decorator pattern comes up often in games. The Decorator pattern is used when instancing objects into a scene. We use this pattern extensively in Unity 3D. For each component you attach to a gameObject, you’re decorating it with new behaviors.

Behavioral design patterns focus on communication between objects in a system. Some behavioral patterns include Iterator, Mediator, Observer, and Visitor. In this section, we’ll take a close look at the Iterator and Observer patterns.

> 关于设计模式在游戏中的应用，可以阅读[Game Programming Patterns](http://gameprogrammingpatterns.com/contents.html)
Anything can happen, and a project can get canceled before it sees the light of day. The end result can be months or worse yet years invested into a lost cause. Nothing is worse than walking away from a gigantic project with nothing to show for your work. The games industry is volatile; it’s filled with politics and instability. The more you know, the easier it is to remain relevant. The more skills you have, the wider your opportunities. Eventually, once you’ve accumulated enough skill, it’s time to work on personal projects that mean more to you.

# chapter 9 Stuff We Couldn't Cover
Not all features added to C# are allowed in Unity 3D for reasons of security or platform compatibility.
When C# is compiled into other platforms, such as iOS or Android, many of the tricks we discussed don't exist.

The *extern* keyword is specifically used to point a function at the contents of a DLL.

We’ve used var, but there’s also a keyword dynamic. How is this different? The dynamic keyword is intended to allow for more compatibility with different systems. It works in many ways the same as var.

**The best way to learn is to do.**

**Learning by doing, testing, and playing is the best experience anyone can have.** To start a project and find problems that might be easy or tough to solve is all a part of the experience. When things get too difficult, start over using a different approach. Never let a single problem keep you from learning. Start something else and see how far you get.

Start and complete enough projects; eventually you'll finish one.

# chapter 10 Good Luck
The most important advice I can give you is that you remain focused on learning with your first few projects rather than finishing that massively multiplayer online role-playing, first-person World War II zombie shooter game. It’s important that you understand what you’re capable of, and to do this, you need to learn your own limitations.

> 一个完整可玩的小游戏胜过构思宏大的不可玩的半残品. 从完成一个小游戏开始，在实现的过程中发现自己能做什么，还要学习和提高什么，不断的磨练知识和技能.

对C#和Unity有初步了解后，可采用Learning by doing的学习方式，结合[Unity Manual](https://docs.unity3d.com/Manual/index.html)和[Unity Tutorials Topics](https://unity3d.com/learn/tutorials)，按照Graphics, Physics, Scripting, Networking, Audio, Animation, UI, Navigation and Pathfinding, Virtual Reality几个主题的顺序阅读文档和编码实践。
