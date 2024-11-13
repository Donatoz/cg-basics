#api #opengl #textures

#### Description

An [[OpenGL API]] function.`

Generates all the mipmap levels for the currently bound texture image of the active texture unit. It derives all required mipmap images from the base level which should be specified before calling this function.

Each subsequent mipmap image will be of a half size of the previous image, until it reaches 1 pixel in width and height.

#### Usage

##### C++
``` cpp
// usage goes here
```