# 使用Image_NativeModule编辑图片Exif信息
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

Image Kit提供图片Exif信息的读取与编辑能力。

Exif（Exchangeable image file format）是专门为数码相机的照片设定的文件格式，可以记录数码照片的属性信息和拍摄数据。当前支持JPEG、PNG、HEIF、WEBP<sup>23+</sup>格式，且需要图片包含Exif信息。

在图库等应用中，需要查看或修改数码照片的Exif信息。由于摄像机的手动镜头参数无法自动写入到Exif信息中或者因为相机断电等原因会导致拍摄时间出错，这时需要手动修改错误的Exif数据，即可使用本功能。

OpenHarmony目前仅支持对部分Exif信息的查看和修改，具体支持的范围请参见：[OHOS_IMAGE_PROPERTY_XXX](../../reference/apis-image-kit/capi-image-common-h.md#变量)。

## 开发步骤

### 添加链接库

在进行应用开发之前，开发者需要打开native工程的src/main/cpp/CMakeLists.txt，在target_link_libraries依赖中添加libimage_source.so 以及日志依赖libhilog_ndk.z.so。

```txt
target_link_libraries(entry PUBLIC libhilog_ndk.z.so libimage_source.so)
```

### Native接口调用

Exif信息的读取与编辑相关C API接口的详细介绍请参见[OH_ImageSource_GetImageProperty](../../reference/apis-image-kit/capi-image-source-native-h.md#oh_imagesourcenative_getimageproperty) 和 [OH_ImageSource_ModifyImageProperty](../../reference/apis-image-kit/capi-image-source-native-h.md#oh_imagesourcenative_modifyimageproperty)。

在Deveco Studio新建Native C++应用，默认生成的项目中包含index.ets文件，在entry\src\main\cpp目录下会自动生成一个cpp文件（hello.cpp或napi_init.cpp，本示例以hello.cpp文件名为例）。在hello.cpp中实现C API接口调用逻辑，示例代码如下：

**读取和编辑图片Exif信息接口使用示例**

> **说明：**
> 部分接口为API20以后才支持的，请开发者在进行开发时选择合适的API版本。

1. 导入相关头文件。

   <!-- @[editExif_operations_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadImageSource.cpp) -->     

2. 日志宏定义可参考下述代码按实际需求自行修改。

   <!-- @[define_logInfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadImageSource.cpp) -->   

3. 定义ImageSourceNative类。

   <!-- @[define_sourceClass](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/imageKits.h) -->   

4. 创建ImageSourceNative的一个实例。

   <!-- @[create_sourceClass](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadImageSource.cpp) -->   

5. 创建GetJsResult函数处理napi返回值。

   <!-- @[get_returnValue](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/napi_init.cpp) -->   

6. 在成功创建ImageSource对象后，读取、编辑Exif信息。

   >**说明：**
   >创建ImageSource对象可参考[图片解码](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/image-source-c)。

   <!-- @[editExif_operations](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadImageSource.cpp) -->   
