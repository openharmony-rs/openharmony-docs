# OH_AuxiliaryPictureInfo

```c
typedef struct OH_AuxiliaryPictureInfo OH_AuxiliaryPictureInfo
```

## 概述

AuxiliaryPictureInfo结构体类型，用于执行AuxiliaryPictureInfo相关操作。<br>使用[OH_AuxiliaryPictureInfo_Create](capi-picture-native-h.md#oh_auxiliarypictureinfo_create)函数创建OH_AuxiliaryPictureInfo对象。<br>使用[OH_AuxiliaryPictureNative_GetInfo](capi-picture-native-h.md#oh_auxiliarypicturenative_getinfo)函数从OH_AuxiliaryPictureNative对象中获取OH_AuxiliaryPictureInfo对象。<br>使用[OH_AuxiliaryPictureInfo_Release](capi-picture-native-h.md#oh_auxiliarypictureinfo_release)函数释放OH_AuxiliaryPictureInfo对象。<br>使用约束：使用OH_AuxiliaryPictureInfo对象前，需先创建或获取对象；使用完成后，应调用[OH_AuxiliaryPictureInfo_Release](capi-picture-native-h.md#oh_auxiliarypictureinfo_release)释放对象。调用[OH_AuxiliaryPictureInfo_GetType](capi-picture-native-h.md#oh_auxiliarypictureinfo_gettype)、[OH_AuxiliaryPictureInfo_GetSize](capi-picture-native-h.md#oh_auxiliarypictureinfo_getsize)、[OH_AuxiliaryPictureInfo_GetRowStride](capi-picture-native-h.md#oh_auxiliarypictureinfo_getrowstride)或[OH_AuxiliaryPictureInfo_GetPixelFormat](capi-picture-native-h.md#oh_auxiliarypictureinfo_getpixelformat)时，输出参数不允许传入nullptr；接口返回失败时，输出参数的内容不能在后续流程中继续使用。只有在明确辅助图实际状态与OH_AuxiliaryPictureInfo对象信息不一致或有明确业务诉求时，才需要手动设置OH_AuxiliaryPictureInfo。<br>资源管理：[OH_AuxiliaryPictureNative_GetInfo](capi-picture-native-h.md#oh_auxiliarypicturenative_getinfo)成功返回的OH_AuxiliaryPictureInfo对象由调用方管理。通过[OH_AuxiliaryPictureNative_SetInfo](capi-picture-native-h.md#oh_auxiliarypicturenative_setinfo)设置辅助图信息时，接口会读取并保存OH_AuxiliaryPictureInfo中的信息值，接口返回后调用方仍需自行管理该OH_AuxiliaryPictureInfo对象的生命周期。<br>OH_AuxiliaryPictureInfo结构体内容和操作方式如下：

**起始版本：** 13

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [picture_native.h](capi-picture-native-h.md)

