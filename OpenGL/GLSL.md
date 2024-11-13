GLSL is a C-like shading language used in [[OpenGL API]], which is (along with SPIR-V) is supported directly by the API.

>The last version of GLSL is 4.60 *(06.2024)*

GLSL can be extended via OpenGL extensions.

*See https://www.khronos.org/opengl/wiki/OpenGL_Extension

### Syntax

``` cs
#version version_number 
in type in_variable_name; 
in type in_variable_name; 

out type out_variable_name; 

uniform type uniform_name; 

void main() { 
	//process input(s) and do some weird graphics stuff 
	// ... 
	// output processed stuff to output variable
	
	out_variable_name = weird_stuff_we_processed; 
}

```

### Input and output

Each shader can specify input and output variables in order to transfer computed data. 

The vertex shader **should** receive some form of input data, otherwise it would be ineffective. To define how this data is organized, **layout (location = n)** is used to link the variable with vertex data

``` cs
layout (location = 0) in vec3 position;
```

The fragment shader requires `vec4` color output to specify the resulting color of a fragment.

### Uniforms

Uniforms are another way to to pass data from CPU to GPU. Unlike vertex attributes, uniforms are global per shader program and can be accessed by any shader at any stage.

The `uniform` keyword is used to declare an uniform variable.

```cs
uniform vec4 color;
```

If uniform is not used in any shader - it will be destroyed by compiler.

