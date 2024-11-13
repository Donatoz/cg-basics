#api #opengl #shaders 

#### Description

An [[OpenGL API]] function.`

Attaches specified shader object to the specified shader program. Any number of distinct-type shader objects can be attached to a program.

#### Usage

##### C++
``` cpp
// Create a shader
const uint32_t shader = create_shader(/*params*/);
// Create shader porgram
const uint32_t program = glCreateProgram();
// Attach shader object to a program
glAttachShader(program, shader);
```