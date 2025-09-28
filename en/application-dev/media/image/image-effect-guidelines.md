# Using ImageEffect to Edit Images
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zyj208-->
<!--Designer: @wangshoucheng-->
<!--Tester: @gengfei-->
<!--Adviser: @zengyawen-->
## When to Use

The **ImageEffect** class provides a series of APIs for editing an image. You can use the APIs to implement various filter effects on images of different input types (pixel map, native window, native buffer, or URI).
With the native APIs provided by **ImageEffect**, you can:

- Add a filter or filter chain, set an input image, and make the filter effective on the image.
- Customize a filter.
- Use a system defined filter.

## **Available APIs**

For details about the APIs, see [ImageEffect](../../reference/apis-image-kit/capi-imageeffect.md).

## How to Develop

**Adding Dynamic Link Libraries**

Add the following libraries to **CMakeLists.txt**.

```txt
target_link_libraries(entry PUBLIC
    libace_ndk.z.so
    libimage_effect.so
    libpixelmap.so
    libnative_window.so
    libnative_buffer.so
)
```

Add the following dynamic link libraries based on the image type: **libpixelmap.so** for the pixel map type, **libnative_window.so** for the native window type, and **libnative_buffer.so** for the native buffer type.

**Adding the Header Files**

```c++
#include <hilog/log.h>
#include <multimedia/image_effect/image_effect.h>
#include <multimedia/image_effect/image_effect_filter.h>
#include <multimedia/image_effect/image_effect_errors.h>
```

### Making a Filter Effective

1. Create an ImageEffect instance.

    ```c++
    // Create an ImageEffect instance, with the alias set to ImageEdit.
    OH_ImageEffect *imageEffect = OH_ImageEffect_Create("ImageEdit");
    ```

2. Add a filter.

    ```c++
    // Add a filter to obtain an OH_EffectFilter instance. You can call this API multiple times to add multiple filters to form a filter chain.
    OH_EffectFilter *filter = OH_ImageEffect_AddFilter(imageEffect, OH_EFFECT_BRIGHTNESS_FILTER);
    if (filter == nullptr) {
    	OH_LOG_ERROR(LOG_APP, "OH_ImageEffect_AddFilter fail!");
        return;
    }
    // Set a filter parameter. For example, set the intensity to 50.
    ImageEffect_Any value = { .dataType = ImageEffect_DataType::EFFECT_DATA_TYPE_FLOAT, .dataValue.floatValue = 50.f };
    ImageEffect_ErrorCode errorCode = OH_EffectFilter_SetValue(filter, OH_EFFECT_FILTER_INTENSITY_KEY, &value);
    ```

3. Set the data to be processed.

    **Scenario 1: Set the OH_PixelmapNative input type.**

    For details about how to use OH_PixelmapNative, see [PixelMap Data Processing (C/C++)](image-pixelmap-operation-native.md).

    ```c++
    // Set an input pixel map.
    errorCode = OH_ImageEffect_SetInputPixelmap(imageEffect, inputPixelmap);
    if (errorCode != ImageEffect_ErrorCode::EFFECT_SUCCESS) {
    	OH_LOG_ERROR(LOG_APP, "OH_ImageEffect_SetInputPixelmap fail!");
        return;
    }
    
    // (Optional) Set an output pixel map. If this API is not called, the filter effect directly takes effect on the input pixel map.
    errorCode = OH_ImageEffect_SetOutputPixelmap(imageEffect, outputPixelmap);
    if (errorCode != ImageEffect_ErrorCode::EFFECT_SUCCESS) {
    	OH_LOG_ERROR(LOG_APP, "OH_ImageEffect_SetOutputPixelmap fail!");
        return;
    }
    ```

    **Scenario 2: Set the OH_NativeBuffer input type.**

    For details about how to use OH_NativeBuffer, see [Native Buffer Development (C/C++)](../../graphics/native-buffer-guidelines.md).

    ```c++
    // Set an input native buffer.
    errorCode = OH_ImageEffect_SetInputNativeBuffer(imageEffect, inputNativeBuffer);
    if (errorCode != ImageEffect_ErrorCode::EFFECT_SUCCESS) {
    	OH_LOG_ERROR(LOG_APP, "OH_ImageEffect_SetInputNativeBuffer fail!");
        return;
    }
    
    // (Optional) Set an output native buffer. If this API is not called, the filter effect directly takes effect on the input native buffer.
    errorCode = OH_ImageEffect_SetOutputNativeBuffer(imageEffect, outputNativeBuffer);
    if (errorCode != ImageEffect_ErrorCode::EFFECT_SUCCESS) {
    	OH_LOG_ERROR(LOG_APP, "OH_ImageEffect_SetOutputNativeBuffer fail!");
        return;
    }
    ```

    **Scenario 3: Set the URI input type.**

    ```c++
    // Set an input URI.
    errorCode = OH_ImageEffect_SetInputUri(imageEffect, inputUri);
    if (errorCode != ImageEffect_ErrorCode::EFFECT_SUCCESS) {
    	OH_LOG_ERROR(LOG_APP, "OH_ImageEffect_SetInputUri fail!");
        return;
    }
    // (Optional) Set an output URI. If this API is not called, the filter effect directly takes effect on the input URI.
    errorCode = OH_ImageEffect_SetOutputUri(imageEffect, outputUri);
    if (errorCode != ImageEffect_ErrorCode::EFFECT_SUCCESS) {
    	OH_LOG_ERROR(LOG_APP, "OH_ImageEffect_SetOutputUri fail!");
        return;
    }
    ```
    **Scenario 4: Set the texture input type.**

    In the texture input scenario, the GPU is used for rendering. In this scenario, the application needs to provide a valid OpenGL context environment, set parameters, and perform rendering operations in the correct environment.
    ```c++
    // Set the input texture ID.
    errorCode = OH_ImageEffect_SetInputTextureId(imageEffect, inputTex, ColorSpaceName::SRGB);
    if (errorCode != ImageEffect_ErrorCode::EFFECT_SUCCESS) {
    	OH_LOG_ERROR(LOG_APP, "OH_ImageEffect_SetInputTextureId fail!");
        return;
    }
    
    // Set the output texture ID. Note that the output texture ID cannot be the same as the input texture ID. Otherwise, rendering exceptions may occur.
    errorCode = OH_ImageEffect_SetOutputTextureId(imageEffect, outputTex);
    if (errorCode != ImageEffect_ErrorCode::EFFECT_SUCCESS) {
    	OH_LOG_ERROR(LOG_APP, "OH_ImageEffect_SetOutputTextureId fail!");
        return;
    }
    ```

    **Scenario 5: Set the OHNativeWindow input type.**

    The following uses camera preview as an example to describe the scenario. The surface ID provided by the **XComponent** for camera preview streams can be converted into an OHNativeWindow instance at the native C++ layer.

    For details about how to use the **XComponent**, see [XComponent](../../reference/apis-arkui/arkui-ts/ts-basic-components-xcomponent.md).

    For details about how to use the native window module, see [OHNativeWindow](../../reference/apis-arkgraphics2d/capi-nativewindow.md).

    For details about how to use the camera, see [Camera Preview (C/C++)](../camera/native-camera-preview.md).

    (1) Add an **XComponent** to the .ets file.

     ```ts
     XComponent({ 
         id: 'xcomponentId', 
         type: 'surface',
         controller: this.mXComponentController, 
         libraryname: 'entry'
     })
     .onLoad(() => {
         // Obtain the surface ID of the XComponent.
         this.mSurfaceId = this.mXComponentController.getXComponentSurfaceId()
     
         // Obtain the input surface ID.
         this.mSurfaceId = imageEffect.getSurfaceId(this.mSurfaceId)
     
         // Call the camera API to start preview and transfer the input surface ID to the camera framework.
         // ...
     })
     .width('100%')
     .height('100%')
     ```

    (2) Implement **imageEffect.getSurfaceId** at the native C++ layer.

     ```c++
     // Create a NativeWindow instance based on the surface ID. Note that the instance must be released by calling OH_NativeWindow_DestoryNativeWindow when it is no longer needed.
     uint64_t outputSurfaceId;
     std::istrstream iss(outputSurfaceIdStr);
     issue >> outputSurfaceId;
     OHNativeWindow *outputNativeWindow = nullptr;
     int32_t res = OH_NativeWindow_CreateNativeWindowFromSurfaceId(outputSurfaceId, &outputNativeWindow);
    if (res != 0) {
    	OH_LOG_ERROR(LOG_APP, "OH_NativeWindow_CreateNativeWindowFromSurfaceId fail!");
        return;
    }
     
     // Set an output surface.
     ImageEffect_ErrorCode errorCode = OH_ImageEffect_SetOutputSurface(imageEffect, outputNativeWindow);
    if (res != 0) {
    	OH_LOG_ERROR(LOG_APP, "OH_ImageEffect_SetOutputSurface fail!");
        return;
    }
     // Obtain the input surface. Note that the obtained inputNativeWindow instance must be released by calling OH_NativeWindow_DestoryNativeWindow when it is no longer needed.
     OHNativeWindow *inputNativeWindow = nullptr;
     errorCode = OH_ImageEffect_GetInputSurface(imageEffect, &inputNativeWindow);
    if (errorCode != ImageEffect_ErrorCode::EFFECT_SUCCESS) {
    	OH_LOG_ERROR(LOG_APP, "OH_ImageEffect_GetInputSurface fail!");
        return;
     }
     
     // Obtain the surface ID from the inputNativeWindow instance.
     uint64_t inputSurfaceId = 0;
     res = OH_NativeWindow_GetSurfaceId(inputNativeWindow, &inputSurfaceId);
    if (res != 0) {
    	OH_LOG_ERROR(LOG_APP, "OH_NativeWindow_GetSurfaceId fail!");
        return;
     }
     
     // Convert the surface ID to a string and return the string.
     std::string inputSurfaceIdStr = std::to_string(inputSurfaceId);
     ```

4. Start the image effector.

    ```c++
    // Start the image effector.
    errorCode = OH_ImageEffect_Start(imageEffect);
    if (errorCode != ImageEffect_ErrorCode::EFFECT_SUCCESS) {
    	OH_LOG_ERROR(LOG_APP, "OH_ImageEffect_Start fail!");
        return;
    }
    ```

5. (Optional) Stop the image effector. This operation is required only in the input surface scenario.

    ```c++
    // Stop the image effector.
    errorCode = OH_ImageEffect_Stop(imageEffect);
    if (errorCode != ImageEffect_ErrorCode::EFFECT_SUCCESS) {
    	OH_LOG_ERROR(LOG_APP, "OH_ImageEffect_Stop fail!");
        return;
    }
    ```

6. (Optional) Serialize the image effector.

    ```c++
    char *info = nullptr;
    errorCode = OH_ImageEffect_Save(imageEffect, &info);
    if (errorCode != ImageEffect_ErrorCode::EFFECT_SUCCESS) {
    	OH_LOG_ERROR(LOG_APP, "OH_ImageEffect_Save fail!");
        return;
    }
    ```

7. Destroy the ImageEffect instance.

    ```c++
    // Release the ImageEffect instance.
    errorCode = OH_ImageEffect_Release(imageEffect);
    if (errorCode != ImageEffect_ErrorCode::EFFECT_SUCCESS) {
    	OH_LOG_ERROR(LOG_APP, "OH_ImageEffect_Release fail!");
        return;
    }
    ```

### Customizing a Filter

To implement and register a custom filter, perform the following steps:

1. Define **ImageEffect_FilterDelegate**.

    ```c++
    // Image information struct.
    struct EffectBufferInfo {
        void *addr = nullptr;
        int32_t width = 0;
        int32_t height = 0;
        int32_t rowSize = 0;
        ImageEffect_Format format = ImageEffect_Format::EFFECT_PIXEL_FORMAT_UNKNOWN;
    };

    // Implement a custom filter.
    ImageEffect_FilterDelegate filterDelegate = {
        .setValue = [](OH_EffectFilter *filter, const char *key, const ImageEffect_Any *value) {
            // Verify the parameters. If the verification is successful, true is returned. Otherwise, false is returned.
            // ...
            return true;
        },
        .render = [](OH_EffectFilter *filter, OH_EffectBufferInfo *info, OH_EffectFilterDelegate_PushData pushData) {
            return Render(filter, info, pushData);
        },
        .save = [](OH_EffectFilter *filter, char **info) {
            // Obtain the custom filter parameter. In this example, Brightness is the key of the custom filter.
            ImageEffect_Any value;
            ImageEffect_ErrorCode errorCode = OH_EffectFilter_GetValue(filter, "Brightness", &value);
            if (errorCode != ImageEffect_ErrorCode::EFFECT_SUCCESS) {
    			OH_LOG_ERROR(LOG_APP, "OH_EffectFilter_GetValue fail!");
        		return false;
    		}
            
            // Generate a key-value pair.
            json values;
            values["Brightness"] = value.dataValue.floatValue;         
            json root;
            root["name"] = "CustomBrightness";
            root["values"] = values;
        
        　　 // Convert the JSON object into the string infoStr.
            // ...

            // Assign a serialized string address to *info.
            *info = infoStr;
            return true;
        },
        .restore = [](const char *info) {
            // Create an OH_EffectFilter instance, in which CustomBrightness is the name of the custom filter.
            OH_EffectFilter *filter = OH_EffectFilter_Create("CustomBrightness");
            // Parse the JSON string info to obtain the key and value.
            // ...
        
            // Set a filter parameter. value is the parameter parsed based on the JSON string in info.
            ImageEffect_ErrorCode errorCode = OH_EffectFilter_SetValue(filter, "Brightness", &value);
            
            // ...
            return filter;
        }
    };
    ```

    You can implement the **Render** API in two scenarios.

    **Scenario 1: The custom algorithm can directly modify the pixel data in info (for example, the brightness filter).**

    ```c++
    bool Render(OH_EffectFilter *filter, OH_EffectBufferInfo *info, OH_EffectFilterDelegate_PushData pushData)
    {
        // Obtain the image information.
        EffectBufferInfo inputBufferInfo;
        OH_EffectBufferInfo_GetAddr(info, &inputBufferInfo.addr);
        OH_EffectBufferInfo_GetWidth(info, &inputBufferInfo.width);
        OH_EffectBufferInfo_GetHeight(info, &inputBufferInfo.height);
        OH_EffectBufferInfo_GetRowSize(info, &inputBufferInfo.rowSize);
        OH_EffectBufferInfo_GetEffectFormat(info, &inputBufferInfo.format);

        // Invoke the custom filter algorithm.
        ApplyCustomAlgo(inputBufferInfo);

        // After the editing is complete, call pushData to directly transfer the original image.
        pushData(filter, info);
        return true;
    }
    ```

    **Scenario 2: The custom algorithm cannot directly modify the pixel data in info (for example, the crop filter).**

    ```c++
    bool Render(OH_EffectFilter *filter, OH_EffectBufferInfo *info, OH_EffectFilterDelegate_PushData pushData)
    {
        // Obtain the image information.
        EffectBufferInfo inputBufferInfo;
        OH_EffectBufferInfo_GetAddr(info, &inputBufferInfo.addr);
        OH_EffectBufferInfo_GetWidth(info, &inputBufferInfo.width);
        OH_EffectBufferInfo_GetHeight(info, &inputBufferInfo.height);
        OH_EffectBufferInfo_GetRowSize(info, &inputBufferInfo.rowSize);
        OH_EffectBufferInfo_GetEffectFormat(info, &inputBufferInfo.format);

        // Create output pixel information.
        EffectBufferInfo outputBufferInfo = CreateOutputBufferInfo(inputBufferInfo);

        // Invoke the custom filter algorithm.
        ApplyCustomAlgo(inputBufferInfo, outputBufferInfo);

        // Generate outputOhInfo.
        OH_EffectBufferInfo *outputOhInfo = OH_EffectBufferInfo_Create();
        OH_EffectBufferInfo_SetAddr(outputOhInfo, outputBufferInfo.addr);
        OH_EffectBufferInfo_SetWidth(outputOhInfo, outputBufferInfo.width);
        OH_EffectBufferInfo_SetHeight(outputOhInfo, outputBufferInfo.height);
        OH_EffectBufferInfo_SetRowSize(outputOhInfo, outputBufferInfo.rowSize);
        OH_EffectBufferInfo_SetEffectFormat(outputOhInfo, outputBufferInfo.format);

        // Call pushData to transfer outputOhInfo after editing.
        pushData(filter, outputOhInfo);

        // Release resources.
        OH_EffectBufferInfo_Release(outputOhInfo);
        ReleaseOutputBuffer(outputBufferInfo.addr);

        return true;
    }
    ```

2. Generate custom filter information.

    ```c++
    // Create an OH_EffectFilterInfo instance.
    OH_EffectFilterInfo *customFilterInfo = OH_EffectFilterInfo_Create();
    if (customFilterInfo ==nullptr) {
    	OH_LOG_ERROR(LOG_APP, "OH_EffectFilter_GetValue fail!");
        return;
    }
    
    // Set the name of the custom filter.
    OH_EffectFilterInfo_SetFilterName(customFilterInfo, "CustomBrightness");
    
    // Set the buffer types supported by the custom filter.
    ImageEffect_BufferType bufferTypeArray[] = { ImageEffect_BufferType::EFFECT_BUFFER_TYPE_PIXEL };
    OH_EffectFilterInfo_SetSupportedBufferTypes(customFilterInfo, sizeof(bufferTypeArray) / sizeof(ImageEffect_BufferType), bufferTypeArray);
    
    // Set the pixel formats supported by the custom filter.
    ImageEffect_Format formatArray[] = { ImageEffect_Format::EFFECT_PIXEL_FORMAT_RGBA8888 };
    OH_EffectFilterInfo_SetSupportedFormats(customFilterInfo, sizeof(formatArray) / sizeof(ImageEffect_Format), formatArray);
    ```

3. Register **ImageEffect_FilterDelegate** with the image effector.

    ```c++
    // Register the custom filter.
    ImageEffect_ErrorCode errorCode = OH_EffectFilter_Register(customFilterInfo, &filterDelegate);
    if (errorCode != ImageEffect_ErrorCode::EFFECT_SUCCESS) {
    	OH_LOG_ERROR(LOG_APP, "OH_EffectFilter_Register fail!");
        return;
    }
    ```

### Using a System Defined Filter

1. Create a filter.

    ```c++
    // Create a filter, for example, a contrast filter.
    OH_EffectFilter *filter = OH_EffectFilter_Create(OH_EFFECT_CONTRAST_FILTER);
    ```

2. Set a filter parameter.

    ```c++
    // Set a filter parameter. For example, set the intensity to 50.
    ImageEffect_Any value = {.dataType = ImageEffect_DataType::EFFECT_DATA_TYPE_FLOAT, .dataValue.floatValue = 50.f};
    ImageEffect_ErrorCode errorCode = OH_EffectFilter_SetValue(filter, OH_EFFECT_FILTER_INTENSITY_KEY, &value);
    if (errorCode != ImageEffect_ErrorCode::EFFECT_SUCCESS) {
    	OH_LOG_ERROR(LOG_APP, "OH_EffectFilter_SetValue fail!");
        return;
    }
    ```

3. Make the filter take effect.

    ```c++
    // Start rendering with the filter.
    errorCode = OH_EffectFilter_Render(filter, inputPixelmap, outputPixelmap);
    ```

4. Destroy the filter instance.

    ```c++
    // Destroy the filter instance.
    errorCode = OH_EffectFilter_Release(filter);
    ```

### Query Capabilities

- Query filter information based on the filter name.

    ```c++
    // Create an OH_EffectFilterInfo instance.
    OH_EffectFilterInfo *filterInfo = OH_EffectFilterInfo_Create();
    if (filterInfo == nullptr) {
    	OH_LOG_ERROR(LOG_APP, "OH_EffectFilterInfo_Create fail!");
        return;
    }

    // Query the filter information based on the filter name.
    ImageEffect_ErrorCode errorCode = OH_EffectFilter_LookupFilterInfo(OH_EFFECT_BRIGHTNESS_FILTER, filterInfo);
    if (errorCode != ImageEffect_ErrorCode::EFFECT_SUCCESS) {
    	OH_LOG_ERROR(LOG_APP, "OH_EffectFilter_LookupFilterInfo fail!");
        return;
    }

    // Obtain the filter name from the filter information.
    char *name = nullptr;
    OH_EffectFilterInfo_GetFilterName(filterInfo, &name);

    // Obtain the supported buffer types.
    uint32_t supportedBufferTypesCnt = 0;
    ImageEffect_BufferType *bufferTypeArray = nullptr;
    OH_EffectFilterInfo_GetSupportedBufferTypes(filterInfo, &supportedBufferTypesCnt, &bufferTypeArray);

    // Obtain the supported pixel formats.
    uint32_t supportedFormatsCnt = 0;
    ImageEffect_Format *formatArray = nullptr;
    OH_EffectFilterInfo_GetSupportedFormats(filterInfo, supportedFormatsCnt, &formatArray);

    // Destroy the OH_EffectFilterInfo instance.
    OH_EffectFilterInfo_Release(filterInfo);
    ```

- Query filters that meet given conditions.

    ```c++
    // Query all filters. Resources need to be released.
    ImageEffect_FilterNames *filterNames = OH_EffectFilter_LookupFilters("Default");
    
    // ...
    
    // Release virtual memory resources by filter names.
    OH_EffectFilter_ReleaseFilterNames();
    ```

<!--no_check-->