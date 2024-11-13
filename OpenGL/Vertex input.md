#rendering #opengl 

OpenGL processes coordinates that are only in the range of -1.0 to 1.0 on all three axes. The coordinates in this range range are called **Normalized device coordinates (NDC)**, and **only** these coordinates can be seen on the screen, otherwise they will be discarded. This is one of the main responsibilities of the [[Vertex shader]].

NDC coordinates are transformed into **screen-space coordinates** via viewport transform using the data provided in [[glViewport]].

NDC coordinate system looks like this:


![[NDC_1.png]]


