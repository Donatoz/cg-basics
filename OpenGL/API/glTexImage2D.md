#api #opengl #textures 

#### Description

An [[OpenGL API]] function.`

Generates the texture image on currently bound texture object at the active texture unit.

#### Usage

##### C++
``` cpp
const void* data = /* some data */0;
const int width = 128;
const int height = 128;

// Generate texture on currently bound texture object
// With mipmap level 0
// With resulting texture format as RGB
// With width and height specified
// With empty border (0)
// With original image format as RGB
// With original image data type as unsigned byte
// With specified data
glTexImage2D(GL_TEXTURE_2D, 0, GL_RGB, width, height, 0, GL_RGB, GL_UNSIGNED_BYTE, data);
```