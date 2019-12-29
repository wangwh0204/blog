title: Stanford CS148 - Introduction to Computer Graphics and Imaging
date: 2016-06-21
updated: 2016-09-19
categories:
- [technology]
tags:
- Stanford
- Computer Graphics
- OpenGL
---

CS148一年有2次课程，在每年的Summer(6.21 ~ 08.12)和Autumn(09.23 ~ 12.08)开课。本文基于 Summer 2016 的 课件 所做的笔记 ... TBD <!--more-->
TBD, 有机会准备再学习一遍CS148

> 2016.09.23 CS148 Fall 2016课程开始, 从2016.09.23 ~ 2016.12.08， 主题上有一些不同

今天(2016-06-28)碰巧看到[Stanford CS148 Summer 2016](https://mdzahidh.github.io/cs148/)(通过http://cs148.stanford.edu/重定向到这里)的课程正在进行，同时刚好我正想系统的学习Computer Graphics(从2016.05.23开始，正看到<<Computer Graphics with opengl>>中文版第6章，本书将理论和OpenGL实践结合。时间紧迫，必须看中文的情况下可以阅读本书。去年看过OpenGL Programming Guide，但看不懂)， 所以决定跟着课程安排学习这门课. 也由此得到一个启发，时间容许的话，可以跟随[Stanford Course Timetables](http://cs.stanford.edu/academics/courses)的安排来同步学习感兴趣的课程.( **感激互联网的伟大和stanford的开放** ，如果课程能视频直播就更好了)

整个课程持续差不多2个月左右时间(2016.06.21 ~ 2016.08.12)，共计8周，每周有2节课，每节课2个小时时间，每上完一节课，会在网站公布Slides(课件), Reading Assignment(阅读任务)以及Homework（课后作业). 参考书有三本：

目标： 渲染一副计算机生成的image

**Prerequisites: MATH51, CS107**
**Reading: **
- Fundamentals of Computer Graphics, 3rd Edition
- OpenGL Programming Guide 8th
**Description: **
What do the following technologies have in common: robots that can navigate space and perform duties, search engines that can index billions of images and videos, algorithms that can diagnose medical images for diseases, or smart cars that can see and drive safely? Lying in the heart of these modern AI applications are computer vision technologies that can perceive, understand and reconstruct the complex visual world.  This course is designed to open the doors for students who are interested in learning about the fundamental principles and important applications of computer vision. 

因为时间的关系，课程对应的讲义只列出了大纲和关键的知识点，要深入的理解需要查阅资料，比如wiki和参考书；同时花时间编写代码实践。在课程完成后，需要进一步的实践和通读参考书，因为参考书内容更加完整和系统，通读有助于完善，巩固知识，加深理解。

# 01 [Introduction](https://mdzahidh.github.io/cs148/assets/slides/01-Introduction.pdf)
本节课程主要简述图形学的几个应用场景及对应的stanford课程；也介绍了本课程CS148 summer 2016的基本信息.

为什么要学习Computer Graphics？ 学以致用。Computer Graphics技术主要应用到如下行业领域：
- Video Games
游戏行业市场规模已经超过电影行业，接近1000亿美金。http://www.gamelook.com.cn/2015/06/218771
范例 ： 
芯片公司 : Geforece(Nvidia), HD7970(AMD), PowerVR(Imagination), Adreno(Qualcomm)
主机设备 : PS4(Sony)，Switch(Nintendo), XBox(Mirosoft)
主机游戏 : Uncharted(Naughty Dog)，HALO(Mirosoft), Call Of Duty(ActionVision), GTA(Rockstar)
PC单机  : Civilization(Firaxis，立意之高，无与伦比)，Doom(id), StarCraft(Blizzard), Counter-Strike(Valve), Minecraft(Mojang)
网络游戏 : World of Warcraft(Blizzard), LOL(Riot)
手机游戏 : Angry Birds(Rovio), COC(SuperCell)

课程 ：
CS148  - Introduction to Computer Graphics
CS248  - Interactive Computer Graphics
CS205a - Math for Robotics, Vision and Graphics

- Movies
包括影视特效(VFX),3D动画， 奥斯卡专门设立了技术
stanford 的 [Ron Fedkiw ](http://physbam.stanford.edu/~fedkiw/)(主页有大量的视频和论文) awarded an Academy Award from The Academy of Motion Picture Arts and Sciences (twice: 2008 and 2015)
[Pat Hanrahan](http://graphics.stanford.edu/~hanrahan/)更是获得了3次奥斯卡科技成果奖(1993, 2004, 2014)，最近是因为这本书:&lt;&lt;Physically Based Rendering&gt;&gt;, Stanford’s CS348B 课程内容就是基于这本书。

范例 ： ILM, RenderMan(Pixar), Weta, Dreamworks, AfterEffect, Houdini, 
课程 ：
CS348b - Image Synthesis Techniques
CME306 - Numerical Methods, Level Sets etc.

- CADs, Animators, Modelers
范例 ： AutoCAD(Autodesk), Maya(Autodesk), 3DMax(Autodesk), Blender(Blender Foundation), CINMEA4D,
课程 ：
CS268  - Geometric Algorithm
CS348A - Geometric Modeling
CS368  - Advanced Geometric Algorithm
CS468  - Differential Geometry
CS228  - Probabilistic Graphical Model
CS229  - Machine Learning
CS231N - Convolutional Neural Networks for Visual Recognition

- 2D Image Processing
范例 ： Photoshop(Adobe), GIMP(The GIMP Team)
课程 ：
CS178  - Digital Photography
CS131  - Intro. To Computer Vision
CS231  - Computer Vision II
CS478  - Computational Photography

- Visualization
CS448b - Visualization
EE169  - Intro to Bioimaging

- Simulators
范例 : da Vinci surgical robot, Boeing 737 Simulator
课程 :
CS277  - Experimental Haptics
CS327  - Advanced Robotic Manipulation

- Virtual and Augmented Reality
范例 ： Oculus Rift(Oculus), HTC Vive(HTC, Valve), Hololens(Microsoft)
课程 ：
CS211  - Content Creation in VR
EE267  - Virtual Reality
CS377M - HCI in Mixed and AR

- User Interfaces
范例 ： Windows(Microsoft), Android(Google), iOS(Apple)
课程 ：
CS247  - HCI Design Studio

# 02 [Light and Colors](https://mdzahidh.github.io/cs148/assets/slides/02-Light%20and%20Colors.pdf)
本节课程主要简述光和颜色的基本概念和物理特性，主要阅读FCG的第20和21章，重点要理解渲染方程：BRDF
- Light

[What is light](http://en.wikipedia.org/wiki/Electromagnetic_radiation)

C = 299,799,458 m/s (In Vacuum)
Refraction([折射](https://zh.wikipedia.org/wiki/%E6%8A%98%E5%B0%84)) & total internal reflection([反射](https://zh.wikipedia.org/wiki/%E5%8F%8D%E5%B0%84_(%E7%89%A9%E7%90%86%E5%AD%A6)))
Wave Particle Duality([波粒二象性](https://zh.wikipedia.org/wiki/%E6%B3%A2%E7%B2%92%E4%BA%8C%E8%B1%A1%E6%80%A7))

Photon([光子](https://zh.wikipedia.org/wiki/%E5%85%89%E5%AD%90)) : A quantum of light that has a position, a direction of propagation, and a wavelength.

- Colors
Color Space : RGB, XYZ, Munsell, L*a*b, HSV

## Reading Assignment 1
阅读FCG第20章(Light)以及第21章(Color)，然后回答下面的问题：
1. What is the difference between radiance and irradiance?
2. Explain what a BRDF is and why it is important for graphics.
3. In the mathematical definition of luminance, why are the bounds of the integral 380nm to 800nm?
4. What is a steradian?  Draw a picture if it helps.
5. A [FILL_THIS_BLANK] describes how much energy is available at each [FILL_THIS_BLANK] lambda.
6. Name 3 types of cones.
7. CIE has defined three primaries to be monochromatic light sources - what are those?
8. How long did it take for you to (a) read the material and (b) answer these questions? 


# 03 [Rasterization](https://mdzahidh.github.io/cs148/assets/slides/03-Rasterization.pdf)
本章主要介绍Rendering(渲染)以及Rasterization(光栅化)的概念，基本的绘制直线，圆的Rasterization算法：Bresenham's Algorithm, Midpoint Algorithm

Render(渲染) : The process of generating an image from a description of a scene by means of a computer program. 
详细的看一下: https://en.wikipedia.org/wiki/Rendering_(computer_graphics)，以下内容引用自上面的wiki:
> A scene file contains objects in a strictly defined language or data structure; it would contain geometry, viewpoint, texture, lighting, and shading information as a description of the virtual scene. 
> Shading – how the color and brightness of a surface varies with lighting
> Texture-mapping – a method of applying detail to surfaces

> Therefore, a few loose families of more-efficient light transport modelling techniques have emerged:
> - rasterization, including scanline rendering, geometrically projects objects in the scene to an image plane, without advanced optical effects;
> - ray casting considers the scene as observed from a specific point of view, calculating the observed image based only on geometry and very basic optical laws of reflection intensity, and perhaps using Monte Carlo techniques to reduce artifacts;
> - ray tracing is similar to ray casting, but employs more advanced optical simulation, and usually uses Monte Carlo techniques to obtain more realistic results at a speed that is often orders of magnitude slower.

Two Way to Render an Image : 
- Rasterization(光栅化)
- Raytracing(光线跟踪)

> Ray tracing aims to simulate the natural flow of light, interpreted as particles. Often, ray tracing methods are utilized to approximate the solution to the rendering equation by applying Monte Carlo methods to it. 

Rasterize : To convert vector data to raster-pixel or dot-format.

[Bresenham's Algorithm (1967)](https://en.wikipedia.org/wiki/Bresenham%27s_line_algorithm)，将Wiki和PPT结合起来
> 非常简单的绘制直线算法，还有一个[Xiaolin Wu's line algorithm](https://en.wikipedia.org/wiki/Xiaolin_Wu%27s_line_algorithm), a similarly fast method of drawing lines with antialiasing
Equation of a line : y = mx + b

To derive Bresenham's algorithm, two steps must be taken. The first step is transforming the equation of a line from the typical slope-intercept form into something different; and then using this new equation for a line to draw a line based on the idea of accumulation of error.


Rasterizing Circle : Midpoint Algorithm

Filling Triangles, two methods for filling:
- Check if each pixel in bounding box is inside the triangle(Parallelizable)
- Rasterize border; sweep from left to right(Less Computation)

Barycentric Coordinates(重心坐标)


## Reading Assignment 2
Basic Raster Graphics Algorithms for Drawing 2D Primitives


# 04 [Coordinates & Transformation](https://mdzahidh.github.io/cs148/assets/slides/04-Transformation.pdf)
Transformation(变换)本质是[矩阵](https://zh.wikipedia.org/wiki/%E7%9F%A9%E9%98%B5)运算，主要有三种变换形式：translation(平移，矩阵加法), scaling(缩放,矩阵乘法), rotation(旋转，矩阵乘法)
**旋转的矩阵怎么推导的？**
- What
Just functions acting on points
- Why
1. Viewing:
    - Convert between coorinates systems
    - Virtual camera, e.g. perspective projections
[3D投影](https://en.wikipedia.org/wiki/3D_projection)是一种映射3D点到2D平面的方法。分为Orthographic projection(正投影)和[Perspective projection](https://en.wikipedia.org/wiki/Perspective_(graphical))(透视投影): When the human eye views a scene, objects in the distance appear smaller than objects close by - this is known as perspective. While orthographic projection ignores this effect to allow accurate measurements, perspective projection shows distant objects as smaller to provide additional realism.

2. Modeling:
    - Create objects in a convenient orientation
    - Use multiple instances of a given shape
    - Kinematics - characters/robots
[Linear Transformation](https://en.wikipedia.org/wiki/Linear_map)

[Homogenous Coordinates](https://en.wikipedia.org/wiki/Homogeneous_coordinates)(齐次坐标) ： 
Given a point (x, y) on the Euclidean plane, for any non-zero real number Z, the triple (xZ, yZ, Z) is called a set of homogeneous coordinates for the point. 

 Homogeneous coordinates have a range of applications, including computer graphics and 3D computer vision, where they allow [affine transformations](https://en.wikipedia.org/wiki/Affine_transformation) and, in general, [projective transformations](https://en.wikipedia.org/wiki/Homography) to be easily represented by a matrix.
 
 Homogeneous coordinates are ubiquitous in computer graphics because they allow common vector operations such as translation, rotation, scaling and perspective projection to be represented as a matrix by which the vector is multiplied
 
By the chain rule, any sequence of such operations can be multiplied out into a single matrix, allowing simple and efficient processing. 
 
By contrast, using Cartesian coordinates, translations and perspective projection cannot be expressed as matrix multiplications, though other operations can.
 
许多图形应用涉及到几何变换，主要包括平移、旋转、缩放。以矩阵表达式来计算这些变换时，平移是矩阵相加，旋转和缩放则是矩阵相乘，综合起来可以表示为p' = m1*p+ m2（注：因为习惯的原因，实际使用时一般使用变化矩阵左乘向量）(m1旋转缩放矩阵， m2为平移矩阵， p为原向量 ，p'为变换后的向量)。引入齐次坐标的目的主要是合并矩阵运算中的乘法和加法，表示为p' = p*M的形式。即它提供了用矩阵运算把二维、三维甚至高维空间中的一个点集从一个坐标系变换到另一个坐标系的有效方法。
其次，它可以表示无穷远的点。n+1维的齐次坐标中如果h=0，实际上就表示了n维空间的一个无穷远点。https://oncemore2020.github.io/blog/homogeneous/

仿射变换（Affine Transformation) ，又称仿射映射，是指在几何中，一个向量空间进行一次线性变换并接上一个平移，变换为另一个向量空间。

齐次变换矩阵其实就是将仿射变换矩阵推广到齐次坐标系，从而将平移，缩放，旋转等变换合成到一个矩阵中；消除矩阵运算中的加减法，只留下乘法，以实现快速运算。

Hierarchical Modeling (层次建模)

Camera and Projection Matrices
- The world is in 3D
- But our Screen is in 2D
- Imagine our screen is a camera looking out into the world
- Tasks
1. Convert 3D world Coordinates to Camera Coordinates (虚拟camera，使用透视投影)
2. Project the Camera Coordinate on 2D screen

OpenGL Projection Matrix: 参见下面的推导过程：
http://www.songho.ca/opengl/gl_projectionmatrix.html
http://www.scratchapixel.com/lessons/3d-basic-rendering/perspective-and-orthographic-projection-matrix/projection-matrix-introduction

# 05 [OpenGL](https://mdzahidh.github.io/cs148/assets/slides/05-OpenGL.pdf)
SIMD : Single Instruction Multiple Data

NDC = M(proj) x M(eye) x M(model) x V

OpenGL 1.x Pipeline : 
Display List(Stores subrouties) -> Evaluator(Construct geometric objects) -> Pre-Vertex Operations(Change geometry) / Primitive Assembly(Store primitive shapes) -> Rasterization -> Pre-Fragment Operations(Modify and combine per-pixel information)  -> Frame Buffer(Prepare image to be displayed)

Fragment : The data necessary to generate a single pixel's worth of a primitive.

Vertex Lighting
[Normal](https://en.wikipedia.org/wiki/Normal_(geometry)) : A vector perpendicular to a surface; constant over a plane
- Specifying Normals
- Diffuse Term
- Specular Term
- Ambient light
Color = (DiffuseFactor x DiffuseColor) + ([DiffuseFactor > 0] x SpecularFactor x SpecularColor) + AmbientColor

Vertex Lighting types : Directional Light Source, Point Light Source, Spot Light Source, Ambient Light Source

Next Generation APIs: Lower Driver/CPU Overhead, Support multi-core CPUs
- Vulkan(Nextgen OpenGL)
随着2016年02月16日Vulkan 1.0 规范发布，Opengl以及Opengl ES可能还有几年的生命周期，未来将主要基于Vulkan API。
- DirectX 12(Microsoft)
- Metal(Apple)

本节课程介绍[OpenGL](https://www.opengl.org/)，为了方便讲解和演示代码，采用的是OpenGL 1.x API(固定管线)和GLUT API(实际使用的是[freeglut](http://freeglut.sourceforge.net/))，在实际的开发过程中，目前都是基于OpenGL 3.3+(可编程管线)以及[GLFW](http://www.glfw.org/)；而且对OpenGL的rendering pipeline，lighting model等知识也仅仅提及而以。本节课的内容没有提供具体的OpenGL实践，因此要真正理解和应用OpenGL，需要其他学习资料，根据上节课程的推荐，学习http://learnopengl.com/，学习和实践完Learn OpenGL的前2部分(Getting started, Lighting)就可以学习下一节，在CS148的学习结束后，可以继续学习Learn OpenGL后续的章节，我的学习笔记[在此](http://wangwh0204.github.io/2016/09/28/learnopengl/)

# 06 [Texture](https://mdzahidh.github.io/cs148/assets/slides/06-Textures.pdf)
[Texture Mapping](https://en.wikipedia.org/wiki/Texture_mapping) is a method for defining high frequency detail, surface texture, or color information on a computer-generated graphic or 3D model. Its application to 3D graphics was pioneered by Edwin Catmull in 1974.
- A technique for specifying variationsin surface reflectance properties of an object
- Store the reflectance as an image and "map" it onto the object
- The stored image is called a texture map
- A texture map is defied in its own 2D coordinate system, parameterized by (u,v)
- Establish a correspondence by assigning (u,v) coordinates to triangle vertices
- Then, for each pixel inside a triangle, calculate the pixel's (u,v) texture coordinates using barycentric interpolation of the triangle vertices' texture coordinates

UV mapping is the 3D modeling process of projecting a 2D image to a 3D model's surface for texture mapping. The UV Mapping process at its simplest requires three steps: unwrapping the mesh, creating the texture, and applying the texture.


## Reading Assignment 3
阅读FCG第6章(Transformation Matrices)，第7章(Viewing)，第8章(The Graphics Pipeline)


# 07 [GPU, Shaders & OpenGL 3.2](https://mdzahidh.github.io/cs148/assets/slides/07-GPU,%20Shaders%20&%20OpenGL%203.2.pdf)
本课程介绍支持可编程管线的OpenGL API，


# 08 [Basics of Rendering](https://mdzahidh.github.io/cs148/assets/slides/08-Rendering.pdf)



## Reading Assignment 4
OpenGL Programming Guide 8th  Chapter 15:
1. What is a vertex shader and a fragment shader, and how are they related?
2. What shader handles the functional stage of the Projection Matrix - vertex or fragment?
3. Name at least two outputs that a vertex program must provide.
4. How long did it take for you to (a) read the material and (b) answer these questions?


# 09 [Materials](https://mdzahidh.github.io/cs148/assets/slides/09-Material.pdf)


# 10 [Ray-Tracing](https://mdzahidh.github.io/cs148/assets/slides/10-Ray%20Tracing.pdf)
## Reading Assignment 5
阅读FCG第4章(Ray Tracing)，第13章(More Ray Tracing)
348B

# 11 [Geometric Modeling](https://mdzahidh.github.io/cs148/assets/slides/11-Geometry.pdf)
348A

# 12 [Animation](https://mdzahidh.github.io/cs148/assets/slides/12-Animation.pdf)
## Reading Assignment 6
阅读FCG第12章(Data Structures for Graphics)
248

# 13 [Physically Based Animation](https://mdzahidh.github.io/cs148/assets/slides/13-Physically%20Based%20Animation.pdf)
348C

# 14 [Sampling](https://mdzahidh.github.io/cs148/assets/slides/14-Sampling.pdf)


# 15 [Recap](https://mdzahidh.github.io/cs148/assets/slides/15-Recap.pdf)

**实践：渲染一个实际的场景(基于Ray Tracing 或者 Scanline Rendering)**


回顾整理之前的知识，也是时候实践和系统的阅读参考书来完善，巩固知识体系了：
- Learn OpenGL
- Fundamentals of Computer Graphics, 3rd Edition

在夯实基础理论及简单的实践后，可以学习使用Unity这样的3D引擎来实现更复杂的游戏。
