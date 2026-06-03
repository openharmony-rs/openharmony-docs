# Adding Image Effects (C/C++)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanamaru-->
<!--Designer: @chensiyi_CE-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=444d4b7458e1317b3c2f1a471488b9c4b8344c2e translatedAt=2026-06-03T06:17:55.163Z pushedAt=2026-06-03T09:22:43.495Z -->

## When to Use

When processing images offline, you can set some image effects to achieve different visual presentations, such as setting the image blur level, adjusting the image brightness and grayscale, and setting image inversion.

It is mainly based on Filter to set different image effects.

## Available APIs

The common APIs for setting image effects using filters are shown in the table below. For detailed usage and parameters, see [effect_filter](../reference/apis-arkgraphics2d/capi-effect-filter-h.md).

| Name | Description |
| -------- | -------- |
| EffectErrorCode OH_Filter_CreateEffect(OH_PixelmapNative\* pixelmap, OH_Filter\*\* filter)| Creates a filter object based on a Pixelmap object. |
| EffectErrorCode OH_Filter_Blur(OH_Filter\* filter, float radius)| Creates a blur effect and adds it to the filter. |
| EffectErrorCode OH_Filter_Brighten(OH_Filter\* filter, float brightness) | Creates a brighten effect and adds it to the filter. |
| EffectErrorCode OH_Filter_GrayScale(OH_Filter\* filter) | Creates a grayscale effect and adds it to the filter. |
| EffectErrorCode OH_Filter_Invert(OH_Filter\* filter) | Creates an invert effect and adds it to the filter. |
| EffectErrorCode OH_Filter_GetEffectPixelMap(OH_Filter\* filter, OH_PixelmapNative\*\* pixelmap) | Gets the Pixelmap object generated after filter processing. |
| EffectErrorCode OH_Filter_Release(OH_Filter\* filter) | Releases the filter object.|

## How to Develop

1. Add the following link libraries to **src/main/cpp/CMakeLists.txt** in the native project:

   ``` C++
   target_link_libraries(entry PUBLIC libnative_drawing.so)
   target_link_libraries(entry PUBLIC libhilog_ndk.z.so)
   target_link_libraries(entry PUBLIC libnative_effect.so)
   target_link_libraries(entry PUBLIC libpixelmap.so)
   ```

2. Import the dependent header files.

   ``` C++
   #include "multimedia/image_framework/image/pixelmap_native.h"
   #include "native_effect/effect_filter.h"
   ```

3. Create an **OH_PixelmapNative** pixelmap object.

   Creating a filter requires a pixelmap object (**OH_PixelmapNative**) defined by the image framework. You can create a custom pixelmap using **OH_PixelmapNative_CreatePixelmap()**, or import an external pixelmap using **OH_PixelmapNative_ConvertPixelmapNativeFromNapi()**.

   This section uses **OH_PixelmapNative_CreatePixelmap()** as an example to create an **OH_PixelmapNative**. This function accepts 4 parameters: the first parameter is the buffer for the image pixel data, used to initialize the pixelmap's pixels; the second parameter is the buffer length; the third parameter is the pixelmap format (including width, height, color type, alpha type, etc.); the fourth parameter is the **OH_PixelmapNative** object, used as an output parameter.

   ``` C++
   // The image size is 600 * 400.
   uint32_t width = 600;
   uint32_t height = 400;
   const uint16_t RGBA_MIN = 0x00;
   const uint16_t RGBA_MAX = 0xFF;
   const uint16_t RGBA_SIZE = 4;
   // Byte length, RGBA_8888 occupies 4 bytes per pixel.
   size_t bufferSize = width * height * RGBA_SIZE;
   uint8_t *pixels = new uint8_t[bufferSize];
   for (uint32_t i = 0; i < width * height; ++i) {
        // Traverse and edit each pixel to form stripes alternating in red, green, and blue
        uint32_t n = i / 20 % 3;
        pixels[i * RGBA_SIZE] = RGBA_MIN; // Red channel.
        pixels[i * RGBA_SIZE + 1] = RGBA_MIN; // +1 indicates the green channel.
        pixels[i * RGBA_SIZE + 2] = RGBA_MIN; // +2 indicates the blue channel.
        pixels[i * RGBA_SIZE + 3] = RGBA_MAX; // +3 indicates the opacity channel.
        if (n == 0) {
            pixels[i * RGBA_SIZE] = RGBA_MAX; // Assign value to red channel, the color appears red.
        } else if (n == 1) {
            pixels[i * RGBA_SIZE + 1] = RGBA_MAX; // +1 means assigning value to the green channel, with other channels set to 0, the color appears green.
        } else {
            pixels[i * RGBA_SIZE + 2] = RGBA_MAX; // +2 means assigning value to the blue channel, with other channels set to 0, the color appears blue.
        }
   }
   // Set the bitmap format (length, width, color type, opacity type)
   OH_Pixelmap_InitializationOptions *createOps = nullptr;
   OH_PixelmapInitializationOptions_Create(&createOps);
   OH_PixelmapInitializationOptions_SetWidth(createOps, width);
   OH_PixelmapInitializationOptions_SetHeight(createOps, height);
   OH_PixelmapInitializationOptions_SetPixelFormat(createOps, PIXEL_FORMAT_RGBA_8888);
   OH_PixelmapInitializationOptions_SetAlphaType(createOps, PIXELMAP_ALPHA_TYPE_UNKNOWN);
   // Create an OH_PixelmapNative object
   OH_PixelmapNative *pixelMapNative = nullptr;
   OH_PixelmapNative_CreatePixelmap(pixels, bufferSize, createOps, &pixelMapNative);
   ```

4. Based on the **OH_PixelmapNative** pixelmap object generated above, use the **OH_Filter_CreateEffect()** API to initialize the **OH_Filter** object.

   ``` C++
   OH_Filter *filter = nullptr;
   EffectErrorCode errCodeCreate = OH_Filter_CreateEffect(pixelMapNative, &filter);
   ```

5. Add different image effects to the filter as needed.

    - You can use the OH_Filter_Blur() API to add a blur effect to the filter.

      ``` C++
      float radius = 20.0; // Blur radius radius
      EffectErrorCode errCodeEffect = OH_Filter_Blur(filter, radius);
      ```

    - You can use the OH_Filter_Brighten() API to add a brightening effect to the filter.

      ``` C++
      float brightness = 0.5; // Brightening level (0~1)ng level (0~1)
      EffectErrorCode errCodeEffect = OH_Filter_Brighten(filter, brightness);
      ```

    - You can use the OH_Filter_GrayScale() API to add a grayscale effect to the filter.

      ``` C++
      EffectErrorCode errCodeEffect = OH_Filter_GrayScale(filter);
      ```

    - You can use the OH_Filter_Invert() API to add an invert effect to the filter.

      ``` C++
      EffectErrorCode errCodeEffect = OH_Filter_Invert(filter);
      ```

6. Obtain the **OH_PixelmapNative** object that has been processed by the filter.

   ``` C++
   OH_PixelmapNative* filterResult = nullptr;
   EffectErrorCode errCodeResult = OH_Filter_GetEffectPixelMap(filter, &filterResult);
   ```

7. When the filter is no longer needed to generate image effects, promptly use **OH_Filter_Release()** to destroy the **OH_Filter** object.

   ``` C++
   EffectErrorCode errCodeRelease = OH_Filter_Release(filter);
   ```

   The rendering effects are as follows:

   | image processing | Rendering Effect |
   | -------- | -------- |
   | Original Image | ![effectfilter_origin](figures/effectfilter_origin.png) |
   | Adding Blur Effect |![effectfilter_blur](figures/effectfilter_blur.png) |
   | Adding Brighten Effect |![effectfilter_brighten](figures/effectfilter_brighten.png) |
   | Adding Grayscale Effect |![effectfilter_grayscale](figures/effectfilter_grayscale.png)  |
   | Adding Invert Effect |![effectfilter_invert](figures/effectfilter_invert.png)  |