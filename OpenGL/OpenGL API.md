#api #opengl #khronos-group #opengl-3_3 #cpp

### Summary

**OpenGL** - an API currently maintained by **Khronos Group**.  Represents a large set of functionality that is used to manipulate computer graphics and images. 

### Context

OpenGL itself represents a large state machine, the state of which can be manipulated by mentioned functions. It is commonly referred as **context**. We can change the context and the perform rendering using this context.

### Objects

In OpenGL, there are several abstractions that provide an interface for mutations to perform. One of these abstractions is **Object**.

``` cpp
struct object_name { 
	float option1; 
	int option2; 
	char[] name; 
};
```

The context contains different objects that are exposed for mutation.

``` cpp
// The State of OpenGL 
struct OpenGL_Context { 
	// ... 
	object_name* object_Window_Target; 
	// ... 
};


// some code

// create object 
unsigned int objectId = 0;
glGenObject(1, &objectId);
// bind/assign object to context
glBindObject(GL_WINDOW_TARGET, objectId);
// set options of object currently bound to GL_WINDOW_TARGET 
glSetObjectOption(GL_WINDOW_TARGET, GL_OPTION_WINDOW_WIDTH, 800);
glSetObjectOption(GL_WINDOW_TARGET, GL_OPTION_WINDOW_HEIGHT, 600);
// set context target back to default
glBindObject(GL_WINDOW_TARGET, 0);

// ...
```

We can create objects using function `glGenObject(amount, &container)` and the bind to some target using `glBindObject(GL_Target, id)`. Note that id is provided by `glGenObject` function as return value.