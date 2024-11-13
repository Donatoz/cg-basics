#api #opengl #shaders 

#### Description

An [[OpenGL API]] function.`

Specifies how OpenGL should interpret vertex buffer data (e.g. provided by [[Vertex buffer object (VBO)]] ) whenever a draw call is made. The interpretation is further stored in currently bound [[Vertex array object (VAO)]].

#### Usage

##### C++
``` cpp
// Configure first (at idx 0) vertex attribute (location = 0)
// With the size of 3 (vec3)
// With the type of float (vec3 consists of floats)
// With data not normalized to 0 (int) or -1 (uint)
// With stride of 3 * sizeof(float) = 12 bytes
// With the data start position at 0 (nullptr)
glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 3 * sizeof(float), nullptr);
```