#lighting #rendering 

Material is a description of the visual part of an object.
Material can depict how does the object interact with light rays, or, for example, can describe how intense is the glow of an object.

Material is commonly represented as a set of variables that are used by [[Shader]]s to compute the resulting color.

```cpp
struct Material {  
    vec3 ambient;  
    vec3 diffuse;  
    vec3 specular;  
    float shininess;  
};
```

