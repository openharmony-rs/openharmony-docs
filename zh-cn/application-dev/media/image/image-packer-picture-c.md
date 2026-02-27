# 使用Image_NativeModule完成多图对象编码
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

图像编码类，用于创建以及释放ImagePacker实例，并编码多图对象。

## 开发步骤

### 添加链接库

在进行应用开发之前，开发者需要打开native工程的src/main/cpp/CMakeLists.txt，在target_link_libraries依赖中添加libimage_packer.so 以及日志依赖libhilog_ndk.z.so。

```txt
target_link_libraries(entry PUBLIC libhilog_ndk.z.so libimage_source.so libimage_packer.so libpixelmap.so)
```

### Native接口调用

具体接口说明请参考[API文档](../../reference/apis-image-kit/capi-image-nativemodule.md)。

在DevEco Studio新建Native C++应用，默认生成的项目中包含index.ets文件，在entry\src\main\cpp目录下会自动生成一个cpp文件（hello.cpp或napi_init.cpp，本示例以hello.cpp文件名为例）。在hello.cpp中实现C API接口调用逻辑，示例代码如下：

**编码接口使用示例**

> **说明：**
>
> 根据MIME标准，标准编码格式为image/jpeg。当使用image编码时，编码参数中的编码格式image_MimeType设置为image/jpeg，image编码后的文件扩展名可设为.jpg或.jpeg，可在支持image/jpeg解码的平台上使用。
>
> 部分接口在API version 20以后才支持，需要开发者在进行开发时选择合适的API版本。

1. 导入相关头文件。

   <!-- @[decodingPicture_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadPicture.cpp) -->     
   
   ``` C++
   #include <hilog/log.h>
   #include <multimedia/image_framework/image/image_native.h>
   #include <multimedia/image_framework/image/image_packer_native.h>
   #include <multimedia/image_framework/image/image_source_native.h>
   #include <multimedia/image_framework/image/picture_native.h>
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

3. 定义用于图像处理的常量。

   <!-- @[define_const](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadPicture.cpp) -->      
   
   ``` C++
   #define AUTO 0
   #define SDR 1
   const int MAX_SIZE = 1024;
   const int MAX_FORMAT_LENGTH = 20;
   ```

4. 定义ImagePictureNative类。

   <!-- @[define_pictureClass](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/imageKits.h) -->   
   
   ``` C
   class ImagePictureNative {
   public:
       Image_ErrorCode errorCode = IMAGE_SUCCESS;
       OH_DecodingOptionsForPicture *options = nullptr;
       OH_ImagePackerNative *imagePacker = nullptr;
       OH_PackingOptions *packerOptions = nullptr;
       OH_PictureNative *picture = nullptr;
       OH_ImageSourceNative *source = nullptr;
       ImagePictureNative() {}
       ~ImagePictureNative() {}
   };
   ```

5. 创建ImagePictureNative的一个实例。

   <!-- @[create_pictureClass](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadPicture.cpp) -->   
   
   ``` C++
   static ImagePictureNative *g_thisPicture = new ImagePictureNative();
   ```

6. 创建GetJsResult函数处理napi返回值。

   <!-- @[get_returnValue](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/napi_init.cpp) -->   
   
   ``` C++
   // 处理napi返回值。
   napi_value GetJsResult(napi_env env, int result)
   {
       napi_value resultNapi = nullptr;
       napi_create_int32(env, result, &resultNapi);
       return resultNapi;
   }
   ```

7. 创建ImagePacker实例，指定编码参数后，将Picture多图对象编码至文件或缓冲区。

   <!-- @[pack_picture](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadPicture.cpp) -->    
   
   ``` C++
   // 设置编码参数。
   void SetPackOptions(OH_PackingOptions *packerOptions,
                       Image_MimeType format,
                       uint32_t quality,
                       bool needsPackProperties,
                       int32_t desiredDynamicRange)
   {
       OH_PackingOptions_SetMimeType(packerOptions, &format);
       OH_PackingOptions_SetQuality(packerOptions, quality);
       OH_PackingOptions_SetNeedsPackProperties(packerOptions, needsPackProperties);
       OH_PackingOptions_SetDesiredDynamicRange(packerOptions, desiredDynamicRange);
   }
   
   // PackToData。
   napi_value PackToDataFromPicture(napi_env env, napi_callback_info info)
   {
       size_t argc = 1;
       napi_value args[1] = {nullptr};
       if (napi_get_cb_info(env, info, &argc, args, nullptr, nullptr) != napi_ok) {
           OH_LOG_ERROR(LOG_APP, "napi_get_cb_info failed!");
           return GetJsResult(env, g_thisPicture->errorCode);
       }
       
       size_t outDataSize = 10000 * 10000;
       uint8_t *outData = new uint8_t[outDataSize];
   
       if (g_thisPicture->packerOptions == nullptr) {
           g_thisPicture->errorCode = OH_PackingOptions_Create(&g_thisPicture->packerOptions);
       }
       if (g_thisPicture->imagePacker == nullptr) {
           g_thisPicture->errorCode = OH_ImagePackerNative_Create(&g_thisPicture->imagePacker);
       }
       
       char strFormat[MAX_FORMAT_LENGTH];
       size_t strFormatSize;
       napi_get_value_string_utf8(env, args[0], strFormat, MAX_FORMAT_LENGTH, &strFormatSize);
       OH_LOG_DEBUG(LOG_APP, "PackToDataFromPicture format: %{public}s", strFormat);
   
       Image_MimeType format;
       format.size = strFormatSize;
       format.data = const_cast<char *>(strFormat);
       uint32_t quality = 95;
       bool needsPackProperties = true;
       int32_t desiredDynamicRange = AUTO;
       SetPackOptions(g_thisPicture->packerOptions, format, quality, needsPackProperties, desiredDynamicRange);
       // 确保picture对象已被创建。
       g_thisPicture->errorCode = OH_ImagePackerNative_PackToDataFromPicture(
           g_thisPicture->imagePacker, g_thisPicture->packerOptions, g_thisPicture->picture, outData, &outDataSize);
       
       // 释放imagePacker和packerOptions。
       OH_PackingOptions_Release(g_thisPicture->packerOptions);
       g_thisPicture->packerOptions = nullptr;
       OH_ImagePackerNative_Release(g_thisPicture->imagePacker);
       g_thisPicture->imagePacker = nullptr;
       
       if (g_thisPicture->errorCode != IMAGE_SUCCESS) {
           OH_LOG_ERROR(LOG_APP, "OH_ImagePackerNative_PackToDataFromPicture failed, errCode: %{public}d.",
                        g_thisPicture->errorCode);
           delete[] outData;
           return GetJsResult(env, g_thisPicture->errorCode);
       } else {
           OH_LOG_DEBUG(LOG_APP, "OH_ImagePackerNative_PackToDataFromPicture success !");
       }
       delete[] outData;
       return GetJsResult(env, g_thisPicture->errorCode);
   }
   
   // PackToFile。
   napi_value PackToFileFromPicture(napi_env env, napi_callback_info info)
   {
       size_t argc = 2;
       napi_value args[2] = {nullptr};
       if (napi_get_cb_info(env, info, &argc, args, nullptr, nullptr) != napi_ok) {
       OH_LOG_ERROR(LOG_APP, "napi_get_cb_info failed!");
           return GetJsResult(env, g_thisPicture->errorCode);
       }
       uint32_t fd = 0;
       napi_get_value_uint32(env, args[0], &fd);
   
       if (g_thisPicture->packerOptions == nullptr) {
           g_thisPicture->errorCode = OH_PackingOptions_Create(&g_thisPicture->packerOptions);
       }
       if (g_thisPicture->imagePacker == nullptr) {
           g_thisPicture->errorCode = OH_ImagePackerNative_Create(&g_thisPicture->imagePacker);
       }
       
       char strFormat[MAX_FORMAT_LENGTH];
       size_t strFormatSize;
       napi_get_value_string_utf8(env, args[1], strFormat, MAX_FORMAT_LENGTH, &strFormatSize);
       OH_LOG_INFO(LOG_APP, "PackToFileFromPicture format: %{public}s", strFormat);
   
       Image_MimeType format;
       format.size = strFormatSize;
       format.data = const_cast<char *>(strFormat);
       uint32_t quality = 95;
       bool needsPackProperties = false;
       int32_t desiredDynamicRange = SDR;
       SetPackOptions(g_thisPicture->packerOptions, format, quality, needsPackProperties, desiredDynamicRange);
       // 确保picture对象已被创建。
       g_thisPicture->errorCode = OH_ImagePackerNative_PackToFileFromPicture(
           g_thisPicture->imagePacker, g_thisPicture->packerOptions, g_thisPicture->picture, fd);
       
       // 释放imagePacker和packerOptions。
       OH_PackingOptions_Release(g_thisPicture->packerOptions);
       g_thisPicture->packerOptions = nullptr;
       OH_ImagePackerNative_Release(g_thisPicture->imagePacker);
       g_thisPicture->imagePacker = nullptr;
       
       if (g_thisPicture->errorCode != IMAGE_SUCCESS) {
           OH_LOG_ERROR(LOG_APP, "OH_ImagePackerNative_PackToFileFromPicture failed,"
                        "errCode: %{public}d.", g_thisPicture->errorCode);
           return GetJsResult(env, g_thisPicture->errorCode);
       } else {
           OH_LOG_DEBUG(LOG_APP, "OH_ImagePackerNative_PackToFileFromPicture success !");
       }
   
       return GetJsResult(env, g_thisPicture->errorCode);
   }
   ```
