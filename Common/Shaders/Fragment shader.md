#shaders 

### Description

Processes a generated fragment into a set of colors and a single depth value.

#### Syntax

##### GLSL

A GLSL fragment shader requires one output variable of type `vec4` which is a resulting fragment color.

``` cs
#version 100

out vec4 FragColor;

void main() {
	FragColor = vec4(1.0f, 0.5f, 0.2f, 1.0f);
}

```

*Check out https://www.khronos.org/opengl/wiki/Fragment_Shader