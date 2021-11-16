# Urban Terror OpenGL Chams
Referenced in https://gamehacking.academy/lesson/5/4.

A chams hack for Urban Terror 4.3.4 that both reveals entities through walls and changes these models to a bright red color. It works by hooking the game's OpenGL function glDrawElements and disabling depth testing and textures for OpenGL.

This is done by locating the glDrawElements function inside the OpenGL library and creating a code cave at the start of the function. In the code cave, we check the number of vertices associated with the element. If it is over 500, we call glDepthRange to clear the depth clipping plane and glDepthFunc to disable depth testing. We then disable texture and color arrays and enable color material before setting the color to red with glColor.

Otherwise, we call these same functions to re-enable the depth clipping plane, re-enable depth testing, and re-enable textures.

This DLL must be injected into the Urban Terror process to work. One way to do this is to use a DLL injector. Another way is to enable AppInit_DLLs in the registry.
