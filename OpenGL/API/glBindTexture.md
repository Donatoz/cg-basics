#api #opengl #textures 

#### Description

An [[OpenGL API]] function.`

Sets the given texture object as the currently active texture object. Any subsequent texture operations will affect the active texture object.

#### Usage

##### C++
``` cpp
// Create texture object
uint32_t texture; 
glGenTextures(1, &texture);
// Bind the texture object as an active one
glBindTexture(GL_TEXTURE_2D, texture);
```