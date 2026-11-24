# OpenGL
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @samhu1989-->
<!--Designer: @shi-yang-2012-->
<!--Tester: @yhl0101-->
<!--Adviser: @ge-yafang-->
[OpenGL](https://www.khronos.org/opengl/)是一种跨平台的图形API，用于为3D图形处理硬件指定标准的软件接口。OpenHarmony现已支持OpenGL 4.2。

## 支持的能力及设备

支持能力：

- 从API version 20开始，支持使用OpenGL 3.0。

- 从API version 22开始，支持使用OpenGL 4.2。

支持设备：

从API version 20开始，支持在PC设备上使用OpenGL能力；从API version 22开始，新增支持在部分Tablet设备上使用OpenGL能力，具体Tablet设备是否支持可通过OH_Graphics_QueryGL接口判断。

## 查询当前设备是否支持OpenGL

从API version 22开始，支持使用OH_Graphics_QueryGL接口判断设备是否支持使用OpenGL功能以及是否需要回退使用OpenGL ES。

**设备行为差异：** OH_Graphics_QueryGL接口在PC、Tablet设备上可正常调用，在其他设备上返回为空。

具体示例如下：

```c++
typedef EGLBoolean(*OH_Graphics_QueryGL_FUNC)(void);
static napi_value QueryGL(napi_env env, napi_callback_info info)
{
    const char &r0 = u8"OH_Graphics_QueryGL不存在，使用GLES";
    const char &r1 = u8"OH_Graphics_QueryGL存在，返回0，使用GLES";
    const char &r2 = u8"OH_Graphics_QueryGL存在，返回1，使用GL";
    napi_value result = nullptr;
    napi_status status = napi_invalid_arg;
    OH_Graphics_QueryGL_FUNC OH_Graphics_QueryGL = (OH_Graphics_QueryGL_FUNC)eglGetProcAddress("OH_Graphics_QueryGL");
    if (OH_Graphics_QueryGL) {
        if (OH_Graphics_QueryGL()) {
            status = napi_create_string_utf8(env, r2, (size_t)strlen(r2), &result);
        } else {
            status = napi_create_string_utf8(env, r1, (size_t)strlen(r1), &result);
        }
    } else {
        status = napi_create_string_utf8(env, r0, (size_t)strlen(r0), &result);
    }
    if (status != napi_ok) {
        napi_throw_error(env, nullptr, "Failed to create UTF-8 string");
    }
    return result;
}
```


## 标准库中导出的符号列表

[native api中导出的OpenGL符号列表](opengl-symbol.md)

## OpenGL扩展接口

OpenGL扩展接口及使用，可参考[OpenGL ES扩展接口](opengles.md#opengl-es扩展接口)。

## 引入OpenGL能力

如果开发者需要使用OpenGL的相关能力，需要添加相关动态链接库和头文件。

**添加动态链接库**

CMakeLists.txt中添加以下lib。

```txt
libace_ndk.z.so
libace_napi.z.so
libGLv4.so
libEGL.so
```

**头文件**

```c++
#include <ace/xcomponent/native_interface_xcomponent.h>
#include <EGL/egl.h>
#include <EGL/eglext.h>
#include <EGL/eglplatform.h>
#include <GL/gl.h>
#include <GL/glcorearb.h>
```

**修改app.json5配置文件**

```json5
"appEnvironments": [
 {
   "name":"NEED_OPENGL",
   "value": "1"
 }
],
```

## 相关参考

针对OpenGL的使用和相关开发，需要同步了解NDK的开发过程，以及XComponent组件等的使用。具体可参考：

- [NDK开发参考](../../napi/ndk-development-overview.md)

- [Node-API参考](./napi.md)

- [XComponentNode参考](../apis-arkui/js-apis-arkui-xcomponentNode.md)

- [XComponent参考](../apis-arkui/arkui-ts/ts-basic-components-xcomponent.md)

## 简单示例

部分接口使用示例，可参考[OpenGL ES简单示例](opengles.md#简单示例)。

### 使用eglCreateImage导入OH_NativeBuffer

EGL扩展EGL_OHOS_image_native_buffer支持在eglCreateImage接口中以EGL_NATIVE_BUFFER_OHOS为目标，直接将[OH_NativeBuffer](../apis-arkgraphics2d/capi-oh-nativebuffer-oh-nativebuffer.md)指针作为EGLClientBuffer传入来创建EGLImage。创建成功后，通过glEGLImageTargetTexture2DOES将EGLImage绑定为OpenGL纹理，即可在着色器中当作普通2D纹理直接采样。借助该能力，相机、视频编解码、UI合成等模块产出的图像数据无需拷贝即可进入OpenGL渲染管线，实现零拷贝的跨模块图像共享。

使用时需要注意：

- eglCreateImage的context参数必须为EGL_NO_CONTEXT，否则将产生EGL_BAD_CONTEXT错误。
- 传入的OH_NativeBuffer指针必须有效，且像素格式需为NATIVEBUFFER_PIXEL_FMT_RGB_565、NATIVEBUFFER_PIXEL_FMT_RGBA_8888、NATIVEBUFFER_PIXEL_FMT_RGBX_8888、NATIVEBUFFER_PIXEL_FMT_BGRA_8888、NATIVEBUFFER_PIXEL_FMT_RGBA_1010102或NATIVEBUFFER_PIXEL_FMT_RGBA16_FLOAT，否则将产生EGL_BAD_PARAMETER错误。

具体使用方法请参考如下示例代码：

```c++
// 在EGLCore成员变量中已经定义好了如下变量
EGLDisplay m_eglDisplay = EGL_NO_DISPLAY;
OH_NativeBuffer* m_nativeBuffer = {nullptr};
GLuint m_textureId = 0;
EGLImage m_eglImage = EGL_NO_IMAGE_KHR;
// 通过如下函数流程即可实现将OH_NativeBuffer直接绑定为OpenGL纹理
bool EGLCore::ImportNativeBufferAsTexture() {
    // 检查并分配nativeBuffer
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
        return false;
    }

    // CPU侧对nativeBuffer进行写入
    uint32_t* nativeBuffer;
    OH_NativeBuffer_Map(m_nativeBuffer, (void**)&nativeBuffer);
    for (uint32_t i = 0; i < 128; i++) {
        for (uint32_t j = 0; j < 128; j++) {
            float ypos = static_cast<float>(i) / 127.0f;
            float hue = ypos * 360.0f;
            float xpos = static_cast<float>(j) / 127.0f * 0.6f + 0.4f;
            // 饱和度和亮度设置为最大值以获取鲜艳的颜色
            nativeBuffer[i * 128 + j] = HSVtoRGB_U32(hue, xpos, 1.0f);
        }
    }
    OH_NativeBuffer_Unmap(m_nativeBuffer);

    // 以EGL_NATIVE_BUFFER_OHOS为目标，直接传入OH_NativeBuffer指针创建EGLImage
    // 注意：context必须传EGL_NO_CONTEXT，否则将产生EGL_BAD_CONTEXT错误
    EGLAttrib attribs[] = {EGL_IMAGE_PRESERVED_KHR, EGL_TRUE, EGL_NONE};
    m_eglImage = eglCreateImage(
        m_eglDisplay,
        EGL_NO_CONTEXT,
        EGL_NATIVE_BUFFER_OHOS,
        (EGLClientBuffer)m_nativeBuffer,
        attribs);
    if (m_eglImage == EGL_NO_IMAGE_KHR) {
        OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN, "EGLCore", "Failed to create eglImage.");
        return false;
    }

    // 创建并绑定纹理
    glGenTextures(1, &m_textureId);
    if (m_textureId == 0) {
        OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN, "EGLCore", "Failed to generate textures.");
        return false;
    }
    glBindTexture(GL_TEXTURE_2D, m_textureId);

    // 设置纹理参数
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_LINEAR);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_CLAMP_TO_EDGE);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_T, GL_CLAMP_TO_EDGE);

    // 绑定EGLImage
    auto glEGLImageTargetTexture2DOES = reinterpret_cast<PFNGLEGLIMAGETARGETTEXTURE2DOESPROC>(
        eglGetProcAddress("glEGLImageTargetTexture2DOES"));
    if (!glEGLImageTargetTexture2DOES) {
        OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN, "EGLCore",
            "Failed to get glEGLImageTargetTexture2DOES pointer.");
        return false;
    }
    glEGLImageTargetTexture2DOES(GL_TEXTURE_2D, m_eglImage);
    // 此时m_nativeBuffer已经绑定到了m_textureId纹理上，可以在OpenGL着色器中当作普通2D纹理直接采样
    return true;
}
```

EGLImage和OH_NativeBuffer在使用完成后需要主动释放，否则会产生内存泄漏，具体释放方式参考下列代码片段的示例：

```c++
// 在前面已经通过eglCreateImage创建了m_eglImage，并分配了m_nativeBuffer
// 使用完成后调用如下函数进行释放
void EGLCore::Release() {
    if (m_eglImage != EGL_NO_IMAGE_KHR) {
        eglDestroyImage(m_eglDisplay, m_eglImage);
        m_eglImage = EGL_NO_IMAGE_KHR;
    }
    if (m_textureId != 0) {
        glDeleteTextures(1, &m_textureId);
        m_textureId = 0;
    }
    if (m_nativeBuffer != nullptr) {
        OH_NativeBuffer_Unreference(m_nativeBuffer);
        m_nativeBuffer = nullptr;
    }
}
```