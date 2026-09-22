# OH_AuxiliaryPictureNative

```c
typedef struct OH_AuxiliaryPictureNative OH_AuxiliaryPictureNative
```

## 概述

AuxiliaryPicture结构体类型，用于执行AuxiliaryPicture相关操作。<br>使用{@link OH_AuxiliaryPictureNative_Create}<br>函数创建OH_AuxiliaryPictureNative对象。<br>使用{@link OH_PictureNative_GetAuxiliaryPicture}<br>函数从OH_PictureNative对象中按辅助图类型获取OH_AuxiliaryPictureNative对象。<br>使用{@link OH_AuxiliaryPictureNative_Release}<br>函数释放OH_AuxiliaryPictureNative对象。<br>使用约束：使用OH_AuxiliaryPictureNative对象前，需先创建或获取对象；使用完成后，应调用<br>{@link OH_AuxiliaryPictureNative_Release}释放对象。通过{@link OH_AuxiliaryPictureNative_Create}创建对象时，data、<br>size和auxiliaryPicture均不能为空指针，dataLength必须大于0，type必须为当前支持的{@link Image_AuxiliaryPictureType}。<br>资源管理：<br>释放OH_PictureNative对象不会自动释放已经获取出的OH_AuxiliaryPictureNative对象；<br>释放OH_AuxiliaryPictureNative对象也不会从OH_PictureNative对象中移除对应辅助图。通过{@link OH_AuxiliaryPictureNative_GetInfo}<br>获取到的OH_AuxiliaryPictureInfo对象由调用方管理，使用完成后应调用{@link OH_AuxiliaryPictureInfo_Release}释放。通过<br>{@link OH_AuxiliaryPictureNative_GetMetadata}获取到的OH_PictureMetadata对象由调用方管理，使用完成后应调用<br>{@link OH_PictureMetadata_Release}释放。接口返回失败时，输出参数的内容不能在后续流程中继续使用。<br>OH_AuxiliaryPictureNative结构体内容和操作方式如下：

**系统能力：** SystemCapability.Multimedia.Image.Core

**起始版本：** 13

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [picture_native.h](capi-picture-native-h.md)

