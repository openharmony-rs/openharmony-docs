# 使用Image_NativeModule完成图片接收
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

图像接收类，用于获取组件的surfaceId、接收最新的图片、读取下一张图片以及释放ImageReceiver实例。结合camera API实现的相机预览示例代码可参考[预览流二次处理(C/C++)](../camera/native-camera-preview-imageReceiver.md)。

> **说明：**
>
> ImageReceiver只作为图片的接收方、消费者，在ImageReceiver设置的size、format等属性实际上并不会生效。图片属性需要在发送方、生产者进行设置，可参考[预览(C/C++)](../camera/native-camera-preview.md)设置previewProfiles。

## 开发步骤

### 添加依赖

在进行应用开发之前，开发者需要打开native工程的src/main/cpp/CMakeLists.txt，在target_link_libraries依赖中添加libohimage.so、libimage_receiver.so、libnative_image.so以及日志依赖libhilog_ndk.z.so。

```txt
target_link_libraries(entry PUBLIC libhilog_ndk.z.so libohimage.so libimage_receiver.so libnative_image.so)
```

### Native接口调用

具体接口说明请参考[API文档](../../reference/apis-image-kit/capi-image-nativemodule.md)。

下述代码主要演示了Receiver的初始化、相机预览流的创建以及获取图像的信息和Receiver的释放等相关功能。

> **说明：**
>
> 部分接口在API version 20以后才支持，需要开发者在进行开发时选择合适的API版本。

1. 导入相关头文件。

   <!-- @[receiver_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadReceiver.cpp) -->        
   
   ``` C++
   #include <hilog/log.h>
   #include "napi/native_api.h"
   #include <string>
   #include <multimedia/image_framework/image/image_native.h>
   #include <multimedia/image_framework/image/image_receiver_native.h>
   
   #include "ohcamera/camera.h"
   #include "ohcamera/camera_input.h"
   #include "ohcamera/capture_session.h"
   #include "ohcamera/photo_output.h"
   #include "ohcamera/preview_output.h"
   #include "ohcamera/video_output.h"
   #include "ohcamera/camera_manager.h"
   
   #include <mutex>
   #include <condition_variable>
   ```

2. 常量定义。

   <!-- @[receiver_defineConst](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadReceiver.cpp) -->      
   
   ``` C++
   #undef LOG_DOMAIN
   #define LOG_DOMAIN 0x3200
   
   #undef LOG_TAG
   #define LOG_TAG "MY_TAG"
   
   #define IMAGE_WIDTH 320
   #define IMAGE_HEIGHT 480
   #define IMAGE_CAPACITY 2
   ```

3. 定义全局变量。

   <!-- @[define_receiverInstance](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/imageKits.h) -->      

4. 定义一些工具类函数，用来处理napi的返回值和参数类型的转换。
 
   <!-- @[receiver_utility](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadReceiver.cpp) -->      
   
   ``` C++
   // 处理napi返回值。
   napi_value GetJsResultDemo(napi_env env, int result)
   {
       napi_value resultNapi = nullptr;
       napi_create_int32(env, result, &resultNapi);
       return resultNapi;
   }
   
   // 将uint64_t转换为一个以null结尾的char数组。
   std::unique_ptr<char[]> ConvertUint64ToCharTemp(uint64_t value)
   {
       std::string strValue = std::to_string(value);
       auto charBuffer = std::make_unique<char[]>(strValue.size() + 1);
       std::copy(strValue.begin(), strValue.end(), charBuffer.get());
       charBuffer[strValue.size()] = '\0';
   
       return charBuffer;
   }
   ```

5. 初始化Receiver。

   - 创建并设置ReceiverOptions。

     <!-- @[set_receiverOptions](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadReceiver.cpp) -->       
     
     ``` C++
     static Image_ErrorCode CreateAndConfigOptions(OH_ImageReceiverOptions** options)
     {
         Image_ErrorCode errCode = OH_ImageReceiverOptions_Create(options);
         if (errCode != IMAGE_SUCCESS) {
             OH_LOG_ERROR(LOG_APP, "Create image receiver options failed, errCode: %{public}d.", errCode);
             return errCode;
         }
         Image_Size imgSize = {IMAGE_WIDTH, IMAGE_HEIGHT};
         errCode = OH_ImageReceiverOptions_SetSize(*options, imgSize);
         if (errCode != IMAGE_SUCCESS) {
             OH_LOG_ERROR(LOG_APP, "Set image receiver options size failed, errCode: %{public}d.", errCode);
             OH_ImageReceiverOptions_Release(*options);
             return errCode;
         }
         errCode = OH_ImageReceiverOptions_SetCapacity(*options, IMAGE_CAPACITY);
         if (errCode != IMAGE_SUCCESS) {
             OH_LOG_ERROR(LOG_APP, "Set image receiver options capacity failed, errCode: %{public}d.", errCode);
             OH_ImageReceiverOptions_Release(*options);
             return errCode;
         }
         return IMAGE_SUCCESS;
     }
     ```

   - 获取ReceiverOptions。

     <!-- @[get_receiverOptions](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadReceiver.cpp) -->       
     
     ``` C++
     static Image_ErrorCode ValidateOptions(OH_ImageReceiverOptions* options)
     {
         Image_Size imgSizeRead;
         Image_ErrorCode errCode = OH_ImageReceiverOptions_GetSize(options, &imgSizeRead);
         if (errCode != IMAGE_SUCCESS) {
             OH_LOG_ERROR(LOG_APP, "Get image receiver options size failed, errCode: %{public}d.", errCode);
             return errCode;
         }
         if (imgSizeRead.width != IMAGE_WIDTH || imgSizeRead.height != IMAGE_HEIGHT) {
             OH_LOG_ERROR(LOG_APP, "Get image receiver options size failed,"
                          "width: %{public}d, height: %{public}d.", imgSizeRead.width, imgSizeRead.height);
             return IMAGE_BAD_PARAMETER;
         }
         int32_t capacity = 0;
         errCode = OH_ImageReceiverOptions_GetCapacity(options, &capacity);
         if (errCode != IMAGE_SUCCESS) {
             OH_LOG_ERROR(LOG_APP, "Get image receiver options capacity failed, errCode: %{public}d.", errCode);
             return errCode;
         }
         if (capacity != IMAGE_CAPACITY) {
             OH_LOG_ERROR(LOG_APP, "Get image receiver options capacity failed, capacity: %{public}d.", capacity);
             return IMAGE_BAD_PARAMETER;
         }
         return IMAGE_SUCCESS;
     }
     ```

   - 创建Receiver对象。

     <!-- @[create_receiver](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadReceiver.cpp) -->       
     
     ``` C++
     static Image_ErrorCode CreateReceiver(OH_ImageReceiverOptions* options, OH_ImageReceiverNative** receiver)
     {
         Image_ErrorCode errCode = OH_ImageReceiverNative_Create(options, receiver);
         if (errCode != IMAGE_SUCCESS) {
             OH_LOG_ERROR(LOG_APP, "Create image receiver failed, errCode: %{public}d.", errCode);
             return errCode;
         }
         return IMAGE_SUCCESS;
     }
     ```
     
   - 定义获取下一张图片的callback函数。

     <!-- @[define_callback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadReceiver.cpp) -->         
     
     ``` C++
     static void OnCallback(OH_ImageReceiverNative* receiver)
     {
         OH_LOG_INFO(LOG_APP, "ImageReceiverNativeCTest buffer available.");
     
         OH_ImageNative* image = nullptr;
         Image_ErrorCode errCode = OH_ImageReceiverNative_ReadNextImage(receiver, &image);
         if (errCode != IMAGE_SUCCESS) {
             OH_LOG_ERROR(LOG_APP, "ImageReceiverNativeCTest get image receiver next image failed,"
                          "errCode: %{public}d.", errCode);
             OH_ImageNative_Release(image);
             return;
         }
     
         {
             std::lock_guard<std::mutex> lock(g_mutex);
             g_imageInfoResult = image;
             g_imageReady = true;
         }
         g_condVar.notify_one();
     }
     ```

   - 注册callback。

     <!-- @[register_callback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadReceiver.cpp) -->       
     
     ``` C++
     static Image_ErrorCode RegisterCallbackAndQuery(OH_ImageReceiverNative* receiver)
     {
         uint64_t surfaceID = 0;
         Image_ErrorCode errCode = OH_ImageReceiverNative_On(receiver, OnCallback);
         if (errCode != IMAGE_SUCCESS) {
             OH_LOG_ERROR(LOG_APP, "Image receiver on failed, errCode: %{public}d.", errCode);
             return errCode;
         }
         errCode = OH_ImageReceiverNative_GetReceivingSurfaceId(receiver, &surfaceID);
         if (errCode != IMAGE_SUCCESS) {
             OH_LOG_ERROR(LOG_APP, "Get image receiver surfaceID failed, errCode: %{public}d.", errCode);
             return errCode;
         }
         OH_LOG_INFO(LOG_APP, "Get image receiver surfaceID: %{public}lu.", surfaceID);
         Image_Size imgSizeRead;
         errCode = OH_ImageReceiverNative_GetSize(receiver, &imgSizeRead);
         if (errCode != IMAGE_SUCCESS) {
             OH_LOG_ERROR(LOG_APP, "Get image receiver size failed, errCode: %{public}d.", errCode);
             return errCode;
         }
         OH_LOG_INFO(LOG_APP, "Get image receiver size: width = %{public}d, height = %{public}d.",
                     imgSizeRead.width, imgSizeRead.height);
         int32_t capacity = 0;
         errCode = OH_ImageReceiverNative_GetCapacity(receiver, &capacity);
         if (errCode != IMAGE_SUCCESS) {
             OH_LOG_ERROR(LOG_APP, "Get image receiver capacity failed, errCode: %{public}d.", errCode);
             return errCode;
         }
         OH_LOG_INFO(LOG_APP, "Get image receiver capacity: %{public}d.", capacity);
         return IMAGE_SUCCESS;
     }
     ```
 
   - 初始化Receiver的整体流程。

     <!-- @[init_receiver](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadReceiver.cpp) -->      

6. 调用相机拍照流进行拍照，触发回调。

   - 创建一个CameraManager实例。

     <!-- @[init_camera](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadReceiver.cpp) -->     

   - 获取相机输出能力

     <!-- @[get_cameraOutCapability](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadReceiver.cpp) -->      
     
     ``` C++
     Camera_ErrorCode GetCameraOutputCapability(Camera_Manager* cameraManager,
                                                Camera_Device* cameras,
                                                uint32_t cameraDeviceIndex,
                                                Camera_OutputCapability*& capability)
     {
         capability = nullptr;
         Camera_ErrorCode ret = OH_CameraManager_GetSupportedCameraOutputCapability(cameraManager,
                                                                                    &cameras[cameraDeviceIndex],
                                                                                    &capability);
         if (capability == nullptr || ret != CAMERA_OK) {
             OH_LOG_ERROR(LOG_APP, "OH_CameraManager_GetSupportedCameraOutputCapability failed.");
         }
         return ret;
     }
     ```

   - 创建相机捕获会话，用于捕获相机拍摄的照片。

      <!-- @[create_captureSession](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadReceiver.cpp) -->      

   - 开启捕获会话。

     <!-- @[start_captureSession](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadReceiver.cpp) -->      

   - 创建相机拍照流。

     <!-- @[start_cameraSession](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadReceiver.cpp) -->      

   - 调用相机拍照的整体流程。

     <!-- @[load_cameraSession](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadReceiver.cpp) -->    

7. 获取Receiver接收到的图片信息。

   - 等待OnCallback回调通知。

     <!-- @[wait_callBack](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadReceiver.cpp) -->     

   - 获取图片大小。

     <!-- @[get_imageSize](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadReceiver.cpp) -->       
     
   - 获取组件类型。

     <!-- @[get_componentType](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadReceiver.cpp) -->      

   - 获取组件信息。

     <!-- @[get_componentInfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadReceiver.cpp) -->      

   - 获取图片属性并封装为napi对象。

     <!-- @[get_imageInfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadReceiver.cpp) -->      

   - 获取ReceiverImageInfo的整体流程。

     <!-- @[get_receiverImageInfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadReceiver.cpp) -->      

8. 释放receiver。

   <!-- @[release_receiver](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadReceiver.cpp) -->     
