#opengl #buffers #rendering 

An [[OpenGL API]] object that stores all of the state needed to supply vertex data. It stores the format of the vertex data (e.g. provided by `glVertexAttribPointer`) as well as [[Vertex buffer object (VBO)|VBO]]'s that provide vertex data arrays.

VAO is not copying or freezing VBO states or data, so any changes done to the VBO's will be effective on the VAO.