# OpenGL
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @samhu1989-->
<!--Designer: @shi-yang-2012-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=dc7a8e368647662e8a65a9c70e09750d1b0eed33 translatedAt=2026-11-04T04:21:14.914Z pushedAt=2026-11-04T08:04:44.645Z nl=2 -->

[OpenGL](https://www.khronos.org/opengl/) is a cross-platform graphics API that specifies a standard software interface for 3D graphics processing hardware. OpenHarmony now supports OpenGL 4.2.

## Supported Capabilities and Devices

Capabilities:

- OpenGL 3.0 is supported since API version 20.

- OpenGL 4.2 is supported since API version 22.

Devices:

OpenGL is supported on PC devices starting from API version 20. Starting from API version 22, support for OpenGL is newly added on some tablet devices. Whether a specific tablet device supports this capability can be determined through the **OH_Graphics_QueryGL** API.

## Checking the Support for OpenGL

Starting from API version 22, the OH_Graphics_QueryGL API can be used to determine whether a device supports OpenGL and whether it is necessary to fall back to OpenGL ES.

**Device behavior differences**: The **OH_Graphics_QueryGL** API works properly on PCs and tablets but returns null on other devices.

Specific examples are as follows:

```c++
typedef EGLBoolean(*OH_Graphics_QueryGL_FUNC)(void);
static napi_value QueryGL(napi_env env, napi_callback_info info)
{
    const char &r0 = u8"OH_Graphics_QueryGL does not exist. Use GLES";
    const char &r1 = u8"OH_Graphics_QueryGL exists; returns 0. Use GLES";
    const char &r2 = u8"OH_Graphics_QueryGL exists; returns 1. Use GL";
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


## Symbols Exported from the Standard Library

[OpenGL Symbols Exported from Native APIs](opengl-symbol.md)

## OpenGL Extensions and Examples

For details about the OpenGL extensions and their usage, see [OpenGL ES Extensions](opengles.md#opengl-es-extensions).

For details about how to use these extensions, see [OpenGL ES Example](opengles.md#example).

## Introducing OpenGL

To use OpenGL capabilities, you must add related dynamic link libraries (DLLs) and header files.

**Adding Dynamic Link Libraries**

Add the following libraries to **CMakeLists.txt**.

```txt
libace_ndk.z.so
libace_napi.z.so
libGLv4.so
libEGL.so
```

**Including Header Files**

```c++
#include <ace/xcomponent/native_interface_xcomponent.h>
#include <EGL/egl.h>
#include <EGL/eglext.h>
#include <EGL/eglplatform.h>
#include <GL/gl.h>
#include <GL/glcorearb.h>
```

**Modifying the app.json5 Configuration File**

```json5
"appEnvironments": [
 {
   "name":"NEED_OPENGL",
   "value": "1"
 }
],
```

## References

When using OpenGL and performing related development, you also need to understand the NDK development process and the use of components such as XComponent. For details, see:

- [Getting Started with the NDK](../../napi/ndk-development-overview.md)

- [Node-API](./napi.md)

- [XComponentNode](../apis-arkui/js-apis-arkui-xcomponentNode.md)

- [XComponent](../apis-arkui/arkui-ts/ts-basic-components-xcomponent.md)