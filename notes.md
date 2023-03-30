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
