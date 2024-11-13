The light in 3D scene is not always a static phenomenon - it may have an origin (**source**) of its traversal.

Light casters are light source objects that cast the light in a specific way. There are different types of light casters:

 - Directional light
 - Point light
 - Spot light
 - Area light
 - *etc...*

### Directional light

If the light source is far away from the object, the light rays it emits may seem parallel to each other, meaning that for each object fragment the light direction is nearly the same. 

A directional light is modelled to be infinitely far away from any object, thus every object affected will have same light ray direction.

```cpp
struct Light { 
	// Light direction
	vec3 direction;
};
```


### Point light

A point light is the light source positioned somewhere in a 3D scene that illuminates light in all directions. Point light rays do not have infinite length, therefore they fade out over distance.

```cpp
struct Light { 
	// Light position
	vec3 position;
};
```

To reduce ray intensity over distance, **light attenuation** is used. Linear equation can be used to attenuate the light, like:
$$
F_{att}=\frac{1.0}{d}
$$
Resulting in a value which affects the intensity of shading components:

```cpp
float attenuation = 1.0 / length(light.position - fragPosition)

ambient *= attenuation;  
diffuse *= attenuation;  
specular *= attenuation;
```

However, such result seems not realistic, as lights are generally quite bright standing close by, but the brightness of a light source diminishes quickly at a distance

To reach more realistic results, the next equation is used instead:
$$
F_{att}=\frac{1.0}{K_c+K_lx \cdot d+K_q \cdot d^2}
$$
Where $K_c$ is **constant term**, $K_l$ is **linear term** and $K_q$ is **quadratic term**. 

The constant term is usually kept at `1.0`, so that denominator never reaches `0`. The linear term reduces the light intensity in linear form, and quadratic term defines the quadratic decrease of light intensity.

```cpp
struct Light { 
	// Light position
	vec3 position;
	
	float constant; 
	float linear; 
	float quadratic;
};
```

```cpp
float distance = length(light.position - fragPosition); float attenuation = 1.0 / (light.constant + light.linear * distance + light.quadratic * (distance * distance));
```

### Spot light

The spot light is a specific type of point light with one key difference: it shoots light rays in specific direction, the impact area of which may also be constrained.

```cpp
struct Light { 
	// Light position
	vec3 position;
	// Light direction
	vec3 direction;
	// Cutoff angle
	float cutOff;
};
```

