#shaders 

### Description

Commonly used to perform different transformations upon given vertex. 

#### Syntax

##### GLSL
``` cs
#version 100

in vec3 position;

void main() {
	gl_Position = vec4(position, 1.0);
}
```