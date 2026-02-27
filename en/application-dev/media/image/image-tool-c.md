# Using Image_NativeModule to Edit Exif Data
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

Image Kit provides the capabilities of reading and editing Exchangeable Image File Format (Exif) data.

Exif is a file format dedicated for photos taken by digital cameras and is used to record attributes and shooting data of the photos. Currently, JPEG, PNG, HEIF, and WEBP<sup>23+</sup> images that contain Exif data are supported.

Users may need to view or modify the Exif data of photos in the Gallery application. When the manual lens parameters of the camera are not automatically written as part of the Exif data or the shooting time is incorrect due to camera power-off, you can manually correct the Exif data.

Currently, OpenHarmony allows you to view and modify part of Exif data. For details, see [OHOS_IMAGE_PROPERTY_XXX](../../reference/apis-image-kit/capi-image-common-h.md#variables).

## How to Develop

### Adding a Link Library

Open the **src/main/cpp/CMakeLists.txt** file of the native project, add **libimage_source.so** and **libhilog_ndk.z.so** (on which the log APIs depend) to the **target_link_libraries** dependency.

```txt
target_link_libraries(entry PUBLIC libhilog_ndk.z.so libimage_source.so)
```

### Calling the Native APIs

For details about the C APIs for reading and editing Exif data, see [OH_ImageSource_GetImageProperty](../../reference/apis-image-kit/capi-image-source-native-h.md#oh_imagesourcenative_getimageproperty) and [OH_ImageSource_ModifyImageProperty](../../reference/apis-image-kit/capi-image-source-native-h.md#oh_imagesourcenative_modifyimageproperty).

Create a native C++ application in DevEco Studio. The project created by default contains the **index.ets** file, and a **hello.cpp** or **napi_init.cpp** file is generated in the **entry\src\main\cpp** directory. In this example, the generated file is **hello.cpp**. Implement the C APIs in **hello.cpp**. Refer to the sample code below.

**Example for Reading and Editing Exif Data**

> **NOTE**
>
> Certain APIs are supported only in API version 20 or later. You should select an appropriate API version during development.

1. Import the required header files.

   <!-- @[editExif_operations_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadImageSource.cpp) -->      
   
   ``` C++
   #include <string>
   #include <hilog/log.h>
   #include <multimedia/image_framework/image/image_source_native.h>
   #include "napi/native_api.h"
   ```

2. Modify the log macro definition as required.

   <!-- @[define_logInfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadImageSource.cpp) -->     
   
   ``` C++
   #undef LOG_DOMAIN
   #undef LOG_TAG
   #define LOG_DOMAIN 0x3200
   #define LOG_TAG "IMAGE_SAMPLE"
   ```

3. Define the ImageSourceNative class.

   <!-- @[define_sourceClass](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/imageKits.h) -->    
   
   ``` C
   class ImageSourceNative {
   public:
       OH_ImageSource_Info *imageInfo;
       OH_ImageSourceNative *source = nullptr;
       OH_PixelmapNative *resPixMap = nullptr;
       OH_Pixelmap_ImageInfo *pixelmapImageInfo = nullptr;
       uint32_t frameCnt = 0;
       ImageSourceNative() {}
       ~ImageSourceNative() {}
   };
   ```
   
4. Create an instance of ImageSourceNative.

   <!-- @[create_sourceClass](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadImageSource.cpp) -->   
   
   ``` C++
   static ImageSourceNative *g_thisImageSource = new ImageSourceNative();
   ```

5. Create the GetJsResult function to process the NAPI return value.

   <!-- @[get_returnValue](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/napi_init.cpp) -->     
   
   ``` C++
   // Process the NAPI return value.
   napi_value GetJsResult(napi_env env, int result)
   {
       napi_value resultNapi = nullptr;
       napi_create_int32(env, result, &resultNapi);
       return resultNapi;
   }
   ```

6. After an ImageSource object is created, read and edit its Exif data.

   > **NOTE**
   >
   > For details about how to create an ImageSource object, see [Image Decoding](../image/image-source-c.md).

   <!-- @[editExif_operations](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadImageSource.cpp) -->     
   
   ``` C++
   // Obtain the value of a specified property.
   napi_value GetImageProperty(napi_env env, napi_callback_info info)
   {
       napi_value argValue[1] = {nullptr};
       size_t argCount = 1;
       if (napi_get_cb_info(env, info, &argCount, argValue, nullptr, nullptr) != napi_ok || argCount < 1 ||
           argValue[0] == nullptr) {
           OH_LOG_ERROR(LOG_APP, "GetImageProperty napi_get_cb_info failed!");
           return GetJsResult(env, IMAGE_BAD_PARAMETER);
       }
       // Modify the value of a specified property key.
       char key[MAX_STRING_LENGTH];
       size_t keySize = MAX_STRING_LENGTH;
       napi_get_value_string_utf8(env, argValue[0], (char *)key, sizeof(key), &keySize);
       Image_String getKey;
       getKey.data = key;
       getKey.size = keySize;
       Image_String getValue;
       OH_LOG_INFO(LOG_APP, "OH_ImageSourceNative_GetImageProperty key: %{public}s.", getKey.data);
       Image_ErrorCode errCode = OH_ImageSourceNative_GetImagePropertyWithNull(g_thisImageSource->source,
                                                                               &getKey, &getValue);
       if (errCode != IMAGE_SUCCESS) {
           OH_LOG_ERROR(LOG_APP, "OH_ImageSourceNative_GetImageProperty failed, errCode: %{public}d.", errCode);
           return GetJsResult(env, errCode);
       }
       napi_value resultNapi = nullptr;
       napi_create_string_utf8(env, getValue.data, getValue.size, &resultNapi);
       free(getValue.data);
       getValue.data = nullptr;
       return resultNapi;
   }
   
   // Modify the value of a specified property.
   napi_value ModifyImageProperty(napi_env env, napi_callback_info info)
   {
       napi_value argValue[2] = {nullptr};
       size_t argCount = 2;
       const size_t minCount = 2;
       if (napi_get_cb_info(env, info, &argCount, argValue, nullptr, nullptr) != napi_ok || argCount < minCount ||
           argValue[0] == nullptr || argValue[1] == nullptr) {
           OH_LOG_ERROR(LOG_APP, "ModifyImageProperty napi_get_cb_info failed!");
           return GetJsResult(env, IMAGE_BAD_PARAMETER);
       }
   
       // Obtain the key to be modified.
       char key[MAX_STRING_LENGTH];
       size_t keySize = MAX_STRING_LENGTH;
       napi_get_value_string_utf8(env, argValue[0], (char *)key, sizeof(key), &keySize);
       Image_String setKey;
       setKey.data = key;
       setKey.size = keySize;
       OH_LOG_INFO(LOG_APP, "ModifyImageProperty key: %{public}s.", setKey.data);
       
       // Obtain the value to be modified.
       char value[MAX_STRING_LENGTH];
       size_t valueSize;
       napi_get_value_string_utf8(env, argValue[1], (char *)value, MAX_STRING_LENGTH, &valueSize);
       Image_String setValue;
       setValue.data = value;
       setValue.size = valueSize;
       OH_LOG_INFO(LOG_APP, "ModifyImageProperty value: %{public}s.", setValue.data);
   
       Image_ErrorCode errCode = OH_ImageSourceNative_ModifyImageProperty(g_thisImageSource->source, &setKey, &setValue);
       return ReturnErrorCode(env, errCode, "OH_ImageSourceNative_ModifyImageProperty");
   }
   ```
