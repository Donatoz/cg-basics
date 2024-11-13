#rendering #technique

When drawing in a single buffer, the resulting image may flicker as the draw process involves updating each pixel color one by one. This **is not an instant process**, so a user can see a part of previous frame behind the new one. The **double buffering** is being used to fix that issue.

The **front buffer** contains the final output image that is shown on the screen, while all rendering happens at **back buffer**. As soon as all rendering commands are finished on the back buffer, it is being swapped with the front buffer, so the front buffer contains up-to-date image.