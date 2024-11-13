#lighting

Phong is one of many lighting models. It is pretty simple in terms of implementation and complexity, and consists of three components:

 1. **Ambient** - there is always some amount of light in every position of the world, so the objects are not completely black. To simulate this light, a constant color can be used.
 2. **Diffuse** - simulation of the light impact on an object. The bigger part of an object is faced towards light source, the brighter the object is.
 3. **Specular** - simulation of the bright spot on shiny objects. Specular lights are more inclined to the light color than object color.

![[Phong.png]]

##### Ambient lighting

Light usually does not come from a single light source, but from many light sources scattered all around us, even when they're not immediately visible.

One of the light properties is that it can scatter and bounce in many directions, that are not directly visible, light can thus reflect on other surfaces and have an indirect impact on the lighting of an object. There are several complex algorithms that simulate this behavior in different ways, like:

 - **Ray Tracing**
 - **Path Tracing
 - **Monte-Carlo integration
 - **BRDF**
 - **Metropolis light transport**
 - **Photon mapping**

The **ambient lighting** is pretty simple algorithm that takes the constant dim light color and adds it to the resulting color of **each** fragment. 

GLSL example:

```cpp

// Ambient lighting  
vec3 ambient = ambientStrength * lightColor;  

// further calculations ...
```

![[Ambient_example.png]]

##### Diffuse lighting

Diffuse lighting gives significant impact on the object color. The closer fragments are aligned to the light rays, the more bright they are.

Here is the scheme of how fragment reacts to the light ray:

![[Diffuse_lighting.png]]

The larger θ is, the less impact the light ray has on a fragment. 

In order to calculate fragment color affected by diffuse lighting, next values must be predefined:

 - Fragment normal
 - Light position (**world space**)
 - Fragment position (**world space**)

GLSL example (world space):

```cpp
// Diffuse lighting 
vec3 norm = normalize(vertexNormal);  
vec3 lightDir = normalize(lightPosition - fragPosition);  
float diff = max(dot(norm, lightDir), 0.0);  
vec3 diffuse = diff * lightColor; 

// further calculations ...
```

![[Diffuse_example.png]]
##### Specular lighting

Specular lighting, like diffuse lighting, is based on light direction and fragment normal vectors. Additionally, specular lighting uses the view direction.

![[Specular_lighting.png]]

The reflection vector is calculated by reflecting light direction around normal vector. Then, the angle between view direction and reflection vector is calculated, the smaller angle is, the stronger is specular light from the view perspective.

GLSL example (world space):

```cs
// Diffuse lighting calculations...

// Specular lighting
vec3 viewDir = normalize(viewPosition - fragPosition);  
vec3 reflectDir = reflect(-lightDir, norm);  
float spec = pow(max(dot(viewDir, reflectDir), 0.0), 32);  
vec3 specular = specularStrength * spec * lightColor;
```

![[Specular_example.png]]