#opengl #buffers #rendering 

A special buffer that stores a large number of vertices on the GPU side. It is used to configure how driver should interpret the memory and specify how to send the data to GPU.

The advantage of using VBO's is that developer can send large batches of data to the GPU at once and keep it there if there is enough free memory, without having to send all vertices one by one, as transferring data from CPU to GPU is relatively slow.

Once all transferred vertices are held in the GPU memory, the access to them is **nearly instant**.

In OpenGL, the vertex buffer is generated using [[glGenBuffers]] function. The type of the created buffer is `GL_ARRAY_BUFFER`.
The buffer can be the bound using [[glBindBuffer]] function. The data can be copied into bound buffer using [[glBufferData]] function.

### Memory alignment

Lets suppose we have an array of triangle vertices positions:

``` cpp
constexpr float vertices[] = {
	-0.5f, -0.5f, 0.0f, 
	0.5f,  -0.5f, 0.0f, 
	0.0f,  0.5f,  0.0f
}
```

In RAM, it is aligned as:

![[VBO_alignment_1.png]]

Knowing that, we can interpret this data using [[glVertexAttribPointer]] function as:

```cpp
glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 3 * sizeof(float), nullptr);
```

Meaning that we start from `0 bytes` offset, each vertex will take `3 * sizeof(float) = 12 bytes` in continuous memory.

___

But if, for example we specify vertex data as position + color pairs?

In vertex shader:

```cs
layout (location = 0) in vec3 aPos;  
layout (location = 1) in vec3 aColor;
```

On CPU side:

```cpp
constexpr float vertices[] = { 
	// positions       // colors 
	0.5f, -0.5f, 0.0f, 1.0f, 0.0f, 0.0f,
	-0.5f, -0.5f, 0.0f, 0.0f, 1.0f, 0.0f,
	0.0f, 0.5f, 0.0f, 0.0f, 0.0f, 1.0f 
};
```

In RAM, it would be aligned as:

![[VBO_alignemt_2.png]]

Now, to interpret that vertex data, we should alter the `glVertexAttribPointer` the next way:

```cpp
// Position
glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 6 * sizeof(float), nullptr);

// Color
glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 6 * sizeof(float), (void*)(sizeof(float) * 3));
```

Note that position pointer takes `nullptr (0 bytes)` as offset in a single vertex data token, but for color we need to use last 3 floats, so the offset would be `3 * sizeof(float) = 12 bytes`.

Also note that the stride is now `6 * sizeof(float) = 24 bytes`, as each vertex now is interpreted as position (`3 floats`) + color (`3 floats`) pair.