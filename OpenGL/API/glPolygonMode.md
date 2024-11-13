#api #opengl #rendering 

#### Description

An [[OpenGL API]] function.`

Sets polygon rasterization mode of how OpenGL should draw primitives. 

Available faces:
 - `GL_FRONT`
 - `GL_BACK`
 - `GL_FRONT_AND_BACK`
 
 Available modes:
  - `GL_POINT`
  - `GL_LINE`
  - `GL_FILL`
  
#### Usage

##### C++
``` cpp
// Rasterize front and back faces as lines
glPolygonMode(GL_FRONT_AND_BACK, GL_LINE);
```