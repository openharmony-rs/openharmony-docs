# EGL
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @samhu1989-->
<!--Designer: @shi-yang-2012-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->
[EGL](https://registry.khronos.org/EGL/sdk/docs/man/) is an interface between Khronos rendering APIs (such as [OpenGLES](https://registry.khronos.org/OpenGL-Refpages/es3/) or OpenVG) and the underlying window system. OpenHarmony supports EGL.

## Introducing EGL

To use EGL capabilities, include the following header file:

```c++
#include <EGL/egl.h>
```

Add the following dynamic link library to **CMakeLists.txt**:

```txt
libEGL.so
```

To call the EGL extended APIs, include the following header file and add the macro definition to **CMakeLists.txt**:
```c++
#include <EGL/eglext.h>
```
```txt
EGL_EGLEXT_PROTOTYPES
```
## Extension APIs

**eglGetNativeClientBufferANDROID**

Since API version 23, the EGL extended API **eglGetNativeClientBufferANDROID** can be used to convert [OH_NativeBuffer](../apis-arkgraphics2d/capi-native-buffer-h.md) to the **EGLClientBuffer** type for texture binding and GPU sampling. For details, see the following sample code:

```c++
// The following variables have been defined in the EGLCore member variables.
EGLDisplay m_eglDisplay = EGL_NO_DISPLAY;
OH_NativeBuffer* m_nativeBuffer = {nullptr};
GLuint m_textureId = 0;
// Bind OH_NativeBuffer as a texture by using the following function process:
bool EGLCore::PrepareNativeBuffer() {
    // Check and allocate nativeBuffer.
    if (m_nativeBuffer != nullptr) {
        return true;
    }
    OH_NativeBuffer_Config config {
        .width = 128,
        .height = 128,
        .format = NATIVEBUFFER_PIXEL_FMT_RGBA_8888,
        .usage = NATIVEBUFFER_USAGE_CPU_WRITE | NATIVEBUFFER_USAGE_CPU_READ | NATIVEBUFFER_USAGE_HW_RENDER | NATIVEBUFFER_USAGE_HW_TEXTURE | NATIVEBUFFER_USAGE_CPU_READ_OFTEN | NATIVEBUFFER_USAGE_ALIGNMENT_512
        };
    m_nativeBuffer = OH_NativeBuffer_Alloc(&config);
    if (m_nativeBuffer == nullptr) {
        OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN, "EGLCore", "Failed to allocate native buffer.");
    }

    // Write data to nativeBuffer on the CPU.
    uint32_t* nativeBuffer;
    OH_NativeBuffer_Map(m_nativeBuffer, (void**)&nativeBuffer);
    for (uint32_t i = 0; i < 128; i++) {
        for (uint32_t j = 0; j < 128; j++) {
            float ypos = static_cast<float>(i) / 127.0f;
            float hue = ypos * 360.0f;
            float xpos = static_cast<float>(j) / 127.0f * 0.6f + 0.4f;
            // Set saturation and brightness to the maximum values to obtain vivid colors.
            nativeBuffer[i * 128 + j] = HSVtoRGB_U32(hue, xpos, 1.0f);
        }
    }
    OH_NativeBuffer_Unmap(m_nativeBuffer);

    // Check whether the EGL extension is supported.
    const char* extensions = eglQueryString(m_eglDisplay, EGL_EXTENSIONS);
    if(!strstr(extensions, "EGL_ANDROID_get_native_client_buffer")) {
        OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN, "EGLCore", "Extension not support.");
        return false;
    }

    // Obtain the EGL function pointer.
    PFNEGLGETNATIVECLIENTBUFFERANDROIDPROC eglGetNativeClientBufferANDROID =
        reinterpret_cast<PFNEGLGETNATIVECLIENTBUFFERANDROIDPROC>(
            eglGetProcAddress("eglGetNativeClientBufferANDROID"));
    if (!eglGetNativeClientBufferANDROID) {
        OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN, "EGLCore", "Failed to get eglGetNativeClientBufferANDROID pointer.");
        return false;
    }

    // Obtain EGLClientBuffer.
    EGLClientBuffer clientBuffer = eglGetNativeClientBufferANDROID((struct AHardwareBuffer*)m_nativeBuffer);
    if(!clientBuffer) {
        OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN, "EGLCore", "Client buffer error.");
        return false;
    }
    PFNEGLCREATEIMAGEKHRPROC eglCreateImageKHR =
        reinterpret_cast<PFNEGLCREATEIMAGEKHRPROC>(
            eglGetProcAddress("eglCreateImageKHR"));
    if(!eglCreateImageKHR) {
        OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN, "EGLCore", "Failed to get eglCreateImageKHR pointer.");
        return false;
    }

    // Create and bind a texture.
    EGLint attribs[] = {EGL_IMAGE_PRESERVED_KHR, EGL_TRUE, EGL_NONE};
    EGLImageKHR eglImage = eglCreateImageKHR(
        m_eglDisplay,
        EGL_NO_CONTEXT,
        EGL_NATIVE_BUFFER_OHOS,
        clientBuffer,
        attribs);
    if (eglImage == EGL_NO_IMAGE_KHR) {
        OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN, "EGLCore", "Failed to create eglImage.");
        return false;
    }
    glGenTextures(1, &m_textureId);
    if(m_textureId == 0) {
        OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN, "EGLCore", "Failed to generate textures.");
        return false;
    }
    glBindTexture(GL_TEXTURE_2D, m_textureId);

    // Set texture parameters.
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_LINEAR);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_CLAMP_TO_EDGE);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_T, GL_CLAMP_TO_EDGE);

    // Bind EGLImage.
    glEGLImageTargetTexture2DOES(GL_TEXTURE_2D, eglImage);
    // In this case, m_nativeBuffer has been bound to the m_textureId texture and can be used as a normal texture.
    return true;
}
```
The **EGLClientBuffer** object generated by calling **eglGetNativeClientBufferANDROID** needs to be destroyed after use. Otherwise, memory leaks may occur. For details about how to destroy the object, see the following code snippet:
```c++
// The clientBuffer variable of the EGLClientBuffer type has been created by calling eglGetNativeClientBufferANDROID.
// Call the following function to destroy the object after use:
OH_NativeWindow_DestroyNativeWindowBuffer((OHNativeWindowBuffer*)clientBuffer);
```
## Supported APIs

Currently, OpenHarmony supports the EGL APIs listed in the topic below. The supported APIs will be continuously updated as the version evolves.

 

[EGL Symbols Exported from Native APIs](egl-symbol.md)
