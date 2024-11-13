#api #opengl #shaders 

#### Description

An [[OpenGL API]] function.`

Creates an empty shader object.

Available shader types:
 - `GL_COMPUTE_SHADER`
 - `GL_VERTEX_SHADER`
 - `GL_TESS_CONTROL_SHADER`
 - `GL_TESS_EVALUATION_SHADER`
 - `GL_GEOMETRY_SHADER`
 - `GL_FRAGMENT_SHADER`

#### Usage

##### C++
``` cpp
// Create vertex shader and get its objectId.
uint32_t vertId = glCreateShader(GL_VERTEX_SHADER);
```