# Native Image Development (C/C++)
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @Felix-fangyang; @li_hui180; @dingpy-->
<!--Designer: @conan13234-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
## When to Use

The native image module is used for associating a surface with an OpenGL external texture. It functions as the consumer of a graphics queue. You can use the APIs of this module to obtain and use a buffer, and output the buffer content to an OpenGL external texture.
The following scenario is common for native image development:

* Use the native image APIs to create an **OH_NativeImage** instance as the consumer and obtain the corresponding **OHNativeWindow** instance (functioning as the producer). Use the native window APIs to fill in and flush the buffer, and then use the native image APIs to update the buffer content to an OpenGL ES texture.<br> The native image module must be used together with the native window, native buffer, EGL, and GLES3 modules.

## Available APIs

| API                                                      | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| OH_NativeImage_Create (uint32_t textureId, uint32_t textureTarget) | Creates an **OH_NativeImage** instance to be associated with the specified OpenGL ES texture ID and target. This function must be used in pair with **OH_NativeImage_Destroy**. Otherwise, memory leak occurs.|
| OH_NativeImage_AcquireNativeWindow (OH_NativeImage \*image)  | Obtains an **OHNativeWindow** instance associated with an **OH_NativeImage** instance. It is unnecessary to manually release this **OHNativeWindow** with **OH_NativeWindow_DestroyNativeWindow** as it will be automatically freed upon calling **OH_NativeImage_Destroy**. Failing to do so could result in memory access violations after the memory has been freed, which might cause the application to crash.|
| OH_NativeImage_AttachContext (OH_NativeImage \*image, uint32_t textureId) | Attaches an **OH_NativeImage** instance to the current OpenGL ES context. The OpenGL ES texture will be bound to an **GL_TEXTURE_EXTERNAL_OES** instance and updated through the **OH_NativeImage** instance.|
| OH_NativeImage_DetachContext (OH_NativeImage \*image)        | Detaches an **OH_NativeImage** instance from the current OpenGL ES context.             |
| OH_NativeImage_UpdateSurfaceImage (OH_NativeImage \*image)   | Updates the OpenGL ES texture associated with the latest frame through an **OH_NativeImage** instance.     |
| OH_NativeImage_GetTimestamp (OH_NativeImage \*image)         | Obtains the timestamp of the texture image that recently called the **OH_NativeImage_UpdateSurfaceImage** function.|
| OH_NativeImage_GetTransformMatrix (OH_NativeImage \*image, float matrix[16]) | Obtains the transformation matrix of the texture image that recently called the **OH_NativeImage_UpdateSurfaceImage** function.|
| OH_NativeImage_Destroy (OH_NativeImage \*\*image)            | Destroys an **OH_NativeImage** instance created by calling **OH_NativeImage_Create**. After the instance is destroyed, the pointer to it is assigned **NULL**.|

For details about the APIs, see [native_image](../reference/apis-arkgraphics2d/capi-oh-nativeimage.md).

## How to Develop

The following steps describe how to use the native Image APIs to create an **OH_NativeImage** instance as the consumer and update the data to a OpenGL external texture.

**Adding Dynamic Link Libraries**

Add the following libraries to **CMakeLists.txt**:

```txt
libEGL.so
libGLESv3.so
libnative_image.so
libnative_window.so
libnative_buffer.so
```

**Including Header Files**

```c++
#include <iostream>
#include <string>
#include <EGL/egl.h>
#include <EGL/eglext.h>
#include <GLES3/gl3.h>
#include <GLES2/gl2ext.h>
#include <sys/mman.h>
#include <native_image/native_image.h>
#include <native_window/external_window.h>
#include <native_buffer/native_buffer.h>
```

1. Initialize the EGL environment.

   Refer to the code snippet below. For details about how to use the **XComponent**, see [XComponent Development](../ui/napi-xcomponent-guidelines.md).
   ```c++   
   using GetPlatformDisplayExt = PFNEGLGETPLATFORMDISPLAYEXTPROC;
   constexpr const char *EGL_EXT_PLATFORM_WAYLAND = "EGL_EXT_platform_wayland";
   constexpr const char *EGL_KHR_PLATFORM_WAYLAND = "EGL_KHR_platform_wayland";
   constexpr int32_t EGL_CONTEXT_CLIENT_VERSION_NUM = 2;
   constexpr char CHARACTER_WHITESPACE = ' ';
   constexpr const char *CHARACTER_STRING_WHITESPACE = " ";
   constexpr const char *EGL_GET_PLATFORM_DISPLAY_EXT = "eglGetPlatformDisplayEXT";
   EGLContext eglContext_ = EGL_NO_CONTEXT;
   EGLDisplay eglDisplay_ = EGL_NO_DISPLAY;
   static inline EGLConfig config_;
   static inline EGLSurface eglSurface_;
   // OHNativeWindow obtained from the XComponent.
   OHNativeWindow *eglNativeWindow_;
   
   // Check the EGL extension.
   static bool CheckEglExtension(const char *extensions, const char *extension) {
       size_t extlen = strlen(extension);
       const char *end = extensions + strlen(extensions);
   
       while (extensions < end) {
           size_t n = 0;
           if (*extensions == CHARACTER_WHITESPACE) {
               extensions++;
               continue;
           }
           n = strcspn(extensions, CHARACTER_STRING_WHITESPACE);
           if (n == extlen && strncmp(extension, extensions, n) == 0) {
               return true;
           }
           extensions += n;
       }
       return false;
   }
   
   // Obtain the display.
   static EGLDisplay GetPlatformEglDisplay(EGLenum platform, void *native_display, const EGLint *attrib_list) {
       static GetPlatformDisplayExt eglGetPlatformDisplayExt = NULL;
   
       if (!eglGetPlatformDisplayExt) {
           const char *extensions = eglQueryString(EGL_NO_DISPLAY, EGL_EXTENSIONS);
           if (extensions && (CheckEglExtension(extensions, EGL_EXT_PLATFORM_WAYLAND) ||
                              CheckEglExtension(extensions, EGL_KHR_PLATFORM_WAYLAND))) {
               eglGetPlatformDisplayExt = (GetPlatformDisplayExt)eglGetProcAddress(EGL_GET_PLATFORM_DISPLAY_EXT);
           }
       }
   
       if (eglGetPlatformDisplayExt) {
           return eglGetPlatformDisplayExt(platform, native_display, attrib_list);
       }
   
       return eglGetDisplay((EGLNativeDisplayType)native_display);
   }
   
   static void InitEGLEnv() {
       // Obtain the display.
       eglDisplay_ = GetPlatformEglDisplay(EGL_PLATFORM_OHOS_KHR, EGL_DEFAULT_DISPLAY, NULL);
       if (eglDisplay_ == EGL_NO_DISPLAY) {
           std::cout << "Failed to create EGLDisplay gl errno : " << eglGetError() << std::endl;
       }
   
       EGLint major, minor;
       // Initialize the EGL display.
       if (eglInitialize(eglDisplay_, &major, &minor) == EGL_FALSE) {
           std::cout << "Failed to initialize EGLDisplay" << std::endl;
       }
   
       // Bind the OpenGL ES API.
       if (eglBindAPI(EGL_OPENGL_ES_API) == EGL_FALSE) {
           std::cout << "Failed to bind OpenGL ES API" << std::endl;
       }
   
       unsigned int glRet;
       EGLint count;
       EGLint config_attribs[] = {EGL_SURFACE_TYPE,
                                  EGL_WINDOW_BIT,
                                  EGL_RED_SIZE,
                                  8,
                                  EGL_GREEN_SIZE,
                                  8,
                                  EGL_BLUE_SIZE,
                                  8,
                                  EGL_ALPHA_SIZE,
                                  8,
                                  EGL_RENDERABLE_TYPE,
                                  EGL_OPENGL_ES3_BIT,
                                  EGL_NONE};
   
       // Obtain a valid system configuration.
       glRet = eglChooseConfig(eglDisplay_, config_attribs, &config_, 1, &count);
       if (!(glRet && static_cast<unsigned int>(count) >= 1)) {
           std::cout << "Failed to eglChooseConfig" << std::endl;
       }
   
       static const EGLint context_attribs[] = {EGL_CONTEXT_CLIENT_VERSION, EGL_CONTEXT_CLIENT_VERSION_NUM, EGL_NONE};
   
       // Create a context.
       eglContext_ = eglCreateContext(eglDisplay_, config_, EGL_NO_CONTEXT, context_attribs);
       if (eglContext_ == EGL_NO_CONTEXT) {
           std::cout << "Failed to create egl context, error:" << eglGetError() << std::endl;
       }
   
       // Create an eglSurface.
       eglSurface_ = eglCreateWindowSurface(eglDisplay_, config_, reinterpret_cast<EGLNativeWindowType>(eglNativeWindow_), context_attribs);
       if (eglSurface_ == EGL_NO_SURFACE) {
           std::cout << "Failed to create egl surface, error:" << eglGetError() << std::endl;
       }
   
       // Associate the context.
       eglMakeCurrent(eglDisplay_, eglSurface_, eglSurface_, eglContext_);
   
       // The EGL environment initialization is complete.
       std::cout << "Create EGL context successfully, version" << major << "." << minor << std::endl;
   }
   ```

2. Create an **OH_NativeImage** instance.
   
   ```c++
   // Create an OpenGL ES texture.
   GLuint textureId;
   glGenTextures(1, &textureId);
   // Create an OH_NativeImage instance, which will be associated with an OpenGL ES texture.
   OH_NativeImage* image = OH_NativeImage_Create(textureId, GL_TEXTURE_EXTERNAL_OES);
   ```
   
3. Obtain the **OHNativeWindow** instance that functions as the producer.

   ```c++
   // Obtain an OHNativeWindow instance.
   OHNativeWindow* nativeWindow = OH_NativeImage_AcquireNativeWindow(image);
   ```

4. Set the width and height of the **OHNativeWindow** instance.

   ```c++
   int code = SET_BUFFER_GEOMETRY;
   int32_t width = 800;
   int32_t height = 600;
   int32_t ret = OH_NativeWindow_NativeWindowHandleOpt(nativeWindow, code, width, height);
   ```

5. Write the produced content to the **OHNativeWindowBuffer**.

   1. Obtain an **OHNativeWindowBuffer** instance from the **NativeWindow** instance.

      ```c++
      OHNativeWindowBuffer *buffer = nullptr;
      int fenceFd;
      // Obtain an OHNativeWindowBuffer instance by calling OH_NativeWindow_NativeWindowRequestBuffer.
      OH_NativeWindow_NativeWindowRequestBuffer(nativeWindow, &buffer, &fenceFd);
       
      BufferHandle *handle = OH_NativeWindow_GetBufferHandleFromNative(buffer);
      ```

   2. Write the produced content to the **OHNativeWindowBuffer**.

      ```c++
      // Use mmap() to obtain the memory virtual address of buffer handle.
      void *mappedAddr = mmap(handle->virAddr, handle->size, PROT_READ | PROT_WRITE, MAP_SHARED, handle->fd, 0);
      if (mappedAddr == MAP_FAILED) {
          // mmap failed
      }
      static uint32_t value = 0x00;
      value++;
      uint32_t *pixel = static_cast<uint32_t *>(mappedAddr);
      for (uint32_t x = 0; x < width; x++) {
          for (uint32_t y = 0; y < height; y++) {
              *pixel++ = value;
          }
      }
      // Unmap the memory when the memory is no longer required.
      int result = munmap(mappedAddr, handle->size);
      if (result == -1) {
          // munmap failed
      }
      ```

   3. Flush the **OHNativeWindowBuffer** to the **NativeWindow**.

      ```c++
      // Set the refresh region. If the Rect array in Region is a null pointer or rectNumber is 0, all contents in the OHNativeWindowBuffer are changed.
      Region region{nullptr, 0};
      // Flush the buffer to the consumer through OH_NativeWindow_NativeWindowFlushBuffer, for example, by displaying it on the screen.
      OH_NativeWindow_NativeWindowFlushBuffer(nativeWindow, buffer, fenceFd, region);
      ```

   4. Destroy the **OHNativeWindow** instance when it is no longer needed.

      ```c++
      OH_NativeWindow_DestroyNativeWindow(nativeWindow);
      ```

6. Update the content to the OpenGL texture.

   ```c++
   // Update the content to the OpenGL texture.
   ret = OH_NativeImage_UpdateSurfaceImage(image);
   if (ret != 0) {
       std::cout << "OH_NativeImage_UpdateSurfaceImage failed" << std::endl;
   }
   // Obtain the timestamp and transformation matrix of the texture image that recently called the **OH_NativeImage_UpdateSurfaceImage** function.
   int64_t timeStamp = OH_NativeImage_GetTimestamp(image);
   float matrix[16];
   ret = OH_NativeImage_GetTransformMatrix(image, matrix);
   if (ret != 0) {
       std::cout << "OH_NativeImage_GetTransformMatrix failed" << std::endl;
   }
   
   // Perform OpenGL post-processing on the texture, and then display the texture on the screen.
   EGLBoolean eglRet = eglSwapBuffers(eglDisplay_, eglSurface_);
   if (eglRet == EGL_FALSE) {
       std::cout << "eglSwapBuffers failed" << std::endl;
   }
   ```

7. Detach the **OH_NativeImage** from the current OpenGL texture and attach it to a new external texture.

   ```c++
   // Detach an OH_NativeImage instance from the current OpenGL ES context.
   ret = OH_NativeImage_DetachContext(image);
   if (ret != 0) {
       std::cout << "OH_NativeImage_DetachContext failed" << std::endl;
   }
   // Attach an OH_NativeImage instance to the current OpenGL ES context. The OpenGL ES texture will be bound to an GL_TEXTURE_EXTERNAL_OES instance and updated through the OH_NativeImage instance.
   GLuint textureId2;
   glGenTextures(1, &textureId2);
   ret = OH_NativeImage_AttachContext(image, textureId2);
   ```

8. Destroy the **OH_NativeImage** instance when it is no longer needed.

   ```c++
   // Destroy the OH_NativeImage instance.
   OH_NativeImage_Destroy(&image);
   ```

## Samples

The following samples are provided to help you better understand how to use the native image module for development:

- [Native Window (API11)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Native/NdkNativeWindow)
- [Smooth Gradient Animation Effect Based on NdkNativeImage (API 12)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Native/NdkNativeImage)
