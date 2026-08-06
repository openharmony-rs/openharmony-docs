# OH_ImageSourceNative

```c
struct OH_ImageSourceNative
```

## 概述

OH_ImageSourceNative是native层封装的ImageSource结构体，用于创建图片数据。OH_ImageSourceNative结构体不可直接操作，而是采用函数调用方式创建、释放结构体以及操作具体字段。<br>有多种方式创建OH_ImageSourceNative，具体如下：<br>使用[OH_ImageSourceNative_Release](capi-image-source-native-h.md#oh_imagesourcenative_release)函数释放OH_ImageSourceNative对象。<br>使用约束：使用OH_ImageSourceNative对象前，必须先通过上述接口创建对象；使用完成后，应调用[OH_ImageSourceNative_Release](capi-image-source-native-h.md#oh_imagesourcenative_release)释放对象。通过[OH_ImageSourceNative_CreateFromDataWithUserBuffer](capi-image-source-native-h.md#oh_imagesourcenative_createfromdatawithuserbuffer)创建对象时，在OH_ImageSourceNative对象生命周期内，调用方传入的数据缓存必须保持有效，不能被释放、复用或修改为其他图片数据。<br>资源管理：通过OH_ImageSourceNative解码或获取到的{@link OH_PixelmapNative}、[OH_PictureNative](capi-image-nativemodule-oh-picturenative.md)、[OH_ImageRawData](capi-image-nativemodule-oh-imagerawdata.md)对象由调用方分别管理。释放OH_ImageSourceNative对象不会自动释放这些对象，需要调用对应接口释放或销毁。<br>OH_ImageSourceNative结构体内容和操作方式如下：

**起始版本：** 12

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [image_source_native.h](capi-image-source-native-h.md)

