#api #opengl #drawing 

#### Description

An [[OpenGL API]] function.

Clears the entire current frame buffer. If `GL_COLOR_BUFFER_BIT` is specified in args - clears the buffer with solid color which is specified by [[glClearColor]] function. 

Other bit options are:
 - `GL_DEPTH_BUFFER_BIT`
 - `GL_STENCIL_BUFFER_BIT`

#### Usage

##### C++
``` cpp
// Clear frame buffer with a color
glClear(GL_COLOR_BUFFER_BIT);
```