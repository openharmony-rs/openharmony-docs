# 使用Image_NativeModule完成图片接收
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

图像接收类用于获取组件的surfaceId、接收最新的图片、读取下一张图片以及释放ImageReceiver实例。结合camera API实现的相机预览示例代码可参考[C/C++预览流二次处理示例](../camera/native-camera-preview-imageReceiver.md)。

> **说明：**
> ImageReceiver只作为图片的接收方、消费者，在ImageReceiver设置的size、format等属性实际上并不会生效。图片属性需要在发送方、生产者进行设置，可参考[预览(C/C++)](../camera/native-camera-preview.md)设置previewProfiles。

## 开发步骤

### 添加依赖

在进行应用开发之前，开发者需要打开native工程的src/main/cpp/CMakeLists.txt，在target_link_libraries依赖中添加libohimage.so、libimage_receiver.so、libnative_image.so以及日志依赖libhilog_ndk.z.so。

```txt
target_link_libraries(entry PUBLIC libhilog_ndk.z.so libohimage.so libimage_receiver.so libnative_image.so)
```

### Native接口调用

具体接口说明请参考[API文档](../../reference/apis-image-kit/capi-image-nativemodule.md)。

下述代码主要演示了有关Receiver的初始化，相机预览流的创建，以及获取图像的信息和Receiver的释放等相关功能。

> **说明：**
> 部分接口为API20以后才支持的，请开发者在进行开发时选择合适的API版本。

<!-- @[receiver_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageNativeSample/entry/src/main/cpp/loadReceiver.cpp) -->   

