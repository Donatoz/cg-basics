#api #opengl #drawing 

#### Description

An [[OpenGL API]] function.`

Draws the specified amount of vertex indices using provided drawing mode. Vertex indices are taken from [[Element buffer object (EBO)]] and vertex data is taken from [[Vertex buffer object (VBO)]]. The order of drawing is incremental: starting from 0 index until the end.

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
// Draw first 6 vertices (from the 0 index) 
// Of type uint
// As triangles
glDrawElements(GL_TRIANGLES, 6, GL_UNSIGNED_INT, 0);
```