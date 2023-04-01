## Durian Software - WebGl Get Started

[Link](https://duriansoftware.com/joe/an-intro-to-modern-opengl.-chapter-1:-the-graphics-pipeline)

### OpenGL

- Cross platform library for interacting with programmable GPU's for the purpose of rendering 3d graphics
- 'OpenGL is pushed to the we domain with WebGL'


### The Graphics Pipeline

- Scenes are drawn using triangles
- OpenGL manages a memory buffer; the host program fills this with arrays of vertices
- These go through the following process:
    - Projected onto screen space
    - Assembled into triangles
    - Rasterized into pixel sized fragments
    - Pixels are assigned colour values
    - Drawn to the framebuffer
- Shaders are programs which manage the 'project into screen space' and 'assign colour values' parts

### The Vertex and Element Arrays

- Vertex buffers are filled with arrays of vertex attributes
- These attributes are often things like the vertex's location in 3d space, and how the vertex maps to a point on a texture
- The set of rendering buffers supplying data to a rendering job are collectively called the vertex array
- When a render job is submitted, we also submit an element array, an array of indexes of vertices, which selects which vertices get fed into the pipeline
- The order of these vertices also affects how vertices are assembled into triangles

### Uniform State and Textures

- A rendering job also has a set of fixed values, for parameters that do not change between vertices
- Often used for textures (one, two, or three dimensional arrays representing images that can be mapped to surfaces)
- Can also be used as lookup tables for precalculated functions, or as datasets for various kinds of effects

### The Vertex Shader

- The vertex shader is a program which takes in a set of vertex attributes and outputs a new set of attributes
- The minimum the vertex shader will do is calculate the vertex's position in the projected screen space
- The vertex shader may also provide attributes such a texture coordinates

### Triangle Assembly

- The GPU then takes the element array and grouping them into groups of 3
- This can be done in one of three ways:
    - Take every 3 elements as a separate triangle
    - Make a triangle strip, reusing each element along with the previous 2 to form a new triangle
    - Make a triangle fan, connecting the first element to every subsequent pair of elements

### Rasterization

- The rasterizer takes each triangle, clips it and discards parts that are not on the screen
- It then breaks the parts which remain into pixel sized fragments
- The rasterizer will smooth values across the triangle


### Fragment shader

- Receives the varying values output by the rasterizer
- It outputs the colour and depth values which then get output to the frame buffer
- Common fragment shader operations include texture mapping and lighting
- Can run independtly for every pixel drawn
- Can perform the most complicated special effects
- Most performance-sensitive part of the pipeline

### Final output

- Most opengl implementations allow off-screen drawing
- Frame buffers can also filter out values based off of two things; depth buffer and stencil buffer
- Depth testing removes those values which are behind others
- Stencil buffer can constrain which parts of the screen are drawable