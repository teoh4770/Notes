# A1 Report

Author: Chee Kian Teoh

Date: 2024-09-11 

Check [readme.txt](readme.txt) for course work statement and self-evaluation. 
   
## Q1 Concepts of raster display systems (short answer)


### Q1.1 framebuffers

Framebuffer is an image memory to store image information, such as colour values.


### Q1.2 pixels, color depth, and resolution

Pixels: A collection of illuminated dots on the screen, sometimes refer as picture elements or pen in short.

Color depth: Color depth, or depth, is the amount of bits a pixel takes in an image memory. Amount of bits a pixel can hold ranging from 1, 3, 8, 16, 24 bits.

Resolution: The number of pixels that can be plotted on the screen, represented as the number of pixels per scan line(row of pixels) times the number of scan line. E.g. 640 x 480 means the raster contains 640 rows of pixels, and each rows contains 480 pixels. 


### Q1.3 Frame, refreshment, and refresh rate

Frame: Refers to a complete screen area. 

Refreshment: ?

Refresh rate: The number of frames rendered per second on screen. E.g. 60Hz means 60 frames per second.


## Q2 Concepts of image rendering (short answer)


### Q2.1 What are the two basic image rendering approaches?
1. Rasterization
2. Ray Tracing


### Q2.2 Why rasterization is commonly used in graphics applications?
- Graphic applications require a lot of real-time image creation and rendering. Speed and efficiency of creating and rendering the images are the priority.
- Although the images produced using ray tracing would contain more realistic elements, such as lighting, reflections, shadow, but to produce such quality images requires computational powers a normal computer couldn't support, thus slow and not efficient.
- Rasterisation is less complex approach compared to ray tracing (render the image on image memory before mapping them to the display is cheap and fast), thus faster and more efficient, which fit the requirement of graphic applications, therefore commonly used.
 

## Q3 Roles of CPU and GPU in CG (short answer)


### Q3.1 CPU roles

- CPU does model computing (modelling)
- Sends graphic object model data (e.g. vertices of triangle) to
  - video memory and
  - GPU
  to be stored and processed

### Q3.2 GPU roles

- GPU does rendering computing (rendering)
- It is focus on 
  - processing object data (received from CPU)
  - rasterizing (generates pixel data) and
  - stores the pixel data in framebuffer
- Things that writes to framebuffer include basic graphic primitives (dot, line, triangle, polygon)


## Q4 C/C++ OpenGL programming environment (lab practice)

Link to lab practice: https://mylearningspace.wlu.ca/d2l/le/content/549078/viewContent/3825045/View


### Q4.1 C/C++ OpenGL installation 

Complete? Yes or No 

<!--If you answer Yes, insert a screenshot image to show the completion.-->
Yes. Screen image below as a proof.

<!-- ![Image caption](images/demo.png){width=90%} -->


<!-- If No, add a short description to describe the issues encountered.-->

### Q4.2 OpenGL C project 

Complete? Yes or No 

<!--If you answer Yes, insert a screenshot image to show the completion.-->

![Image caption](images/demo.png){width=90%}

<!-- If No, add a short description to describe the issues encountered.-->

### Q4.3 OpenGL C++ project 

Complete? Yes or No 

<!--If you answer Yes, insert a screenshot image to show the completion.-->

![Image caption](images/demo.png){width=90%}

<!-- If No, add a short description to describe the issues encountered.-->



**References**

1. CP411 a1
2. Add your references if you used any. 
