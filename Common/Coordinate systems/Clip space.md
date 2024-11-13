#rendering #space 

The clip space contains the coordinates that are clipped out (if they do not fit) and transformed using **projection matrix**, which specifies a range of coordinates of (-1000, 1000) in each dimension, which is called **frustum** and each coordinate, that lays in that range, will not be clipped.

![[Clip_space.png]]

The projection matrix then converts coordinates within this specified range to normalized 2D device coordinates `(-1, 1)`. 