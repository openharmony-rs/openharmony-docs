# OpenGL ES
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @samhu1989-->
<!--Designer: @shi-yang-2012-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->
OpenGL is a cross-platform graphics API that specifies a standard software interface for 3D graphics processing hardware. [OpenGL ES](https://www.khronos.org/opengles/) is a flavor of the OpenGL specification intended for embedded devices. OpenHarmony now supports OpenGL ES 3.2.

## Supported Capabilities

OpenGL ES 3.2

## Symbols Exported from the Standard Library

[OpenGL ES 3.2 Symbols Exported from Native APIs](openglesv3-symbol.md)

## Introducing OpenGL

To use OpenGL capabilities, you must add related dynamic link libraries (DLLs) and header files.

**Adding Dynamic Link Libraries**

Add the following libraries to **CMakeLists.txt**.

```txt
libace_ndk.z.so
libace_napi.z.so
libGLESv3.so
libEGL.so
```

**Including Header Files**

```c++
#include <ace/xcomponent/native_interface_xcomponent.h>
#include <EGL/egl.h>
#include <EGL/eglext.h>
#include <EGL/eglplatform.h>
#include <GLES3/gl3.h>
```

## References

To use the OpenGL ES API in your application development, familiarize yourself with the NDK development process and the **XComponent** usage, which are described in the following topics:

- [Getting Started with the NDK](../../napi/ndk-development-overview.md)

- [Node-API](./napi.md)

- [XComponentNode](../apis-arkui/js-apis-arkui-xcomponentNode.md)

- [XComponent](../apis-arkui/arkui-ts/ts-basic-components-xcomponent.md)

## OpenGL ES Extensions

- To obtain the official reference document for OpenGL ES extensions, visit [Khronos OpenGL ES Registry](https://registry.khronos.org/OpenGL/index_es.php).
- You can call **glGetString** to query the extensions supported by the chip. Before calling **glGetString**, you must initialize the context. The following is an example:

```c++
EGLDisplay display;
EGLConfig config;
EGLContext context;
EGLSurface surface;
EGLint majorVersion;
EGLint minorVersion;
EGLNativeWindowType win;
display = eglGetDisplay(EGL_DEFAULT_DISPLAY);
eglInitialize(display, &majorVersion, &minorVersion);
EGLint attribs[] = {
    EGL_RENDERABLE_TYPE,
    EGL_OPENGL_ES2_BIT,
    EGL_BLUE_SIZE, 8,
    EGL_GREEN_SIZE, 8,
    EGL_RED_SIZE, 8,
    EGL_NONE
};
eglChooseConfig(display, attribs, &config, 1, &numConfigs);
context = eglCreateContext(display, config, EGL_NO_CONTEXT, NULL);
surface = eglCreatePbufferSurface(display, config, NULL);
eglMakeCurrent(display, surface, surface, context);

char *strTest = new char[1024];
strTest = (char *)glGetString(GL_EXTENSIONS); // The return value of strTest lists all extensions supported, separated by spaces.
bool isHave = strTest.find("GL_OES_matrix_palette") != -1 ?
    true :
    false; // Check whether an extension exists. If yes, the value of isHave is true. If no, the value of isHave is false.
```

## Example

```cpp

void enableVertexAttrib(GLuint index, float *data, int32_t len)
{
    GLuint buffer;
    glGenBuffers(1, &buffer);
    glBindBuffer(GL_ARRAY_BUFFER, buffer);
    glBufferData(GL_ARRAY_BUFFER, len, data, GL_STATIC_DRAW);
    glVertexAttribPointer(index, TRIANGLES_POINT, GL_FLOAT, GL_FALSE, 0, 0);
    glEnableVertexAttribArray(index);
    return;
}

int32_t Init(void *window, int32_t width,  int32_t height)
{
    EGLNativeWindowType mEglWindow;
    EGLDisplay mEGLDisplay = EGL_NO_DISPLAY;
    EGLConfig mEGLConfig = nullptr;
    EGLContext mEGLContext = EGL_NO_CONTEXT;
    EGLContext mSharedEGLContext = EGL_NO_CONTEXT;
    EGLSurface mEGLSurface = nullptr;
    EGLint configsNum;
    mEglWindow = reinterpret_cast<EGLNativeWindowType>(window);
    
    // Initialize the EGL display.
    mEGLDisplay = eglGetDisplay(EGL_DEFAULT_DISPLAY);
    EGLint eglMajVers;
    EGLint eglMinVers;
    eglInitialize(mEGLDisplay, &eglMajVers, &eglMinVers);

    // Configure EGL.
    EGLint attribList[] = {
            EGL_SURFACE_TYPE, EGL_WINDOW_BIT, EGL_RENDERABLE_TYPE, EGL_OPENGL_ES3_BIT,
            EGL_RED_SIZE, 8,
            EGL_GREEN_SIZE, 8,
            EGL_BLUE_SIZE, 8,
            EGL_NONE
    };
    eglChooseConfig(mEGLDisplay, attribList, &mEGLConfig, 1, &configsNum);

    EGLint winAttribs[] = {EGL_GL_COLORSPACE_KHR, EGL_GL_COLORSPACE_SRGB_KHR, EGL_NONE};
    
    // Create an EGL surface.
    mEGLSurface = eglCreateWindowSurface(mEGLDisplay, mEGLConfig, mEglWindow, winAttribs);
    
    // Create an EGL context.
    EGLint attrib3_list[] = {
        EGL_CONTEXT_CLIENT_VERSION, 3,
    };
    mEGLContext = eglCreateContext(mEGLDisplay, mEGLConfig, mSharedEGLContext, attrib3_list);
    
    // Bind the EGL context to the surface.
    eglMakeCurrent(mEGLDisplay, mEGLSurface, mEGLSurface, mEGLContext);
    
    // Create a shader program.
    const char* g_vertexShader =
        "#version 300 es\n"
        "in vec4 a_pos;\n"
        "in vec4 a_color;\n"
        "uniform mat4 a_mx;\n"
        "uniform mat4 a_my;\n"
        "out vec4 v_color;\n"
        "void main() {\n"
        "    gl_Position = a_mx * a_my * a_pos;\n"
        "    v_color = a_color;\n"
        "}";
    
    const char* g_fragmentShader =
        "#version 300 es\n"
        "precision mediump float;\n"
        "in vec4 v_color;\n"
        "out vec4 fragColor;\n"
        "void main() {\n"
        "    fragColor = v_color;\n"
        "}";
    
    // Create a vertex shader.
    GLuint vertexShader = glCreateShader(GL_VERTEX_SHADER);
    glShaderSource(vertexShader, 1, &g_vertexShader, nullptr);
    glCompileShader(vertexShader);

    // Create a fragment shader.
    GLuint fragmentShader = glCreateShader(GL_FRAGMENT_SHADER);
    glShaderSource(fragmentShader, 1, &g_fragmentShader, nullptr);
    glCompileShader(fragmentShader);

    
    // Create a shader program.
    mProgramHandle = glCreateProgram();
    glAttachShader(mProgramHandle, vertexShader);
    glAttachShader(mProgramHandle, fragmentShader);
    glLinkProgram(mProgramHandle);
    
    // Use the shader program.
    glUseProgram(mProgramHandle);
    
    // Clear the resources.
    glDeleteShader(vertexShader);
    glDeleteShader(fragmentShader);
    
    return 0;
}

void Update(float angleXOffset, float angleYOffset)
{
    const float pi = 3.141592;
    
    // Create the vertex position data array vertexData.
    float g_vertexData[] = {
        -0.75, -0.50, -0.43, 0.75, -0.50, -0.43, 0.00,  -0.50, 0.87,  0.75, -0.50, -0.43,
        0.00,  -0.50, 0.87,  0.00, 1.00,  0.00,  0.00,  -0.50, 0.87,  0.00, 1.00,  0.00,
        -0.75, -0.50, -0.43, 0.00, 1.00,  0.00,  -0.75, -0.50, -0.43, 0.75, -0.50, -0.43,
    };
    
    // Create the vertex color array colorData.
    float g_colorData[] = {
        1, 0, 0, 1, 0, 0, 1, 0, 0, /*Red - face 1*/
        1, 0, 0, 1, 0, 0, 1, 0, 0, /*Red - face 2*/
        1, 0, 0, 1, 0, 0, 1, 0, 0, /*Red - face 3*/
        1, 0, 0, 1, 0, 0, 1, 0, 0 /*Red - face 4*/
    };
    
    // Vertex normal array normalData.
    float g_normalData[] = {
        0.00,  -1.00, 0.00,  0.00,  -1.00, 0.00,  0.00,  -1.00, 0.00, -0.83, -0.28, -0.48,
        -0.83, -0.28, -0.48, -0.83, -0.28, -0.48, -0.83, 0.28,  0.48, -0.83, 0.28,  0.48,
        -0.83, 0.28,  0.48,  0.00,  -0.28, 0.96,  0.00,  -0.28, 0.96, 0.00,  -0.28, 0.96,
    };
    
    // Set the viewport size.
    glViewport(0, 0, m_width, m_height);
    
    // Clear the color buffer.
    glClearColor(1.0f, 1.0f, 1.0f, 1.0f);
    glClear(GL_COLOR_BUFFER_BIT);
    
    // Obtain the location handles of the variables in the shader program.
    GLint aPos = glGetAttribLocation(mProgramHandle, "a_pos");
    GLint aColor = glGetAttribLocation(mProgramHandle, "a_color");
    GLint aNormal = glGetAttribLocation(mProgramHandle, "a_normal");
    GLint uLightColor = glGetUniformLocation(mProgramHandle, "u_lightColor");
    GLint uLightDirection = glGetUniformLocation(mProgramHandle, "u_lightDirection");
    GLint aMx = glGetUniformLocation(mProgramHandle, "a_mx");
    GLint aMy = glGetUniformLocation(mProgramHandle, "a_my");

    angleX = angleXOffset;
    angleY = angleYOffset;

    // Y-axis rotation angle.
    float radianY = (angleY * pi) / 180.0;
    float cosY = cosf(radianY);
    float sinY = sinf(radianY);
    float myArr[] = {
        cosY, 0, -sinY, 0,
        0, 1, 0, 0,
        sinY, 0, cosY, 0,
        0, 0, 0, 1
    };

    // Pass 4x4 matrix data to the shader.
    glUniformMatrix4fv(aMy, 1, false, myArr);

    // X-axis rotation angle.
    float radianX = (angleX * pi) / 180.0;
    float cosX = cosf(radianX);
    float sinX = sinf(radianX);
    float mxArr[] = {
        1, 0, 0, 0, 0, cosX, -sinX, 0, 0, sinX, cosX, 0, 0, 0, 0, 1
    };

    glUniformMatrix4fv(aMx, 1, false, mxArr);

    // Pass the color and direction data (RGB(1,1,1), unit vector (x,y,z)) to the parallel light.
    glUniform3f(uLightColor, 1.0, 1.0, 1.0);

    // Ensure that the vector (x,y,z) has a length of 1, that is, a unit vector.
    float x = 2.0 / sqrt(15);
    float y = 2.0 / sqrt(15);
    float z = 3.0 / sqrt(15);

    glUniform3f(uLightDirection, x, -y, z);

    // Create a buffer and pass the vertex position data g_vertexData.
    enableVertexAttrib(aPos, g_vertexData, sizeof(g_vertexData));
    enableVertexAttrib(aNormal, g_normalData, sizeof(g_normalData));
    // Create a color buffer and pass the vertex color data g_colorData.
    enableVertexAttrib(aColor, g_colorData, sizeof(g_colorData));

    glEnable(GL_DEPTH_TEST);

    // Draw the tetrahedron.
    glDrawArrays(GL_TRIANGLES, 0, TETRAHEDRON_POINT);
    
    // Swap the buffers.
    eglSwapBuffers(mEGLDisplay, mEGLSurface);
}
```

This example walks through the process of creating and setting up an OpenGL ES rendering environment using EGL to render a 3D tetrahedron. Below is a detailed breakdown of each step.

### Using eglGetDisplay to Obtain an EGL Display Connection
```cpp
EGLDisplay eglGetDisplay(EGLNativeDisplayType display_id);
```

**eglGetDisplay** is a function in the EGL library. It returns an EGLDisplay object to represent the connection to the rendering target device. If the display connection is unavailable, **EGL_NO_DISPLAY** is returned.

The **display_id** parameter indicates the local display type of the display. The **EGLNativeDisplayType** parameter is the window display type, which has different definitions on different platforms. If you just want to use the default display, use **EGL_DEFAULT_DISPLAY** without explicitly specifying **display_id**.

### Using eglInitialize to Initialize the EGL Display Connection
Call **eglInitialize** to initialize the EGL display connection obtained.
```cpp
EGLBoolean eglInitialize(EGLDisplay display,    // EGL display connection.
                         EGLint *majorVersion,  // Major version number of the EGL implementation. The value may be NULL.
                         EGLint *minorVersion); // Minor version number of the EGL implementation. The value may be NULL.
```
The function is used to initialize the internal data structure of the EGL, return the EGL version numbers, and save them in **majorVersion** and **minorVersion**.
If the initialization is successful, **EGL_TRUE** is returned. Otherwise, **EGL_FALSE** is returned. You can also call **EGLint eglGetError()** to query the EGL error status.

- **EGL_BAD_DISPLAY**: The specified EGL display is invalid.

- **EGL_NOT_INITIALIZED**: EGL cannot be initialized.

### Using eglChooseConfig to Determine the Rendering Configuration
After the EGL display connection is initialized, determine the type and configuration of the available surface in either of the following ways:
- Specify a set of required configurations and use **eglChooseConfig** to enable EGL to recommend the optimal configuration.

   You are advised to use this method if no special configuration is required, because it is easier to obtain the optimal configuration.

    ```cpp
    EGLBoolean eglChooseConfig(EGLDisplay dpy,     // Handle to the EGL display connection for which configurations are selected.
                        const EGLint *attrib_list, // An integer array of pointers to attributes. Each element in the array consists of an attribute name (for example, EGL_RED_SIZE) and attribute value, and the array is terminated with EGL_NONE. An example attribute array is {EGL_RED_SIZE, 8, EGL_GREEN_SIZE, 8, EGL_BLUE_SIZE, 8, EGL_NONE}.
                           EGLConfig *configs,     // An array of pointers to the selected configurations. The eglChooseConfig function selects the configurations that match the attributes from the available configurations and stores them in this array.
                           EGLint config_size,     // Size of the configs array.
                           EGLint *num_config);    // Number of configurations that match the attributes.
    ```

    ```cpp
    // Here, the following attributes are used:
	EGLint attribList[] = {
            EGL_SURFACE_TYPE, EGL_WINDOW_BIT, EGL_RENDERABLE_TYPE, EGL_OPENGL_ES3_BIT,  // The renderable type is OpenGL ES 3.
            EGL_RED_SIZE, 8, // The number of bits in the red buffer is 8.
            EGL_GREEN_SIZE, 8, // The number of bits in the green buffer is 8.
            EGL_BLUE_SIZE, 8,   // The number of bits in the blue buffer is 8.
            EGL_NONE
    };
    eglChooseConfig(mEGLDisplay, attribList, &mEGLConfig, 1, &configsNum);
    ```
   When you call the **eglChooseConfig** function, the system returns EGL configurations that match the specified attributes in **attribList**. The configurations are stored in the **mEGLConfig** parameter. In the sample code, **configsNum** is set to **1**, indicating that the **mEGLConfig** array can hold only one configuration. Although this setting limits the number of configurations returned, it is usually enough for most applications. Moreover, **configsNum** reflects the total number of configurations that meet the specified attributes, providing a full count of available options.

- Use **eglGetConfigs** to query all supported configurations and use **eglGetConfigAttrib** to filter the desired ones.

   The following describes how to use this method to obtain the desired configurations.

  ```cpp
  #include <EGL/egl.h>
  #include <iostream>
  #include <vector>
  int main() {
      // Initialize EGL.
      EGLDisplay display = eglGetDisplay(EGL_DEFAULT_DISPLAY);
      eglInitialize(display, nullptr, nullptr);
  
      // Obtain all the configurations.
      EGLint numConfigs;
      eglGetConfigs(display, nullptr, 0, &numConfigs);
      std::vector<EGLConfig> configs(numConfigs);
      eglGetConfigs(display, configs.data(), numConfigs, &numConfigs);
  
      // Select a proper configuration.
      EGLConfig chosenConfig = nullptr;
      for (const auto& config : configs) {
          EGLint redSize, greenSize, blueSize;
          eglGetConfigAttrib(display, config, EGL_RED_SIZE, &redSize);
          eglGetConfigAttrib(display, config, EGL_GREEN_SIZE, &greenSize);
          eglGetConfigAttrib(display, config, EGL_BLUE_SIZE, &blueSize);
          if (redSize == 8 && greenSize == 8 && blueSize == 6) {
              chosenConfig = config;
              break;
          }
      }
  
      // If no configuration is selected, print the error information and exit.
      if (!chosenConfig) {
          std::cerr << "Failed to find a suitable EGL configuration." << std::endl;
          return 1;
      }
      return 0;
  }
  ```

  ```cpp
  EGLBoolean eglGetConfigs(EGLDisplay display, // Handle to the EGL display connection for which configurations are selected.
                           EGLConfig *configs, // Array for storing the obtained configurations.
                           EGLint config_size, // Size of the configs array.
                           EGLint *num_config); // Number of available configurations.
  ```
  
   The **eglGetConfigs** function can be used in either of the following ways:
  
  - If a null pointer is passed in to **configs**, **EGL_TRUE** is returned and the number of available configurations obtained is saved in **num_config**. In this case, **configs** can be initialized based on the number to store the configurations. For details, see the preceding code.
  - If **configs** is configured to accept all configurations, all configurations obtained are saved in **configs**. You can filter them as required and store the desired ones.
  
  ```cpp
  // Select a proper configuration.
     EGLConfig chosenConfig = nullptr;
         for (const auto& config : configs) {
             EGLint redSize, greenSize, blueSize;
             eglGetConfigAttrib(display, config, EGL_RED_SIZE, &redSize);
             eglGetConfigAttrib(display, config, EGL_GREEN_SIZE, &greenSize);
             eglGetConfigAttrib(display, config, EGL_BLUE_SIZE, &blueSize);
             if (redSize == 8 && greenSize == 8 && blueSize == 6) {
                 chosenConfig = config;
                 break;
             }
         }
  ```
  
  The preceding code snippet traverses each configuration in **configs** and uses **eglGetConfigAttrib** to query the value of a specific attribute in the configuration, save the value in the fourth parameter, check whether the configuration is the desired one, and if yes, save the configuration. If the call is successful, **EGL_TRUE** is returned. Otherwise, **EGL_FALSE** is returned. In the latter case, you can use **eglGetError** to obtain the failure cause. If **EGL_BAD ATTRIBUTE** is returned, the attribute is invalid.
  
  ```cpp
  EGLBoolean eglGetConfigAttrib(EGLDisplay display,     // Handle to the EGL display connection for which configurations are selected.
                                     EGLConfig config, // EGL configuration to query.
                                     EGLint attribute, // Attribute identifier of the EGLint type, indicating the attribute to query.
                                     EGLint *value); // Pointer to the variable of the EGLint type, which is used to store the attribute value obtained.
  ```


### Using eglCreateWindowSurface to Create a Window Surface

After obtaining the EGL configurations that meet the rendering requirements, use **eglCreateWindowSurface** to create a window surface.
```cpp
EGLSurface eglCreateWindowSurface(EGLDisplay dpy,             // EGL display connection to be associated with the window surface.
                                  EGLConfig config,           // EGL configuration of the window surface to create.
                                  EGLNativeWindowType win,    // Parameter of the EGLNativeWindowType type. It is the handle or identifier of the window and is used to associate with the EGL surface.
                                  const EGLint *attrib_list); // Pointer to the EGL attribute list. It specifies the attributes of the window surface. It is an integer array terminating with EGL_NONE.
```
The following values can be passed in to **attrib_list** of **eglCreateWindowSurface**:

```cpp
EGL_RENDER_BUFFER EGL_SINGLE_BUFFER or EGL_BACK_BUFFER
EGL_SINGLE_BUFFER // There is only one render buffer on the EGL surface. After the rendering is complete, the content in the render buffer is directly displayed on the screen. As a result, screen flickering or tearing may occur.
EGL_BACK_BUFFER // There is a front buffer and a back buffer. After the rendering is complete, the content in the render buffer is first rendered to the back buffer, and then the content in the back buffer is displayed on the screen by means of buffer swapping. In this way, screen flickering or tearing can be avoided. 
// The default value is EGL_BACK_BUFFER. If this parameter is set to null, the default value is used.
```
The possible causes of a failure to call **eglCreateWindowSurface** are as follows:

- **EGL_BAD_MATCH**: The window attributes do not match the EGL configuration. This may be because the EGL configuration does not support rendering to the window (the **EGL_SURFACE_TYPE** attribute is not set to **EGL_WINDOW_BIT**).

- **EGL_BAD_CONFIG**: The EGL configuration is not supported by the system.

- **EGL_BAD_NATIVE_WINDOW**: The window handle is invalid.

- **EGL_BAD_ALLOC**: Resources cannot be created for a new EGL window or there is already an EGL configuration associated with the window.

```cpp
EGLint attribList[] = { EGL_RENDER_BUFFER, EGL_BACK_BUFFER, EGL_NONE };
EGLSurface surface = eglCreateWindowSurface(display, config, nativeWindow, attribList);
if (surface == EGL_NO_SURFACE) {
    switch (eglGetError()) {
        case EGL_BAD_MATCH:
            // Check the window and EGL configuration to determine the compatibility, or check whether the EGL configuration supports rendering to the window.
            break;
        case EGL_BAD_CONFIG:
            // Check whether the EGL configuration is valid.
            break;
        case EGL_BAD_NATIVE_WINDOW:
            // Check whether the EGL native window is valid.
            break;
        case EGL_BAD_ALLOC:
            // Resources are insufficient. Handle and rectify the fault.
            break;
        default:
            // Handle other errors.
            break;
    }
}
```
The process of using the **XComponent** to obtain a native window is as follows:
1. Define the **XComponent** and set the **XComponentController** in ArkTS. The **XComponent** is used to embed rendering content implemented based on graphics APIs such as OpenGL or Vulkan in the UI.
   ```typescript
   Column() {
       XComponent({
           id: 'myXComponent',
           type: XComponentType.SURFACE,
           controller: this.xComponentController
       })
   }
   ```
2. Create an **XComponentController** child class and implement its callbacks.
   ```typescript
   class MyXComponentController extends XComponentController {
       onSurfaceCreated(surfaceId: string): void {
           console.info(`onSurfaceCreated surfaceId: ${surfaceId}`);
           nativeRender.SetSurfaceId(BigInt(surfaceId));
           // The surface ID will be used to associate with the native window.
       }

       onSurfaceChanged(surfaceId: string, rect: SurfaceRect): void {
           console.info(`onSurfaceChanged surfaceId: ${surfaceId}`);
       }

       onSurfaceDestroyed(surfaceId: string): void {
           console.info(`onSurfaceDestroyed surfaceId: ${surfaceId}`);
       }
   }
   ```
3. Use the surface ID to obtain the native window. The surface ID is generated during the XComponent creation. In the **onSurfaceCreated** callback, you can use **OH_NativeWindow_CreateNativeWindowFromSurfaceId** to obtain a native window based on the surface ID.
   ```cpp
   napi_value PluginManager::SetSurfaceId(napi_env env, napi_callback_info info)
   {
       int64_t surfaceId = ParseId(env, info);
       OHNativeWindow *nativeWindow;
       PluginRender *pluginRender;
       if (windowMap_.find(surfaceId) == windowMap_.end()) {
           OH_NativeWindow_CreateNativeWindowFromSurfaceId(surfaceId, &nativeWindow);
           windowMap_[surfaceId] = nativeWindow;
       } else {
           return nullptr;
       }
       if (pluginRenderMap_.find(surfaceId) == pluginRenderMap_.end()) {
           pluginRender = new PluginRender(surfaceId);
           pluginRenderMap_[surfaceId] = pluginRender;
       }
       pluginRender->InitNativeWindow(nativeWindow);
       return nullptr;
   }
   ```
<!--Del-->
For details about how to use the **XComponent**, see [ArkTS XComponent Usage Example](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Native/XComponent).
<!--DelEnd-->

### Using eglCreateContext to Create a Rendering Context

Use **eglCreateContext** to create an EGL rendering context and associate it with a specific display and configuration. You can specify a shared context to share status information with an existing OpenGL context. The parameters in the function are described as follows:

```cpp
EGLContext eglCreateContext(EGLDisplay display,        // Type of the EGL display connection for which the context is to be created.
                            EGLConfig config,          // Type of the EGL configuration associated with the context.
                            EGLContext shareContext,   // Type of the EGL context whose status information is to be shared with the newly created context. If you do not want to share the status information, pass in EGL_NO_CONTEXT.
                            const EGLint *attribList); // Pointer to the attribute list. It specifies the attributes of the context. An attribute list is a series of attribute-value pairs terminating with EGL_NONE.
```
The value of **attribList** in **eglCreateContext** is as follows:
```cpp
EGLint attrib3_list[] = {
    EGL_CONTEXT_CLIENT_VERSION, 3, // Context type related to OpenGL ES version 3.
    EGL_NONE
};
```

If **eglCreateContext** fails to create the rendering context, the possible cause is **EGL_BAD_CONFIG**, which means that the EGL configuration is invalid.

### Using eglMakeCurrent to Attach the EGL Rendering Context to the EGL Surface

```cpp
EGLBoolean eglMakeCurrent(EGLDisplay display, // Handle to the EGL display connection.
                          EGLSurface draw, // Handle to the EGL draw surface.
                          EGLSurface read, // Handle to the EGL read surface. It is used to read pixels. Generally, you can set this parameter to the same value as draw.
                          EGLContext context); // Handle to the EGL rendering context to be attached to the surface.
```

### Creating and Using a Shader Program

```cpp
// Create a vertex shader.
GLuint vertexShader = glCreateShader(GL_VERTEX_SHADER);
glShaderSource(vertexShader, 1, &g_vertexShader, nullptr);
glCompileShader(vertexShader);

// Create a fragment shader.
GLuint fragmentShader = glCreateShader(GL_FRAGMENT_SHADER);
glShaderSource(fragmentShader, 1, &g_fragmentShader, nullptr);
glCompileShader(fragmentShader);

// Create a shader program.
mProgramHandle = glCreateProgram();
glAttachShader(mProgramHandle, vertexShader);
glAttachShader(mProgramHandle, fragmentShader);
glLinkProgram(mProgramHandle);

// Use the shader program.
glUseProgram(mProgramHandle);
```

```cpp
GLuint glCreateShader(GLenum shaderType);
```
Use **glCreateShader** to create a shader object of a specified type and return a handle to the object. The **shaderType** parameter specifies the type of shader to create, which can be **GL_VERTEX_SHADER** (vertex shader) or **GL_FRAGMENT_SHADER** (fragment shader).

```cpp
void glShaderSource(GLuint shader, GLsizei count, const GLchar \**string, const GLint *length);
```

Use **glShaderSource** set the source code of the shader object. The following parameters are available in the function:

- **shader**: identifier of the shader object for which the source code is set.
- **count**: number of source code strings.
- **string**: array of pointers to the source code strings.
- **length**: pointer to an integer array that contains the length of each source code string. The value can be a null pointer, indicating that each string ends with **null**.

```cpp
void glCompileShader(GLuint shader);
```

Use **glCompileShader** to compile a shader object, where the **shader** parameter is the identifier of the target shader object.

```cpp
GLuint glCreateProgram(void);
```

Use **glCreateProgram** to create a shader program object and return the object identifier.

```cpp
void glAttachShader(GLuint program, GLuint shader);
```

Use **glAttachShader** to attach a shader object to a shader program object. The **program** parameter is the identifier of the target shader program object, and the **shader** parameter is the identifier of the target shader object.

```cpp
void glLinkProgram(GLuint program);
```

Use **glLinkProgram** to link a shader program object, that is, to link the shader attached to the program object to an executable rendering pipeline.

The **program** parameter is the identifier of the target shader program object. After the shader program is linked, OpenGL merges the code in each individual shader object into an executable rendering pipeline, performs connector optimization to optimize the performance of the rendering pipeline, and binds the **Uniform** variable to the information about the Uniform block.

```cpp
void glUseProgram(GLuint program);
```
Use **glUseProgram** to activate a shader program object. After **glUseProgram** is called, all rendering calls are processed using the activated shader program.

You can use the following code to check whether the call of **glCompileShader** is normal:

```cpp
// Compile the shader.
glCompileShader(shader);

// Check the compilation status.
glGetShaderiv(shader, GL_COMPILE_STATUS, &compiled);

if (!compiled)
{
    GLint infoLen = 0;
    // Obtain the length of the shader information log.
    glGetShaderiv(shader, GL_INFO_LOG_LENGTH, &infoLen);
    if ( infoLen > 1 )
    {
        // Allocate the memory for storing the information log.
        char *infoLog = malloc(sizeof(char) * infoLen);
        // Obtain and print the shader information log.
        glGetShaderInfoLog(shader, infoLen, NULL, infoLog);
        esLogMessage("Error compiling shader:\n%s\n", infoLog);
        // Release the allocated memory.
        free(infoLog);
    }
    // Delete the shader that fails to be compiled.
    glDeleteShader(shader);
    return 0;
}
```

You can use the following code to check whether the call of **glLinkProgram** is normal:

```cpp
// Link the program object.
glLinkProgram(programObject);

// Check the linking status.
glGetProgramiv(programObject, GL_LINK_STATUS, &linked);

if (!linked)
{
    GLint infoLen = 0;
    // Obtain the length of the program object information log.
    glGetProgramiv(programObject, GL_INFO_LOG_LENGTH, &infoLen);
    if (infoLen > 1)
    {
        // Allocate the memory for storing the information log.
        char *infoLog = malloc(sizeof(char) * infoLen);
        // Obtain and print the information log of the program object.
        glGetProgramInfoLog(programObject, infoLen, NULL, infoLog);
        esLogMessage("Error linking program:\n%s\n", infoLog);
        // Release the allocated memory.
        free(infoLog);
    }
    // Delete the program object that fails to be linked.
    glDeleteProgram(programObject);
    return FALSE;
}
```

### Using glViewport to Set the Viewport

```cpp
void glViewport(GLint x, GLint y, GLsizei width, GLsizei height)
```

Use **glViewport** to set the viewport and specify the position and size of the OpenGL ES rendering area in the window. The **x** and **y** parameters specify the coordinates of the lower-left corner of the viewport in the window. The **width** and **height** parameters specify the width and height of the viewport.

### Using glClearColor to Set the Color Used to Clear the Color Buffer

```cpp
void glClearColor(GLfloat red, GLfloat green, GLfloat blue, GLfloat alpha);
```
In the **glClearColor(1.0f, 1.0f, 1.0f, 1.0f)** function, the color used for clearing the color buffer is set to (1.0, 1.0, 1.0). That is, the red component is 1.0, the green component is 1.0, the blue component is 1.0, and the alpha value is 1.0 (opaque).

### Using glClear to Clear Buffers

```cpp
void glClear(GLbitfield mask);
```
Use **glClear** to clear a buffer. The **mask** parameter specifies the buffer to clear. It can be a combination of the following values:
- **GL_COLOR_BUFFER_BIT**: clears the color buffer.
- **GL_DEPTH_BUFFER_BIT**: clears the depth buffer.
- **GL_STENCIL_BUFFER_BIT**: clears the stencil buffer.

You can call **glClear(GL_COLOR_BUFFER_BIT)** to clear the color buffer and fill the buffer with the color set by **glClearColor**. Clearing the color buffer is a common operation before you start frame rendering. This operation ensures that each pixel on the screen is initialized to the specified color value. It is also a mandatory preparation for drawing a new frame, similar to painting a background color on the canvas to start a new painting.

### Using glGetAttribLocation to Obtain the Location of an Attribute Variable

```cpp
GLint glGetAttribLocation(GLuint program, const GLchar *name);
```

Use **glGetAttribLocation** to obtain the location of an attribute variable in a vertex shader. This location is determined based on the attribute name when the vertex shader program is compiled and linked. **program** is the program object to be queried, and **name** is the name of the attribute variable whose location is to be queried.

### Using glGetUniformLocation to Obtain the Location of a Uniform Variable

```cpp
GLint glGetUniformLocation(GLuint program, const GLchar *name);
```

Use **glGetUniformLocation** to obtain the location of a uniform variable in a program object. **program** is the program object to be queried, and **name** is the name of the uniform variable whose location is to be queried.

### Using glUniformMatrix4fv to Pass a 4 x 4 Matrix

```cpp
void glUniformMatrix4fv(GLint location, GLsizei count, GLboolean transpose, const GLfloat *value);
```

Use **glGetUniformLocation** to obtain the location of a uniform variable in a shader. The following parameters are available in the function:
- **location**: location of the uniform variable to modify.
- **count**: Number of matrices to modify. If the target uniform variable is not an array, the value must be **1**. If the target uniform variable is an array, the value must be greater than or equal to **1**.
- **transpose**: whether to transpose the matrix. If the value is **GL_FALSE**, the matrix is passed in column-major order. If the value is **GL_TRUE**, the matrix is passed in row-major order.
- **value**: pointer to an array of **count** elements that will be used to update the specified uniform variable.

### Using glUniform3f to Pass Colors and Directions to a Shader

```cpp
void glUniform3f(GLint location, GLfloat v0, GLfloat v1, GLfloat v2);
```

Use **glUniform3f** to set the value of a uniform variable for the current program object. **location** is the position of the variable, and **v0**, **v1**, and **v2** are the new values.

### Creating a Buffer and Uploading Data to the GPU

```cpp
GLuint buffer;
glGenBuffers(1, &buffer);                                                  // Generate a buffer object.
glBindBuffer(GL_ARRAY_BUFFER, buffer);                                     // Bind the buffer, and set it as the current one.
glBufferData(GL_ARRAY_BUFFER, len, data, GL_STATIC_DRAW);                  // Upload data to the GPU.
glVertexAttribPointer(index, TRIANGLES_POINT, GL_FLOAT, GL_FALSE, 0, 0);   // Set the vertex attribute pointer.
glEnableVertexAttribArray(index);                                          // Enable the vertex attribute array.
```
```cpp
void glBindBuffer(GLenum target,   // target specifies the buffer target to bind. The value can be one of the following:
                                   // GL_ARRAY_BUFFER: stores vertex attribute data.
                                   // GL_ELEMENT_ARRAY_BUFFER: stores index data and other data.
                  GLuint buffer);  // buffer specifies the name of the buffer object to bind.
```
```cpp
void glBufferData(GLenum target,       // target specifies the type of the buffer object. The value can be one of the following:
                                       // GL_ARRAY_BUFFER: stores vertex attribute data.
                                       // GL_ELEMENT_ARRAY_BUFFER: stores index data.
                  GLsizeiptr size,     // Size (in bytes) of the buffer to be allocated.
                  const GLvoid* data,  // Pointer to the initial data to be copied to the buffer.
                  GLenum usage);       // Expected buffer usage mode. The value can be one of the following:
                                       // GL_STATIC_DRAW: Data is rarely modified and used multiple times.
                                       // GL_DYNAMIC_DRAW: Data is frequently modified and used multiple times.
                                       // GL_STREAM_DRAW: Data is modified and used a few times.
```

Once **glBufferData** is called, the data is copied into an OpenGL buffer and stored in the GPU's memory. This allows the data to be efficiently accessed and processed on the GPU without frequent transfers from CPU memory, improving rendering performance.

```cpp
void glVertexAttribPointer(GLuint index,         // Start index of the vertex array. The index is bound to the attribute variable in the vertex shader. (layout (location = 0) in vec3 aPos;)
                           GLint size,           // Number of components of each vertex attribute.
                           GLenum type,          // Type of each component.
                           GLboolean normalized, // Whether to map the vertex data to [0, 1] or [-1, 1] when accessing the data.
                           GLsizei stride,       // Stride between the vertex attributes. For precision arrangement, set this parameter to 0.
                           const void *offset);  // Offset of the attribute in the buffer. It is the position from which data reading starts in the buffer.
```

```cpp
void glEnableVertexAttribArray(GLuint index);
```

Use **glEnableVertexAttribArray** to enable an array of vertex attributes with a specified index. For example, you can call **glEnableVertexAttribArray(0)** to enable the vertex attribute array with the location index of **0**.

### Enabling Features

```cpp
void glEnable(GLenum cap);
```

Use **glEnable** to activate various features, with the specific feature determined by the **cap** parameter:
- **GL_BLEND**: enables color blending for effects like translucency.
- **GL_DEPTH_TEST**: enables depth testing to hide obscured graphics based on depth.
- **GL_CULL_FACE**: culls polygons based on their winding order in window coordinates.

### Drawing and Displaying Primitives

```cpp
void glDrawArrays(GLenum mode,   // Type of the primitive to draw. For example, GL_TRIANGLES indicates that a triangle will be drawn.
                  GLint first,   // Start index of the vertex array to draw.
                  GLsizei count // Number of vertices to draw.
                  );
```

Use **glDrawArrays** to draw primitives based on the currently bound vertex array, vertex attributes, and other settings.

```cpp
EGLBoolean eglSwapBuffers(EGLDisplay dpy,      // EGL display connection.
                          EGLSurface surface); // EGL surface whose buffers are to be swapped.
```

Use **eglSwapBuffers** to swap the front and back buffers and display the rendering result on the screen.

<!--RP1--><!--RP1End-->



