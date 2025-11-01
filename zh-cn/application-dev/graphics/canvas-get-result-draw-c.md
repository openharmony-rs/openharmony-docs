# 画布的获取与绘制结果的显示（C/C++）

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hangmengxin-->
<!--Designer: @wangyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

## 场景介绍

Canvas即画布，提供绘制基本图形的能力，用于在屏幕上绘制图形和处理图形。开发者可以通过Canvas实现自定义的绘图效果，增强应用的用户体验。

Canvas是图形绘制的核心，本章中提到的所有绘制操作（包括基本图形的绘制、文字的绘制、图片的绘制、图形变换等）都是基于Canvas的。

目前C/C++有两种获取Canvas的方式：获取可直接上屏显示的Canvas、获取离屏的Canvas，前者在调用绘制接口之后无需进行额外的操作即可完成绘制结果的上屏显示，而后者需要依靠已有的显示手段来显示绘制结果。


## 接口说明

创建Canvas常用接口如下表所示，详细的使用和参数说明请见[drawing_canvas.h](../reference/apis-arkgraphics2d/capi-drawing-canvas-h.md)。

| 接口 | 描述 |
| -------- | -------- |
| OH_Drawing_Canvas\* OH_Drawing_CanvasCreate (void) | 用于创建一个画布对象。 |
| void OH_Drawing_CanvasBind (OH_Drawing_Canvas\*, OH_Drawing_Bitmap\*) | 用于将一个位图对象绑定到画布中，使得画布绘制的内容输出到位图中。 |
| OH_Drawing_Canvas\* OH_Drawing_SurfaceGetCanvas (OH_Drawing_Surface \*) | 通过surface对象获取画布对象。 |


## 获取可直接显示的Canvas画布

通过XComponent获取可直接显示的Canvas画布。

1. 添加链接库。

   在Native工程的src/main/cpp/CMakeLists.txt，添加如下链接库：

   ```c++
   // CMakeLists.txt
   target_link_libraries(entry PUBLIC libnative_drawing.so)
   ```

2. 导入依赖的相关头文件。

   相关文件：
   <!-- @[ndk_graphics_draw_include_native_drawing_canvas](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.h) -->
   
   ``` C
   #include <native_drawing/drawing_canvas.h>
   ```

   相关文件：
   <!-- @[ndk_graphics_draw_include_native_drawing_surface](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->
   
   ``` C++
   #include <native_drawing/drawing_surface.h>
   ```

3. 从XComponent对应的NativeWindow中获取BufferHandle对象。NativeWindow相关的API请参考[_native_window](../reference/apis-arkgraphics2d/capi-nativewindow.md)。

   <!-- @[ndk_graphics_draw_get_buffer_handle](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->
   
   ``` C++
   // 通过 OH_NativeWindow_NativeWindowRequestBuffer 获取 OHNativeWindowBuffer 实例
   int ret = OH_NativeWindow_NativeWindowRequestBuffer(nativeWindow_, &buffer_, &fenceFd_);
   SAMPLE_LOGI("request buffer ret = %{public}d", ret);
   // 通过 OH_NativeWindow_GetBufferHandleFromNative 获取 buffer 的 handle
   bufferHandle_ = OH_NativeWindow_GetBufferHandleFromNative(buffer_);
   ```

4. 从BufferHandle中获取对应的内存地址。

   <!-- @[ndk_graphics_draw_get_mapped_addr](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->
   
   ``` C++
   // 使用系统mmap接口拿到bufferHandle的内存虚拟地址
   mappedAddr_ = static_cast<uint32_t *>(
       mmap(bufferHandle_->virAddr, bufferHandle_->size, PROT_READ | PROT_WRITE, MAP_SHARED, bufferHandle_->fd, 0));
   if (mappedAddr_ == MAP_FAILED) {
       SAMPLE_LOGE("mmap failed");
   }
   ```

5. 创建窗口画布。

   <!-- @[ndk_graphics_draw_create_canvas](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->
   
   ``` C++
   // 创建一个bitmap对象
   cScreenBitmap_ = OH_Drawing_BitmapCreate();
   // 定义bitmap的像素格式
   OH_Drawing_BitmapFormat cFormat{COLOR_FORMAT_RGBA_8888, ALPHA_FORMAT_OPAQUE};
   // 构造对应格式的bitmap
   OH_Drawing_BitmapBuild(cScreenBitmap_, width, height_, &cFormat);
   
   // 创建一个canvas对象
   cScreenCanvas_ = OH_Drawing_CanvasCreate();
   // 将画布与bitmap绑定，画布画的内容会输出到绑定的bitmap内存中
   OH_Drawing_CanvasBind(cScreenCanvas_, cScreenBitmap_);
   ```

6. 利用上一步中得到的Canvas进行自定义的绘制操作，即本章下文中的内容。

7. 利用XComponent完成显示。

   <!-- @[ndk_graphics_draw_native_window_flush_buffer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->


## 离屏Canvas画布的获取与显示

目前有两种创建离屏Canvas的方式：创建CPU后端Canvas、创建GPU后端Canvas，这两种Canvas都需要依靠XComponent来完成绘制结果的上屏显示。由于历史原因，早期的Canvas都是CPU后端Canvas。目前已经支持GPU后端Canvas，GPU的并行计算能力更强，更适合图形绘制。但GPU后端Canvas对部分场景的支持还有欠缺，比如复杂的路径，对于简短文字的绘制性能也比不上CPU后端Canvas。


### CPU后端Canvas的创建与显示

目前C/C++接口的绘制需要依赖于NativeWindow，CPU后端Canvas需要先离屏绘制，生成位图或像素图（从API Version 20开始支持），再借助XComponent上屏。


方式一：通过绑定位图（Bitmap）的方式创建Canvas。
1. 导入依赖的相关头文件。

   <!-- @[ndk_graphics_draw_include_native_drawing_canvas_and_bitmap](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.h) -->

2. 创建基于CPU的Canvas。需要通过OH_Drawing_BitmapCreate()接口创建一个位图对象（具体可参考[图片绘制](pixelmap-drawing-c.md)），并通过OH_Drawing_CanvasBind()接口将位图绑定到Canvas中，从而使得Canvas绘制的内容可以输出到位图中。

   <!-- @[ndk_graphics_draw_create_canvas_by_cpu](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->

   如果需要将背景设置为白色，需要执行以下步骤：

   <!-- @[ndk_graphics_draw_clear_canvas_cpu](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->

3. 将上一步中创建的位图绘制到[窗口画布](#获取可直接显示的canvas画布)上。

   <!-- @[ndk_graphics_draw_drawing_to_window_canvas_cpu](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->



方式二：通过像素图（PixelMap）创建Canvas。从API Version 20开始，支持使用此种方式创建Canvas。
像素图是系统中用来表示图片的统一的数据结构，相比于drawing模块中提供的位图，像素图具备通用性，并且能够更好地发挥系统的能力。

1. 添加链接库。

   在Native工程的src/main/cpp/CMakeLists.txt，添加如下链接库：

   ```c++
   // CMakeLists.txt
   target_link_libraries(entry PUBLIC libhilog_ndk.z.so libpixelmap.so)
   ```

2. 导入依赖的相关头文件。

   相关文件：
   <!-- @[ndk_graphics_draw_include_pixelmap_native](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->

   相关文件：
   <!-- @[ndk_graphics_draw_include_drawing_pixel_map](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->


3. 需要通过OH_Drawing_PixelMapGetFromOhPixelMapNative()接口创建一个像素图对象（具体可参考[图片绘制](pixelmap-drawing-c.md)），并通过OH_Drawing_CanvasCreateWithPixelMap()接口借助像素图对象创建Canvas。

   <!-- @[ndk_graphics_draw_image](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->

   如果需要将背景设置为白色，需要执行以下步骤：

   ```c++
   OH_Drawing_CanvasClear(pixelmapCanvas, OH_Drawing_ColorSetArgb(0xFF, 0xFF, 0xFF, 0xFF));
   ```

4. 将上一步中创建的像素图绘制到[窗口画布](#获取可直接显示的canvas画布)上。

   <!-- @[ndk_graphics_draw_image_to_canvas](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->


### GPU后端Canvas的创建与显示

GPU后端Canvas指画布是基于GPU进行绘制的，GPU的并行计算能力优于CPU，适用于绘制图片或区域相对大的场景，但目前GPU后端的Canvas针对绘制复杂路径的能力还有欠缺。同CPU后端Canvas，目前C/C++接口的绘制需要依赖于XComponent，GPU后端Canvas需要先离屏绘制再借助XComponent上屏。

1. 当前创建GPU后端的Canvas依赖EGL的能力，需要在CMakeList.txt中添加EGL的动态依赖库。

   ```c++
   // CMakeLists.txt
   libEGL.so
   ```

2. 导入依赖的头文件。

   相关文件：
   <!-- @[ndk_graphics_draw_include_egl_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.h) -->

   相关文件：
   <!-- @[ndk_graphics_draw_include_native_drawing_surface_and_gpu_context](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->

3. 初始化EGL上下文。

   初始化上下文相关参数:
   <!-- @[ndk_graphics_draw_initialize_egl_context_parameter](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.h) -->

   初始化上下文相关配置：
   <!-- @[ndk_graphics_draw_initialize_egl_context](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->

4. 创建GPU后端Canvas。GPU后端Canvas需要借助Surface对象来获取，需先创建surface，surface的API请参考[drawing_surface.h](../reference/apis-arkgraphics2d/capi-drawing-surface-h.md)。通过OH_Drawing_GpuContextCreateFromGL接口创建绘图上下文，再将这个上下文作为参数创建surface，最后通过OH_Drawing_SurfaceGetCanvas接口从surface中获取到canvas。

   <!-- @[ndk_graphics_draw_create_canvas_by_gpu](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->

   如果需要将背景设置为白色，需要执行以下步骤：

   <!-- @[ndk_graphics_draw_clear_canvas_gpu](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->

5. 将上一步中的绘制结果拷贝到[窗口画布](#获取可直接显示的canvas画布)上。

   <!-- @[ndk_graphics_draw_drawing_to_window_canvas_gpu](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->

6. 使用完之后需要将EGL上下文销毁。

   <!-- @[ndk_graphics_draw_deinitialize_egl_context](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->

<!--RP1-->
## 相关实例

针对Drawing(C/C++)的开发，有以下相关实例可供参考：

- [NDKGraphicsDraw (API20)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Drawing/NDKGraphicsDraw)
<!--RP1End-->