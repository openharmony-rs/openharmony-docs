# Image Region Decoding and Downsampling (C/C++)

<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=444d4b7458e1317b3c2f1a471488b9c4b8344c2e translatedAt=2026-06-03T07:05:53.231Z pushedAt=2026-06-03T10:12:34.026Z -->

When processing large images, directly decoding the entire image may lead to high memory usage and long decoding time. Region decoding and downsampling decoding can effectively optimize this scenario:

- **Region Decoding**: Decodes only the specified rectangular region of an image, suitable for scenarios where you need to view a part of the image.

- **Downsampling Decoding**: Decodes the image to the desired size, with the decoder automatically selecting the optimal sampling rate, suitable for large image preview scenarios.

**Use Cases**:

| Scenario | Recommended Approach | Description |
|------|----------|------|
| Partial zoom-in viewing of an image | Region decoding | Decodes only the region to be viewed. |
| Large image preview (e.g., displaying a 4K image on a phone screen) | Downsampling decoding | Reduces resolution to lower memory usage. |
| Map/panorama tile loading | Combined use | Specifies a region and sets the output size. |

## Region Decoding

Region decoding specifies the rectangular area to be decoded by setting the decoding parameter `cropRegion`. The decoder only decodes the data within that region. For details about the parameter, see [Image_Region](../../reference/apis-image-kit/capi-image-nativemodule-image-region.md).

> **NOTE**
> The Native C version of region decoding requires the `OH_DecodingOptions_SetCropRegion` interface, not `SetDesiredRegion`. The `SetDesiredRegion` interface does not take effect.

### How to Develop

1. For details, see [Using Image_NativeModule to Decode Images
](image-source-c.md) to create an OH_ImageSourceNative instance.

2. Set the cropRegion parameter to perform region decoding.

   <!-- @[decode_region](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadImageSource.cpp) --> 

   ``` C++
   // Region decoding example.
   napi_value DecodeRegion(napi_env env, napi_callback_info info)
   {
       OH_DecodingOptions *ops = nullptr;
       OH_DecodingOptions_Create(&ops);
       
       // Set the crop region parameter and use SetCropRegion to implement region decoding.
       Image_Region region = {
           .x = 0,
           .y = 0,
           .width = 1000,
           .height = 1000
       };
       OH_DecodingOptions_SetCropRegion(ops, &region);
       
       OH_PixelmapNative_Release(g_thisImageSource->resPixMap);
       g_thisImageSource->resPixMap = nullptr;
       
       Image_ErrorCode errCode = OH_ImageSourceNative_CreatePixelmap(g_thisImageSource->source,
                                                                     ops, &g_thisImageSource->resPixMap);
       OH_DecodingOptions_Release(ops);
       ops = nullptr;
       
       if (errCode != IMAGE_SUCCESS) {
           OH_LOG_ERROR(LOG_APP, "DecodeRegion failed, errCode: %{public}d.", errCode);
           return GetJsResult(env, errCode);
       }
       OH_LOG_INFO(LOG_APP, "DecodeRegion succeeded.");
       return GetJsResult(env, errCode);
   }
   ```

### Constraints

- The region coordinates and size must be within the bounds of the original image.

- The region size must be a positive integer.

## Downsampling Decoding

Downsampling decoding specifies the desired output image size by setting the decoding parameter `desiredSize`. The decoder outputs a PixelMap based on the desired size, reducing the final memory footprint.

**Decoding Processing Differences**:

- **JPEG, PNG, and HEIF formats**: A downsampling strategy is used during decoding, decoding at the optimal sampling rate for higher decoding efficiency.

- **Other formats**: The original image is fully decoded first, then scaled to the desired size.

For details about the parameters, see [OH_DecodingOptions](../../reference/apis-image-kit/capi-image-nativemodule-oh-decodingoptions.md).

### How to Develop

1. Create an OH_ImageSourceNative instance by referring to [Image Development Guide (C/C++)](image-source-c.md).

2. Set the `desiredSize` parameter to perform downsampling decoding.

   <!-- @[decode_downsample](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadImageSource.cpp) --> 

   ``` C++
   // Downsampling decoding example.
   napi_value DownsampleDecode(napi_env env, napi_callback_info info)
   {
       OH_DecodingOptions *ops = nullptr;
       OH_DecodingOptions_Create(&ops);
       
       // Set the desired output size parameter.
       Image_Size desiredSize = {
           .width = 512,
           .height = 512
       };
       OH_DecodingOptions_SetDesiredSize(ops, &desiredSize);
       
       OH_PixelmapNative_Release(g_thisImageSource->resPixMap);
       g_thisImageSource->resPixMap = nullptr;
       
       Image_ErrorCode errCode = OH_ImageSourceNative_CreatePixelmap(g_thisImageSource->source,
                                                                     ops, &g_thisImageSource->resPixMap);
       OH_DecodingOptions_Release(ops);
       ops = nullptr;
       
       if (errCode != IMAGE_SUCCESS) {
           OH_LOG_ERROR(LOG_APP, "DownsampleDecode failed, errCode: %{public}d.", errCode);
           return GetJsResult(env, errCode);
       }
       OH_LOG_INFO(LOG_APP, "DownsampleDecode succeeded.");
       return GetJsResult(env, errCode);
   }
   ```

## Using Region Decoding and Downsampling Together

When both `cropRegion` and `desiredSize` are set, use the `cropAndScaleStrategy` parameter to specify the order of cropping and scaling.

### cropAndScaleStrategy Policy

| Policy | Constant Value | Operation Order | Description |
|------|--------|----------|------|
| IMAGE_CROP_AND_SCALE_STRATEGY_SCALE_FIRST | 1 | Scale first, then crop. | - |
| IMAGE_CROP_AND_SCALE_STRATEGY_CROP_FIRST | 2 | Crop first, then scale. | Recommended, reduces peak decoding memory. |

**CROP_FIRST is recommended**: Cropping first then scaling allows precise control over the crop region and ensures consistent decoding results across different formats.

For details about the parameters, see [Image_CropAndScaleStrategy](../../reference/apis-image-kit/capi-image-source-native-h.md#image_cropandscalestrategy).

### How to Develop

1. For details, see [Image Development Guide (C/C++)](image-source-c.md) to create an OH_ImageSourceNative instance.

2. Set the `cropRegion`, `desiredSize`, and `cropAndScaleStrategy` parameters simultaneously.

   <!-- @[decode_combined](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadImageSource.cpp) --> 

   ``` C++
   // Example of using region decoding and downsampling together.
   napi_value CombinedDecode(napi_env env, napi_callback_info info)
   {
       OH_DecodingOptions *ops = nullptr;
       OH_DecodingOptions_Create(&ops);
       
       Image_Region region = {
           .x = 1000,
           .y = 500,
           .width = 2000,
           .height = 2000
       };
       OH_DecodingOptions_SetCropRegion(ops, &region);
       
       Image_Size desiredSize = {
           .width = 512,
           .height = 512
       };
       OH_DecodingOptions_SetDesiredSize(ops, &desiredSize);
       
       OH_DecodingOptions_SetCropAndScaleStrategy(ops, IMAGE_CROP_AND_SCALE_STRATEGY_CROP_FIRST);
       
       OH_PixelmapNative_Release(g_thisImageSource->resPixMap);
       g_thisImageSource->resPixMap = nullptr;
       
       Image_ErrorCode errCode = OH_ImageSourceNative_CreatePixelmap(g_thisImageSource->source,
                                                                     ops, &g_thisImageSource->resPixMap);
       OH_DecodingOptions_Release(ops);
       ops = nullptr;
       
       if (errCode != IMAGE_SUCCESS) {
           OH_LOG_ERROR(LOG_APP, "CombinedDecode failed, errCode: %{public}d.", errCode);
           return GetJsResult(env, errCode);
       }
       OH_LOG_INFO(LOG_APP, "CombinedDecode succeeded.");
       return GetJsResult(env, errCode);
   }
   ```

## Precautions

- When setting both `cropRegion` and `desiredSize`, it is recommended to set `cropAndScaleStrategy` to `IMAGE_CROP_AND_SCALE_STRATEGY_CROP_FIRST` to ensure consistent decoding results.

- For images with raw pixel memory exceeding 2 GB, it is recommended to use downsampling decoding to avoid memory overflow.