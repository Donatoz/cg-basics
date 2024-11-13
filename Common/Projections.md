#rendering 

### Orthographic projection

An orthographic projection matrix defines a cube-like frustum box that defines the clipping space. Each vertex outside this space is clipped. 

Ortho-projection has width, height and length (depth). All the coordinates within the frustum will be mapped to NDC. 

![[Ortho_projection.png]]

Orthographic projection directly maps coords to 2D plane that is the screen, without taking perspective into account.

### Perspective projection

Within a perspective, each object seems smaller as much as far it is from the POV. Perspective projection tries to mimic this behavior using **projection matrix**, which manipulates `w` value of each vertex 4D coordinate, so the further away the coordinate is, the higher is its `w` value. Once transformed, each coordinate is in the range (`-w`, `w`), everything outside this range is clipped.

Once coordinates are in the clip space, perspective division is applied to them, so that each coordinate results in `(x/w, y/w, z/w)`. 

![[Perspective_projection.png]]