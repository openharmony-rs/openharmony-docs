# Obtaining a Canvas and Displaying Drawing Results (C/C++)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hangmengxin-->
<!--Designer: @wangyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

## Overview

Canvas provides the capability of drawing basic graphics, which is used to draw and process graphics on the screen. You can use Canvas to implement custom drawing effects and enhance user experience.

Canvas is the core of graphics drawing. All drawing operations mentioned in this chapter (including drawing basic graphics, text, and images, and transforming graphics) are based on Canvas.

Currently, C/C++ supports two methods of obtaining the canvas: obtaining the canvas that can be directly displayed on the screen and obtaining the off-screen canvas. For the former, you do not need to perform additional operations after calling the drawing API to display the drawing result on the screen. For the latter, you need to use existing display methods to display the drawing result.


## Available APIs

The following table lists the common APIs for creating a canvas. For details about the APIs and parameters, see [drawing_canvas.h](../reference/apis-arkgraphics2d/capi-drawing-canvas-h.md).

| API| Description|
| -------- | -------- |
| OH_Drawing_Canvas\* OH_Drawing_CanvasCreate (void) | Creates an **OH_Drawing_Canvas** object.|
| void OH_Drawing_CanvasBind (OH_Drawing_Canvas\*, OH_Drawing_Bitmap\*) | Binds a bitmap object to the canvas so that the content drawn on the canvas is output to the bitmap.|
| OH_Drawing_Canvas\* OH_Drawing_SurfaceGetCanvas (OH_Drawing_Surface \*) | Obtains a canvas from an **OH_Drawing_Surface** object.|


## Obtaining the Canvas That Can Be Directly Displayed

Obtain the canvas that can be directly displayed through XComponent.

1. Add the link library.

   Add the following link library to src/main/cpp/CMakeLists.txt of the native project:

   ```c++
   // CMakeLists.txt
   target_link_libraries(entry PUBLIC libnative_drawing.so)
   ```
   <!-- [ndk_graphics_draw_cmake_drawing](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/CMakeLists.txt) -->

2. Imports the header files required for dependency.

   ```c++
   // sample_graphics.h
   #include <native_drawing/drawing_canvas.h>
   ```
   <!-- [ndk_graphics_draw_include_native_drawing_canvas](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.h) -->

   ```c++
   // sample_graphics.cpp
   #include <native_drawing/drawing_surface.h>
   ```
   <!-- [ndk_graphics_draw_include_native_drawing_surface](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->

3. Obtains the BufferHandle object from the NativeWindow corresponding to XComponent. For details about NativeWindow APIs, see _native_window_ (../reference/apis-arkgraphics2d/capi-nativewindow.md).

   ```c++
   // sample_graphics.cpp
   uint64_t width, height;
   // The NativeWindow and its width and height need to be obtained from the XComponent.
   OHNativeWindow *nativeWindow;
   int32_t usage = NATIVEBUFFER_USAGE_CPU_READ | NATIVEBUFFER_USAGE_CPU_WRITE | NATIVEBUFFER_USAGE_MEM_DMA;
   int ret = OH_NativeWindow_NativeWindowHandleOpt(nativeWindow, SET_USAGE, usage);
   if (ret != 0) {
       return;
   }
   
   struct NativeWindowBuffer *buffer = nullptr;
   int fenceFd = 0;
   ret = OH_NativeWindow_NativeWindowRequestBuffer(nativeWindow, &buffer, &fenceFd);
   if (ret != 0) {
       return;
   }
   
   BufferHandle* bufferHandle = OH_NativeWindow_GetBufferHandleFromNative(buffer);
   ```
   <!-- [ndk_graphics_draw_get_buffer_handle](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->

4. Obtain the memory address of the buffer handle.

   ```c++
   // sample_graphics.cpp
   uint32_t* mappedAddr = static_cast<uint32_t *>(mmap(bufferHandle->virAddr, bufferHandle->size, PROT_READ | PROT_WRITE, MAP_SHARED, bufferHandle->fd, 0));
   ```
   <!-- [ndk_graphics_draw_get_mapped_addr](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->

5. Creates a window canvas.

   ```c++
   // sample_graphics.cpp
   //Method 1 for creating a bitmap: Use OH_Drawing_BitmapCreateFromPixels to create cScreenBitmap_ of the OH_Drawing_Bitmap* type.
   // OH_Drawing_Image_Info screenImageInfo = {static_cast<int32_t>(width), static_cast<int32_t>(height), COLOR_FORMAT_RGBA_8888, ALPHA_FORMAT_OPAQUE};
   // OH_Drawing_Bitmap* cScreenBitmap_ = OH_Drawing_BitmapCreateFromPixels(&screenImageInfo, mappedAddr, bufferHandle->stride); 
   //Method 2 for creating a bitmap: Use OH_Drawing_BitmapCreate to create cScreenBitmap_ of the OH_Drawing_Bitmap* type.
   cScreenBitmap_ = OH_Drawing_BitmapCreate();
   // Define the pixel format of the bitmap.
   OH_Drawing_BitmapFormat cFormat{COLOR_FORMAT_RGBA_8888, ALPHA_FORMAT_OPAQUE};
   // Set the pixel format for the bitmap.
   uint32_t width = static_cast<uint32_t>(bufferHandle_->stride / 4);
   OH_Drawing_BitmapBuild(cScreenBitmap_, width, height_, &cFormat);
   OH_Drawing_Canvas* screenCanvas = OH_Drawing_CanvasCreate();
   OH_Drawing_CanvasBind(screenCanvas, cScreenBitmap_);
   ```
   <!-- [ndk_graphics_draw_create_canvas](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->

6. Customize drawing operations using the Canvas obtained in the previous step.

7. Use XComponent to display the Canvas.

   ```c++
   // sample_graphics.cpp
   Region region {nullptr, 0};
   OH_NativeWindow_NativeWindowFlushBuffer(nativeWindow, buffer, fenceFd, region);
   ```
   <!-- [ndk_graphics_draw_native_window_flush_buffer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->


## Obtaining and Displaying the Off-Screen Canvas

Currently, there are two ways to create an off-screen Canvas: creating a CPU backend Canvas and creating a GPU backend Canvas. The drawing results of both Canvases need to be displayed on the screen using XComponent. Due to historical reasons, early Canvases are all CPU backend Canvases. Currently, GPU backend Canvases are supported. GPUs have stronger parallel computing capabilities and are more suitable for graphics drawing. However, GPU backend Canvases do not support some scenarios, such as complex paths. The drawing performance of short texts is not as good as that of CPU backend Canvases.


### Creating and displaying a CPU backend Canvas

Currently, the C/C++ API drawing depends on NativeWindow. The CPU backend Canvas needs to perform off-screen drawing to generate a bitmap or pixel map (supported since API version 20), and then use XComponent to display the bitmap or pixel map on the screen.


Method 1: Create a Canvas by binding a bitmap.
1. Import the required header files.

   ```c++
   // sample_graphics.h
   #include <native_drawing/drawing_canvas.h>
   #include <native_drawing/drawing_bitmap.h>
   ```
   <!-- [ndk_graphics_draw_include_native_drawing_canvas_and_bitmap](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.h) -->

2. Create a CPU-based Canvas. You need to create a bitmap object by calling OH_Drawing_BitmapCreate() (for details, see [Image Drawing](pixelmap-drawing-c.md)) and bind the bitmap to the Canvas by calling OH_Drawing_CanvasBind() so that the content drawn by the Canvas can be output to the bitmap.

   ```c++
   // sample_graphics.cpp
   // Create a bitmap object.
   OH_Drawing_Bitmap* bitmap = OH_Drawing_BitmapCreate();
   OH_Drawing_BitmapFormat cFormat{COLOR_FORMAT_RGBA_8888, ALPHA_FORMAT_PREMUL};
   // Set the width and height of the bitmap as required.
   uint32_t width = 800;
   uint32_t height = 800;
   // Initialize the bitmap.
   OH_Drawing_BitmapBuild(bitmap, width, height, &cFormat);
   // Create a Canvas object.
   OH_Drawing_Canvas* bitmapCanvas = OH_Drawing_CanvasCreate();
   // Bind the canvas to the bitmap. The content drawn on the canvas is output to the memory of the bound bitmap.
   OH_Drawing_CanvasBind(bitmapCanvas, bitmap);
   ```
   <!-- [ndk_graphics_draw_create_canvas_by_cpu](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->

   To set the background color to white, perform the following steps:

   ```c++
   // sample_graphics.cpp
   OH_Drawing_CanvasClear(bitmapCanvas, OH_Drawing_ColorSetArgb(0xFF, 0xFF, 0xFF, 0xFF));
   ```
   <!-- [ndk_graphics_draw_clear_canvas_cpu](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->

3. Draw the bitmap created in the previous step on the window canvas (obtained in # Obtaining a Canvas That Can Be Directly Displayed).

   ```c++
   // sample_graphics.cpp
   OH_Drawing_CanvasDrawBitmap(screenCanvas, bitmap, 0, 0);
   ```
   <!-- [ndk_graphics_draw_drawing_to_window_canvas_cpu](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->



Method 2: Create a canvas using a pixel map. From API version 20, this method can be used to create a canvas.
A pixel map is a unified data structure used to represent images in the system. Compared with bitmaps provided by the drawing module, pixel maps are more universal and can better leverage system capabilities.

1. Add the link library.

   Add the following link library to src/main/cpp/CMakeLists.txt of the native project:

   ```c++
   // CMakeLists.txt
   target_link_libraries(entry PUBLIC libhilog_ndk.z.so libpixelmap.so)
   ```
   <!-- [ndk_graphics_draw_cmake_pixelmap](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/CMakeLists.txt) -->

2. Imports the header files required for dependency.

   ```c++
   // sample_graphics.cpp
   #include <multimedia/image_framework/image/pixelmap_native.h>
   ```
   <!-- [ndk_graphics_draw_include_pixelmap_native](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->

   ```c++
   // sample_graphics.cpp
   #include <native_drawing/drawing_pixel_map.h>
   ```
   <!-- [ndk_graphics_draw_include_drawing_pixel_map](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->


3. You need to create a pixel map object by calling OH_Drawing_PixelMapGetFromOhPixelMapNative() (for details, see [Drawing](pixelmap-drawing-c.md)), and create a canvas with the pixel map object by calling OH_Drawing_CanvasCreateWithPixelMap().

   ```c++
   // sample_graphics.cpp
   // Image width and height
   uint32_t width = 600;
   uint32_t height = 400;
   // Set the bitmap format (width, height, color type, and transparency type).
   OH_Pixelmap_InitializationOptions *createOps = nullptr;
   OH_PixelmapInitializationOptions_Create(&createOps);
   OH_PixelmapInitializationOptions_SetWidth(createOps, width);
   OH_PixelmapInitializationOptions_SetHeight(createOps, height);
   OH_PixelmapInitializationOptions_SetPixelFormat(createOps, PIXEL_FORMAT_RGBA_8888);
   OH_PixelmapInitializationOptions_SetAlphaType(createOps, PIXELMAP_ALPHA_TYPE_UNKNOWN);
   // Byte length. Each pixel of RGBA_8888 occupies four bytes.
   size_t bufferSize = width * height * 4;
   void *buffer = malloc(bufferSize);
   // Create an OH_PixelmapNative object.
   OH_PixelmapNative *pixelMapNative = nullptr;
   OH_PixelmapNative_CreatePixelmap(static_cast<uint8_t *>(buffer), bufferSize, createOps, &pixelMapNative);
   // Create a pixel map object.
   OH_Drawing_PixelMap *pixelMap = OH_Drawing_PixelMapGetFromOhPixelMapNative(pixelMapNative);
   // Create a Canvas object.
   OH_Drawing_Canvas* pixelmapCanvas = OH_Drawing_CanvasCreateWithPixelMap(pixelMap);
   ```
   <!-- [ndk_graphics_draw_image](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->

   To set the background color to white, perform the following steps:

   ```c++
   OH_Drawing_CanvasClear(pixelmapCanvas, OH_Drawing_ColorSetArgb(0xFF, 0xFF, 0xFF, 0xFF));
   ```

4. Draw the pixel map created in the previous step to the window canvas (obtained in # Obtaining the Canvas That Can Be Directly Displayed).

   ```c++
   // sample_graphics.cpp
   // Area from which pixels are captured in PixelMap.
   OH_Drawing_Rect *src = OH_Drawing_RectCreate(0, 0, width, height);
   // Area displayed on the canvas.
   OH_Drawing_Rect *dst = OH_Drawing_RectCreate(0, 0, width, height);
   // Sampling option object.
   OH_Drawing_SamplingOptions* samplingOptions = OH_Drawing_SamplingOptionsCreate(
       OH_Drawing_FilterMode::FILTER_MODE_LINEAR, OH_Drawing_MipmapMode::MIPMAP_MODE_LINEAR);
   // Draw the pixel map.
   OH_Drawing_CanvasDrawPixelMapRect(screenCanvas, pixelMap, src, dst, samplingOptions);
   ```
   <!-- [ndk_graphics_draw_image_to_canvas](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->


### Creating and Displaying a Canvas with the GPU Backend

The canvas with the GPU backend is drawn based on the GPU. The parallel computing capability of the GPU is better than that of the CPU. The canvas with the GPU backend is applicable to scenarios where images or large areas are drawn. However, the canvas with the GPU backend is not good at drawing complex paths. Similar to the canvas with the CPU backend, the drawing of the C/C++ API depends on XComponent. The canvas with the GPU backend needs to be drawn offscreen and then displayed on the screen through XComponent.

1. Currently, creating a canvas with the GPU backend depends on the EGL capability. You need to add the dynamic dependency library of EGL to CMakeList.txt.

   ```c++
   // CMakeLists.txt
   libEGL.so
   ```
   <!-- [ndk_graphics_draw_cmake_EGL](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/CMakeLists.txt) -->

2. Import the dependency header file.

   ```c++
   // sample_graphics.h
   #include <EGL/egl.h>
   #include <EGL/eglext.h>
   ```
   <!-- [ndk_graphics_draw_include_egl_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.h) -->

   ```c++
   // sample_graphics.cpp
   #include <native_drawing/drawing_gpu_context.h>
   #include <native_drawing/drawing_surface.h>
   ```
   <!-- [ndk_graphics_draw_include_native_drawing_surface_and_gpu_context](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->

3. Initializes an EGL context.

   ```c++
   // sample_graphics.h
   //Initialize EGL context parameters.
   EGLDisplay mEGLDisplay = EGL_NO_DISPLAY;
   EGLConfig mEGLConfig = nullptr;
   EGLContext mEGLContext = EGL_NO_CONTEXT;
   EGLSurface mEGLSurface = nullptr;
   ```
   <!-- [ndk_graphics_draw_initialize_egl_context_parameter](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.h) -->

   ```c++
   // sample_graphics.cpp
   //Initialize EGL context configurations.
   EGLConfig getConfig(int version, EGLDisplay eglDisplay)
   {
      int attribList[] = {EGL_SURFACE_TYPE,
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
                           EGL_OPENGL_ES2_BIT,
                           EGL_NONE};
      EGLConfig configs = NULL;
      int configsNum;

      if (!eglChooseConfig(eglDisplay, attribList, &configs, 1, &configsNum)) {
         return NULL;
      }

      return configs;
   }

   // Call InitializeEglContext at the place where the EGL context needs to be initialized.
   int32_t InitializeEglContext(EGLDisplay mEGLDisplay, EGLConfig mEGLConfig,
      EGLContext mEGLContext, EGLSurface mEGLSurface)
   {
      mEGLDisplay = eglGetDisplay(EGL_DEFAULT_DISPLAY);
      if (mEGLDisplay == EGL_NO_DISPLAY) {
         return -1;
      }

      EGLint eglMajVers;
      EGLint eglMinVers;
      if (!eglInitialize(mEGLDisplay, &eglMajVers, &eglMinVers)) {
         mEGLDisplay = EGL_NO_DISPLAY;
         return -1;
      }

      int version = 3;
      mEGLConfig = getConfig(version, mEGLDisplay);
      if (mEGLConfig == nullptr) {
         return -1;
      }

      int attribList[] = {EGL_CONTEXT_CLIENT_VERSION, 2, EGL_NONE};

      mEGLContext = eglCreateContext(mEGLDisplay, mEGLConfig, EGL_NO_CONTEXT, attribList);

      EGLint attribs[] = {EGL_WIDTH, 1, EGL_HEIGHT, 1, EGL_NONE};
      mEGLSurface = eglCreatePbufferSurface(mEGLDisplay, mEGLConfig, attribs);
      if (!eglMakeCurrent(mEGLDisplay, mEGLSurface, mEGLSurface, mEGLContext)) {
         return -1;
      }
      
      return 0;
   }
   ```
   <!-- [ndk_graphics_draw_initialize_egl_context](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->

4. Creates a GPU backend canvas. The GPU backend canvas can be obtained only through the surface object. You need to create a surface first. For details about the surface APIs, see [drawing_surface.h](../reference/apis-arkgraphics2d/capi-drawing-surface-h.md). Create a drawing context by calling OH_Drawing_GpuContextCreateFromGL, create a surface using the context, and obtain the canvas from the surface by calling OH_Drawing_SurfaceGetCanvas.

   ```c++
   // sample_graphics.cpp
   // Set the width and height as required.
   int32_t cWidth = 800;
   int32_t cHeight = 800;
   // Set the image, including the width, height, color format, and transparency format.
   OH_Drawing_Image_Info imageInfo = {cWidth, cHeight, COLOR_FORMAT_RGBA_8888, ALPHA_FORMAT_PREMUL};
   // GPU context options.
   OH_Drawing_GpuContextOptions options{false};
   // Create a drawing context with OpenGL (GL) as the GPU backend.
   OH_Drawing_GpuContext *gpuContext = OH_Drawing_GpuContextCreateFromGL(options);
   // Create a surface object.
   OH_Drawing_Surface *surface = OH_Drawing_SurfaceCreateFromGpuContext(gpuContext, true, imageInfo);
   // Create a canvas object.
   OH_Drawing_Canvas* gpuCanvas = OH_Drawing_SurfaceGetCanvas(surface);
   ```
   <!-- [ndk_graphics_draw_create_canvas_by_gpu](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->

   To set the background to white, perform the following steps:

   ```c++
   // sample_graphics.cpp
   OH_Drawing_CanvasClear(gpuCanvas, OH_Drawing_ColorSetArgb(0xFF, 0xFF, 0xFF, 0xFF));
   ```
   <!-- [ndk_graphics_draw_clear_canvas_gpu](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->

5. Copy the drawing result in the previous step to the window canvas (obtained in #).

   ```c++
   // sample_graphics.cpp
   void* dstPixels = malloc(cWidth * cHeight * 4); // 4 for rgba
   OH_Drawing_CanvasReadPixels(gpuCanvas, &imageInfo, dstPixels, 4 * cWidth, 0, 0);
   OH_Drawing_Bitmap* bitmap = OH_Drawing_BitmapCreateFromPixels(&imageInfo, dstPixels, 4 * cWidth);
   OH_Drawing_CanvasDrawBitmap(screenCanvas, bitmap, 0, 0);
   ```
   <!-- [ndk_graphics_draw_drawing_to_window_canvas_gpu](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->

6. After using the EGL context, destroy it.

   ```c++
   // sample_graphics.cpp
   //Call DeInitializeEglContext to destroy the EGL context.
   void DeInitializeEglContext(EGLDisplay mEGLDisplay, EGLContext mEGLContext, EGLSurface mEGLSurface)
   {
      //The following three methods return values to determine whether the EGL context is successfully destroyed. You can debug the methods if necessary.
      eglDestroySurface(mEGLDisplay, mEGLSurface);
      eglDestroyContext(mEGLDisplay, mEGLContext);
      eglTerminate(mEGLDisplay);

      mEGLSurface = NULL;
      mEGLContext = NULL;
      mEGLDisplay = NULL;
   }
   ```
   <!-- [ndk_graphics_draw_deinitialize_egl_context](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->

<!--RP1-->
## Samples

The following sample is available for Drawing (C/C++):

- [NDKGraphicsDraw (API14)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Drawing/NDKGraphicsDraw)
<!--RP1End-->
