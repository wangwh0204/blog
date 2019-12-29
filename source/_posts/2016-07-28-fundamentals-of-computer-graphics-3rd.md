title: Fundamentals of Computer Graphics 3rd
date: 2016-07-28
updated: 2016-10-02
categories:
- [reading]
- [technology]
tags: 
- Computer Graphics
---

&lt;&lt;Fundamentals of Computer Graphics 3rd&gt;&gt;读书笔记，计算机图形学的最佳入门书籍，结合http://learnopengl.com/实践更佳 ... TBD <!--more-->

# 01 Introduction

The term *computer graphics* describes any use of computers to create and manipulate images.
## Graphics Areas :
-  **Modeling** deals with the mathematical specification of shape and appearance properties in a way that can be stored on the computer.
-  **Rendering** is a team inherited from art and deals with the createion of shaded images from 3D computer models. 
-  **Animation** is a technique to create an illusion of motion through sequences of images.
-  **User interaction** deals with the interface between input devices such as mice and tablets , the application, feedback to the user in imagery, and other sensory feedback.
-  **Virtual reality** attempts to immerse the user into a 3D virtual world. Because this area requires advanced 3D graphics and advanced display technology, it is often closely associated with graphics.
-  **Visualization** attempts to give users insight into complex information via visual display.
-  **Image processing** deals with the manipulation of 2D images and is used in both the fields of graphics and vision.
-  **3D scanning** uses rang-finding technology to create measured 3D models.
-  **Computational photography** is the use of computer graphics, computer vision, and image processing methods to enable new ways of photographically capturing objects, scenes, and environments.

## Major Applications
-  **Video games** increasingly use sophisticated 3D models and rendering algorithms.
-  **Cartoons** are often rendered directly from 3D models.
-  **Visual effects** use almost all types of computer graphics technology.
-  **Animated films** use many of the same techniques that are used for visual effects, but without necessarily aiming for images that look real.
-  **CAD/CAM** stands for *computer-aided design* and *computer-aided manufacturing*.
-  **Simulation** can be thought of as accurate video gaming.
-  **Medical imaging** create meaningful images of scanned patient data.
-  **Information visualization** creates images of data that do not necessarily have a "natural" visual depiction.

## Graphics APIs
A key part of using graphics libraries is dealing with a *graphics* API.
Every graphics program needs to be able to use two related APIs: a graphics API for visual output and a user-interface API to get input from the user.

## Graphics Pipeline
The basic operations in the pipeline map the 3D vertex locations to 2D screen positions and shade the triangles to that they both look realistic and appear in proper back-to-front order.
Although drawing the triangles in valid back-to-front order was once the most important research issue in computer graphics, it is now almost always solved using the *z-buffer*, which uses a special memory buffer to solve the problem in a brute-force manner.

It turns out that the geometric manipulation used in the graphics pipeline can be accomplished almost entirely in a 4D coordinate space composed of three traditional geometric coordinates and a fourth homogeneous coordinate that helps with perspective viewing. These 4D coordinates are manipulated using 4 × 4 matrices and 4-vectors. The graphics pipeline, therefore, contains much machinery for efficiently processing and composing such matrices and vectors. 
This 4D coordinate system is one of the most subtle and beautiful constructs used in
computer science, and it is certainly the biggest intellectual hurdle to jump when
learning computer graphics. A big chunk of the first part of every graphics book
deals with these coordinates.


> [homogeneous coordinate](https://en.wikipedia.org/wiki/Homogeneous_coordinates) :
Given a point (x, y) on the Euclidean plane, for any non-zero real number Z, the triple (xZ, yZ, Z) is called a set of homogeneous coordinates for the point.
> [matrix](https://en.wikipedia.org/wiki/Matrix_(mathematics)) :
In mathematics, a matrix (plural matrices) is a rectangular array of numbers, symbols, or expressions, arranged in rows and columns.
> [vector](https://en.wikipedia.org/wiki/Coordinate_vector) : 

## Numerical Issues
First, and most important, is to understand that there are three "special" values for real numbers in IEEE floating-point:
1. infinity (∞). This is a valid number that is larger than all other valid numbers.
2. minus infinity (−∞). This is a valid number that is smaller than all other valid numbers.
3. not a number (NaN). This is an invalid number that arises from an operation with undefined consequences, such as zero divided by zero.

Perhaps the most useful aspect of IEEE floating-point is how divide-by-zero is handled; for any positive real number a, the following rules involving division by zero values hold:
+a/ +0 = +∞
−a/ +0 = −∞

## 1.6 Efficiency
A reasonable approach to making code fast is to proceed in the following order, taking only those steps which are needed:
1. Write the code in the most straightforward way possible. Compute intermediate results as needed on the fly rather than storing them.
2. Compile in optimized mode.
3. Use whatever profiling tools exist to find critical bottlenecks.
4. Examine data structures to look for ways to improve locality. If possible, make data unit sizes match the cache/page size on the target architecture.
5. If profiling reveals bottlenecks in numeric computations, examine the assembly code generated by the compiler for missed efficiencies. Rewrite
source code to solve any problems you find.

The most important of these steps is the first one. Most “optimizations” make the code harder to read without speeding things up. 

## Designing and Coding Graphics Programs

We have found several debugging strategies to be particularly useful in graphics.
The Scientific Method
Images as Coded Debugging Output
Using a Debugger
Data Visualization for Debugging

# 02 Miscellaneous Math
Much of graphics is just translating math directly into code.



# 06 Transformation Matrices




> 2016.07.28 ~ 2016.08.05 根据CS148的要求阅读第20章(P12)，21章(P21)
# 20 Light
In this chapter, we discuss the practical issues of measuring light, usually called *radiometry*.(辐射度)
To aid our intuition, we will describe radiometry in terms of collections of large numbers of *photons*(光子)
a photon is a quantum of light that has a position, direction of propagation, and a wavelength 

[irradiance](https://en.wikipedia.org/wiki/Irradiance)(辐射照度,单位时间内投射到单位面积上的辐射能量)tells how much light is arriving at a point.

[Radiance](https://en.wikipedia.org/wiki/Radiance)

BRDF[（Bidirectional reflectance distribution function)](https://en.wikipedia.org/wiki/Bidirectional_reflectance_distribution_function) is all we need to know to characterize the directional properties of how a surface reflects light.

An idealized diffuse surface is called *Lambertian*. The Lambertian BRDF has equal to a constant for all angles.

[rendering equation](https://en.wikipedia.org/wiki/Rendering_equation) 

# 21 Color
Photons are the carriers of optical information. They propagate through media taking on properties associated with waves. At surface boundaries they interact with matter, behaving more as particles. They can also be absorbed by the retina, where the information they carry is transcoded into electrical signals that are subsequently processed by the brain. It is only there that a sensation of color is generated.

Photons travel along straight paths until they hit a surface boundary and then reflected according to a reflection function of some sort. A single photo will carry a certain amount of energy, which is represented by its wavelength. Thus, a photon will have only one wavelength.

In computer graphics, it is not very efficient to simulate single photons; instead large collections of them are simulated at the same time. 
At surface boundaries, we normally model what happens with light by means of a reflectance function.  These reflectance functions are empirical in nature, ie, they abstract away the chemistry that happens when a photon is absorbed and re-emitted by an electron. We can therefore not use reflectance functions to explain why the light reflected off a banana has a spectral composition that appears to us as yellow. For that, we would have to study molecular orbital theory, a topic beond the scope of this book.

Color is the aspect of visual perception by which an observer may distinguish differences between two structure-free fields of view of the same size and shape, such as may be caused by differences in the spectral composition of the radiant energy concerned in the observation. In essence, without a human observer there is no color.

[Colorimetry](https://en.wikipedia.org/wiki/Colorimetry) is the science of color measurement and description.
The photodetectors in the human retina consist of rods([视杆细胞](http://baike.baidu.com/view/555308.htm)) and cones([视锥细胞](http://baike.baidu.com/view/852250.htm)). The rods are highly sensitive and come into play in low light conditions. Under normal lighting conditions, the cones are operational, mediating human vision. There are three cone types and together they are primarily responsible for color vision.

Given that humans have three different cone types, the experimental laws of color matching can be summed up as the trichromatic generalization, which states that any color stimulus can be matched completely with an additive mixture of three appropriately modulated color sources. This feature of color is often used in practice, for instance by televisions and monitors wich reproduce many different colors by adding a mixture of red, green, and blue light for each pixel. It is also the reason that renderers can be built using only three values to describe each color.

Grassmann was the first to describe the algebraic rules to which color matching adheres. They are known as Grassmann's laws of additive color matching.

Each cone type is sensitive to a range of wavelengths, spanning most of the full visible range. The three cone types are classified aa S,M,and L cones, where the letters stand for short, medium, and long, indicating where in the visible spectrum the peak sensitivity is located.

Metamerism is the key feature of human vision that allows the construction of color reproduction devices, including the color reproduction devices, including the color figures in this book and anything reproduced on printers, televisions, and monitors.

The Commission Internationaled' Eclairage (CIE) has defined three such primaries to be monochromatic light sources of 435.8, 546.1 and 700 nm, respectively. With these three monochromatic light sources, all other visible wavelengths can be matched by adding different amounts of each. Tristimulus values associated with these color matching functions are termed R, G, and B.

Every color can be represented by a set of three tristimulus values(X, Y, Z). We could define an orthogonal coordinate system with X, Y, and Z axes and plot each color in the resulting 3D space. This is called a *color space*. 

Of all the books on color theory, Reinhard et al.'s work(Reinhard et al., 2008) is most directly geared towards engineering disciplines, including computer graphics, computer vision, and image processing.











