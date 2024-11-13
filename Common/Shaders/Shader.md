#rendering #shaders

A description of a program that runs on **GPU**. Typically used in a graphics pipeline (Vertex, Fragment, Geometry) to provide the developer a configuration interface.

Shaders are written using different languages: GLSL, HLSL, Cg, SKSL, etc...

There are also general purpose shaders named **Compute Shaders**, which are run on **GPU** as well. Their main purpose is to perform some heavy computations in parallel.

#### OpenGL

In OpenGL, shaders are extremely isolated programs that are allowed to communicate between each other only through inputs and outputs.

*See [[GLSL]]*