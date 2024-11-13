#api #opengl #shaders 

#### Description

An [[OpenGL API]] function.`

Sets a uniform value of the currently active shader program. 
It has multiple overloaded functions, like:
 - `glUniform1i` - single integer uniform
 - `glUniform1f` - single float uniform
 - `glUnifrom3f` - `vec3` uniform
 - `glUniformMatrix2fv` - `mat2` uniform
 - *etc...*

#### Usage

##### C++
``` cpp
uint32_t program = get_shader_program();
uint32_t loc = glGetUniformLocation(program, "myInt");

// Set integer uniform variable named "myInt" to 0.
glUniform1i(loc, 0);
```