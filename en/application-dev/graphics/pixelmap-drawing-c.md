# Drawing Images (C/C++)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hangmengxin-->
<!--Designer: @wangyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

A bitmap is a data structure used to store and represent images in memory. It is a collection of uncompressed pixels. Images in formats such as JPEG and PNG are compressed and are different from bitmaps. If you want to draw a JPEG or PNG image on the screen, you need to decode the image into a bitmap first. For details, see the image decoding section in Image Kit.


Currently, bitmap drawing in Drawing (C/C++) depends on PixelMap, which can be used to read or write image data and obtain image information. For details about the APIs, see [drawing_pixel_map.h](../reference/apis-arkgraphics2d/capi-drawing-pixel-map-h.md).


Multiple APIs can be used to create a PixelMap. The following uses OH_Drawing_PixelMapGetFromOhPixelMapNative() as an example.


1. Add the link library.

   Add the following link library to src/main/cpp/CMakeLists.txt of the native project:

   ```c++
   // CMakeLists.txt
   target_link_libraries(entry PUBLIC libnative_drawing.so)
   ```
   <!-- [ndk_graphics_draw_cmake_drawing](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/CMakeLists.txt) -->

   ```c++
   // CMakeLists.txt
   target_link_libraries(entry PUBLIC libhilog_ndk.z.so)
   ```
   <!-- [ndk_graphics_draw_cmake_hilog](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/CMakeLists.txt) -->

   ```c++
   // CMakeLists.txt
   target_link_libraries(entry PUBLIC libpixelmap.so)
   ```
   <!-- [ndk_graphics_draw_cmake_pixelmap](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/CMakeLists.txt) -->

2. Import the related header files.

   ```c++
   // sample_graphics.cpp
   #include <multimedia/image_framework/image/pixelmap_native.h>
   ```
   <!-- [ndk_graphics_draw_include_pixelmap_native](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->

3. Create an OH_PixelmapNative object.

   PixelMap needs to be obtained from the pixel map object (OH_PixelmapNative) defined by the image framework. Therefore, you need to create OH_PixelmapNative by calling OH_PixelmapNative_CreatePixelmap(). This function accepts four parameters. The first parameter is the buffer of image pixel data, which is used to initialize the pixel of PixelMap. The second parameter is the buffer length. The third parameter is the bitmap format (including the length, width, color type, and transparency type). The fourth parameter is the OH_PixelmapNative object, which is used as the output parameter.
   
   ```c++
   // sample_graphics.cpp
   // The image width and height are 600 x 400.
    uint32_t width = 600;
    uint32_t height = 400;
    // Byte length. Each pixel of RGBA_8888 occupies four bytes.
    size_t bufferSize = width * height * 4;
    uint8_t *pixels = new uint8_t[bufferSize];
    for (uint32_t i = 0; i < width * height; ++i) {
        // Traverse and edit each pixel to form a stripe with red, green, and blue alternating.
        uint32_t n = i / 20 % 3;
        pixels[i * 4] = 0x00; // Red channel
        pixels[i * 4 + 1] = 0x00; // +1 indicates the green channel.
        pixels[i * 4 + 2] = 0x00; // +2 indicates the blue channel.
        pixels[i * 4 + 3] = 0xFF; // +3 indicates the opacity channel.
        if (n == 0) {
            pixels[i * 4] = 0xFF; // Red channel value, which is red.
        } else if (n == 1) {
            pixels[i * 4 + 1] = 0xFF; // +1 indicates the green channel value. The values of other channels are 0. The color is green.
        } else {
            pixels[i * 4 + 2] = 0xFF; // +2 indicates the blue channel value. The values of other channels are 0. The color is blue.
        }
    }
    // Set the bitmap format (length, width, color type, and transparency type).
    OH_Pixelmap_InitializationOptions *createOps = nullptr;
    OH_PixelmapInitializationOptions_Create(&createOps);
    OH_PixelmapInitializationOptions_SetWidth(createOps, width);
    OH_PixelmapInitializationOptions_SetHeight(createOps, height);
    OH_PixelmapInitializationOptions_SetPixelFormat(createOps, PIXEL_FORMAT_RGBA_8888);
    OH_PixelmapInitializationOptions_SetAlphaType(createOps, PIXELMAP_ALPHA_TYPE_UNKNOWN);
    // Create an OH_PixelmapNative object.
    OH_PixelmapNative *pixelMapNative = nullptr;
    OH_PixelmapNative_CreatePixelmap(pixels, bufferSize, createOps, &pixelMapNative);
   ```
   <!-- [ndk_graphics_draw_image_pixel_map](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->

4. Create a **PixelMap** instance.

   Obtain the PixelMap from OH_PixelmapNative by using the OH_Drawing_PixelMapGetFromOhPixelMapNative() function.

   ```c++
   // sample_graphics.cpp
   OH_Drawing_PixelMap *pixelMap = OH_Drawing_PixelMapGetFromOhPixelMapNative(pixelMapNative);
   ```
   <!-- [ndk_graphics_draw_create_pixel_map](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->

5. Draw the PixelMap.

   You need to use OH_Drawing_CanvasDrawPixelMapRect() to draw the PixelMap. The function accepts five parameters: canvas, PixelMap object, pixel cropping area in the PixelMap, display area on the canvas, and sampling option object.

   The sampling option object (OH_Drawing_SamplingOptions) indicates the specific way of sampling from the original pixel data (that is, Bitmap) to generate new pixel values. For details, see [drawing_sampling_options.h](../reference/apis-arkgraphics2d/capi-drawing-sampling-options-h.md).

   ```c++
   // sample_graphics.cpp
   // Pixel cropping area in the PixelMap
   OH_Drawing_Rect *src = OH_Drawing_RectCreate(0, 0, 600, 400);
   // Display area on the canvas
   OH_Drawing_Rect *dst = OH_Drawing_RectCreate(200, 200, 800, 600);
   // Sampling option object
   OH_Drawing_SamplingOptions* samplingOptions = OH_Drawing_SamplingOptionsCreate(
      OH_Drawing_FilterMode::FILTER_MODE_LINEAR, OH_Drawing_MipmapMode::MIPMAP_MODE_LINEAR);
   // Draw the PixelMap.
   OH_Drawing_CanvasDrawPixelMapRect(canvas, pixelMap, src, dst, samplingOptions);
   ```
   <!-- [ndk_graphics_draw_image_to_canvas](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->

6. Release related objects after the drawing is complete.

   ```c++
   // sample_graphics.cpp
   OH_PixelmapNative_Release(pixelMapNative);
   delete[] pixels;
   ```
   <!-- [ndk_graphics_draw_release_pixelmap](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/NDKGraphicsDraw/entry/src/main/cpp/samples/sample_graphics.cpp) -->

   The drawing effect is as follows:

   ![Screenshot_20241225200426678](figures/Screenshot_20241225200426678.jpg)

<!--RP1-->
## Samples

The following samples are available for Drawing (C/C++):

- [NDKGraphicsDraw (API14)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Drawing/NDKGraphicsDraw)
<!--RP1End-->
