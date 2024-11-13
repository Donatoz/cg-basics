#api #opengl #drawing 

#### Description

An [[OpenGL API]] function.`

Draws the specified number of vertices currently stored in bound [[Vertex buffer object (VBO)]].

Available modes:
 - `GL_POINTS`
 - `GL_LINE_STRIP`
 - `GL_LINE_LOOP`
 - `GL_LINES`
 - `GL_TRIANGLE_STRIP`
 - `GL_TRIANGLE_FAN`
 - `GL_TRIANGLES`
 - `GL_QUADS`
 - `GL_QUAD_STRIP`
 - `GL_POLYGON`

#### Usage

##### C++
``` cpp
// Draw 3 vertices starting from index 0 as a triangle
glDrawArrays(GL_TRIANGLES, 0, 3);
```