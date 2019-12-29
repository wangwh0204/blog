title: Stanford EE267 - Virtual Reality
date: 2017-04-03
updated: 2017-06-09
categories:
- [technology]
tags: 
- VR
- Stanford
---

[Stanford EE267](http://stanford.edu/class/ee267/) 学习笔记<!--more-->

> History :
2017-04-03 基于 Spring 2017 的课件记录的笔记。

EE267是Stanford在2016年3月28第一次开设的关于Virtual Reality(VR)的课程，整个课程持续差不多2个月左右时间，每节课1个半小时，每周2节课，一共10周的课程，总计30小时 ....

**Prerequisites: C++, MATH51, CS148, CS248**
**Reading: **
- http://learnopengl.com/
- Fundamentals of Computer Graphics 3rd

**Description: **
OpenGL and WebGL, real-time rendering, 3D display systems, display optics & electronics, IMUs and sensors, tracking, haptics, rendering pipeline, multimodal human perception and depth perception, stereo rendering, presence. Emphasis on VR technology.

# 01 Introduction and Overview
Oculus VR, Microsoft Hololens
simulation & training
visualization & entertainment
gaming

1968 Ivan Sutherland
I.Sutherland "A head-mounted three-dimensional display", Fall Joint Computer Conference 1968
1995 Nintendo Virtual Boy
2012 Oculus Rift, Sony PS VR, Valve HTC Vive, 

About EE267 - Goals
- understand fundamental concepts of VR and Computer Graphics
- Implement software + hardware of a head mounted display
- learn basic WebGL/JavaScript and Arduino programming
- build your own HMD

# 02 The Graphics Pipeline and WebGL I: Overview and Transformations
## what is computer graphics
at the most basic level : conversion from 3D scene description to 2D image

what do you need to describe a static scene
- 3D geometry and transformations
- lights
- material properties

most common geometry primitives in graphics
- vertices(3D points) and normals(unit-length vector associated with vertex)
- triangles(set of 3 vertices, high-resolution 3D models have M or B of triangles)

## the graphics pipeline

- geometry + transformations
- cameras and viewing
- lighting and shading
- rasterization
- texturing

SiliconGraphics history
- Stanford startup in 1981
- computer graphics goes hardware
- based on Jim Clark's geometry engine

monolithic graphics workstations of the 80s have been replaced by modular GPUs(Graphics Processing Units),major companies: Nvidia, AMD, Intel
在手机时代，这些公司没有什么贡献，主要的手机GPU是Imagination的PowerVR，Qualcomm的Adreno，ARM的Maili，随着GPU在AI/VR/MR应用的重要度，未来会有更多公司自行开发GPU

early versions of these GPUs implemented fixed-function rendering pipeline in hardware
GPUs have become programmable starting in the late 90s, in 2001 Nvidia Geforce 3 is first programmable shaders

OpenGL is our interface to the GPU

WebGL
- JavaScript application programmer interface(API) for 2D and 3D graphics
- OpenGL ES 2.0 running in the browser, implemented by all modern browsers
- overview, tutorials, documentation:!
https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API

three.js
- cross-browser JavaScript library/API
- higher-level library that provides a lot of useful helper functions, tools, and abstractions around WebGL – easy and convenient to use
- https://threejs.org/
- great introduction (in WebGL):
http://davidscottlyons.com/threejs/presentations/frontporch14/


The Graphics Pipeline : 
https://www.ntu.edu.sg/home/ehchua/programming/opengl/CG_BasicsTheory.html
需要反复阅读同时结合OpenGL实例去彻底理解，对于3D 图形学的开发至关重要。

Raw Vertices  --Vertex Shader--> Transformed Vertices --Rasterizer--> Fragments --Fragment Shader --> Processed Fragments --Output Merging--> Pixels --> Display

Coordinate System
- Right hand coordinate system
- Object coordinates
- World coordinates
确定一个world center，其他物体相对坐标
- Viewing coordinates
- clip, normalized device, and window coordinates

Primitives
- vertex = 3D pint(x,y,z)
- triangle = 3 vertices
- normal = 3D vecctor per vertex describing surface orientation

Vertex Transforms
3D Object经过MVP变换，最终以2D形式呈现在Display上
Model spaces -- Model Transform --> World Space -- View Transform --> Camera Space -- Projection Transform --> Clipping-Volume Space --> NDC -- Viewport Transform --> Screen Space --> Display

- Arrange the objects(or modles, or avatar) in the world(Model Transformation or World transformation)
- Position and orientation the camera(View transformation)
- Select a camrea lens(wide angle, normal or telescopic), adjust the focus length and zoom factor to set the camera's field of view(Projection transformation)
- Print the photo on a selected area of the paper(Viewport transformation) - in rasterization stage

View Transform
- one simple 4x4 transfom matrix is sufficient to go from world space to view space

specify camera by eye position, reference position, up vector
怎么得到view transform matrix，还需要再查看更多的资料

Projection Transform - Perspective Projection
Perspective Projection : The camera's view frustum is specified via 4 view parameters: fovy, aspect, zNear and zFar
- fovy: vertical angle in degress
- aspect: ratio of width/height
- zNear: near clipping plane
- zFar: far clipping plane

对于Screen Space，注意它的中心(原点)是在左上角，依然可以用(x,y,z)表示，只是所有的z为0.

Summary
- graphics pipeline is a series of operations that takes 3D vertices/normals/triangles as input and generates fragments and pixels
- transforms include: rotation, scale, translaton, perspective projection, perspective division, and viewport transform
- most transforms are represented as 4x4 matrices in homogeneous coordinates

# 03 The Graphics Pipeline and WebGL II: Lighting and Shading, Fragment Processing
这一章的内容结合LearnOpenGL的代码和实作效果来学习，理解会更深刻
The Rendering Equation(BRDFs)
Kajija "The Rendering Equation", SIGGRAPH 1986

drop time, wavelength, emission & global illumination, we get a simple function

Bidirectional Reflectance Distribution Function(BRDF)
- many different BRDF modles exist: analytic, data driven
Acquired data, Ashikhmin, Blinn-Phong, Cook-Torrance, Lafortune, Ward
- can approximate BRDF with a few simple components

Phong Lighting
- simple model for direct lighting
- ambient, diffuse, and specular 
- requires: 
material color for each of ambient, diffuse, specular
light color for each of ambient, diffuse, specular

this is a simple, but efficient lighting model, has been used by OpenGL for ~25 years

Phong Lighting: Ambient
- independent of light/surface position, viewer, normal
- basically adds some background color

Phong Lighting: Diffuse
漫反射的光强度根据距离会衰减
- needs normal and light source direction
- adds intensity cos-falloff with incident angle

Phong Lighting: Specular
- needs normal, light & viewer direction
- models reflections = specular highlights
- shininess - exponent, larger for smaller highlights(more mirror-like surfaces)

Lighting vs Shading
Lighting : interaction between light and surface(e.g. using Phong lighting model)
shading: how to compute color of each fragment'
- Flat shading
compute color only once per triangle
pro:usually fast to compute; con: fast creates a flat, unrealistic appearance

- Gourand shading(per-vertex shading)
compute color once per vertex
interpolate per-vertex colors to all fragments within the triangles
pro: usually fast-ish to compute; con: flat, unrealistic specular highlights

- Phong shading(per-fragment shading - different from Phong lighting)
compute color once per fragment
need to interpolate per-vertex normals to all fragments to do the lighting calculation
pro:better appearance of specular highlights; con: usually slower to compute


Vertex and Fragment shaders
- shaders are small programs that are executed in parallel on the GPU for each vertex(vertex shader) or each fragment(fragment shader)
- vertex shader
modelview projection transform of vertex & normal
- fragment shader
assign final color to each fragment

Fragment Processing
- lighting and shading(per-fragment)
- texture mapping
- fog calculations
- alpha blending
- hidden surface removal(using depth buffer)
- scissor test, stencil test, dithering, bitmasking, ...

Texture Mapping
- texture = 2D image(e.g. RGBA)
- we want to use it as a "sticker" on our 3D surfaces
- mapping from vertex to position on texture(texture coordinates u,v)

# 04 The Graphics Pipeline and WebGL III: OpenGL Shading Language(GLSL 1.10)
The Rasterizer, two goals:
- determine which fragments are inside the primitives(triangles) and which ones aren't
- interpolate per-vertex attributes(color, texture coordinates, normals, ...) to each fragment in the primitive


vertex shader(executed for each vertex)
- transforms
- (per-vertex) lighting

input : vertex position, normal, color, material, texture coordinates; modelview matrix, projection matrix, normal matrix
output : transformed vertex position(in clip coords), texture coordinates

fragment shader(executed for each fragment)
- texturing
- (per-fragment) lighting

input: vertex position in window coords, texture coordinates
output: fragment color, fragment depth

Why Do We Need Shaders?
- massively parallel computing
- single instruction multiple data(SIMD) paradigm -> GPUs are designed to be parallel processors
- vertex shaders are independently executed for each vertex on GPU(in parallel)
- fragment shaders are independently executed for each fragment on GPU(in parallel)
- most important: vertex transforms and lighting & shading calculations
- shading: how to compute color of each fragment(e.g. interpolate colors)

OpenGL Shading Language(GLSL)
- high-level programming language for shaders
- syntax similar to C
- usually very short programs that are executed in parallel on GPU

# 05 The Human Visual System
这一章主要说明人眼的生物特性，包括Retina, FOV, Fovea，要深入的理解，需要进一步阅读相关书籍。

Retina VR Display - What does it take
need per eye : 150° x 135° with pixels covering 1 arc min = 9000 x 8100 pixels(probably 2-3x in practice)  150 x 60 = 9000

biggest challenge: bandwidth (9000 x 8100 x 4 x 90 = 24GB/s)
capture or render stereo panoramas or images at that resolution
compress and transmit huge amount of data
drive and operate display pixels

Foveated Rendering
- Guenter et al. 2016: split image into n layers, e.g. inner(foveal, 1), middle(2), outer(3)
- render image in each zone with progressively lower resolution
- goal: save computation

Depth Perception
- monocular cues : perspective, relative object size, absolute size, occlusion, accommodation, retinal blur, motion parallax, texture gradients, shading
- binocular cues : (con)vergence, disparity/parallax

binocular disparity, convergence, motion parallax, accommodation/blur

current :  glasses-based (stereoscopic) displays
near-term : light field displays
longer-term : holographic displays

Stereoscopic Displays

Oculumotor Processes

Accommodation and Retinal Blur

Summary
- Visual Acuity: each photorecepter is ~1 arc min(1/60 of a degree) 也就是60 pixels/degree才能满足视网膜程度的视觉效果。
visual acuity varies over retina: can exploit via foveated rendering
- field of view: ~190° monocular, ~120° binocular, ~135° vertical
- temporal resolution: ~60 Hz (depends on contrast, luminance)
- dynamic range: instantaneous 6.5 f-stops, adapt to 46.5 f-stops
- color: everything in the CIE xy diagram; distances are linear in CIE Lab
- depth cues in 3D displays: vergence, focus, conflicts, (dis)comfort
- accommodation range: ~8cm to ∞, degrades with age

References and Further Reading!
interesting textbooks on perception:
• Wandell, “Foundations of Vision”, Sinauer Associates,1995
• Howard, “Perceiving in Depth”, Oxford University Press, 2012

foveated rendering:
• Guenter, Finch, Drucker, Tan, Snyder “Foveated 3D Graphics”, ACM SIGGRAPH Asia 2012
• Patney, Salvi, Kim, Kaplanyan, Wyman, Benty, Luebke, Lefohn “Towards Foveated Rendering for Gaze-Tracked Virtual Reality”, ACM SIGGRAPH Asia 2016

depth cues and more:
• Cutting & Vishton,” Perceiving layout and knowing distances: The interaction, relative potency, and contextual use of different information about depth”, Epstein and Rogers
(Eds.), Perception of space and motion, 1995
• Held, Cooper, O’Brien, Banks, “Using Blur to Affect Perceived Distance and Size”, ACM Transactions on Graphics, 2010
• Hoffman and Banks, “Focus information is used to interpret binocular images”. Journal of Vision 10, 2010
• Hoffman, Girshick, Akeley, and Banks, “Vergence-accommodation conflicts hinder visual performance and cause visual fatigue”. Journal of Vision 8, 2008
• Huang, Chen, Wetzstein, “The Light Field Stereoscope”, ACM SIGGRAPH 2015

the retina, visual acuity, visual field
• Roorda, Williams, “The arrangement of the three cone classes in the living human eye”, Nature, Vol 397, 1999
• Snellen chart: https://en.wikipedia.org/wiki/Snellen_chart
• Ruch and Fulton, Medical physiology and biophysics, 1960

contrast sensitivity function & hybrid images:
• Oliva, Torralba, Schyns, “Hybrid Images”, ACM Transactions on Graphics (SIGGRAPH), 2006
• Spatio-temporal CSF: Kelly, Motion and Vision. II. Stabilized spatio-temporal threshold surface, Journal of the Optical Society of America,1979


# 06 The Graphics Pipeline and OpenGL IV: Stereo Rendering, Depth of Field Rendering, Multi-pass Rendering
演讲人是[steve Mann](https://en.wikipedia.org/wiki/Steve_Mann)，被称为The Father of The Wearable Computer可穿戴之父，也是Chief Scietist of Meta 


Nvidia提出了Multi-Res Rendering的技术，在硬件层面提升效率

- stereo rendering with OpenGL
- offscreen frame buffers and multi-render passes
- anaglyph stereo rendering with GLSL
- depth of field rendering


Stereo Rendering with OpenGL/WebGL: View Matrix!
• need to modify view matrix and projection matrix!
• rendering pipeline does not change – only those two matrices!
• however: need to render two images in sequence (more details later)!
• look at view matrix first: THREE.Matrix4().lookAt(eye,center,up) !
• function is as useful as it has been, just need to adjust parameters!

IPD : interpupillary distance

Anaglyph with OpenGL!
• most efficient way: !
1. clear color and depth buffer!
2. set left modelview and project matrix, render scene only into red channel !
3. clear depth buffer!
4. set right modelview and project matrix, render scene only into green & blue
channels !
•

OpenGL Frame Buffers!
• usually (frame) buffers are provided by the window manager (i.e., your browser)!
• for most mono applications, two (double) buffers: back buffer and front buffer!
• render into back buffer; swap buffers when done rendering!
• advantage: rendering takes time, you don’t want the user to see how triangles
get drawn!
• in many stereo applications, 4 (quad) buffers: front/back left and right buffer !
• render left and right images into back buffers, then swap both together!


# 07 HMD Display Optics I
1. Stereo rendering for HMDs
使用makePerspective(left, right, top, bottom, near, far)和lookAt(eye, center, up)

2. Lens distortion correcting using GLSL

# 08 Head Mounted Display Optics II



# 09 Inertial Measurement Units I
gyros, accelerometers, magnetometers


# 10 Inertial Measurement Units II
sensor fusion, complementary filter, arduino


# 11 Positional Tracking I


# 12 Positional Tracking II


# 13 Spatial Sound


# 14 Haptics


# 15 Panoramic Imaging and Cinematic VR


# 16 VR Engines and Unity




