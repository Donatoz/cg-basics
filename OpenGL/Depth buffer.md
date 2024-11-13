#opengl #rendering 

OpenGL stores all depth information in z-buffer (a.k.a. depth buffer). The depth is stored within each fragment (just like the [[Color Buffer]] stores the color of a fragment) and whenever the color of a fragment is being retrieved, OpenGL compares its depth values with depth buffer. If there is any fragment is in front of the current fragment - the current one is being discarded, otherwise another is being overwritten. This process is called **depth test**.

The depth buffer is automatically created by the window host.

The depth test can be enabled in OpenGL using:

```cpp
glEnable(GL_DEPTH_TEST);
```

Note that [[glClear]] function needs to supply `GL_DEPTH_BUFFER_BIT` in order to clear depth buffer.

Depth buffer stores depth values as 16, 24 (commonly used) or 32 bit floats. Depth testing is performed after the fragment shader and stencil test. 

`gl_FragCoord.z` coordinate corresponds to the fragment's depth value.

> Most modern GPU's support *early depth testing*, which is performed before the fragment shader. If the fragment is not going to be visible, it can be discarded. The only restriction of the early depth test is that `gl_FragCoord.z` value cannot be written to.


