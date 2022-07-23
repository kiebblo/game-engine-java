# game-engine-java
2D GAME ENGINE

- LWJGL - Lightweight Java Game Library (wrapper around graphics libraries - bindings of C code)
- OpenGL - Open Graphics Library (uploading data to the GPU and allows to draw using the GPU)
- GLFW - Graphics Library Framework (window handler and key events)
- Rendering 
	- Shaders
	- Meshes
	- Batching
-Animation System
	- Finite State Automata
	- Sprite Based Animation (implement keyframes for taming out animations in different lenghts)
-Physics
	- Static / Dynamic Physics
	- Collision Detection
	- Collision Resolution
-User Interface
	- Window Management
	- Fully Featured Level Editor
- Packaging and Distribution


1.- ** Starting the Project & Creating the Window

	1.- Java Project using Gradle
	On link below get the required dependencies
	https://www.lwjgl.org/download 
	
	project.ext.lwjglVersion = "3.3.1"
	project.ext.jomlVersion = "1.10.4"
	project.ext.lwjglNatives = "natives-windows"
	
	repositories {
		mavenCentral()
	}
	
	dependencies {
		implementation platform("org.lwjgl:lwjgl-bom:$lwjglVersion")
	
		implementation "org.lwjgl:lwjgl"
		implementation "org.lwjgl:lwjgl-assimp"
		implementation "org.lwjgl:lwjgl-glfw"
		implementation "org.lwjgl:lwjgl-nfd"
		implementation "org.lwjgl:lwjgl-openal"
		implementation "org.lwjgl:lwjgl-opengl"
		implementation "org.lwjgl:lwjgl-stb"
		runtimeOnly "org.lwjgl:lwjgl::$lwjglNatives"
		runtimeOnly "org.lwjgl:lwjgl-assimp::$lwjglNatives"
		runtimeOnly "org.lwjgl:lwjgl-glfw::$lwjglNatives"
		runtimeOnly "org.lwjgl:lwjgl-nfd::$lwjglNatives"
		runtimeOnly "org.lwjgl:lwjgl-openal::$lwjglNatives"
		runtimeOnly "org.lwjgl:lwjgl-opengl::$lwjglNatives"
		runtimeOnly "org.lwjgl:lwjgl-stb::$lwjglNatives"
		implementation "org.joml:joml:${jomlVersion}"
	}
	
	2.- Generate Main class to run Window
	our Window will have the get() method and the run() function on it
	The window needs to be set as a Singleton since we will only have one window at the run time.
	
	on the https://www.lwjgl.org/guide link we can find the one time setup of the screen
	includding the init() and loop() methods
	
		--"glfwWindow" is a memory address where the glfwCreateWindow is on the memory space
