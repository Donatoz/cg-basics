#opengl #rendering 

Large set of instructions which main purpose is to transform 3D coordinates to 2D pixels that fit user screen. The pipeline can be split into two parts: 3D to 2D coordinates transformation and transformation of 2D coordinates into actual pixels.

[[OpenGL API]] graphics pipeline is divided into several steps, where each step requires previous step results as input. All of these steps have one specific function and can be executed in parallel.

The processing cores run small programs on the GPU for each step in the pipeline. These programs are called [[Shader]]s

[[Graphics pipeline scheme.canvas|Graphics pipeline scheme]]

___
### Pipeline steps (common)

#### Vertex data

A list of 3D coordinates are passed to the pipeline as raw input data in an array form. This array is called **Vertex data** and is represented using vertex attributes that can contain any user data, for example a position and vertex color.

> In order for OpenGL to know what to make of your collection of coordinates and color values OpenGL requires you to hint what kind of render types you want to form with the data. Do we want the data rendered as a collection of points, a collection of triangles or perhaps just one long line? Those hints are called primitives and are given to OpenGL while calling any of the drawing commands. Some of these hints are GL_POINTS, GL_TRIANGLES and GL_LINE_STRIP.

#### Vertex shader

*See [[Vertex shader]]*

Takes a single vertex as input. Perform a processing of 3D coordinates and vertex attributes. The output of this shader can be passed into next stage.

#### Geometry shader

Takes as input a collection of vertices that form a primitive. Has an option to generate shapes by generating new vertices to form a new primitive(s).

#### Shape (primitive) assembly

Takes as input all the vertices (or vertex if `GL_POINTS` is chosen in Vertex data stage) from vertex/geometry shader, forms one or more primitives and assembles all the points.

#### Rasterization

Takes as input primitives from the Shape assembly and maps them to the corresponding pixels on the screen, resulting in fragments. Also preforms clipping that discard all fragments that are outside of the view.

#### Fragment shader

*See [[Fragment shader]]*

Calculates the final color of a fragment provided by Rasterization stage. Commonly used for advanced OpenGL effects implementation and contains 3D scene data (lights, shadows, light color, etc...)

#### Tests and blending

Checks the corresponding depth and stencil values of a fragment and uses those values to determine whether if the resulting fragment is in front or behind other objects or should the fragment be discarded. Blends objects based on their alpha values.

___

In modern OpenGL, developer is **required** to define a vertex and fragment shaders, as there are no default ones.

See [[Vertex input]] for further information.