# 使用Image_NativeModule完成图片解码
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

创建ImageSource，获取位图的宽、高信息，以及释放ImageSource实例。

从API version 22开始支持对部分专业相机格式图片的预览图解码，具体格式包括：CR2、CR3、ARW、NEF、RAF、NRW、ORF、RW2、PEF、SRW。

## 开发步骤

### 添加链接库

在进行应用开发之前，开发者需要打开native工程的src/main/cpp/CMakeLists.txt，在target_link_libraries依赖中添加libimage_source.so、libpixelmap.so以及日志功能依赖的libhilog_ndk.z.so。

```txt
target_link_libraries(entry PUBLIC libhilog_ndk.z.so libimage_source.so libpixelmap.so)
```

### Native接口调用

具体接口说明请参考[API文档](../../reference/apis-image-kit/capi-image-nativemodule.md)。

在Deveco Studio新建Native C++应用，默认生成的项目中包含index.ets文件，在entry\src\main\cpp目录下会自动生成一个cpp文件（hello.cpp或napi_init.cpp，本示例以hello.cpp文件名为例）。在hello.cpp中实现C API接口调用逻辑，示例代码如下：

**解码接口使用示例**

> **说明：**
>
> 部分接口在API version 20以后才支持，需要开发者在进行开发时选择合适的API版本。

1. 导入相关头文件。

   <!-- @[decodingPixel_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadImageSource.cpp) -->     
   
   ``` C++
   #include <string>
   #include <hilog/log.h>
   #include <multimedia/image_framework/image/image_source_native.h>
   #include "napi/native_api.h"
   #include <multimedia/image_framework/image/image_common.h>
   #include <multimedia/image_framework/image/pixelmap_native.h>
   ```

2. 日志宏定义可参考下述代码按实际需求自行修改。

   <!-- @[define_logInfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadImageSource.cpp) -->     
   
   ``` C++
   #undef LOG_DOMAIN
   #undef LOG_TAG
   #define LOG_DOMAIN 0x3200
   #define LOG_TAG "IMAGE_SAMPLE"
   ```

3. 定义ImageSourceNative类。

   <!-- @[define_sourceClass](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/imageKits.h) -->     
   
4. 创建ImageSourceNative的一个实例。

   <!-- @[create_sourceClass](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadImageSource.cpp) -->     
   
5. 创建GetJsResult函数处理napi返回值。

   <!-- @[get_returnValue](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/napi_init.cpp) -->       

6. 常量定义。

   <!-- @[define_maxStringLength](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadImageSource.cpp) -->     

7. 创建ImageSource实例。

   <!-- @[decodingPixel_operations](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadImageSource.cpp) -->    

8. 在创建ImageSource实例后，进行指定属性值的获取和修改、通过解码参数创建PixelMap对象、获取图像帧数等操作。

   - 创建PixelMap对象。

     <!-- @[create_pixelMap](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadImageSource.cpp) -->    
     
     ``` C++
     // 通过图片解码参数创建PixelMap对象。
     napi_value CreatePixelMap(napi_env env, napi_callback_info info)
     {
         // ops参数支持传入nullptr, 当不需要设置解码参数时，不用创建。
         OH_DecodingOptions *ops = nullptr;
         OH_DecodingOptions_Create(&ops);
         // 设置为AUTO会根据图片资源格式和设备支持情况进行解码，如果图片资源为HDR资源且设备支持HDR解码则会解码为HDR的pixelmap。
         OH_DecodingOptions_SetDesiredDynamicRange(ops, IMAGE_DYNAMIC_RANGE_AUTO);
         
         OH_PixelmapNative_Release(g_thisImageSource->resPixMap);
         g_thisImageSource->resPixMap = nullptr;
         
         Image_ErrorCode errCode = OH_ImageSourceNative_CreatePixelmap(g_thisImageSource->source,
                                                                       ops, &g_thisImageSource->resPixMap);
         OH_DecodingOptions_Release(ops);
         ops = nullptr;
         if (errCode != IMAGE_SUCCESS) {
             OH_LOG_ERROR(LOG_APP, "OH_ImageSourceNative_CreatePixelmap failed, errCode: %{public}d.", errCode);
             return GetJsResult(env, errCode);
         }
     
         // 判断pixelmap是否为HDR内容。
         OH_PixelmapImageInfo_Create(&g_thisImageSource->pixelmapImageInfo);
         OH_PixelmapNative_GetImageInfo(g_thisImageSource->resPixMap, g_thisImageSource->pixelmapImageInfo);
         bool pixelmapIsHdr;
         OH_PixelmapImageInfo_GetDynamicRange(g_thisImageSource->pixelmapImageInfo, &pixelmapIsHdr);
         if (pixelmapIsHdr) {
             OH_LOG_INFO(LOG_APP, "The pixelMap's dynamicRange is HDR.");
         }
         OH_PixelmapImageInfo_Release(g_thisImageSource->pixelmapImageInfo);
         g_thisImageSource->pixelmapImageInfo = nullptr;
         return GetJsResult(env, errCode);
     }
     ```

   - 创建定义图片信息的结构体对象，并获取图片信息。

     <!-- @[get_imageInfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadImageSource.cpp) -->     
     
     ``` C++
     // 创建定义图片信息的结构体对象，并获取图片信息。
     napi_value GetImageInfo(napi_env env, napi_callback_info info)
     {
         OH_ImageSourceInfo_Create(&g_thisImageSource->imageInfo);
         Image_ErrorCode errCode = OH_ImageSourceNative_GetImageInfo(g_thisImageSource->source,
                                                                     0, g_thisImageSource->imageInfo);
         if (errCode != IMAGE_SUCCESS) {
             OH_LOG_ERROR(LOG_APP, "OH_ImageSourceInfo_Create failed, errCode: %{public}d.", errCode);
             return GetJsResult(env, errCode);
         }
         
         uint32_t width;
         uint32_t height;
         OH_ImageSourceInfo_GetWidth(g_thisImageSource->imageInfo, &width);
         OH_ImageSourceInfo_GetHeight(g_thisImageSource->imageInfo, &height);
         OH_LOG_INFO(LOG_APP, "OH_ImageSourceNative_GetImageInfo success,"
                    "width: %{public}d, height: %{public}d.", width, height);
         OH_ImageSourceInfo_Release(g_thisImageSource->imageInfo);
         g_thisImageSource->imageInfo = nullptr;
         return GetJsResult(env, width); // 返回获取到info信息的width。
     }
     ```

   - 读取、编辑Exif信息。

     <!-- @[editExif_operations](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadImageSource.cpp) -->     

   - 获取图像帧数。

     <!-- @[get_frameCount](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadImageSource.cpp) -->     

   - 通过图片解码参数创建Pixelmap列表。

     <!-- @[create_pixelmapList](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadImageSource.cpp) -->        

   - 获取图像延迟时间列表。

     <!-- @[get_delayTimeList](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadImageSource.cpp) -->       

9. 释放ImageSource。

     <!-- @[release_imageSource](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadImageSource.cpp) -->       
     
     ``` C++
     // 释放资源。
     napi_value ReleaseImageSource(napi_env env, napi_callback_info info)
     {
         Image_ErrorCode errCode = OH_ImageSourceNative_Release(g_thisImageSource->source);
         g_thisImageSource->source = nullptr;
         OH_PixelmapNative_Release(g_thisImageSource->resPixMap);
         g_thisImageSource->resPixMap = nullptr;
         return ReturnErrorCode(env, errCode, "OH_ImageSourceNative_Release");
     }
     ```
