# OH_AuxiliaryPictureNative

```c
typedef struct OH_AuxiliaryPictureNative OH_AuxiliaryPictureNative
```

## 概述

AuxiliaryPicture结构体类型，用于执行AuxiliaryPicture相关操作。<br>使用[OH_AuxiliaryPictureNative_Create](capi-picture-native-h.md#oh_auxiliarypicturenative_create)函数创建OH_AuxiliaryPictureNative对象。<br>使用[OH_PictureNative_GetAuxiliaryPicture](capi-picture-native-h.md#oh_picturenative_getauxiliarypicture)函数从OH_PictureNative对象中按辅助图类型获取OH_AuxiliaryPictureNative对象。<br>使用[OH_AuxiliaryPictureNative_Release](capi-picture-native-h.md#oh_auxiliarypicturenative_release)函数释放OH_AuxiliaryPictureNative对象。<br>使用约束：使用OH_AuxiliaryPictureNative对象前，需先创建或获取对象；使用完成后，应调用[OH_AuxiliaryPictureNative_Release](capi-picture-native-h.md#oh_auxiliarypicturenative_release)释放对象。通过[OH_AuxiliaryPictureNative_Create](capi-picture-native-h.md#oh_auxiliarypicturenative_create)创建对象时，data、size和auxiliaryPicture均不能为空指针，dataLength必须大于0，type必须为当前支持的[Image_AuxiliaryPictureType](capi-picture-native-h.md#image_auxiliarypicturetype)。<br>资源管理：释放OH_PictureNative对象不会自动释放已经获取出的OH_AuxiliaryPictureNative对象；释放OH_AuxiliaryPictureNative对象也不会从OH_PictureNative对象中移除对应辅助图。通过[OH_AuxiliaryPictureNative_GetInfo](capi-picture-native-h.md#oh_auxiliarypicturenative_getinfo)获取到的OH_AuxiliaryPictureInfo对象由调用方管理，使用完成后应调用[OH_AuxiliaryPictureInfo_Release](capi-picture-native-h.md#oh_auxiliarypictureinfo_release)释放。通过[OH_AuxiliaryPictureNative_GetMetadata](capi-picture-native-h.md#oh_auxiliarypicturenative_getmetadata)获取到的OH_PictureMetadata对象由调用方管理，使用完成后应调用[OH_PictureMetadata_Release](capi-image-common-h.md#oh_picturemetadata_release)释放。接口返回失败时，输出参数的内容不能在后续流程中继续使用。<br>OH_AuxiliaryPictureNative结构体内容和操作方式如下：

**起始版本：** 13

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [picture_native.h](capi-picture-native-h.md)

