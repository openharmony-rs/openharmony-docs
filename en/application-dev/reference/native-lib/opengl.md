# OpenGL
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @samhu1989-->
<!--Designer: @shi-yang-2012-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->
[OpenGL](https://www.khronos.org/opengl/) is a cross-platform graphics API that specifies a standard software interface for 3D graphics processing hardware. OpenHarmony now supports OpenGL 4.2.

## Supported Capabilities

OpenGL 3.0 is supported since API version 20.

OpenGL 4.2 is supported since API version 22.

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
```c++
"appEnvironments": [
 {
   "name":"NEED_OPENGL",
   "value": "1"
 }
],
```
**Checking the Support for OpenGL**

Starting from API version 22, you can call the **OH_Graphics_QueryGL** API to check whether the device supports OpenGL and whether it needs to fall back to OpenGL ES.

**Device behavior differences**: This API works properly on PCs and tablets but returns null on other devices.

Specific examples are as follows:

```c++
typedef EGLBoolean(&OH_Graphics_QueryGL_FUNC)(void);
static napi_value QueryGL(napi_env env, napi_callback_info info)
{
    const char &r0 = u8"OH_Graphics_QueryGL does not exist. Use GLES";
    const char &r1 = u8"OH_Graphics_QueryGL exists; returns 0. Use GLES";
    const char &r2 = u8"OH_Graphics_QueryGL exists; returns 1. Use GL";
    napi_value result = nullptr;
    napi_status status = napi_invalid_arg;
    OH_Graphics_QueryGL_FUNC OH_Graphics_QueryGL = (OH_Graphics_QueryGL_FUNC)EglGetProcAddress("OH_Graphics_QueryGL");
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


## References

To use the OpenGL API in your application development, familiarize yourself with the NDK development process and the **XComponent** usage, which are described in the following topics:

- [Getting Started with the NDK](../../napi/ndk-development-overview.md)

- [Node-API](./napi.md)

- [XComponentNode](../apis-arkui/js-apis-arkui-xcomponentNode.md)

- [XComponent](../apis-arkui/arkui-ts/ts-basic-components-xcomponent.md)
