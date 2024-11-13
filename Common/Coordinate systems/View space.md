#rendering #space 

The view space is referred to the camera or point of view (also known as **camera space**). World-space coordinates are transformed to the coordinates that are in front of camera view, so the space is now seen from the camera POV. 

This is usually accomplished with a combination of translations and rotations to translate/rotate the scene so that certain items are transformed to the front of the camera. These combined transformations are generally stored inside a **view matrix** that transforms world coordinates to view space.

> Imagine that we want to move camera by some delta. It is the same as moving the whole scene in inverse delta from the camera perspective. This is what view matrix roughly does.

![[View_space.png]]