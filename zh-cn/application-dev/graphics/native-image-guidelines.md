# NativeImage开发指导 (C/C++)
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @Felix-fangyang; @BruceXu; @dingpy-->
<!--Designer: @conan13234-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
## 场景介绍

NativeImage是提供**Surface与OpenGL外部纹理相互绑定**的模块，表示图形队列的消费者端。开发者可以通过`NativeImage`接口接收和使用`Buffer`，并将`Buffer`关联输出到绑定的OpenGL外部纹理。
NativeImage常见的开发场景如下：

* 通过`NativeImage`提供的Native API接口创建`NativeImage`实例作为消费者端，获取与该实例对应的`NativeWindow`作为生产者端。`NativeWindow`相关接口可用于填充`Buffer`内容并提交，`NativeImage`将`Buffer`内容更新到OpenGL外部纹理上。本模块需要配合NativeWindow、NativeBuffer、EGL、GLES3模块一起使用。

## 接口说明

| 接口名                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| OH_NativeImage_Create (uint32_t textureId, uint32_t textureTarget) | 创建一个OH_NativeImage实例，该实例与OpenGL ES的纹理ID和纹理目标相关联。本接口需要与OH_NativeImage_Destroy接口配合使用，否则会存在内存泄露。 |
| OH_NativeImage_AcquireNativeWindow (OH_NativeImage \*image)  | 获取与OH_NativeImage相关联的OHNativeWindow指针，该OHNativeWindow在调用OH_NativeImage_Destroy时会将其释放，不需要调用OH_NativeWindow_DestroyNativeWindow释放，否则会出现访问已释放内存错误，可能会导致崩溃。 |
| OH_NativeImage_AttachContext (OH_NativeImage \*image, uint32_t textureId) | 将OH_NativeImage实例附加到当前OpenGL ES上下文，且该OpenGL ES纹理会绑定到 GL_TEXTURE_EXTERNAL_OES，并通过OH_NativeImage进行更新。 |
| OH_NativeImage_DetachContext (OH_NativeImage \*image)        | 将OH_NativeImage实例从当前OpenGL ES上下文分离。              |
| OH_NativeImage_UpdateSurfaceImage (OH_NativeImage \*image)   | 通过OH_NativeImage获取最新帧更新相关联的OpenGL ES纹理。      |
| OH_NativeImage_GetTimestamp (OH_NativeImage \*image)         | 获取最近调用OH_NativeImage_UpdateSurfaceImage的纹理图像的相关时间戳。 |
| OH_NativeImage_GetTransformMatrixV2 (OH_NativeImage \*image, float matrix[16]) | 获取最近调用OH_NativeImage_UpdateSurfaceImage的纹理图像的变化矩阵。 |
| OH_NativeImage_Destroy (OH_NativeImage \*\*image)            | 销毁通过OH_NativeImage_Create创建的OH_NativeImage实例，销毁后该OH_NativeImage指针会被赋值为空。 |

详细的接口说明请参考[native_image](../reference/apis-arkgraphics2d/capi-oh-nativeimage.md)。

## 开发步骤

以下步骤描述了如何使用`NativeImage`提供的Native API接口，创建`OH_NativeImage`实例作为消费者端，将数据内容更新到OpenGL外部纹理上。

**添加动态链接库**

CMakeLists.txt中添加以下库文件。

```txt
libEGL.so
libGLESv3.so
libnative_image.so
libnative_window.so
libnative_buffer.so
```

**头文件**

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

1. **初始化EGL环境**。

   这里提供初始化EGL环境的代码示例。XComponent模块的详细使用方法，请参阅[XComponent开发指导](../ui/napi-xcomponent-guidelines.md)。
   <!-- @[init_egl](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/NdkNativeImage/entry/src/main/cpp/render/image_render.cpp) -->

2. **创建OH_NativeImage实例**。
   <!-- @[nativeimage_create](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/NdkNativeImage/entry/src/main/cpp/render/render_engine.cpp) -->
   
3. **获取对应的数据生产者端NativeWindow**。
   <!-- @[nativeimage_acquire_nativewindow](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/NdkNativeImage/entry/src/main/cpp/render/native_render.cpp) -->

4. **设置NativeWindow的宽高**。
   <!-- @[set_buffer_geometry](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/NdkNativeImage/entry/src/main/cpp/render/native_render.cpp) -->

5. **将生产的内容写入OHNativeWindowBuffer**。

   1. 从NativeWindow中获取OHNativeWindowBuffer。
      <!-- @[nativewindow_request_buffer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/NdkNativeImage/entry/src/main/cpp/render/native_render.cpp) -->

   2. 将生产的内容写入OHNativeWindowBuffer。
      <!-- @[write_addr](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/NdkNativeImage/entry/src/main/cpp/render/native_render.cpp) -->

   3. 将OHNativeWindowBuffer提交到NativeWindow。
      <!-- @[flush_buffer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/NdkNativeImage/entry/src/main/cpp/render/native_render.cpp) -->

4. 在不再需要使用NativeWindow时，需要销毁它。
      <!-- @[destroy_nativewindow](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/NdkNativeImage/entry/src/main/cpp/render/native_render.cpp) -->

6. **更新内容到OpenGL纹理**。
   <!-- @[update_surfaceimage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/NdkNativeImage/entry/src/main/cpp/render/render_engine.cpp) -->

7. **解绑OpenGL纹理，绑定到新的外部纹理上**。
   <!-- @[nativeimage_change_context](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/NdkNativeImage/entry/src/main/cpp/render/render_engine.cpp) -->

8. **OH_NativeImage实例使用完需要销毁掉**。
   <!-- @[destroy_nativeimage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/NdkNativeImage/entry/src/main/cpp/render/render_engine.cpp) -->

## 相关实例

针对NativeImage的开发，有以下相关实例可供参考：

- [Native Window（API11）](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Native/NdkNativeWindow)
- [基于NdkNativeImage的平滑渐变动画效果（API12）](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Native/NdkNativeImage)