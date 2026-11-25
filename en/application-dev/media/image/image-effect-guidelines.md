# Using ImageEffect to Edit Images
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zyj208-->
<!--Designer: @wangshoucheng-->
<!--Tester: @gengfei-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=845794b034d10b5616e22d22f955f6fbaa59d85f translatedAt=2026-11-09T07:45:43.703Z pushedAt=2026-11-09T08:11:29.763Z nl=2 -->

## When to Use

The **ImageEffect** class provides a series of APIs for editing images. You can use the **ImageEffect** APIs to process images of different input types, such as `Pixelmap`, `NativeWindow`, `NativeBuffer`, and `Uri`, to obtain filter effects.

Common development scenarios for **ImageEffect** are as follows:

- Add a filter or filter chain by using the native APIs provided by **ImageEffect**, set the input image, and apply the filter effect.
- Register a custom filter to implement a developer-defined filter effect.
- Use the native APIs provided by **EffectFilter** to quickly implement the processing effect of a single filter.

## **Available APIs**

For details about the APIs, see [ImageEffect](../../reference/apis-image-kit/capi-imageeffect.md).

## How to Develop

**Adding Dynamic Link Libraries**

Add the following libraries to `CMakeLists.txt`.

```txt
target_link_libraries(entry PUBLIC
    libace_ndk.z.so
    libimage_effect.so
    libpixelmap.so
    libnative_window.so
    libnative_buffer.so
)
```

Add the corresponding dynamic link library based on the processed image type: `Pixelmap` (`libpixelmap.so`), `NativeWindow` (`libnative_window.so`), or `NativeBuffer` (`libnative_buffer.so`).

**Adding Header Files**

<!-- @[image_effect_include_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageEffect/entry/src/main/cpp/backend/image_edit.cpp) -->
```c++
#include <multimedia/image_effect/image_effect.h>
#include <multimedia/image_effect/image_effect_filter.h>
#include <multimedia/image_effect/image_effect_errors.h>
```

### Making an Image Effect Take Effect by Using ImageEffect APIs

1. Create an **ImageEffect** instance.

   <!-- @[image_effect_instance_creation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageEffect/entry/src/main/cpp/backend/image_edit.cpp) -->
   
   ``` C++
   OH_ImageEffect *imageEffect = OH_ImageEffect_Create("imageEdit");
   ```

2. Add an **EffectFilter** filter.

   <!-- @[image_effect_add_filter](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageEffect/entry/src/main/cpp/backend/image_edit.cpp) -->
   
   ``` C++
   OH_EffectFilter *filter = OH_ImageEffect_AddFilter(imageEffect, filterName);
   CHECK_AND_RETURN_RET_LOG(filter != nullptr, filter, "OH_ImageEffect_AddFilter fail!");
   ```

3. Set the data to be processed.

   **Scenario 1: Set the `OH_PixelmapNative` input type.**

   For details about how to use `OH_PixelmapNative`, see [PixelMap Data Processing (C/C++)](image-pixelmap-operation-native.md).

   <!-- @[image_effect_pixelmap_native](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageEffect/entry/src/main/cpp/backend/image_edit.cpp) -->
   ```c++
   ImageEffect_ErrorCode errorCode = OH_ImageEffect_SetInputPixelmap(imageEffectPtr.get(), pixelmapNativePtr.get());
   CHECK_AND_RETURN_RET_LOG(errorCode == ImageEffect_ErrorCode::EFFECT_SUCCESS, result,
                            "OH_ImageEffect_SetInputPixelMap fail! errorCode = %{public}d", errorCode);

   // Set an output pixel map (optional). If this API is not called, the filter effect directly takes effect on the input pixel map.
   errorCode = OH_ImageEffect_SetOutputPixelmap(imageEffectPtr.get(), pixelmapNativePtr.get());
   CHECK_AND_RETURN_RET_LOG(errorCode == ImageEffect_ErrorCode::EFFECT_SUCCESS, result,
                            "OH_ImageEffect_SetOutputPixelmap fail!");
   ```

   **Scenario 2: Set the `OH_NativeBuffer` input type.**

   For details about how to use `OH_NativeBuffer`, see [Native Buffer Development (C/C++)](../../graphics/native-buffer-guidelines.md).

   <!-- @[image_effect_native_buffer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageEffect/entry/src/main/cpp/backend/image_edit.cpp) -->
   ```c++
   // Set an input native buffer.
   ImageEffect_ErrorCode errorCode = OH_ImageEffect_SetInputNativeBuffer(imageEffect, inputNativeBuffer);
   CHECK_AND_RETURN_RET_LOG(errorCode == ImageEffect_ErrorCode::EFFECT_SUCCESS, result,
                            "OH_ImageEffect_SetInputNativeBuffer fail!");

   // Set an output native buffer (optional). If this API is not called, the filter effect directly takes effect on the input native buffer.
   errorCode = OH_ImageEffect_SetOutputNativeBuffer(imageEffect, outputNativeBuffer);
   CHECK_AND_RETURN_RET_LOG(errorCode == ImageEffect_ErrorCode::EFFECT_SUCCESS, result,
                            "OH_ImageEffect_SetOutputNativeBuffer fail!");
   ```

   **Scenario 3: Set the URI input type.**

   <!-- @[image_effect_url](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageEffect/entry/src/main/cpp/backend/image_edit.cpp) -->
   ```c++
   // Set an input URI.
   ImageEffect_ErrorCode errorCode = OH_ImageEffect_SetInputUri(imageEffectPtr.get(), path.c_str());
   CHECK_AND_RETURN_RET_LOG(errorCode == ImageEffect_ErrorCode::EFFECT_SUCCESS, result,
                            "OH_ImageEffect_SetInputPixelMap fail! errorCode = %{public}d", errorCode);

   // Set an output URI (optional). If this API is not called, the filter effect directly takes effect on the input URI.
   errorCode = OH_ImageEffect_SetOutputUri(imageEffect, path.c_str());
   CHECK_AND_RETURN_RET_LOG(errorCode == ImageEffect_ErrorCode::EFFECT_SUCCESS, result,
                            "OH_ImageEffect_SetOutputUri fail!");
   ```

   **Scenario 4: Set the texture input type.**

   The texture input scenario is a high-performance scenario that uses the hardware GPU for rendering. In this scenario, the application needs to provide a valid OpenGL context and set parameters and perform rendering operations in the correct environment.

   ```c++
   // Set the input texture ID.
   errorCode = OH_ImageEffect_SetInputTextureId(imageEffect, inputTex, ColorSpaceName::SRGB);
   if (errorCode != ImageEffect_ErrorCode::EFFECT_SUCCESS) {
       OH_LOG_ERROR(LOG_APP, "OH_ImageEffect_SetInputTextureId fail!");
       return;
   }

   // Set the output texture ID. Note that it cannot be the same texture as the input. Otherwise, rendering exceptions may occur.
   errorCode = OH_ImageEffect_SetOutputTextureId(imageEffect, outputTex);
   if (errorCode != ImageEffect_ErrorCode::EFFECT_SUCCESS) {
       OH_LOG_ERROR(LOG_APP, "OH_ImageEffect_SetOutputTextureId fail!");
       return;
   }
   ```

   **Scenario 5: Set the `OHNativeWindow` input type.**

   The following uses camera preview as an example to describe the `OHNativeWindow` input scenario. The `SurfaceId` provided by the **XComponent** for camera preview streams can be converted into `OHNativeWindow` at the native C++ layer. A code example is provided below.

   For details about how to use the **XComponent** module, see [XComponent](../../reference/apis-arkui/arkui-ts/ts-basic-components-xcomponent.md).

   For details about how to use the native window module, see [OHNativeWindow](../../reference/apis-arkgraphics2d/capi-nativewindow.md).

   For details about how to use the camera, see [Camera Preview (C/C++)](../camera/native-camera-preview.md).

   (1) Add an **XComponent** to `xxx.ets`.

   ```ts
   XComponent({ 
      id: 'xcomponentId', 
      type: 'surface',
      controller: this.mXComponentController, 
      libraryname: 'entry'
   })
   .onLoad(() => {
      // Obtain the SurfaceId of the XComponent.
      this.mSurfaceId = this.mXComponentController.getXComponentSurfaceId()

      // Call the native API to obtain the input SurfaceId.
      this.mSurfaceId = imageEffect.getSurfaceId(this.mSurfaceId)

      // Call the camera API to start preview and transfer the obtained input SurfaceId to the camera framework.
      // ...
   })
   .width('100%')
   .height('100%')
   ```

   (2) The following shows how **imageEffect.getSurfaceId** is implemented at the native C++ layer.

   ```c++
   // Create a NativeWindow based on the SurfaceId. Note that the created NativeWindow must be released by calling OH_NativeWindow_DestroyNativeWindow when it is no longer needed.
   uint64_t outputSurfaceId;
   std::istrstream iss(outputSurfaceIdStr);
   iss >> outputSurfaceId;
   OHNativeWindow *outputNativeWindow = nullptr;
   int32_t res = OH_NativeWindow_CreateNativeWindowFromSurfaceId(outputSurfaceId, &outputNativeWindow);
   if (res != 0) {
       OH_LOG_ERROR(LOG_APP, "OH_NativeWindow_CreateNativeWindowFromSurfaceId fail!");
       return;
   }

   // Set the output display surface.
   ImageEffect_ErrorCode errorCode = OH_ImageEffect_SetOutputSurface(imageEffect, outputNativeWindow);
   if (errorCode != ImageEffect_ErrorCode::EFFECT_SUCCESS) {
       OH_LOG_ERROR(LOG_APP, "OH_ImageEffect_SetOutputSurface fail!");
       return;
   }
   // Obtain the input surface. Note that the obtained inputNativeWindow must be released by calling OH_NativeWindow_DestroyNativeWindow when it is no longer needed.
   OHNativeWindow *inputNativeWindow = nullptr;
   errorCode = OH_ImageEffect_GetInputSurface(imageEffect, &inputNativeWindow);
   if (errorCode != ImageEffect_ErrorCode::EFFECT_SUCCESS) {
       OH_LOG_ERROR(LOG_APP, "OH_ImageEffect_GetInputSurface fail!");
       return;
   }

   // Obtain the SurfaceId from the input NativeWindow.
   uint64_t inputSurfaceId = 0;
   res = OH_NativeWindow_GetSurfaceId(inputNativeWindow, &inputSurfaceId);
   if (res != 0) {
       OH_LOG_ERROR(LOG_APP, "OH_NativeWindow_GetSurfaceId fail!");
       return;
   }

   // Convert the SurfaceId into a string and return it.
   std::string inputSurfaceIdStr = std::to_string(inputSurfaceId);
   ```

4. Start the image effector.

   <!-- @[image_effect_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageEffect/entry/src/main/cpp/backend/image_edit.cpp) -->
   ```c++
   errorCode = OH_ImageEffect_Start(imageEffectPtr.get());
   CHECK_AND_RETURN_RET_LOG(errorCode == ImageEffect_ErrorCode::EFFECT_SUCCESS, result,
                            "OH_ImageEffect_Start fail! errorCode = %{public}d", errorCode);
   ```

5. Stop the image effect (optional, available only in the input surface scenario).

   <!-- @[image_effect_stop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageEffect/entry/src/main/cpp/backend/image_edit.cpp) -->
   ```c++
   // Stop the image effector.
   ImageEffect_ErrorCode errorCode = OH_ImageEffect_Stop(imageEffect);
   CHECK_AND_RETURN_RET_LOG(errorCode == ImageEffect_ErrorCode::EFFECT_SUCCESS, result, "OH_ImageEffect_Stop fail!");
   ```

6. Serialize the image effector (optional).

   <!-- @[image_effect_save](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageEffect/entry/src/main/cpp/backend/image_edit.cpp) -->
   ```c++
   // Serialize the effect (optional).
   char *imageinfo = nullptr;
   errorCode = OH_ImageEffect_Save(imageEffect, &imageinfo);
   CHECK_AND_RETURN_RET_LOG(errorCode == ImageEffect_ErrorCode::EFFECT_SUCCESS, result, "OH_ImageEffect_Save fail!");
   ```

7. Destroy the image effector instance.

   <!-- @[image_effect_release](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageEffect/entry/src/main/cpp/backend/image_edit.cpp) -->
   
   ``` C++
   ImageEffect_ErrorCode errorCode = OH_ImageEffect_Release(imageEffect);
   CHECK_AND_RETURN_LOG(errorCode == ImageEffect_ErrorCode::EFFECT_SUCCESS, "OH_ImageEffect_Release fail!");
   ```

### Customizing a Filter

The following steps describe how to implement and register a custom filter:

1. Define `ImageEffect_FilterDelegate`.

   <!-- @[image_effect_buffer_info](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageEffect/entry/src/main/cpp/backend/image_edit.cpp) -->
   ```c++
   // Image information struct.
   struct EffectBufferInfo {
       void *addr = nullptr;
       int32_t width = 0;
       int32_t height = 0;
       int32_t rowSize = 0;
       ImageEffect_Format format = ImageEffect_Format::EFFECT_PIXEL_FORMAT_UNKNOWN;
   };
   ```

   <!-- @[image_effect_custom_filter](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageEffect/entry/src/main/cpp/backend/image_edit.cpp) -->
   ```c++
   // Custom filter implementation.
   delegateBrightness = {
       .setValue =
           [](OH_EffectFilter *filter, const char *key, const ImageEffect_Any *value) {
               // Validate parameters. Return true if validation succeeds, otherwise return false.
               if (value->dataValue.floatValue >= DATA_VALUE_MIN && value->dataValue.floatValue <= DATA_VALUE_MAX) {
                   return true;
               } else {
                   return false;
               }
           },
       .render = [](OH_EffectFilter *filter, OH_EffectBufferInfo *info,
                    OH_EffectFilterDelegate_PushData pushData) { return RenderBrightness(filter, info, pushData); },
       .save = SaveFilterBrightness,
       .restore = [](const char *info) -> OH_EffectFilter * {
           // Create an OH_EffectFilter instance, where "CustomBrightness" is the filter name of the custom filter.
           OH_EffectFilter *filter = OH_EffectFilter_Create("CustomBrightness");
           CHECK_AND_RETURN_RET_LOG(filter != nullptr, nullptr, "OH_EffectFilter_Create fail!");
           // Parse the JSON string info to obtain the key and value.
           std::map<std::string, std::string> parsedJson = Json::Parse(info);
           if (parsedJson.find("values") != parsedJson.end()) {
               std::string valuesStr = parsedJson["values"];
               std::map<std::string, std::string> valuesJson = Json::Parse(valuesStr);
               if (valuesJson.find("brightness") != valuesJson.end()) {
                   float brightness =
                       std::stof(valuesJson["brightness"].substr(1, valuesJson["brightness"].size() - 2));
                   ImageEffect_Any value;
                   value.dataType = ImageEffect_DataType::EFFECT_DATA_TYPE_FLOAT;
                   value.dataValue.floatValue = brightness;
                   // Set the filter parameters, where value is the parameter parsed from info as JSON.
                   LOG_E("brightness value: %{public}f ", value.dataValue.floatValue);
                   ImageEffect_ErrorCode errorCode = OH_EffectFilter_SetValue(filter, "brightness", &value);
                   CHECK_AND_RETURN_RET_LOG(errorCode == ImageEffect_ErrorCode::EFFECT_SUCCESS, nullptr,
                                            "OH_EffectFilter_SetValue fail!");
               }
           }
           return filter;
       }};
   ```

   The **Render** API can be implemented in the following two scenarios.

   **Scenario 1: The custom algorithm can directly modify the pixel data in `info` (for example, the brightness adjustment filter).**

   <!-- @[image_effect_render_brightness](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageEffect/entry/src/main/cpp/backend/image_edit.cpp) -->
   ```c++
   bool RenderBrightness(OH_EffectFilter *filter, OH_EffectBufferInfo *info, OH_EffectFilterDelegate_PushData pushData)
   {
       // Obtain image details.
       EffectBufferInfo inputBufferInfo;
       OH_EffectBufferInfo_GetAddr(info, &inputBufferInfo.addr);
       OH_EffectBufferInfo_GetWidth(info, &inputBufferInfo.width);
       OH_EffectBufferInfo_GetHeight(info, &inputBufferInfo.height);
       OH_EffectBufferInfo_GetRowSize(info, &inputBufferInfo.rowSize);
       OH_EffectBufferInfo_GetEffectFormat(info, &inputBufferInfo.format);

       // Call the custom filter algorithm.
       ApplyCustomBrightnessAlgo(filter, inputBufferInfo);

       // After editing is complete, call pushData to directly pass the original image.
       pushData(filter, info);
       return true;
   }
   ```

   **Scenario 2: The custom algorithm cannot directly modify the pixel data in `info` (for example, the crop filter).**

   <!-- @[image_effect_render_crop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageEffect/entry/src/main/cpp/backend/image_edit.cpp) -->
   
   ``` C++
   bool RenderCrop(OH_EffectFilter *filter, OH_EffectBufferInfo *info, OH_EffectFilterDelegate_PushData pushData)
   {
       // Obtain image details.
       EffectBufferInfo inputBufferInfo;
       OH_EffectBufferInfo_GetAddr(info, &inputBufferInfo.addr);
       OH_EffectBufferInfo_GetWidth(info, &inputBufferInfo.width);
       OH_EffectBufferInfo_GetHeight(info, &inputBufferInfo.height);
       OH_EffectBufferInfo_GetRowSize(info, &inputBufferInfo.rowSize);
       OH_EffectBufferInfo_GetEffectFormat(info, &inputBufferInfo.format);
   
       // Create output pixel information.
       EffectBufferInfo outputBufferInfo;
   
       // Call the custom filter algorithm.
       ApplyCustomCropAlgo(filter, inputBufferInfo, outputBufferInfo);
   
       // Generate outputOhInfo.
       OH_EffectBufferInfo *outputOhInfo = OH_EffectBufferInfo_Create();
       OH_EffectBufferInfo_SetAddr(outputOhInfo, outputBufferInfo.addr);
       OH_EffectBufferInfo_SetWidth(outputOhInfo, outputBufferInfo.width);
       OH_EffectBufferInfo_SetHeight(outputOhInfo, outputBufferInfo.height);
       OH_EffectBufferInfo_SetRowSize(outputOhInfo, outputBufferInfo.rowSize);
       OH_EffectBufferInfo_SetEffectFormat(outputOhInfo, outputBufferInfo.format);
   
       // After editing is complete, call pushData to pass outputOhInfo.
       pushData(filter, outputOhInfo);
   
       // Release resources.
       OH_EffectBufferInfo_Release(outputOhInfo);
   
       return true;
   }
   ```

2. Generate custom filter information.

   <!-- @[image_effect_create_custom_filter_info](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageEffect/entry/src/main/cpp/backend/image_edit.cpp) -->
   
   ``` C++
   // Create an OH_EffectFilterInfo instance.
   OH_EffectFilterInfo *customFilterInfo = OH_EffectFilterInfo_Create();
   CHECK_AND_RETURN_RET_LOG(customFilterInfo != nullptr, result, "OH_EffectFilterInfo_Create fail!");
   // Set the custom filter name.
   OH_EffectFilterInfo_SetFilterName(customFilterInfo, "CustomBrightness");
   // Set the memory types supported by the custom filter.
   ImageEffect_BufferType bufferTypeArray[] = {ImageEffect_BufferType::EFFECT_BUFFER_TYPE_PIXEL};
   OH_EffectFilterInfo_SetSupportedBufferTypes(customFilterInfo,
       sizeof(bufferTypeArray) / sizeof(ImageEffect_BufferType), bufferTypeArray);
   // Set the pixel formats supported by the custom filter.
   ImageEffect_Format formatArray[] = {ImageEffect_Format::EFFECT_PIXEL_FORMAT_RGBA8888};
   OH_EffectFilterInfo_SetSupportedFormats(customFilterInfo,
       sizeof(formatArray) / sizeof(ImageEffect_Format), formatArray);
   ```

3. Register `ImageEffect_FilterDelegate` with the image effector.

   <!-- @[image_effect_custom_filter_register](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageEffect/entry/src/main/cpp/backend/image_edit.cpp) -->
   
   ``` C++
   ImageEffect_ErrorCode errorCode = OH_EffectFilter_Register(customFilterInfo, &delegateBrightness);
   CHECK_AND_RETURN_RET_LOG(errorCode == ImageEffect_ErrorCode::EFFECT_SUCCESS, result,
                            "OH_EffectFilter_Register fail! errorCode = %{public}d", errorCode);
   ```

### Using EffectFilter to Quickly Implement the Processing Effect of a Single Filter

1. Create a filter.

   <!-- @[image_effect_create_filter](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageEffect/entry/src/main/cpp/backend/image_edit.cpp) -->
   
   ``` C++
   // Create a filter. For example, create a contrast effector.
   OH_EffectFilter *filter = OH_EffectFilter_Create(filterName);
   CHECK_AND_RETURN_LOG(filter != nullptr, "OH_EffectFilter_Create fail!");
   ```

2. Set a filter parameter.

   <!-- @[image_effect_set_filter_value](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageEffect/entry/src/main/cpp/backend/image_edit.cpp) -->
   
   ``` C++
   // Set the filter parameters, and set the filter intensity to the passed-in parameter.
   ImageEffect_Any value;
   value.dataType = ImageEffect_DataType::EFFECT_DATA_TYPE_FLOAT;
   value.dataValue.floatValue = static_cast<float>(filterValue);
   ImageEffect_ErrorCode errorCode = OH_EffectFilter_SetValue(filter, OH_EFFECT_FILTER_INTENSITY_KEY, &value);
   CHECK_AND_RETURN_LOG(errorCode == ImageEffect_ErrorCode::EFFECT_SUCCESS, "OH_EffectFilter_SetValue fail!");
   ```

3. Make the filter take effect.

   <!-- @[image_effect_filter_render](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageEffect/entry/src/main/cpp/backend/image_edit.cpp) -->
   
   ``` C++
   // Make the filter take effect.
   errorCode = OH_EffectFilter_Render(filter, inputPixelmap, outputPixelmap);
   CHECK_AND_RETURN_LOG(errorCode == ImageEffect_ErrorCode::EFFECT_SUCCESS, "OH_EffectFilter_Render fail!");
   ```

4. Destroy the filter instance.

   <!-- @[image_effect_filter_release](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageEffect/entry/src/main/cpp/backend/image_edit.cpp) -->
   ```c++
   // Destroy the filter instance.
   errorCode = OH_EffectFilter_Release(filter);
   CHECK_AND_RETURN_LOG(errorCode == ImageEffect_ErrorCode::EFFECT_SUCCESS, "OH_EffectFilter_Release fail!");
   ```

### Querying Capabilities

- Query filter information based on the filter name.

  <!-- @[image_effect_lookup_filter_info_by_name](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageEffect/entry/src/main/cpp/backend/image_edit.cpp) -->
  ```c++
  OH_EffectFilterInfo *filterInfo = OH_EffectFilterInfo_Create();
  // Sample code: pass nullptr as format to obtain the size of OH_Formats.
  ImageEffect_ErrorCode errorCode = OH_EffectFilter_LookupFilterInfo(filterName.c_str(), filterInfo);
  CHECK_AND_RETURN_RET_LOG(errorCode == ImageEffect_ErrorCode::EFFECT_SUCCESS, result,
                           "OH_EffectFilter_LookupFilterInfo fail! errorCode = %{public}d", errorCode);

  char *name = nullptr;
  OH_EffectFilterInfo_GetFilterName(filterInfo, &name);

  uint32_t supportedBufferTypesCount = 0;
  ImageEffect_BufferType *bufferTypeArray = nullptr;
  OH_EffectFilterInfo_GetSupportedBufferTypes(filterInfo, &supportedBufferTypesCount, &bufferTypeArray);

  uint32_t supportedFormatsCount = 0;
  ImageEffect_Format *formatArray = nullptr;
  OH_EffectFilterInfo_GetSupportedFormats(filterInfo, &supportedFormatsCount, &formatArray);

  LOG_I("LookupFilterInfo: name=%{public}s, bufferTypesCount=%{public}d, formatsCount=%{public}d", name,
        supportedBufferTypesCount, supportedFormatsCount);

  std::string infoStr = CommonUtils::EffectInfoToString(filterInfo);
  LOG_I("LookupFilterInfo:%{public}s", infoStr.c_str());
  status = napi_create_string_utf8(env, infoStr.c_str(), strlen(infoStr.c_str()), &result);
  CHECK_AND_RETURN_RET_LOG(status == napi_ok, result, "napi_create_string_utf8 fail!");

  OH_EffectFilterInfo_Release(filterInfo);
  ```

- Query filters that meet given conditions.

  <!-- @[image_effect_lookup_filter_info_by_condition](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageEffect/entry/src/main/cpp/backend/image_edit.cpp) -->
  ```c++
  ImageEffect_FilterNames *filterNames = OH_EffectFilter_LookupFilters(key);
  CHECK_AND_RETURN_RET_LOG(filterNames != nullptr, result, "OH_EffectFilter_LookupFilters fail!");

  std::string res = "size: " + std::to_string(filterNames->size) + std::string(", name: ");
  for (int i = 0; i < filterNames->size; i++) {
      res += filterNames->nameList[i];
      if (i < filterNames->size - 1) {
          res += " | ";
      }
  }
  status = napi_create_string_utf8(env, res.c_str(), res.size(), &result);
  // Release the virtual memory resources occupied by FilterNames.
  OH_EffectFilter_ReleaseFilterNames();
  ```

## Samples

The following sample is available for ImageEffect development:

- [ImageEffect (API12)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Media/ImageEffect)