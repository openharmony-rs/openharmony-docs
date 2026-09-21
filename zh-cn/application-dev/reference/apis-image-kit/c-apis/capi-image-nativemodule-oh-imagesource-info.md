# OH_ImageSource_Info

```c
struct OH_ImageSource_Info
```

## 概述

OH_ImageSource_Info是native层封装的ImageSource信息结构体，OH_ImageSource_Info结构体不可直接操作，而是采用函数调用方式创建、释放结构体以及操作具体字段。<br> 使用{@link OH_ImageSourceInfo_Create}函数创建OH_ImageSource_Info对象。<br>使用{@link OH_ImageSourceNative_GetImageInfo}<br>函数将OH_ImageSourceNative中的图像信息写入创建好的OH_ImageSource_Info对象。<br>使用{@link OH_ImageSourceInfo_Release}<br>函数释放OH_ImageSource_Info对象。<br>使用约束：OH_ImageSource_Info对象通常配合{@link OH_ImageSourceNative_GetImageInfo}使用，用于承载指定序号图片的宽、<br>高、动态范围和MIME类型等信息。使用前需通过{@link OH_ImageSourceInfo_Create}创建对象；使用完成后，应调用{@link OH_ImageSourceInfo_Release}释放对象。<br> OH_ImageSource_Info结构体内容和操作方式如下：

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**起始版本：** 12

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [image_source_native.h](capi-image-source-native-h.md)

