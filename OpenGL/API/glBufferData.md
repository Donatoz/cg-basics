#api #opengl #rendering 

#### Description

An [[OpenGL API]] function.`

Allocates memory and stores data within initialized memory in the currently bound buffer object. 

Possible modes:
 - `GL_STREAM_DRAW` - data is set only once and used by the GPU at most few times
 - `GL_STATIC_DRAW` - data is set only once and used many times
 - `GL_DYNAMIC_DRAW` - data is set multiple times and used multiple times

#### Usage

##### C++
``` cpp
// Declare vertices of a triangle
float vertices[] = { 
	-0.5f, -0.5f, 0.0f,     
	0.5f, -0.5f, 0.0f,     
	0.0f,  0.5f, 0.0f
};

// Copy vertices into GL_ARRAY_BUFFER memory 
// at read-only state
glBufferData(GL_ARRAY_BUFFER, sizeof(vertices), vertices, GL_STATIC_DRAW);
```