#api #opengl #shaders 

#### Description

An [[OpenGL API]] function.`

Returns a uniform id `<int>` in memory for the given shader program `<uint32_t>` and uniform name `<string>`.  Returns `-1` if no location is found, e.g provided uniform name is incorrect or the uniform was deleted/optimized during compilation.

#### Usage

##### C++
``` cpp
uint32_t prog = get_shader_program();
int location = glGetUniformLocation(prog, "offset");
```