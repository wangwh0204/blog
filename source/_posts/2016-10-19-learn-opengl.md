title: Learn OpenGL
date: 2016-10-19
updated: 2016-11-28
categories:
- [technology]
tags: 
- Computer Graphics
- OpenGL
---

根据Stanford CS148 的[推荐](http://wangwh0204.github.io/2016/06/21/stanford-cs148-introduction-to-computer-graphics-and-imaging/)，通过 http://learnopengl.com/ 学习OpenGL知识。<!--more-->

在https://learnopengl-cn.github.io/有中文翻译，不过原文很易读，建议看英文。

# Introduction
作者在https://github.com/JoeyDeVries/LearnOpenGL提供了各章的完整代码，可以参考，但还是要自己动手编写，测试，验证。

# Getting started
## OpenGL
一般它被认为是一个API(Application Programming Interface, 应用程序编程接口)，包含了一系列可以操作图形、图像的函数。然而，[OpenGL](https://www.opengl.org/)本身并不是一个API，它仅仅是一个由[Khronos](http://www.khronos.org/)组织制定并维护的规范(Specification)。
OpenGL规范严格规定了每个函数该如何执行，以及它们的输出值。至于内部具体每个函数是如何实现(Implement)的，将由OpenGL库的开发者自行决定。
实际的OpenGL库的开发者通常是显卡的生产商。

现代函数要求使用者真正理解OpenGL和图形编程，它有一些难度，然而提供了更多的灵活性，更高的效率，更重要的是可以更深入的理解图形编程。

OpenGL的一大特性就是对扩展(Extension)的支持，当一个显卡公司提出一个新特性或者渲染上的大优化，通常会以扩展的方式在驱动中实现。

OpenGL自身是一个巨大的状态机(State Machine)：一系列的变量描述OpenGL此刻应当如何运行。OpenGL的状态通常被称为OpenGL上下文(Context)。我们通常使用如下途径去更改OpenGL状态：设置选项，操作缓冲。最后，我们使用当前OpenGL上下文来渲染。

在OpenGL中一个对象(Object)是指一些选项的集合，它代表OpenGL状态的一个子集。比如，我们可以用一个对象来代表绘图窗口的设置，之后我们就可以设置它的大小、支持的颜色位数等等。可以把对象看做一个C风格的结构体(Struct)

## Creating a window
- GLFW
在我们画出出色的效果之前，首先要做的就是创建一个OpenGL上下文(Context)和一个用于显示的窗口。然而，这些操作在每个系统上都是不一样的，OpenGL有目的地从这些操作抽象(Abstract)出去。这意味着我们不得不自己处理创建窗口，定义OpenGL上下文以及处理用户输入。幸运的是，有一些库已经提供了我们所需的功能。这些库节省了我们书写操作系统相关代码的时间，提供给我们一个窗口和上下文用来渲染。最流行的几个库有GLUT，SDL，SFML和GLFW。在教程里我们将使用[GLFW](http://www.glfw.org/)

> GLFW使用[CMake](https://cmake.org/)来生成各种环境下的构建脚本，大量的基于C/C++的项目使用CMake：OpenCV, LLVM, PCL, ROS, ...
> 和这篇文章里所使用的Visual Studio及Windows平台不同，我在Ubuntu Linux系统应用用GLFW，同样使用CMake来构建自己写的应用程序，通常更高层的游戏/图形引擎会在GLFW的基础上进一步的封装，所以一般将GLFW作为source code和应用程序一起build，同时GLFW编译成静态库，直接嵌入目标程序
> build GLFW 库 参见 http://www.glfw.org/docs/latest/compile.html，
> 使用GLFW编译App 参见 http://www.glfw.org/docs/latest/build_guide.html, 添加头文件: #include <GLFW\glfw3.h>

1. 下载GLFW
既可以git clone https://github.com/glfw/glfw 最新代码，也可以下载.zip文件。我直接使用git clone源代码来开发，这样可以随时与最新的代码保持同步。
2. build
``` bash
$ cmake .
$ make -j4
生成静态库libglfw3.a
```
GLFW支持一些编译选项，在根目录的CMakeLists.txt里有完整的选项，可以通过CMake命令行或者CMake GUI程序来设定，比如-DBUILD_SHARED_LIBS=OFF -DGLFW_BUILD_EXAMPLES=ON，默认编译成静态库libglfw3.a
build出来的glfw/examples/的程序可以运行起来看看

- GLEW
因为OpenGL只是一个标准/规范，具体的实现是由驱动开发商针对特定显卡实现的。由于OpenGL驱动版本众多，它大多数函数的位置都无法在编译时确定下来，需要在运行时查询。任务就落在了开发者身上，开发者需要在运行时获取函数地址并将其保存在一个函数指针中供以后使用。[GLEW](http://glew.sourceforge.net/)是OpenGL Extension Wrangler Library的缩写，它能解决这个繁琐的问题。如果你希望静态链接GLEW，必须在包含GLEW头文件之前定义预处理器宏GLEW_STATIC：
> 同样的，使用GLEW的静态库, 使用时
> #define GLEW_STATIC
> #include <GL/glew.h>
1. 下载GLEW
git clone https://github.com/nigels-com/glew.git
> git有问题，将include, src都过滤掉了，先用.zip里面的代码
2. build
``` bash
$ cd build
$ cmake ./cmake 
$ make -j4
生成静态库libGLEW.a
```
## Hello Window
参考文章代码，基于GLFW, GLEW, GL库，搭建第一个OpenGL程序，我同样使用CMake作为build工具，CMakeLists.txt内容如下：
``` cmake
cmake_minimum_required(VERSION 2.8)

set(3RDPARTY_DIR "${CMAKE_CURRENT_SOURCE_DIR}/..")

add_subdirectory("${3RDPARTY_DIR}/glew/build/cmake" "${CMAKE_CURRENT_BINARY_DIR}/3rdparty/glew")

set(BUILD_SHARED_LIBS OFF)
set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)
add_subdirectory("${3RDPARTY_DIR}/glfw" "${CMAKE_CURRENT_BINARY_DIR}/3rdparty/glfw")

add_executable(hellowindow hellowindow.cpp)

target_link_libraries(hellowindow glew_s)
target_link_libraries(hellowindow glfw)
```

## Hello Triangle
这一章直接使用shader来绘制一个三角形，需要理解Rendering Pipeline的概念。
在OpenGL中，任何事物都在3D空间中，而屏幕和窗口却是2D像素数组，这导致OpenGL的大部分工作都是关于把3D坐标转变为适应你屏幕的2D像素。图形渲染管线可以被划分为两个主要部分：第一部分把你的3D坐标转换为2D坐标，第二部分是把2D坐标转变为实际的有颜色的像素。

图形渲染管线接受一组3D坐标，然后把它们转变为你屏幕上的有色2D像素输出。图形渲染管线可以被划分为几个阶段，每个阶段将会把前一个阶段的输出作为输入。所有这些阶段都是高度专门化的（它们都有一个特定的函数），并且很容易并行执行。正是由于它们具有并行执行的特性，当今大多数显卡都有成千上万的小处理核心，它们在GPU上为每一个（渲染管线）阶段运行各自的小程序，从而在图形渲染管线中快速处理你的数据。这些小程序叫做着色器(Shader)。OpenGL着色器是用OpenGL着色器语言(OpenGL Shading Language, GLSL)写成的。

图形渲染管线包含很多部分，每个部分都将在转换顶点数据到最终像素这一过程中处理各自特定的阶段：
Vertex Data(顶点数据) -> Vertex Shader(顶点着色器) -> Primitive Assembly(图元装配) -> Geometry Shader(几何着色器) -> Rasterization(光栅化) -> Fragment Shader(片段着色器) -> Test and Blending(测试与混合) -> FrameBuffer(帧缓冲)

http://www.learnopengl.com/img/getting-started/pipeline.png

我们以数组的形式传递3个3D坐标作为图形渲染管线的输入，用来表示一个三角形，这个数组叫做 **顶点数据** (Vertex Data)；顶点数据是一系列顶点的集合。一个顶点(Vertex)是一个3D坐标的数据的集合。而顶点数据是用顶点属性(Vertex Attribute)表示的，它可以包含任何我们想用的数据。

1. 图形渲染管线的第一个部分是顶点着色器(Vertex Shader)，它把一个单独的顶点作为输入。顶点着色器主要的目的是把3D坐标转为另一种3D坐标（后面会解释），同时顶点着色器允许我们对顶点属性进行一些基本处理。
2. 图元装配(Primitive Assembly)阶段将顶点着色器输出的所有顶点作为输入（如果是GL_POINTS，那么就是一个顶点），并将所有的点装配成指定图元的形状
3. 图元装配阶段的输出会传递给几何着色器(Geometry Shader)。几何着色器把图元形式的一系列顶点的集合作为输入，它可以通过产生新顶点构造出新的（或是其它的）图元来生成其他形状
4. 几何着色器的输出会被传入光栅化阶段(Rasterization Stage)，这里它会把图元映射为最终屏幕上相应的像素，生成供片段着色器(Fragment Shader)使用的片段(Fragment)。在片段着色器运行之前会执行裁切(Clipping)。裁切会丢弃超出你的视图以外的所有像素，用来提升执行效率。OpenGL中的一个片段是OpenGL渲染一个像素所需的所有数据。
5. 片段着色器的主要目的是计算一个像素的最终颜色，这也是所有OpenGL高级效果产生的地方。通常，片段着色器包含3D场景的数据（比如光照、阴影、光的颜色等等），这些数据可以被用来计算最终像素的颜色。
6. 在所有对应颜色值确定以后，最终的对象将会被传到最后一个阶段，我们叫做Alpha测试和混合(Blending)阶段。这个阶段检测片段的对应的深度（和模板(Stencil)）值（后面会讲），用它们来判断这个像素是其它物体的前面还是后面，决定是否应该丢弃。这个阶段也会检查alpha值（alpha值定义了一个物体的透明度）并对物体进行混合(Blend)。

在现代OpenGL中，我们必须定义至少一个顶点着色器和一个片段着色器（因为GPU中没有默认的顶点/片段着色器）。出于这个原因，刚开始学习现代OpenGL的时候可能会非常困难，因为在你能够渲染自己的第一个三角形之前已经需要了解一大堆知识了。

开始绘制图形之前，我们必须先给OpenGL输入一些顶点数据。OpenGL是一个3D图形库，所以我们在OpenGL中指定的所有坐标都是3D坐标（x、y和z）。OpenGL不是简单地把所有的3D坐标变换为屏幕上的2D像素；OpenGL仅当3D坐标在3个轴（x、y和z）上都为-1.0到1.0的范围内时才处理它。所有在所谓的标准化设备坐标(Normalized Device Coordinates)范围内的坐标才会最终呈现在屏幕上（在这个范围以外的坐标都不会显示）。

一旦你的顶点坐标已经在顶点着色器中处理过，它们就应该是标准化设备坐标了，标准化设备坐标是一个x、y和z值在-1.0到1.0的一小段空间。任何落在范围外的坐标都会被丢弃/裁剪，不会显示在你的屏幕上。
你的标准化设备坐标接着会变换为屏幕空间坐标(Screen-space Coordinates)，这是使用你通过glViewport函数提供的数据，进行视口变换(Viewport Transform)完成的。所得的屏幕空间坐标又会被变换为片段输入到片段着色器中。

定义这样的顶点数据以后，我们会把它作为输入发送给图形渲染管线的第一个处理阶段：顶点着色器。它会在GPU上创建内存用于储存我们的顶点数据，还要配置OpenGL如何解释这些内存，并且指定其如何发送给显卡。顶点着色器接着会处理我们在内存中指定数量的顶点。

我们通过 **顶点缓冲对象** (Vertex Buffer Objects, VBO)管理这个内存，它会在GPU内存(通常被称为显存)中储存大量顶点。使用这些缓冲对象的好处是我们可以一次性的发送一大批数据到显卡上，而不是每个顶点发送一次。从CPU把数据发送到显卡相对较慢，所以只要可能我们都要尝试尽量一次性发送尽可能多的数据。当数据发送至显卡的内存中后，顶点着色器几乎能立即访问顶点，这是个非常快的过程。
顶点着色器允许我们指定任何以顶点属性为形式的输入。这使其具有很强的灵活性的同时，它还的确意味着我们必须手动指定输入数据的哪一个部分对应顶点着色器的哪一个顶点属性。所以，我们必须在渲染前指定OpenGL该如何解释顶点数据。

着色器的源代码需要经过编译，链接成程序。
>  我的理解是，VBO是用作CPU和GPU间通信的流缓冲区，VBO的格式由程序员定义，并使用glVertexAttribPointer函数告知GPU如何理解

使用glVertexAttribPointer函数告诉OpenGL该如何解析顶点数据（应用到逐个顶点属性上）. 每个顶点属性从一个VBO管理的内存中获得它的数据，而具体是从哪个VBO（程序中可以有多个VBO）获取则是通过在调用glVetexAttribPointer时绑定到GL_ARRAY_BUFFER的VBO决定的。
``` c
// 定义顶点数据，对于矩形，定义四个顶点，每个顶点由两部分组成：3字节的position信息(x,y,z)和3字节的颜色信息(r,g,b)
GLfloat vertices[] = {
      0.5f,  0.5f, 0.0f, 1.0f, 0.0f, 0.0f,  // Top Right
      0.5f, -0.5f, 0.0f, 0.0f, 1.0f, 0.0f,  // Bottom Right  
      -0.5f, -0.5f, 0.0f, 0.0f, 0.0f, 0.0f,  // Bottom Left
      -0.5f,  0.5f, 0.0f, 0.0f, 0.0f, 1.0f   // Top Left
};
GLuint VBO;
glGenBuffers(1, &VBO);
glBindBuffer(GL_ARRAY_BUFFER, VBO);
// 拷贝内存中的顶点数据到显存的VBO
glBufferData(GL_ARRAY_BUFFER, sizeof(vertices), vertices, GL_STATIC_DRAW);

// point the Shader how to understand VBO data : position
glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 6 * sizeof(GLfloat), (GLvoid*)0);
glEnableVertexAttribArray(0);

// point the Shader how to understand VBO data : color
glVertexAttribPointer(1, 3, GL_FLOAT, GL_FALSE, 6 * sizeof(GLfloat), (GLvoid*)(3* sizeof(GLfloat)));
glEnableVertexAttribArray(1);

...

glDrawArrays(GL_TRIANGLES, 0, 3);
    
```

> VAO的作用没看明白
顶点数组对象(Vertex Array Object, VAO)可以像顶点缓冲对象那样被绑定，任何随后的顶点属性调用都会储存在这个VAO中。这样的好处就是，当配置顶点属性指针时，你只需要将那些调用执行一次，之后再绘制物体的时候只需要绑定相应的VAO就行了。这使在不同顶点数据和属性配置之间切换变得非常简单，只需要绑定不同的VAO就行了。刚刚设置的所有状态都将存储在VAO中。

一般当你打算绘制多个物体时，你首先要生成/配置所有的VAO（和必须的VBO及属性指针)，然后储存它们供后面使用。当我们打算绘制物体的时候就拿出相应的VAO，绑定它，绘制完物体后，再解绑VAO。

对于要绘制的三角形，OpenGL提供了glDrawArrays函数，它使用当前激活的着色器，之前定义的顶点属性配置，和VBO的顶点数据（通过VAO间接绑定）来绘制图元。

> 为减少重复存储顶点数据所需的空间，OpenGL提供了索引缓冲对象(Element Buffer Object, EBO)，除了定义顶点数据，还定义索引数据，通过指定索引位置并用glDrawElements来绘制图形。因为OpenGL只能绘制点，线，三角形，所以需要将复杂的形状分解为这三种基本类型的组合。比如矩形，可以分解为2个三角形。单单只是绘制一个三角形，就需要150多行代码，这还是在GLEW，GLFW库的帮助下实现的。可想而知开发图形应用的复杂性，这也是cocos2d-x, Unity, Unreal的价值所在。
``` c
GLuint indices[] = {
  0, 1, 3, // First Triangle
  1, 2, 3  // Second Triangle
};

GLuint EBO;
glGenBuffers(1, &EBO);

glBindBuffer(GL_ELEMENT_ARRAY_BUFFER, EBO);
// copy index data to EBO
glBufferData(GL_ELEMENT_ARRAY_BUFFER, sizeof(indices), indices, GL_STATIC_DRAW);

...

glDrawElements(GL_TRIANGLES, 3, GL_UNSIGNED_INT, 0);
```

## Shaders
着色器(Shader)是运行在GPU上的小程序。这些小程序为图形渲染管线的某个特定部分而运行。从本质上来说，着色器只是一种把输入转化为输出的程序。着色器也是一种非常独立的程序，因为它们之间不能相互通信；它们之间唯一的沟通只有通过输入和输出。

着色器是使用一种叫GLSL的类C语言写成的。GLSL是为图形计算量身定制的，它包含一些针对向量和矩阵操作的有用特性。着色器的开头总是要声明版本，接着是输入和输出变量、uniform和main函数。每个着色器的入口点都是main函数，在这个函数中我们处理所有的输入变量，并将结果输出到输出变量中。

GLSL中包含C等其它语言大部分的默认基础数据类型：int、float、double、uint和bool。GLSL也有两种容器类型，分别是向量(Vector)和矩阵(Matrix)

我们希望每个着色器都有输入和输出，这样才能进行数据交流和传递。GLSL定义了in和out关键字专门来实现这个目的。每个着色器使用这两个关键字设定输入和输出，只要一个输出变量与下一个着色器阶段的输入匹配，它就会传递下去。
顶点着色器的输入特殊在，它从顶点数据中直接接收输入。为了定义顶点数据该如何管理，我们使用location这一元数据指定输入变量，这样我们才可以在CPU上配置顶点属性。
另一个例外是片段着色器，它需要一个vec4颜色输出变量，因为片段着色器需要生成一个最终输出的颜色。如果你在片段着色器没有定义输出颜色，OpenGL会把你的物体渲染为黑色（或白色）。

如果我们打算从一个着色器向另一个着色器发送数据，我们必须在发送方着色器中声明一个输出，在接收方着色器中声明一个类似的输入。当类型和名字都一样的时候，OpenGL就会把两个变量链接到一起，它们之间就能发送数据了（这是在链接程序对象时完成的）

Uniform是一种从CPU中的应用向GPU中的着色器发送数据的方式，但uniform和顶点属性有些不同。首先，uniform是全局的(Global)。全局意味着uniform变量必须在每个着色器程序对象中都是独一无二的，而且它可以被着色器程序的任意着色器在任意阶段访问。第二，无论你把uniform值设置成什么，uniform会一直保存它们的数据，直到它们被重置或更新。

如果你声明了一个uniform却在GLSL代码中没用过，编译器会静默移除这个变量，导致最后编译出的版本中并不会包含它，这可能导致几个非常麻烦的错误，记住这点！

可以看到，uniform对于设置一个在渲染迭代中会改变的属性是一个非常有用的工具，它也是一个在程序和着色器间数据交互的很好工具，但假如我们打算为每个顶点设置一个颜色的时候该怎么办？这种情况下，我们就不得不声明和顶点数目一样多的uniform了。在这一问题上更好的解决方案是在顶点属性中包含更多的数据。

> 很显然，将shader的源代码写死在OpenGL的代码中，每次修改都需要重新编译一遍才能看到效果，对于需要频繁修改shader，甚至可以动态更新的情况，将shader的source单独放到一个文本文件会是更好的做法。

## Textures
纹理是一个2D图片（甚至也有1D和3D的纹理），它可以用来添加物体的细节。因为我们可以在一张图片上插入非常多的细节，这样就可以让物体非常精细而不用指定额外的顶点。
为了能够把纹理映射(Map)到三角形上，我们需要指定三角形的每个顶点各自对应纹理的哪个部分。这样每个顶点就会关联着一个纹理坐标(Texture Coordinate)，用来标明该从纹理图像的哪个部分采样，之后在图形的其它片段上进行片段插值(Fragment Interpolation)。
**纹理坐标在x和y轴上，范围为0到1之间（注意我们使用的是2D纹理图像），使用纹理坐标获取纹理颜色叫做采样(Sampling)，纹理坐标起始于(0, 0)，也就是纹理图片的左下角，终始于(1, 1)，即纹理图片的右上角。**
对纹理采样的解释非常宽松，它可以采用几种不同的插值方式。所以我们需要自己告诉OpenGL该怎样对纹理采样。纹理坐标的范围通常是从(0, 0)到(1, 1)，那如果我们把纹理坐标设置在范围之外会发生什么？OpenGL默认的行为是重复这个纹理图像（我们基本上忽略浮点纹理坐标的整数部分），但OpenGL提供了更多的选择：
环绕方式(Wrapping)	描述
GL_REPEAT		对纹理的默认行为。重复纹理图像。
GL_MIRRORED_REPEAT	和GL_REPEAT一样，但每次重复图片是镜像放置的。
GL_CLAMP_TO_EDGE	纹理坐标会被约束在0到1之间，超出的部分会重复纹理坐标的边缘，产生一种边缘被拉伸的效果。
GL_CLAMP_TO_BORDER	超出的坐标为用户指定的边缘颜色。
这里的每个选项都可以使用glTexParameter*函数对单独的一个坐标轴设置

纹理坐标不依赖于分辨率(Resolution)，它可以是任意浮点值，所以OpenGL需要知道怎样将纹理像素(Texture Pixel)映射到纹理坐标。当你有一个很大的物体但是纹理的分辨率很低的时候这就变得很重要了。你可能已经猜到了，OpenGL也有对于纹理过滤(Texture Filtering)的选项。纹理过滤有很多个选项，但是现在我们只讨论最重要的两种：GL_NEAREST和GL_LINEAR：
- GL_NEAREST（也叫邻近过滤，Nearest Neighbor Filtering）是OpenGL默认的纹理过滤方式。当设置为GL_NEAREST的时候，OpenGL会选择中心点最接近纹理坐标的那个像素。
- GL_LINEAR（也叫线性过滤，(Bi)linear Filtering）它会基于纹理坐标附近的纹理像素，计算出一个插值，近似出这些纹理像素之间的颜色。一个纹理像素的中心距离纹理坐标越近，那么这个纹理像素的颜色对最终的样本颜色的贡献越大。
GL_NEAREST产生颗粒状的图案，我们能够清晰看到组成纹理的像素，而GL_LINEAR能够产生更平滑的图案，很难看出单个的纹理像素。GL_LINEAR可以产生更真实的输出，但有些开发者更喜欢8-bit风格，所以他们会用GL_NEAREST选项。

想象一下，假设我们有一个包含着上千物体的大房间，每个物体上都有纹理。有些物体会很远，但其纹理会拥有与近处物体同样高的分辨率。由于远处的物体可能只产生很少的片段，OpenGL从高分辨率纹理中为这些片段获取正确的颜色值就很困难，因为它需要对一个跨过纹理很大部分的片段只拾取一个纹理颜色。在小物体上这会产生不真实的感觉，更不用说对它们使用高分辨率纹理浪费内存的问题了。
OpenGL使用一种叫做多级渐远纹理([Mipmap](https://en.wikipedia.org/wiki/Mipmap))的概念来解决这个问题，它简单来说就是一系列的纹理图像，后一个纹理图像是前一个的二分之一。多级渐远纹理背后的理念很简单：距观察者的距离超过一定的阈值，OpenGL会使用不同的多级渐远纹理，即最适合物体的距离的那个。由于距离远，解析度不高也不会被用户注意到。同时，多级渐远纹理另一加分之处是它的性能非常好。

手工为每个纹理图像创建一系列多级渐远纹理很麻烦，幸好OpenGL有一个glGenerateMipmaps函数，在创建完一个纹理后调用它OpenGL就会承担接下来的所有工作了。

纹理图片可以是各种格式，比如jpg, png, bmp,...，[SOIL](http://www.lonesock.net/soil.html)这个库可以用来加载图片转换为OpenGL的纹理。 
> 原始的SOIL代码2008年就没有更新了，我使用https://github.com/kbranigan/Simple-OpenGL-Image-Library，因为它提供CMake的支持

``` c
// 要使用纹理映射，首先需要将纹理坐标关联到顶点数据：
GLfloat vertices[] = {
//     ---- 位置 ----       ---- 颜色 ----     - 纹理坐标 -
     0.5f,  0.5f, 0.0f,   1.0f, 0.0f, 0.0f,   1.0f, 1.0f,   // 右上
     0.5f, -0.5f, 0.0f,   0.0f, 1.0f, 0.0f,   1.0f, 0.0f,   // 右下
    -0.5f, -0.5f, 0.0f,   0.0f, 0.0f, 1.0f,   0.0f, 0.0f,   // 左下
    -0.5f,  0.5f, 0.0f,   1.0f, 1.0f, 0.0f,   0.0f, 1.0f    // 左上
};

glVertexAttribPointer(2, 2, GL_FLOAT,GL_FALSE, 8 * sizeof(GLfloat), (GLvoid*)(6 * sizeof(GLfloat)));
glEnableVertexAttribArray(2);

// 生成和绑定纹理ID
GLuint texture;
glGenTextures(1, &texture);
glBindTexture(GL_TEXTURE_2D, texture);

// 加载图片数据到纹理
int width, height;
unsigned char* image = SOIL_load_image("container.jpg", &width, &height, 0, SOIL_LOAD_RGB);
glTexImage2D(GL_TEXTURE_2D, 0, GL_RGB, width, height, 0, GL_RGB, GL_UNSIGNED_BYTE, image);

// 生成MIP map
glGenerateMipmap(GL_TEXTURE_2D);

SOIL_free_image_data(image);
glBindTexture(GL_TEXTURE_2D, 0);

// 在顶点着色器中接收顶点数据中的纹理坐标，在片段着色器中使用GLSL内建的texture函数来采样纹理的颜色

``` 
使用glUniform1i，我们可以给纹理采样器分配一个位置值，这样的话我们能够在一个片段着色器中设置多个纹理。一个纹理的位置值通常称为一个纹理单元(Texture Unit)。一个纹理的默认纹理单元是0，它是默认的激活纹理单元，所以教程前面部分我们没有分配一个位置值。

纹理单元的主要目的是让我们在着色器中可以使用多于一个的纹理。通过把纹理单元赋值给采样器，我们可以一次绑定多个纹理，只要我们首先激活对应的纹理单元。就像glBindTexture一样，我们可以使用glActiveTexture激活纹理单元，传入我们需要使用的纹理单元. OpenGL至少保证有16个纹理单元供你使用，也就是说你可以激活从GL_TEXTURE0到GL_TEXTRUE15。

## Transformations
目前为止都是讲述如何显示一个静态的对象，我们可以尝试着在每一帧改变物体的顶点并且重配置缓冲区从而使它们移动，但这太繁琐了，而且会消耗很多的处理时间。我们现在有一个更好的解决方案，使用（多个）矩阵(Matrix)对象可以更好的变换(Transform)一个物体。

向量(Vectors)最基本的定义就是一个方向。或者更正式的说，向量有一个方向(Direction)和大小(Magnitude，也叫做强度或长度)。由于向量表示的是方向，起始于何处并不会改变它的值。数学家喜欢在字母上面加一横表示向量。由于向量是一个方向，所以有些时候会很难形象地将它们用位置(Position)表示出来。为了让其更为直观，我们通常设定这个方向的原点为(0, 0, 0)，然后指向一个方向，对应一个点，使其变为位置向量(Position Vector)（你也可以把起点设置为其他的点，然后说：这个向量从这个点起始指向另一个点）。比如说位置向量(3, 5)在图像中的起点会是(0, 0)，并会指向(3, 5)。我们可以使用向量在2D或3D空间中表示方向与位置.

标量(Scalar)只是一个数字（或者说是仅有一个分量的向量）。当把一个向量加/减/乘/除一个标量，我们可以简单的把向量的每个分量分别进行该运算。

我们使用勾股定理(Pythagoras Theorem)来获取向量的长度(Length)/大小(Magnitude)。如果你把向量的x与y分量画出来，该向量会和x与y分量为边形成一个三角形。

两个向量的点乘(Dot Product)等于它们的数乘结果乘以两个向量之间夹角的余弦值。使用点乘可以很容易测试两个向量是否正交(Orthogonal)或平行（正交意味着两个向量互为直角）。点乘是通过将对应分量逐个相乘，然后再把所得积相加来计算的。点乘的结果除以两个向量的长度之积，得到的结果就是夹角的余弦值，即cosθ，使用反余弦函数，我们很快就计算出了这两个向量的夹角。点乘在计算光照的时候非常有用。

叉乘(Cross Product)只在3D空间中有定义，它需要两个不平行向量作为输入，生成一个正交于两个输入向量的第三个向量。
我们用向量来表示位置，表示颜色，甚至是纹理坐标。让我们更深入了解一下向量，它其实就是一个N×1矩阵，N表示向量分量的个数。

> 矩阵变换用于对象的平移，旋转，缩放处理。矩阵的乘法主要用来描述一元二次方程。使用矩阵进行变换的真正力量在于，根据矩阵之间的乘法，我们可以把多个变换组合到一个矩阵中。因此需要将平移的矩阵加法(3x1)变成3x4的矩阵乘法，x,y,z的3x1变成x, y, z, 1的4x1矩阵，同时为了能将平移，缩放，旋转混合计算，彼此的输入作为对方的输出，就要求顶点坐标必须同一是4x1矩阵，也就是要求这三种变换都要变成4x4的矩阵。这就是 齐次坐标 的概念，也是OpenGL使用4x4变换矩阵的原因。关于矩阵的数据基础，作者推荐可汗学院线性代数的视频:https://www.khanacademy.org/math/linear-algebra/matrix-transformations

> 齐次变换矩阵其实就是将仿射变换矩阵推广到齐次坐标系，从而将平移(加法)，缩放，旋转等变换合成到一个矩阵中；消除矩阵运算中的加减法，只留下乘法，以实现快速运算。

OpenGL没有自带任何的矩阵和向量知识，所以我们必须定义自己的数学类和函数。在教程中我们更希望抽象所有的数学细节，使用已经做好了的数学库。幸运的是，有个易于使用，专门为OpenGL量身定做的数学库，那就是[GLM](http://glm.g-truc.net/)。GLM是OpenGL Mathematics的缩写，它是一个只有头文件的库，也就是说我们只需包含对应的头文件就行了，不用链接和编译。

1. 下载GLM
git clone https://github.com/g-truc/glm

2. 在vertex shader增加 uniform mat4 transform;

3. 在源代码中修改uniform的值
``` cpp
glm::mat4 trans;
trans = glm::rotate(trans, 90.0f, glm::vec3(0.0, 0.0, 1.0));
trans = glm::scale(trans, glm::vec3(0.5, 0.5, 0.5));

GLuint transformLoc = glGetUniformLocation(ourShader.Program, "transform");
glUniformMatrix4fv(transformLoc, 1, GL_FALSE, glm::value_ptr(trans));

```
我们可以定义一个无限数量的变换，把它们组合为仅仅一个矩阵，如果愿意的话我们还可以重复使用它。

## Coordinate Systems
OpenGL希望在所有顶点着色器运行后，所有我们可见的顶点都变为标准化设备坐标(Normalized Device Coordinate, NDC)。也就是说，每个顶点的x，y，z坐标都应该在-1.0到1.0之间，超出这个坐标范围的顶点都将不可见。

Transforming coordinates to NDC and then to screen coordinates is usually accomplished in a step-by-step fashion where we transform an object's vertices to several coordinate systems before finally transforming them to screen coordinates. The advantage of transforming them to several intermediate coordinate systems is that some operations/calculations are easier in certain coordinate systems as will soon become apparent. There are a total of 5 different coordinate systems that are of importance to us:

- Local space (or Object space)
- World space
- View space (or Eye space)
- Clip space
- Screen space

To transform the coordinates in one space to the next coordinate space we'll use several transformation matrices of which the most important are the **model**, **view** and **projection** matrix. Our vertex coordinates first start in local space as local coordinates and are then further processed to world coordinates, view coordinates, clip coordinates and eventually end up as screen coordinates. The following image displays the process and shows what each transformation does:
http://learnopengl.com/img/getting-started/coordinate_systems.png

发现翻译的不怎么好，有时还要猜测对应的原文的意思，看中文和看英文速度差不多，决定还是看英文。

最后的顶点应该被赋予顶点着色器中的gl_Position且OpenGL将会自动进行透视划分和裁剪。

OpenGL存储它的所有深度信息于Z缓冲区(Z-buffer)中，也被称为深度缓冲区(Depth Buffer)

## Camera
OpenGL本身没有摄像机的概念，但我们可以通过把场景中的所有物体往相反方向移动的方式来模拟出摄像机，这样感觉就像我们在移动，而不是场景在移动。

使用键盘移动，通过键盘修改Camera的观看位置，也就是调整场景的矩阵

使用鼠标移动， 
欧拉角(Euler Angle)是表示3D空间中可以表示任何旋转的三个值，由莱昂哈德·欧拉在18世纪提出。有三种欧拉角：俯仰角(Pitch)、偏航角(Yaw)和滚转角(Roll)，


# 光照(Lighting)

## Colors
我们在现实生活中看到某一物体的颜色并不是这个物体的真实颜色，而是它所反射(Reflected)的颜色。换句话说，那些不能被物体吸收(Absorb)的颜色(被反射的颜色)就是我们能够感知到的物体的颜色。

当我们把光源的颜色与物体的颜色相乘，所得到的就是这个物体所反射该光源的颜色(也就是我们感知到的颜色)。

## Basic Lighting
Lighting in the real world is extremely complicated and depends on way too many factors, something we can't afford to calculate on the limited processing power we have. Lighting in OpenGL is therefore based on approximations of reality using simplified models that are much easier to process and look relatively similar. 
These lighting models are based on the physics of light as we understand it. One of those models is called the **Phong lighting model**. The major building blocks of the Phong model consist of 3 components: ambient, diffuse and specular lighting. 

- Ambient lighting: even when it is dark there is usually still some light somewhere in the world (the moon, a distant light) so objects are almost never completely dark. To simulate this we use an ambient lighting constant that always gives the object some color.
- Diffuse lighting: simulates the directional impact a light object has on an object. This is the most visually significant component of the lighting model. The more a part of an object faces the light source, the brighter it becomes.
- Specular lighting: simulates the bright spot of a light that appears on shiny objects. Specular highlights are often more inclined to the color of the light than the color of the object.

## Materials
如果我们想要在OpenGL中模拟多种类型的物体，我们必须为每个物体分别定义材质(Material)属性。

描述物体的时候，我们可以使用3种光照元素：环境光照(Ambient Lighting)、漫反射光照(Diffuse Lighting)、镜面光照(Specular Lighting)定义一个材质颜色。通过为每个元素指定一个颜色，我们已经对物体的颜色输出有了精密的控制。

为一个物体赋予一款正确的材质是非常困难的，这需要大量实验和丰富的经验，所以由于错误的设置材质而毁了物体的画面质量是件经常发生的事。

## Lighting maps

diffuse和specular贴图。它们允许你对一个物体的diffuse（而对于简洁的ambient成分来说，它们几乎总是是一样的）和specular成分能够有更精确的影响。
我们希望通过某种方式对每个原始像素独立设置diffuse颜色。有可以让我们基于物体原始像素的位置来获取颜色值的系统吗

它基本就是一个纹理。我们其实是使用同一个潜在原则下的不同名称：使用一张图片覆盖住物体，以便我们为每个原始像素索引独立颜色值。在光照场景中，通过纹理来呈现一个物体的diffuse颜色，这个做法被称做漫反射贴图(Diffuse texture)(因为3D建模师就是这么称呼这个做法的)。

使用Photoshop或Gimp之类的工具，通过将图片进行裁剪，将某部分调整成黑白图样，并调整亮度/对比度的做法，可以非常容易将一个diffuse纹理贴图处理为specular贴图。

## Light casters
一个光源把光投射到物体上，叫做投光。我们首先讨论定向光(directional light)，接着是作为之前学到知识的扩展的点光(point light)，最后我们讨论聚光(Spotlight)。

当一个光源很远的时候，来自光源的每条光线接近于平行。当一个光源被设置为无限远时，它被称为定向光(Directional Light)，因为所有的光线都有着同一个方向；它会独立于光源的位置。

点光(Point Light)是一个在时间里有位置的光源，它向所有方向发光，光线随距离增加逐渐变暗。想象灯泡和火炬作为投光物，它们可以扮演点光的角色。

随着光线穿越距离的变远使得亮度也相应地减少的现象，通常称之为衰减(Attenuation)。

聚光(Spotlight)。聚光是一种位于环境中某处的光源，它不是向所有方向照射，而是只朝某个方向照射。结果是只有一个聚光照射方向的确定半径内的物体才会被照亮，其他的都保持黑暗。聚光的好例子是路灯或手电筒。
一个真实的聚光的光会在它的边界处平滑减弱的。

## Multiple lights



# Model Loading
## Assimp
那些3D建模工具，可以让美工们构建一些复杂的形状，并将贴图应用到形状上去，即纹理映射。然后，在导出模型文件时，建模工具会自己生成所有的顶点坐标、顶点法线和纹理坐标。这样，美工们可以不用了解大量的图像技术细节，就能有大量的工具集去随心地构建高品质的模型。所有的技术细节内容都隐藏在里导出的模型文件里。而我们，这些图形开发者，就必须得去关注这些技术细节了。因此，我们的工作就是去解析这些导出的模型文件，并将其中的模型数据存储为OpenGL能够使用的数据。

一个常见的问题是，导出的模型文件通常有几十种格式，不同的工具会根据不同的文件协议把模型数据导出到不同格式的模型文件中。 比如 Wavefront的.obj文件格式，Collada文件格式

[Assimp](http://assimp.sourceforge.net/index.html)，全称为Open Asset Import Library。Assimp可以导入几十种不同格式的模型文件（同样也可以导出部分模型格式）。只要Assimp加载完了模型文件，我们就可以从Assimp上获取所有我们需要的模型数据。Assimp把不同的模型文件都转换为一个统一的数据结构，所有无论我们导入何种格式的模型文件，都可以用同一个方式去访问我们需要的模型数据。

当导入一个模型文件时，即Assimp加载一整个包含所有模型和场景数据的模型文件到一个scene对象时，Assimp会为这个模型文件中的所有场景节点、模型节点都生成一个具有对应关系的数据结构，且将这些场景中的各种元素与模型数据对应起来。

所以我们要做的第一件事，就是加载一个模型文件为scene对象，然后获取每个节点对应的Mesh对象（我们需要递归搜索每个节点的子节点来获取所有的节点），并处理每个Mesh对象对应的顶点数据、索引以及它的材质属性。最终我们得到一个只包含我们需要的数据的Mesh集合。

$ git clone git://github.com/assimp/assimp.git assimp

## Mesh
一个网格(Mesh)代表一个可绘制实体。一个网格应该至少需要一组顶点，每个顶点包含一个位置向量，一个法线向量，一个纹理坐标向量。一个网格也应该包含一个索引绘制用的索引，以纹理（diffuse/specular map）形式表现的材质数据。

## Model

# Advanced OpenGL
## Depth testing
细致地讨论被深度缓冲(或z-buffer)所存储的深度值以及它是如何确定一个片段是否被其他片段遮挡。
当深度测试启用的时候， OpenGL 测试深度缓冲区内的深度值。OpenGL 执行深度测试的时候，如果此测试通过，深度缓冲内的值将被设为新的深度值。如果深度测试失败，则丢弃该片段。
深度测试在片段着色器运行之后(并且模板测试运行之后)在屏幕空间中执行的。

两个平面或三角形如此紧密相互平行深度缓冲区不具有足够的精度以至于无法得到哪一个靠前。结果是，这两个形状似乎不断切换顺序导致怪异的问题。这被称为 **深度冲突(Z-fighting)** ，因为它看上去像形状争夺顶靠前的位置。

## Stencil testing
当片段着色器处理完片段之后，模板测试(Stencil Test) 就开始执行了，和深度测试一样，它能丢弃一些片段。仍然保留下来的片段进入深度测试阶段，深度测试可能丢弃更多。模板测试基于另一个缓冲，这个缓冲叫做模板缓冲(Stencil Buffer)，我们被允许在渲染时更新它来获取有意思的效果。

除了物体边框(物体边框算法在一些游戏中显示备选物体时非常常用)以外，模板测试还有很多其他的应用目的，比如在后视镜中绘制纹理，这样它会很好的适合镜子的形状，比如使用一种叫做shadow volumes的模板缓冲技术渲染实时阴影。

## Blending
在OpenGL中，物体透明技术通常被叫做混合(Blending)。透明是物体（或物体的一部分）非纯色而是混合色，这种颜色来自于不同浓度的自身颜色和它后面的物体颜色。一个物体的透明度，被定义为它的颜色的alpha值。alpha颜色值是一个颜色向量的第四个元素
为了渲染出不同的透明度级别，我们需要开启混合(Blending)。像大多数OpenGL的功能一样，我们可以开启GL_BLEND来启用混合(Blending)功能：

glEnable(GL_BLEND);
glBlendFunc(GLenum sfactor, GLenum dfactor)接收两个参数，来设置源（source）和目标（destination）因子。

要让混合在多物体上有效，我们必须先绘制最远的物体，最后绘制最近的物体。普通的无混合物体仍然可以使用深度缓冲正常绘制，所以不必给它们排序。我们一定要保证它们在透明物体前绘制好。当无透明度物体和透明物体一起绘制的时候，通常要遵循以下原则： 先绘制所有不透明物体。 为所有透明物体排序。 按顺序绘制透明物体。 一种排序透明物体的方式是，获取一个物体到观察者透视图的距离。这可以通过获取摄像机的位置向量和物体的位置向量来得到。

## Face culling
OpenGL允许检查所有正面朝向（Front facing）观察者的面，并渲染它们，而丢弃所有背面朝向（Back facing）的面，这样就节约了我们很多片段着色器的命令（它们很昂贵！）。我们必须告诉OpenGL我们使用的哪个面是正面，哪个面是反面。OpenGL使用一种聪明的手段解决这个问题——分析顶点数据的连接顺序（Winding order）。

默认情况下，逆时针的顶点连接顺序被定义为三角形的正面。把所有三角的顶点都定义为逆时针是一个很好的习惯。
开启OpenGL的GL_CULL_FACE选项就能开启面剔除功能： glEnable(GL_CULL_FACE);

## Framebuffers
通过帧缓冲可以将你的场景渲染到一个不同的帧缓冲中，可以使我们能够在场景中创建镜子这样的效果，或者做出一些炫酷的特效。
glGenFramebuffers的函数来创建一个帧缓冲对象（简称FBO）：

GLuint fbo;
glGenFramebuffers(1, &fbo);
glBindFramebuffer(GL_FRAMEBUFFER, fbo);

好处就是我们现在可以自由的获取已经渲染场景中的任何像素，然后把它当作一个纹理图像了，我们可以在片段着色器中创建一些有意思的效果。所有这些有意思的效果统称为后处理特效。Post-processing

Kernel effects ??? 

## Cubemaps
本教程中我们讨论的纹理类型是将多个纹理组合起来映射到一个单一纹理，它就是立方体贴图(Cube Map)。
因为恰巧使用立方体贴图可以简单的实现很多有意思的技术。其中之一便是著名的天空盒(Skybox)。天空盒(Skybox)是一个包裹整个场景的立方体，它由6个图像构成一个环绕的环境，给玩家一种他所在的场景比实际的要大得多的幻觉。比如有些在视频游戏中使用的天空盒的图像是群山、白云或者满天繁星。http://www.custommapmakers.org/skyboxes.php 提供了大量的skybox图片。

我们现在有了一个把整个环境映射到为一个单独纹理的对象，我们利用这个信息能做的不仅是天空盒。使用带有场景环境的立方体贴图，我们还可以让物体有一个反射或折射属性。像这样使用了环境立方体贴图的技术叫做环境贴图技术，其中最重要的两个是反射(reflection)和折射(refraction)。

凡是是一个物体（或物体的某部分）反射(Reflect)他周围的环境的属性，比如物体的颜色多少有些等于它周围的环境，这要基于观察者的角度。例如一个镜子是一个反射物体：它会基于观察者的角度泛着它周围的环境。????

折射是光线通过特定材质对光线方向的改变。折射遵守斯涅尔定律

## Advanced Data
当从文件加载顶点数据时你通常获取一个位置数组，一个法线数组和一个纹理坐标数组。需要花点力气才能把它们结合为交叉数据。使用glBufferSubData可以简单的实现分批处理方式。
当你的缓冲被数据填充以后，你可能打算让其他缓冲能分享这些数据或者打算把缓冲的内容复制到另一个缓冲里。glCopyBufferSubData函数让我们能够相对容易地把一个缓冲的数据复制到另一个缓冲里

## Geometry Shader
在顶点和片段着色器之间有一个可选的着色器，叫做几何着色器(Geometry Shader)。几何着色器以一个或多个表示为一个单独基本图形（primitive）的顶点作为输入，比如可以是一个点或者三角形。几何着色器在将这些顶点发送到下一个着色阶段之前，可以将这些顶点转变为它认为合适的内容。

## Instancing
实例化(Instancing)是一种只调用一次渲染函数却能绘制出很多物体的技术，它节省渲染物体时从CPU到GPU的通信时间，而且只需做一次即可。要使用实例化渲染，我们必须将glDrawArrays和glDrawElements各自改为glDrawArraysInstanced和glDrawElementsInstanced。这些用于实例化的函数版本需要设置一个额外的参数，叫做实例数量(Instance Count)，它设置我们打算渲染实例的数量。这样我们就只需要把所有需要的数据发送给GPU一次就行了，然后告诉GPU它该如何使用一个函数来绘制所有这些实例。

想象一下，在一个场景中有一个很大的行星，行星周围有一圈小行星带。这样一个小行星大可能包含成千上万的石块，对于大多数显卡来说几乎是难以完成的渲染任务。这个场景对于实例渲染来说却不再话下，由于所有小行星可以使用一个模型来表示。每个小行星使用一个变换矩阵就是一个经过少量变化的独一无二的小行星了。

不实例渲染，我们可以流畅渲染1000到1500个小行星。而使用了实例渲染，我们可以设置为100000，每个模型由576个顶点，这几乎有5千7百万个顶点，而且帧率没有丝毫下降！ (接近100倍的性能提升)

在合适的条件下，实例渲染对于你的显卡来说和普通渲染有很大不同。出于这个理由，实例渲染通常用来渲染草、草丛、粒子以及像这样的场景，基本上来讲只要场景中有很多重复物体，使用实例渲染都会获得好处。

## Anti Aliasing
锯齿边(Jagged Edge)出现的原因是由顶点数据像素化之后成为片段的方式所引起的。有很多技术能够减少走样，产生更平滑的边缘，这些技术叫做抗锯齿技术(Anti-aliasing，也被称为反走样技术)。
超级采样抗锯齿技术(Super Sample Anti-aliasing, SSAA)，它暂时使用一个更高的解析度（以超级采样方式）来渲染场景，当视频输出在帧缓冲中被更新时，解析度便降回原来的普通解析度。这个额外的解析度被用来防止锯齿边。虽然它确实为我们提供了一种解决走样问题的方案，但却由于必须绘制比平时更多的片段而降低了性能。所以这个技术只流行了一段时间。
多采样抗锯齿(Multisample Anti-aliasing)或叫MSAA，虽然它借用了SSAA的理念，但却以更加高效的方式实现了它。这节教程我们会展开讨论这个MSAA技术，它是OpenGL内建的。

如果我们打算在OpenGL中使用MSAA，那么我们必须使用一个可以为每个像素储存一个以上的颜色值的颜色缓冲(因为多采样需要我们为每个采样点储存一个颜色)。我们这就需要一个新的缓冲类型，它可以储存要求数量的多重采样样本，它叫做多样本缓冲(Multisample Buffer)。

当默认帧缓冲有了多采样缓冲附件的时候，我们所要做的全部就是调用glEnable(GL_MULTISAMPLE)开启多采样。因为实际的多采样算法在OpenGL驱动光栅化里已经实现了。

可以直接把一个多采样纹理图像传递到着色器中，以取代必须先还原的方式。GLSL给我们一个选项来为每个子样本进行纹理图像采样，所以我们可以创建自己的抗锯齿算法，在比较大的图形应用中，通常这么做。为获取每个子样本的颜色值，你必须将纹理uniform采样器定义为sampler2DMS，而不是使用sampler2D。

# Advanced Lighting
Phong光照很棒，而且性能较高，但是它的镜面反射在某些条件下会失效，特别是当发光值属性低的时候，对应一个非常大的粗糙的镜面区域。

1977年James F. Blinn引入了Blinn-Phong着色，它扩展了我们目前所使用的Phong着色。Blinn-Phong模型很大程度上和Phong是相似的，不过它稍微改进了Phong模型，使之能够克服我们所讨论到的问题。它放弃使用反射向量，而是基于我们现在所说的一个叫做半程向量（halfway vector）的向量，这是个单位向量，它在视线方向和光线方向的中间。半程向量和表面法线向量越接近，镜面反射成份就越大。

Blinn-Phong着色模型也正是早期OpenGL fixed function pipeline 所使用的着色模型。

## Gamma Correction
大多数监视器是阴极射线管显示器（CRT）。这些监视器有一个物理特性就是两倍的输入电压产生的不是两倍的亮度。输入电压产生约为输入电压的2.2次幂的亮度，这叫做监视器Gamma。
人类所感知的亮度恰好和CRT所显示出来相似的指数关系非常匹配。
Gamma校正(Gamma Correction)的思路是在最终的颜色输出上应用监视器Gamma的倒数。

## Shadow Mapping
阴影是光线被阻挡的结果；当一个光源的光线由于其他物体的阻挡不能够达到一个物体的表面的时候，那么这个物体就在阴影中了。阴影能够使场景看起来真实得多，并且可以让观察者获得物体之间的空间位置关系。
当前实时渲染领域还没找到一种完美的阴影算法。目前有几种近似阴影技术，但它们都有自己的弱点和不足。

视频游戏中较多使用的一种技术是阴影贴图（shadow mapping），效果不错，而且相对容易实现。阴影贴图并不难以理解，性能也不会太低，而且非常容易扩展成更高级的算法（比如 Omnidirectional Shadow Maps和 Cascaded Shadow Maps）。

## Normal Mapping
我们的场景中已经充满了多边形物体，其中每个都可能由成百上千平坦的三角形组成。我们以向三角形上附加纹理的方式来增加额外细节，提升真实感，隐藏多边形几何体是由无数三角形组成的事实。纹理确有助益，然而当你近看它们时，这个事实便隐藏不住了。现实中的物体表面并非是平坦的，而是表现出无数（凹凸不平的）细节。

每个fragment使用了自己的法线，我们就可以让光照相信一个表面由很多微小的（垂直于法线向量的）平面所组成，物体表面的细节将会得到极大提升。这种每个fragment使用各自的法线，替代一个面上所有fragment使用同一个法线的技术叫做法线贴图（normal mapping）或凹凸贴图（bump mapping）。

使用法线贴图也是一种提升你的场景的表现的重要方式。在使用法线贴图之前你不得不使用相当多的顶点才能表现出一个更精细的网格，但使用了法线贴图我们可以使用更少的顶点表现出同样丰富的细节。高精度网格和使用法线贴图的低精度网格几乎区分不出来。所以法线贴图不仅看起来漂亮，它也是一个将高精度多边形转换为低精度多边形而不失细节的重要工具。

## Parallax Mapping
视差贴图(Parallax Mapping)技术和法线贴图差不多，但它有着不同的原则。和法线贴图一样视差贴图能够极大提升表面细节，使之具有深度感。它也是利用了视错觉，然而对深度有着更好的表达，与法线贴图一起用能够产生难以置信的效果。
视差贴图背后的思想是修改纹理坐标使一个fragment的表面看起来比实际的更高或者更低。

## HDR
HDR(High Dynamic Range, 高动态范围)。有了HDR，亮的东西可以变得非常亮，暗的东西可以变得非常暗，而且充满细节。

## Bloom
明亮的光源和区域经常很难向观察者表达出来，因为监视器的亮度范围是有限的。一种区分明亮光源的方式是使它们在监视器上发出光芒，光源的的光芒向四周发散。这样观察者就会产生光源或亮区的确是强光区。光晕效果可以使用一个后处理特效泛光来实现。泛光使所有明亮区域产生光晕效果。

## Deferred Shading
我们现在一直使用的光照方式叫做正向渲染(Forward Rendering)或者正向着色法(Forward Shading)，它是我们渲染物体的一种非常直接的方式，在场景中我们根据所有光源照亮一个物体，之后再渲染下一个物体，以此类推。
延迟着色法(Deferred Shading)，或者说是延迟渲染(Deferred Rendering) 基于我们延迟(Defer)或推迟(Postpone)大部分计算量非常大的渲染(像是光照)到后期进行处理的想法。它包含两个处理阶段(Pass)：在第一个几何处理阶段(Geometry Pass)中，我们先渲染场景一次，之后获取对象的各种几何信息，并储存在一系列叫做G缓冲(G-buffer)的纹理中：位置向量(Position Vector)、颜色向量(Color Vector)、法向量(Normal Vector)和/或镜面值(Specular Value)。场景中这些储存在G缓冲中的几何信息将会在之后用来做(更复杂的)光照计算。

我们会在第二个光照处理阶段(Lighting Pass)中使用G缓冲内的纹理数据。在光照处理阶段中，我们渲染一个屏幕大小的方形，并使用G缓冲中的几何数据对每一个片段计算场景的光照；在每个像素中我们都会对G缓冲进行迭代。我们对于渲染过程进行解耦，将它高级的片段处理挪到后期进行，而不是直接将每个对象从顶点着色器带到片段着色器。

G缓冲(G-buffer)是对所有用来储存光照相关的数据，并在最后的光照处理阶段中使用的所有纹理的总称。


## SSAO
在2007年，Crytek公司发布了一款叫做屏幕空间环境光遮蔽(Screen-Space Ambient Occlusion, SSAO)的技术，并用在了他们的看家作孤岛危机上。这一技术使用了屏幕空间场景的深度而不是真实的几何体数据来确定遮蔽量。这一做法相对于真正的环境光遮蔽不但速度快，而且还能获得很好的效果，使得它成为近似实时环境光遮蔽的标准。

# In Practice














