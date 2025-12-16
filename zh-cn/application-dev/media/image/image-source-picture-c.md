# 使用Image_NativeModule完成多图对象解码
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

创建ImageSource实例，解码获取Picture，然后释放ImageSource实例。

## 开发步骤

### 添加链接库

在进行应用开发之前，开发者需要打开native工程的src/main/cpp/CMakeLists.txt，在target_link_libraries依赖中添加libimage_source.so 以及日志依赖libhilog_ndk.z.so。

```txt
target_link_libraries(entry PUBLIC libhilog_ndk.z.so libimage_source.so)
```

### Native接口调用

具体接口说明请参考[API文档](../../reference/apis-image-kit/capi-image-nativemodule.md)。

在Deveco Studio新建Native C++应用，默认生成的项目中包含index.ets文件，在entry\src\main\cpp目录下会自动生成一个cpp文件（hello.cpp或napi_init.cpp，本示例以hello.cpp文件名为例）。在hello.cpp中实现C API接口调用逻辑，示例代码如下：

**解码接口使用示例**

> **说明：**
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

3. 定义ImagePictureNative类。

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

4. 创建一个ImagePictureNative实例。

   <!-- @[create_pictureClass](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadPicture.cpp) -->    
   
   ``` C++
   static ImagePictureNative *g_thisPicture = new ImagePictureNative();
   ```

5. 定义ImageAuxiliaryPictureNative类。

   <!-- @[define_auxPictureClass](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/imageKits.h) -->    
   
   ``` C
   class ImageAuxiliaryPictureNative {
   public:
       Image_ErrorCode errorCode = IMAGE_SUCCESS;
       Image_AuxiliaryPictureType type = AUXILIARY_PICTURE_TYPE_GAINMAP;
       OH_AuxiliaryPictureNative *auxiliaryPicture = nullptr;
       size_t buffSize = 640 * 480 * 4; // 辅助图size：`长 * 宽 * 每个像素占用的字节数`。
       ImageAuxiliaryPictureNative() {}
       ~ImageAuxiliaryPictureNative() {}
   };
   ```

6. 创建一个ImageAuxiliaryPictureNative实例。

   <!-- @[create_auxPictureClass](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadPicture.cpp) -->    
   
   ``` C++
   static ImageAuxiliaryPictureNative *g_thisAuxiliaryPicture  = new ImageAuxiliaryPictureNative();
   ```

7. 创建GetJsResult函数处理napi返回值。

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

8. 创建解码参数，配置解码参数，调用解码接口进行解码并获取辅助图。

   <!-- @[picture_operations](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadPicture.cpp) -->     
   
   ``` C++
   // 释放ImageSource。
   napi_value ReleasePictureSource(napi_env env, napi_callback_info info)
   {
       if (g_thisPicture->source != nullptr) {
           g_thisPicture->errorCode = OH_ImageSourceNative_Release(g_thisPicture->source);
           g_thisPicture->source = nullptr;
           return GetJsResult(env, g_thisPicture->errorCode);
       }
       
       if (g_thisPicture->picture != nullptr) {
           g_thisPicture->errorCode = OH_PictureNative_Release(g_thisPicture->picture);
           g_thisPicture->picture = nullptr;
           return GetJsResult(env, g_thisPicture->errorCode);
       }
       
       OH_LOG_DEBUG(LOG_APP, "ReleasePictureSource source is null !");
       return GetJsResult(env, g_thisPicture->errorCode);
   }
   
   // 创造解码参数。
   napi_value CreateDecodingOptions(napi_env env, napi_callback_info info)
   {
       g_thisPicture->errorCode = OH_DecodingOptionsForPicture_Create(&g_thisPicture->options);
   
       if (g_thisPicture->errorCode != IMAGE_SUCCESS) {
           OH_LOG_ERROR(LOG_APP, "OH_DecodingOptionsForPicture_Create failed, errCode: %{public}d.",
                        g_thisPicture->errorCode);
           return GetJsResult(env, g_thisPicture->errorCode);
       } else {
           OH_LOG_DEBUG(LOG_APP, "OH_DecodingOptionsForPicture_Create success !");
       }
   
       return GetJsResult(env, g_thisPicture->errorCode);
   }
   
   // 配置解码参数 从应用层传入。
   napi_value SetDesiredAuxiliaryPictures(napi_env env, napi_callback_info info)
   {
       size_t argc = 1;
       napi_value args[1] = {nullptr};
       if (napi_get_cb_info(env, info, &argc, args, nullptr, nullptr) != napi_ok || argc < 1 || args[0] == nullptr) {
           OH_LOG_ERROR(LOG_APP, "napi_get_cb_info failed !");
           return GetJsResult(env, IMAGE_BAD_PARAMETER);
       }
   
       uint32_t length = 0;
       napi_get_array_length(env, args[0], &length);
       if (length <= 0) {
           OH_LOG_ERROR(LOG_APP, "napi_get_array_length failed !");
           return GetJsResult(env, IMAGE_UNKNOWN_ERROR);
       }
       Image_AuxiliaryPictureType typeList[length];
       for (int index = 0; index < length; index++) {
           napi_value element;
           uint32_t ulType = 0;
           napi_get_element(env, args[0], index, &element);
           napi_get_value_uint32(env, element, &ulType);
           typeList[index] = static_cast<Image_AuxiliaryPictureType>(ulType);
           OH_LOG_DEBUG(LOG_APP, "ulType is :%{public}d", ulType);
       }
       
       // 调用OH_DecodingOptionsForPicture_Create接口创建DecodingOptions。
       CreateDecodingOptions(env, info);
       g_thisPicture->errorCode =
           OH_DecodingOptionsForPicture_SetDesiredAuxiliaryPictures(g_thisPicture->options, typeList, length);
       if (g_thisPicture->errorCode != IMAGE_SUCCESS) {
           OH_LOG_ERROR(LOG_APP, "OH_DecodingOptionsForPicture_SetDesiredAuxiliaryPictures failed,errCode: %{public}d.",
                        g_thisPicture->errorCode);
           return GetJsResult(env, g_thisPicture->errorCode);
       } else {
           OH_LOG_DEBUG(LOG_APP, "OH_DecodingOptionsForPicture_SetDesiredAuxiliaryPictures success !");
       }
   
       return GetJsResult(env, g_thisPicture->errorCode);
   }
   
   // 解码。
   napi_value CreatePictureByImageSource(napi_env env, napi_callback_info info)
   {
       size_t argc = 1;
       napi_value args[1] = {nullptr};
   
       if (napi_get_cb_info(env, info, &argc, args, nullptr, nullptr) != napi_ok || argc < 1 || args[0] == nullptr) {
           OH_LOG_ERROR(LOG_APP, "CreatePicture_ napi_get_cb_info failed !");
           return GetJsResult(env, IMAGE_BAD_PARAMETER);
       }
       
       char filePath[MAX_SIZE];
       size_t pathSize;
       napi_get_value_string_utf8(env, args[0], filePath, MAX_SIZE, &pathSize);
   
       g_thisPicture->errorCode = OH_ImageSourceNative_CreateFromUri(filePath, pathSize, &g_thisPicture->source);
       if (g_thisPicture->errorCode != IMAGE_SUCCESS) {
           OH_LOG_ERROR(LOG_APP, "OH_ImageSourceNative_CreateFromUri failed, errCode: %{public}d.",
                        g_thisPicture->errorCode);
           return GetJsResult(env, g_thisPicture->errorCode);
       } else {
           OH_LOG_DEBUG(LOG_APP, "OH_ImageSourceNative_CreateFromUri success !");
       }
       
       // 先创建解码参数，再进行解码，此处创建解码参数的接口在SetDesiredAuxiliaryPictures实现。
       g_thisPicture->errorCode =
           OH_ImageSourceNative_CreatePicture(g_thisPicture->source, g_thisPicture->options, &g_thisPicture->picture);
       
       // 释放options。
       OH_DecodingOptionsForPicture_Release(g_thisPicture->options);
       g_thisPicture->options = nullptr;
       
       g_thisAuxiliaryPicture ->errorCode = OH_PictureNative_GetAuxiliaryPicture(g_thisPicture->picture,
           g_thisAuxiliaryPicture ->type, &g_thisAuxiliaryPicture ->auxiliaryPicture);
       if (g_thisAuxiliaryPicture ->errorCode == IMAGE_SUCCESS) {
           uint8_t* buff = new uint8_t[g_thisAuxiliaryPicture ->buffSize];
           OH_AuxiliaryPictureNative_ReadPixels(g_thisAuxiliaryPicture ->auxiliaryPicture, buff,
               &g_thisAuxiliaryPicture ->buffSize);
           OH_AuxiliaryPictureNative_Release(g_thisAuxiliaryPicture ->auxiliaryPicture);
           g_thisAuxiliaryPicture ->auxiliaryPicture = nullptr;
           delete []buff;
       }
       
       if (g_thisPicture->errorCode != IMAGE_SUCCESS) {
           OH_LOG_ERROR(LOG_APP, "ImageSourceNative_CreatePicture failed, errCode: %{public}d.",
                        g_thisPicture->errorCode);
           return GetJsResult(env, g_thisPicture->errorCode);
       } else {
           OH_LOG_DEBUG(LOG_APP, "ImageSourceNative_CreatePicture success !");
       }
       
       return GetJsResult(env, g_thisPicture->errorCode);
   }
   ```
