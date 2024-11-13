#api #opengl #rendering 

#### Description

An [[OpenGL API]] function.`

Binds specified buffer object to the current buffer type target. Only single buffer can be bound for each buffer type. Binding 0 to as a buffer resets currently bound buffer.
#### Usage

##### C++
``` cpp
// Generate buffer
uint32_t bufferId; 
glGenBuffers(1, &bufferId);

// Bind this buffer
glBindBuffer(GL_ARRAY_BUFFER, bufferId);

```