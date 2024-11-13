#rendering #space

When working with vertices in a 3D scene, in the very end of all calculations and transformations, they are required to fit the screen space of the target surface before performing rasterization and blending.

In order to accomplish this task, several coordinate systems are used to transform vertices between them. The purpose of using multiple coordinate systems is that several transformations and calculations are easier to perform in certain systems. 

There are 5 common coordinate systems for transformations:

- **Local Space** (or **Object Space**)
- **World Space**
- **View Space** (or **Eye Space**)
- **Clip Space**
- **Screen Space**

### Transformation process

Overall process of transforming local space vertex to the screen space:

![[Coordinate_spaces.png]]

1. **Local coordinates** are the coordinates of given object relative to its local origin.
2. The next step is to transform these local coordinates to **world-space coordinates** which are global coordinates of the world. These coordinates are relative to the **world origin**, with many other objects placed relative to world origin as well.
3. After that, world-space coordinates are transformed to **view-space coordinates** in such way that each coordinated is positioned as it is seen from the camera or viewer point of view.
4. Next, view-space coordinates are projected to **clip coordinates**. Clip coordinates are transformed to the range of (-1, 1) and determine which vertices will remain on the screen. Projection to clip-space coordinates can bring perspective if using perspective projection.
5. Lastly, clip coordinates are transformed to **screen coordinates** via viewport transformation that transforms coords from (-1, 1) range to the range defined by screen host (e.g. in case of OpenGL, it is defined by [[glViewport]]).

After all these transformations, vertices are sent to a rasterizer and turned into fragments.

*See [[Local space]], [[World space]], [[View space]], [[Clip space]]*.

### Local space to clip space

Vertex coordinate, starting from local space, is transformed to the clip space by:

$$
V_{clip} = M_{proj} \cdot M_{view} \cdot M_{model} \cdot V_{local}
$$