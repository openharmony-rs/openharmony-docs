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
> 根据MIME标准，标准编码格式为image/jpeg。当使用image编码时，编码参数中的编码格式image_MimeType设置为image/jpeg，image编码后的文件扩展名可设为.jpg或.jpeg，可在支持image/jpeg解码的平台上使用。
> 部分接口为API20以后才支持的，请开发者在进行开发时选择合适的API版本。

1. 导入相关头文件。

   <!-- @[decodingPicture_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadPicture.cpp) -->     

2. 日志宏定义可参考下述代码按实际需求自行修改。

   <!-- @[define_logInfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadImageSource.cpp) -->   

3. 定义用于图像处理的常量。

   <!-- @[define_const](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadPicture.cpp) -->      

4. 定义ImagePictureNative类。

   <!-- @[define_pictureClass](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/imageKits.h) -->   

5. 创建ImagePictureNative的一个实例。

   <!-- @[create_pictureClass](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadPicture.cpp) -->   

6. 创建GetJsResult函数处理napi返回值。

   <!-- @[get_returnValue](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/napi_init.cpp) -->   

创建ImagePacker实例，指定编码参数后，将Picture多图对象编码至文件或缓冲区。

   <!-- @[pack_picture](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadPicture.cpp) -->    
