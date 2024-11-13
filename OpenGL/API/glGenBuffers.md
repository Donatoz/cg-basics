#api #opengl

#### Description

An [[OpenGL API]] function.`

Generates one or multiple buffer objects. 
#### Usage

##### C++
``` cpp
// Declare object id for the buffer
uint32_t bufferId;
// Generate 1 buffer and put its id into bufferId.
glGenBuffers(1, &bufferId);

// Declare object id for five different buffers
uint32_t bufferIds[5];
// Generate 5 buffers and put their ids into bufferIds.
glGenBuffers(5, &bufferIds);
```