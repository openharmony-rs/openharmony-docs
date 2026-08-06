# OH_PictureNative

```c
typedef struct OH_PictureNative OH_PictureNative
```

## 概述

Picture结构体类型，用于执行picture相关操作。<br>Picture为多图对象结构体，包含主图、辅助图和元数据。<br>主图包含图像的大部分信息，主要用于显示图像内容。<br>辅助图用于存储与主图相关但不同的数据，展示图像更丰富的信息。<br>元数据一般用来存储关于图像文件的信息。<br>有多种方式创建OH_PictureNative，具体如下：<br>使用[OH_PictureNative_Release](capi-picture-native-h.md#oh_picturenative_release)函数释放OH_PictureNative对象。<br>使用约束：使用OH_PictureNative对象前，需先创建对象；使用完成后，应调用[OH_PictureNative_Release](capi-picture-native-h.md#oh_picturenative_release)释放对象。通过{@link OH_ImageSourceNative_CreatePicture}或{@link OH_ImageSourceNative_CreatePictureAtIndex}解码Picture时，图片源格式需支持Picture解码。通过[OH_PictureNative_CreatePicture](capi-picture-native-h.md#oh_picturenative_createpicture)创建Picture时，mainPixelmap和picture均不能为空指针。<br>资源管理：释放OH_ImageSourceNative对象不会自动释放已创建的OH_PictureNative对象。通过OH_PictureNative获取到的OH_PixelmapNative、OH_AuxiliaryPictureNative和OH_PictureMetadata对象由调用方管理，使用完成后需分别调用{@link OH_PixelmapNative_Destroy}、[OH_AuxiliaryPictureNative_Release](capi-picture-native-h.md#oh_auxiliarypicturenative_release)和[OH_PictureMetadata_Release](capi-image-common-h.md#oh_picturemetadata_release)释放。获取PixelMap、辅助图或元数据的接口返回失败时，输出参数的内容不能在后续流程中继续使用。<br>OH_PictureNative结构体内容和操作方式如下：

**起始版本：** 13

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [picture_native.h](capi-picture-native-h.md)

