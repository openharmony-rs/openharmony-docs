# picture_native.h
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## 概述

提供获取picture数据和信息的API。

**引用文件：** <multimedia/image_framework/image/picture_native.h>

**库：** libpicture.so

**系统能力：** SystemCapability.Multimedia.Image.Core

**起始版本：** 13

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_PictureNative_AuxiliaryPictureCopyItem](capi-image-nativemodule-oh-picturenative-auxiliarypicturecopyitem.md) | OH_PictureNative_AuxiliaryPictureCopyItem | 此结构体用于在创建PictureNative对象的深拷贝时指定辅助图的拷贝规则。描述如何将辅助图从一种类型拷贝到另一种类型。 |
| [OH_PictureNative_MetadataCopyItem](capi-image-nativemodule-oh-picturenative-metadatacopyitem.md) | OH_PictureNative_MetadataCopyItem | 此结构体用于在创建PictureNative对象的深拷贝时指定元数据的拷贝规则。描述如何将元数据从一种类型拷贝到另一种类型。 |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) | - | Picture结构体类型，用于执行picture相关操作。<br> Picture为多图对象结构体，包含主图、辅助图和元数据。<br> 主图包含图像的大部分信息，主要用于显示图像内容。<br> 辅助图用于存储与主图相关但不同的数据，展示图像更丰富的信息。<br> 元数据一般用来存储关于图像文件的信息。 |
| [OH_AuxiliaryPictureNative](capi-image-nativemodule-oh-auxiliarypicturenative.md) | - | AuxiliaryPicture结构体类型，用于执行AuxiliaryPicture相关操作。 |
| [OH_AuxiliaryPictureInfo](capi-image-nativemodule-oh-auxiliarypictureinfo.md) | - | AuxiliaryPictureInfo结构体类型，用于执行AuxiliaryPictureInfo相关操作。 |
| [OH_ComposeOptions](capi-image-nativemodule-oh-composeoptions.md) | OH_ComposeOptions | OH_ComposeOptions是native层封装的合成HDR选项参数结构体，用于设置合成选项参数。用于指定合成HDR所用的参数，例如目标像素格式。 |
| <!--DelRow-->[OH_DecomposeOptions](#oh_decomposeoptions) | OH_DecomposeOptions | OH_DecomposeOptions是native层封装的HDR分解选项参数结构体，用于指定HDR分解所用的参数，包括增益图尺寸和目标像素格式。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [Image_AuxiliaryPictureType](#image_auxiliarypicturetype) | Image_AuxiliaryPictureType | 辅助图类型。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [Image_ErrorCode OH_ComposeOptions_Create(OH_ComposeOptions **options)](#oh_composeoptions_create) | 创建OH_ComposeOptions实例。 |
| [Image_ErrorCode OH_ComposeOptions_SetDesiredPixelFormat(OH_ComposeOptions *options, PIXEL_FORMAT desiredPixelFormat)](#oh_composeoptions_setdesiredpixelformat) | 设置OH_ComposeOptions中的目标像素格式。 |
| [Image_ErrorCode OH_ComposeOptions_GetDesiredPixelFormat(OH_ComposeOptions *options, PIXEL_FORMAT *desiredPixelFormat)](#oh_composeoptions_getdesiredpixelformat) | 获取OH_ComposeOptions中的像素格式。 |
| [Image_ErrorCode OH_ComposeOptions_Release(OH_ComposeOptions *options)](#oh_composeoptions_release) | 释放OH_ComposeOptions指针。 |
| [Image_ErrorCode OH_PictureNative_CreatePicture(OH_PixelmapNative *mainPixelmap, OH_PictureNative **picture)](#oh_picturenative_createpicture) | 创建OH_PictureNative指针。 |
| [Image_ErrorCode OH_PictureNative_GetMainPixelmap(OH_PictureNative *picture, OH_PixelmapNative **mainPixelmap)](#oh_picturenative_getmainpixelmap) | 获取主图的OH_PixelmapNative指针。 |
| [Image_ErrorCode OH_PictureNative_GetHdrComposedPixelmap(OH_PictureNative *picture, OH_PixelmapNative **hdrPixelmap)](#oh_picturenative_gethdrcomposedpixelmap) | 获取hdr图的OH_PixelmapNative指针。 |
| [Image_ErrorCode OH_PictureNative_GetHdrComposedPixelmapWithOptions(OH_PictureNative *picture, OH_ComposeOptions *options, OH_PixelmapNative **hdrPixelmap)](#oh_picturenative_gethdrcomposedpixelmapwithoptions) | 通过设置合成选项OH_ComposeOptions获取HDR图的OH_PixelmapNative指针。 |
| [Image_ErrorCode OH_PictureNative_GetGainmapPixelmap(OH_PictureNative *picture, OH_PixelmapNative **gainmapPixelmap)](#oh_picturenative_getgainmappixelmap) | 获取增益图的OH_PixelmapNative指针。 |
| [Image_ErrorCode OH_PictureNative_SetAuxiliaryPicture(OH_PictureNative *picture, Image_AuxiliaryPictureType type, OH_AuxiliaryPictureNative *auxiliaryPicture)](#oh_picturenative_setauxiliarypicture) | 设置辅助图。 |
| [Image_ErrorCode OH_PictureNative_GetAuxiliaryPicture(OH_PictureNative *picture, Image_AuxiliaryPictureType type, OH_AuxiliaryPictureNative **auxiliaryPicture)](#oh_picturenative_getauxiliarypicture) | 根据类型获取辅助图。 |
| [Image_ErrorCode OH_PictureNative_GetMetadata(OH_PictureNative *picture, Image_MetadataType metadataType, OH_PictureMetadata **metadata)](#oh_picturenative_getmetadata) | 获取主图的元数据。 |
| [Image_ErrorCode OH_PictureNative_SetMetadata(OH_PictureNative *picture, Image_MetadataType metadataType, OH_PictureMetadata *metadata)](#oh_picturenative_setmetadata) | 设置主图的元数据。 |
| [Image_ErrorCode OH_PictureNative_GetAuxiliaryPictureCount(OH_PictureNative *picture, uint32_t *count)](#oh_picturenative_getauxiliarypicturecount) | 获取辅助图数量。 |
| [Image_ErrorCode OH_PictureNative_GetAuxiliaryPictureTypes(OH_PictureNative *picture, Image_AuxiliaryPictureType *auxiliaryPictureTypes, uint32_t *count)](#oh_picturenative_getauxiliarypicturetypes) | 获取辅助图类型。 |
| [Image_ErrorCode OH_PictureNative_GetMetadataCount(OH_PictureNative *picture, uint32_t *count)](#oh_picturenative_getmetadatacount) | 获取Picture对象中元数据的数量。 |
| [Image_ErrorCode OH_PictureNative_GetMetadataTypes(OH_PictureNative *picture, Image_MetadataType *metadataTypes, uint32_t *count)](#oh_picturenative_getmetadatatypes) | 获取Picture对象中元数据的类型。 |
| [Image_ErrorCode OH_PictureNative_RemoveAuxiliaryPicture(OH_PictureNative *picture, Image_AuxiliaryPictureType type)](#oh_picturenative_removeauxiliarypicture) | 从Picture对象中移除辅助图。 |
| [Image_ErrorCode OH_PictureNative_RemoveMetadata(OH_PictureNative *picture, Image_MetadataType type)](#oh_picturenative_removemetadata) | 从Picture对象中移除元数据。 |
| [Image_ErrorCode OH_PictureNative_DeepCopyWithItems(OH_PictureNative *source, const OH_PictureNative_AuxiliaryPictureCopyItem *auxiliaryPictureCopyItems, uint32_t auxiliaryPictureCopyCount, const OH_PictureNative_MetadataCopyItem *metadataCopyItems, uint32_t metadataCopyCount, Image_AuxiliaryPictureType *sourceAuxPictureAsMainPixelMap, OH_PictureNative **picture)](#oh_picturenative_deepcopywithitems) | 创建PictureNative对象的深拷贝，并将指定的辅助图和元数据拷贝到指定的目标类型。 |
| [Image_ErrorCode OH_PictureNative_Release(OH_PictureNative *picture)](#oh_picturenative_release) | 释放OH_PictureNative指针。 |
| [Image_ErrorCode OH_AuxiliaryPictureNative_Create(uint8_t *data, size_t dataLength, Image_Size *size, Image_AuxiliaryPictureType type, OH_AuxiliaryPictureNative **auxiliaryPicture)](#oh_auxiliarypicturenative_create) | 创建OH_AuxiliaryPictureNative指针。该接口仅支持传入[PIXEL_FORMAT](./capi-pixelmap-native-h.md#pixel_format)为BGRA_8888的连续像素数据，会创建出RGBA_8888的辅助图。 |
| <!--DelRow--> [Image_ErrorCode OH_AuxiliaryPictureNative_CreateUsingAllocator(uint8_t *data, uint32_t dataLength, OH_AuxiliaryPictureInfo *info, IMAGE_ALLOCATOR_MODE allocator, OH_AuxiliaryPictureNative **auxiliaryPicture)](#oh_auxiliarypicturenative_createusingallocator) | 创建一个具有指定内存类型的OH_AuxiliaryPictureNative对象。<ul><li>系统默认根据图像类型、图像大小、平台能力等因素选择内存类型。</li><li>处理该接口返回的辅助图时，需要考虑stride的影响。</li><li>如果data为null或dataLength小于等于0，则不会初始化辅助图数据。</li></ul> |
| [Image_ErrorCode OH_AuxiliaryPictureNative_WritePixels(OH_AuxiliaryPictureNative *auxiliaryPicture, uint8_t *source, size_t bufferSize)](#oh_auxiliarypicturenative_writepixels) | 读取缓冲区的图像像素数据，并将结果写入辅助图中。 |
| [Image_ErrorCode OH_AuxiliaryPictureNative_ReadPixels(OH_AuxiliaryPictureNative *auxiliaryPicture, uint8_t *destination, size_t *bufferSize)](#oh_auxiliarypicturenative_readpixels) | 读取辅助图的像素数据，结果写入缓冲区。 |
| [Image_ErrorCode OH_AuxiliaryPictureNative_GetType(OH_AuxiliaryPictureNative *auxiliaryPicture, Image_AuxiliaryPictureType *type)](#oh_auxiliarypicturenative_gettype) | 获取辅助图类型。 |
| [Image_ErrorCode OH_AuxiliaryPictureNative_GetInfo(OH_AuxiliaryPictureNative *auxiliaryPicture, OH_AuxiliaryPictureInfo **info)](#oh_auxiliarypicturenative_getinfo) | 获取辅助图信息。 |
| [Image_ErrorCode OH_AuxiliaryPictureNative_SetInfo(OH_AuxiliaryPictureNative *auxiliaryPicture, OH_AuxiliaryPictureInfo *info)](#oh_auxiliarypicturenative_setinfo) | 设置辅助图信息。 |
| [Image_ErrorCode OH_AuxiliaryPictureNative_GetMetadata(OH_AuxiliaryPictureNative *auxiliaryPicture, Image_MetadataType metadataType, OH_PictureMetadata **metadata)](#oh_auxiliarypicturenative_getmetadata) | 获取辅助图的元数据。 |
| [Image_ErrorCode OH_AuxiliaryPictureNative_SetMetadata(OH_AuxiliaryPictureNative *auxiliaryPicture, Image_MetadataType metadataType, OH_PictureMetadata *metadata)](#oh_auxiliarypicturenative_setmetadata) | 设置辅助图的元数据。 |
| [Image_ErrorCode OH_AuxiliaryPictureNative_AcquirePixelmap(OH_AuxiliaryPictureNative *auxiliaryPicture, OH_PixelmapNative **pixelmap)](#oh_auxiliarypicturenative_acquirepixelmap) | 获取辅助图的OH_PixelmapNative对象。 |
| [Image_ErrorCode OH_AuxiliaryPictureNative_Release(OH_AuxiliaryPictureNative *picture)](#oh_auxiliarypicturenative_release) | 释放OH_AuxiliaryPictureNative指针。 |
| [Image_ErrorCode OH_AuxiliaryPictureInfo_Create(OH_AuxiliaryPictureInfo **info)](#oh_auxiliarypictureinfo_create) | 创建一个OH_AuxiliaryPictureInfo对象。 |
| [Image_ErrorCode OH_AuxiliaryPictureInfo_GetType(OH_AuxiliaryPictureInfo *info, Image_AuxiliaryPictureType *type)](#oh_auxiliarypictureinfo_gettype) | 获取OH_AuxiliaryPictureInfo中的辅助图类型。 |
| [Image_ErrorCode OH_AuxiliaryPictureInfo_SetType(OH_AuxiliaryPictureInfo *info, Image_AuxiliaryPictureType type)](#oh_auxiliarypictureinfo_settype) | 设置OH_AuxiliaryPictureInfo中的辅助图类型。 |
| [Image_ErrorCode OH_AuxiliaryPictureInfo_GetSize(OH_AuxiliaryPictureInfo *info, Image_Size *size)](#oh_auxiliarypictureinfo_getsize) | 获取OH_AuxiliaryPictureInfo中的图片尺寸。 |
| [Image_ErrorCode OH_AuxiliaryPictureInfo_SetSize(OH_AuxiliaryPictureInfo *info, Image_Size *size)](#oh_auxiliarypictureinfo_setsize) | 设置OH_AuxiliaryPictureInfo中的图片尺寸。 |
| [Image_ErrorCode OH_AuxiliaryPictureInfo_GetRowStride(OH_AuxiliaryPictureInfo *info, uint32_t *rowStride)](#oh_auxiliarypictureinfo_getrowstride) | 获取OH_AuxiliaryPictureInfo中的行跨距。 |
| [Image_ErrorCode OH_AuxiliaryPictureInfo_SetRowStride(OH_AuxiliaryPictureInfo *info, uint32_t rowStride)](#oh_auxiliarypictureinfo_setrowstride) | 设置OH_AuxiliaryPictureInfo中的行跨距。 |
| [Image_ErrorCode OH_AuxiliaryPictureInfo_GetPixelFormat(OH_AuxiliaryPictureInfo *info, PIXEL_FORMAT *pixelFormat)](#oh_auxiliarypictureinfo_getpixelformat) | 获取OH_AuxiliaryPictureInfo中的像素格式。 |
| [Image_ErrorCode OH_AuxiliaryPictureInfo_SetPixelFormat(OH_AuxiliaryPictureInfo *info, PIXEL_FORMAT pixelFormat)](#oh_auxiliarypictureinfo_setpixelformat) | 设置OH_AuxiliaryPictureInfo中的像素格式。 |
| [Image_ErrorCode OH_AuxiliaryPictureInfo_Release(OH_AuxiliaryPictureInfo *info)](#oh_auxiliarypictureinfo_release) | 释放OH_AuxiliaryPictureInfo指针。 |
| <!--DelRow-->[Image_ErrorCode OH_DecomposeOptions_Create(OH_DecomposeOptions **outOwnedOptions)](#oh_decomposeoptions_create) | 创建OH_DecomposeOptions实例。 |
| <!--DelRow-->[Image_ErrorCode OH_DecomposeOptions_SetIsFullSizeGainmap(OH_DecomposeOptions *options, bool isFullSizeGainmap)](#oh_decomposeoptions_setisfullsizegainmap) | 设置是否生成全尺寸增益图（指增益图和主图尺寸一致）。若不自行设置，默认值为false，即增益图的尺寸是主图的一半。 |
| <!--DelRow-->[Image_ErrorCode OH_DecomposeOptions_SetDesiredPixelFormat(OH_DecomposeOptions *options, int32_t desiredPixelFormat)](#oh_decomposeoptions_setdesiredpixelformat) | 设置HDR分解后SDR PixelMap的像素格式。 |
| <!--DelRow-->[Image_ErrorCode OH_DecomposeOptions_GetDesiredPixelFormat(OH_DecomposeOptions *options, int32_t *desiredPixelFormat)](#oh_decomposeoptions_getdesiredpixelformat) | 获取HDR分解后SDR PixelMap的像素格式。 |
| <!--DelRow-->[Image_ErrorCode OH_DecomposeOptions_Release(OH_DecomposeOptions *options)](#oh_decomposeoptions_release) | 释放OH_DecomposeOptions指针。 |
| <!--DelRow-->[Image_ErrorCode OH_PictureNative_DecomposeToPicture(OH_PixelmapNative *hdrPixelmap, OH_DecomposeOptions *options, OH_PictureNative **outOwnedPicture)](#oh_picturenative_decomposetopicture) | 将HDR PixelMap分解为包含SDR PixelMap和增益图的Picture对象。 |

## 枚举类型说明

### Image_AuxiliaryPictureType

```c
enum Image_AuxiliaryPictureType
```

**描述**

辅助图类型。

**起始版本：** 13

| 枚举项 | 描述 |
| -- | -- |
| AUXILIARY_PICTURE_TYPE_GAINMAP = 1 | 增益图，代表了一种增强SDR图像以产生具有可变显示调整能力的HDR图像的机制。它是一组描述如何应用gainmap元数据的组合。 |
| AUXILIARY_PICTURE_TYPE_DEPTH_MAP = 2 | 深度图，储存图像的深度数据，通过捕捉每个像素与摄像机之间的距离，提供场景的三维结构信息，通常用于3D重建和场景理解。 |
| AUXILIARY_PICTURE_TYPE_UNREFOCUS_MAP = 3 | 人像未对焦的原图，提供了一种在人像拍摄中突出背景模糊效果的方式，能够帮助用户在后期处理中选择焦点区域，增加创作自由度。 |
| AUXILIARY_PICTURE_TYPE_LINEAR_MAP = 4 | 线性图，用于提供额外的数据视角或补充信息，通常用于视觉效果的增强，它可以包含场景中光照、颜色或其他视觉元素的线性表示。 |
| AUXILIARY_PICTURE_TYPE_FRAGMENT_MAP = 5 | 水印裁剪图，表示在原图中被水印覆盖的区域，该图像用于修复或移除水印影响，恢复图像的完整性和可视性。 |

## 函数说明

### OH_ComposeOptions_Create()

```c
Image_ErrorCode OH_ComposeOptions_Create(OH_ComposeOptions **options)
```

**描述**

创建OH_ComposeOptions实例。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ComposeOptions](capi-image-nativemodule-oh-composeoptions.md) **options | 被操作的OH_ComposeOptions指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_BAD_PARAMETER：参数错误。 |

### OH_ComposeOptions_SetDesiredPixelFormat()

```c
Image_ErrorCode OH_ComposeOptions_SetDesiredPixelFormat(OH_ComposeOptions *options, PIXEL_FORMAT desiredPixelFormat)
```

**描述**

设置OH_ComposeOptions中的目标像素格式。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ComposeOptions](capi-image-nativemodule-oh-composeoptions.md) *options | 被操作的OH_ComposeOptions指针。 |
| [PIXEL_FORMAT](capi-pixelmap-native-h.md#pixel_format) desiredPixelFormat | 被设置的像素格式，支持RGBA_1010102、YCBCR_P010和YCRCB_P010格式。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_BAD_PARAMETER：参数错误，例如options为nullptr或传入了不支持的desiredPixelFormat。 |

### OH_ComposeOptions_GetDesiredPixelFormat()

```c
Image_ErrorCode OH_ComposeOptions_GetDesiredPixelFormat(OH_ComposeOptions *options, PIXEL_FORMAT *desiredPixelFormat)
```

**描述**

获取OH_ComposeOptions中的像素格式。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ComposeOptions](capi-image-nativemodule-oh-composeoptions.md) *options | 被操作的OH_ComposeOptions指针。 |
| [PIXEL_FORMAT](capi-pixelmap-native-h.md#pixel_format) *desiredPixelFormat | 合成选项中的像素格式。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_BAD_PARAMETER：参数错误。 |

### OH_ComposeOptions_Release()

```c
Image_ErrorCode OH_ComposeOptions_Release(OH_ComposeOptions *options)
```

**描述**

释放OH_ComposeOptions指针。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ComposeOptions](capi-image-nativemodule-oh-composeoptions.md) *options | 被操作的OH_ComposeOptions指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_BAD_PARAMETER：参数错误。 |

### OH_PictureNative_CreatePicture()

```c
Image_ErrorCode OH_PictureNative_CreatePicture(OH_PixelmapNative *mainPixelmap, OH_PictureNative **picture)
```

**描述**

创建OH_PictureNative指针。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *mainPixelmap | 主图的OH_PixelmapNative指针。 |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) **picture | 被创建的OH_PictureNative指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。<br>         IMAGE_BAD_PARAMETER：参数错误。 |

### OH_PictureNative_GetMainPixelmap()

```c
Image_ErrorCode OH_PictureNative_GetMainPixelmap(OH_PictureNative *picture, OH_PixelmapNative **mainPixelmap)
```

**描述**

获取主图的OH_PixelmapNative指针。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *picture | 被操作的OH_PictureNative指针。 |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) **mainPixelmap | 获取的OH_PixelmapNative指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_BAD_PARAMETER：参数错误。 |

### OH_PictureNative_GetHdrComposedPixelmap()

```c
Image_ErrorCode OH_PictureNative_GetHdrComposedPixelmap(OH_PictureNative *picture, OH_PixelmapNative **hdrPixelmap)
```

**描述**

获取hdr图的OH_PixelmapNative指针。

使用约束：picture和hdrPixelmap均不能为空指针。Picture不支持HDR合成时，接口会返回IMAGE_UNSUPPORTED_OPERATION。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *picture | 被操作的OH_PictureNative指针。 |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) **hdrPixelmap | 获取的hdr图OH_PixelmapNative指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_BAD_PARAMETER：参数错误。<br>         IMAGE_UNSUPPORTED_OPERATION：操作不支持，例如picture对象中不包含增益图。 |

### OH_PictureNative_GetHdrComposedPixelmapWithOptions()

```c
Image_ErrorCode OH_PictureNative_GetHdrComposedPixelmapWithOptions(OH_PictureNative *picture, OH_ComposeOptions *options, OH_PixelmapNative **hdrPixelmap)
```

**描述**

通过设置合成选项OH_ComposeOptions获取HDR图的OH_PixelmapNative指针。

使用约束：picture、options和hdrPixelmap均不能为空指针。Picture不支持HDR合成时，接口会返回IMAGE_UNSUPPORTED_OPERATION。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *picture | 被操作的OH_PictureNative指针。 |
| [OH_ComposeOptions](capi-image-nativemodule-oh-composeoptions.md) *options | 合成选项OH_ComposeOptions指针。 |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) **hdrPixelmap | 获取的HDR图OH_PixelmapNative指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_BAD_PARAMETER：参数错误。<br>         IMAGE_UNSUPPORTED_OPERATION：操作不支持，例如picture对象中不包含增益图。 |

### OH_PictureNative_GetGainmapPixelmap()

```c
Image_ErrorCode OH_PictureNative_GetGainmapPixelmap(OH_PictureNative *picture, OH_PixelmapNative **gainmapPixelmap)
```

**描述**

获取增益图的OH_PixelmapNative指针。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *picture | 被操作的OH_PictureNative指针。 |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) **gainmapPixelmap | 获取的增益图OH_PixelmapNative指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_BAD_PARAMETER：参数错误。 |

### OH_PictureNative_SetAuxiliaryPicture()

```c
Image_ErrorCode OH_PictureNative_SetAuxiliaryPicture(OH_PictureNative *picture, Image_AuxiliaryPictureType type, OH_AuxiliaryPictureNative *auxiliaryPicture)
```

**描述**

设置辅助图。

使用约束：picture和auxiliaryPicture均不能为空指针，type必须为当前支持的辅助图类型，且必须与auxiliaryPicture对象自身的辅助图类型一致。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *picture | 被操作的OH_PictureNative指针。 |
| [Image_AuxiliaryPictureType](capi-picture-native-h.md#image_auxiliarypicturetype) type | 辅助图的类型。 |
| [OH_AuxiliaryPictureNative](capi-image-nativemodule-oh-auxiliarypicturenative.md) *auxiliaryPicture | 设置的OH_AuxiliaryPictureNative指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_BAD_PARAMETER：参数错误。 |

### OH_PictureNative_GetAuxiliaryPicture()

```c
Image_ErrorCode OH_PictureNative_GetAuxiliaryPicture(OH_PictureNative *picture, Image_AuxiliaryPictureType type, OH_AuxiliaryPictureNative **auxiliaryPicture)
```

**描述**

根据类型获取辅助图。

使用约束：picture和auxiliaryPicture均不能为空指针，type必须为当前支持的辅助图类型。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *picture | 被操作的OH_PictureNative指针。 |
| [Image_AuxiliaryPictureType](capi-picture-native-h.md#image_auxiliarypicturetype) type | 辅助图类型。 |
| [OH_AuxiliaryPictureNative](capi-image-nativemodule-oh-auxiliarypicturenative.md) **auxiliaryPicture | 获取的OH_AuxiliaryPictureNative指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_BAD_PARAMETER：参数错误。 |

### OH_PictureNative_GetMetadata()

```c
Image_ErrorCode OH_PictureNative_GetMetadata(OH_PictureNative *picture, Image_MetadataType metadataType, OH_PictureMetadata **metadata)
```

**描述**

获取主图的元数据。

使用约束：picture和metadata均不能为空指针，metadataType必须为Picture允许的元数据类型；不支持的元数据类型会返回IMAGE_UNSUPPORTED_METADATA。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *picture | 被操作的OH_PictureNative指针。 |
| [Image_MetadataType](capi-image-common-h.md#image_metadatatype) metadataType | 元数据类型。 |
| [OH_PictureMetadata](capi-image-nativemodule-oh-picturemetadata.md) **metadata | 主图的元数据。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_BAD_PARAMETER：参数错误。<br>         IMAGE_UNSUPPORTED_METADATA：不支持的元数据类型。 |

### OH_PictureNative_SetMetadata()

```c
Image_ErrorCode OH_PictureNative_SetMetadata(OH_PictureNative *picture, Image_MetadataType metadataType, OH_PictureMetadata *metadata)
```

**描述**

设置主图的元数据。

使用约束：picture和metadata均不能为空指针，metadataType必须为Picture允许的元数据类型。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *picture | 被操作的OH_PictureNative指针。 |
| [Image_MetadataType](capi-image-common-h.md#image_metadatatype) metadataType | 元数据类型。 |
| [OH_PictureMetadata](capi-image-nativemodule-oh-picturemetadata.md) *metadata | 将设置的元数据。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_BAD_PARAMETER：参数错误。<br>         IMAGE_UNSUPPORTED_METADATA：不支持的元数据类型。 |

### OH_PictureNative_GetAuxiliaryPictureCount()

```c
Image_ErrorCode OH_PictureNative_GetAuxiliaryPictureCount(OH_PictureNative *picture, uint32_t *count)
```

**描述**

获取辅助图数量。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *picture | 指向OH_PictureNative对象的指针。 |
| uint32_t *count | 辅助图数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | <ul><br>         <li>IMAGE_SUCCESS：执行成功。</li><br>         <li>IMAGE_INVALID_PARAMETER：picture或count为空指针、获取picture失败。</li><br>         </ul> |

### OH_PictureNative_GetAuxiliaryPictureTypes()

```c
Image_ErrorCode OH_PictureNative_GetAuxiliaryPictureTypes(OH_PictureNative *picture, Image_AuxiliaryPictureType *auxiliaryPictureTypes, uint32_t *count)
```

**描述**

获取辅助图类型。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *picture | 指向OH_PictureNative对象的指针。 |
| [Image_AuxiliaryPictureType](capi-picture-native-h.md#image_auxiliarypicturetype) *auxiliaryPictureTypes | 指向接收辅助图类型的数组的指针。 |
| uint32_t *count | 输入时，为辅助图类型数组的大小。输出时，为辅助图的实际数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | <ul><br>         <li>IMAGE_SUCCESS：执行成功。</li><br>         <li>IMAGE_INVALID_PARAMETER：picture、auxiliaryPictureTypes或count为空指针、无法获取图片、count小于要求。</li><br>         </ul> |

### OH_PictureNative_GetMetadataCount()

```c
Image_ErrorCode OH_PictureNative_GetMetadataCount(OH_PictureNative *picture, uint32_t *count)
```

**描述**

获取Picture对象中元数据的数量。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *picture | 指向OH_PictureNative对象的指针。 |
| uint32_t *count | 元数据数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | <ul><br>         <li>IMAGE_SUCCESS：执行成功。</li><br>         <li>IMAGE_INVALID_PARAMETER：picture或count为空指针、获取picture失败。</li><br>         </ul> |

### OH_PictureNative_GetMetadataTypes()

```c
Image_ErrorCode OH_PictureNative_GetMetadataTypes(OH_PictureNative *picture, Image_MetadataType *metadataTypes, uint32_t *count)
```

**描述**

获取Picture对象中元数据的类型。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *picture | 指向OH_PictureNative对象的指针。 |
| [Image_MetadataType](capi-image-common-h.md#image_metadatatype) *metadataTypes | 接收元数据类型的数组指针。 |
| uint32_t *count | 输入时，metadataTypes数组的大小。输出时，元数据的实际数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | <ul><br>         <li>IMAGE_SUCCESS：执行成功。</li><br>         <li>IMAGE_INVALID_PARAMETER：picture、metadataTypes或count为空指针、获取picture失败、count小于所需大小。</li><br>         </ul> |

### OH_PictureNative_RemoveAuxiliaryPicture()

```c
Image_ErrorCode OH_PictureNative_RemoveAuxiliaryPicture(OH_PictureNative *picture, Image_AuxiliaryPictureType type)
```

**描述**

从Picture对象中移除辅助图。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *picture | 指向OH_PictureNative对象的指针。 |
| [Image_AuxiliaryPictureType](capi-picture-native-h.md#image_auxiliarypicturetype) type | 移除的辅助图类型。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | <ul><br>         <li>IMAGE_SUCCESS：辅助图被成功移除或不存在。</li><br>         <li>IMAGE_INVALID_PARAMETER：picture为空指针、获取picture失败、辅助图类型不支持。</li><br>         </ul> |

### OH_PictureNative_RemoveMetadata()

```c
Image_ErrorCode OH_PictureNative_RemoveMetadata(OH_PictureNative *picture, Image_MetadataType type)
```

**描述**

从Picture对象中移除元数据。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *picture | 指向OH_PictureNative对象的指针。 |
| [Image_MetadataType](capi-image-common-h.md#image_metadatatype) type | 移除的元数据类型。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | <ul><br>         <li>IMAGE_SUCCESS：元数据被成功移除或不存在。</li><br>         <li>IMAGE_INVALID_PARAMETER：picture为空指针、获取picture失败。</li><br>         <li>IMAGE_UNSUPPORTED_METADATA：不支持的元数据类型。</li><br>         </ul> |

### OH_PictureNative_DeepCopyWithItems()

```c
Image_ErrorCode OH_PictureNative_DeepCopyWithItems(OH_PictureNative *source, const OH_PictureNative_AuxiliaryPictureCopyItem *auxiliaryPictureCopyItems, uint32_t auxiliaryPictureCopyCount, const OH_PictureNative_MetadataCopyItem *metadataCopyItems, uint32_t metadataCopyCount, Image_AuxiliaryPictureType *sourceAuxPictureAsMainPixelMap, OH_PictureNative **picture)
```

**描述**

创建PictureNative对象的深拷贝，并将指定的辅助图和元数据拷贝到指定的目标类型。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *source | 源PictureNative对象，不能为NULL。 |
| [const OH_PictureNative_AuxiliaryPictureCopyItem](capi-image-nativemodule-oh-picturenative-auxiliarypicturecopyitem.md) *auxiliaryPictureCopyItems | 描述需要拷贝的辅助图的结构体。包括源辅助图和目标辅助图类型。如果auxiliaryPictureCopyCount为0，可以为NULL。 |
| uint32_t auxiliaryPictureCopyCount | 需要拷贝的辅助图数量。 |
| [const OH_PictureNative_MetadataCopyItem](capi-image-nativemodule-oh-picturenative-metadatacopyitem.md) *metadataCopyItems | 描述需要拷贝的元数据的结构体。包括源元数据类型和目标元数据类型。如果metadataCopyCount为0，可以为NULL。 |
| uint32_t metadataCopyCount | 需要拷贝的元数据数量。 |
| [Image_AuxiliaryPictureType](capi-picture-native-h.md#image_auxiliarypicturetype) *sourceAuxPictureAsMainPixelMap | 指定源图片中作为拷贝图片主图的辅助图类型。如果应使用原始主图，可以为NULL。 |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) **picture | 输出参数，用于接收新创建的PictureNative对象。当调用者不再需要时释放该对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | <ul><br>         <li>IMAGE_SUCCESS：执行成功。</li><br>         <li>IMAGE_INVALID_PARAMETER：source或picture为空指针、获取picture失败或数量不匹配、数量不为零但对应数组为空指针。</li><br>         <li>IMAGE_ALLOC_FAILED：内存分配失败。</li><br>         </ul> |

### OH_PictureNative_Release()

```c
Image_ErrorCode OH_PictureNative_Release(OH_PictureNative *picture)
```

**描述**

释放OH_PictureNative指针。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *picture | 被操作的OH_PictureNative指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_BAD_PARAMETER：参数错误。 |

### OH_AuxiliaryPictureNative_Create()

```c
Image_ErrorCode OH_AuxiliaryPictureNative_Create(uint8_t *data, size_t dataLength, Image_Size *size, Image_AuxiliaryPictureType type, OH_AuxiliaryPictureNative **auxiliaryPicture)
```

**描述**

创建OH_AuxiliaryPictureNative指针。该接口仅支持传入[PIXEL_FORMAT](capi-pixelmap-native-h.md#pixel_format)为BGRA_8888的连续像素数据，会创建出RGBA_8888的辅助图。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint8_t *data | 图像数据。 |
| size_t dataLength | 图像数据长度。 |
| [Image_Size](capi-image-nativemodule-image-size.md) *size | 辅助图尺寸。 |
| [Image_AuxiliaryPictureType](capi-picture-native-h.md#image_auxiliarypicturetype) type | 辅助图类型。 |
| [OH_AuxiliaryPictureNative](capi-image-nativemodule-oh-auxiliarypicturenative.md) **auxiliaryPicture | 被创建的OH_AuxiliaryPictureNative指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_BAD_PARAMETER：参数错误。 |
<!--Del-->
### OH_AuxiliaryPictureNative_CreateUsingAllocator()

```c
Image_ErrorCode OH_AuxiliaryPictureNative_CreateUsingAllocator(uint8_t *data, uint32_t dataLength, OH_AuxiliaryPictureInfo *info, IMAGE_ALLOCATOR_MODE allocator, OH_AuxiliaryPictureNative **auxiliaryPicture)
```

**描述**

创建一个具有指定内存类型的OH_AuxiliaryPictureNative对象。<ul><li>系统默认根据图像类型、图像大小、平台能力等因素选择内存类型。</li><li>处理该接口返回的辅助图时，需要考虑stride的影响。</li><li>如果data为null或dataLength小于等于0，则不会初始化辅助图数据。</li></ul>

**起始版本：** 26.0.0

**系统接口：** 该接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint8_t *data | 指向图像数据的指针。 |
| uint32_t dataLength | 图像数据的长度。 |
| [OH_AuxiliaryPictureInfo](capi-image-nativemodule-oh-auxiliarypictureinfo.md) *info | 指向辅助图基本信息的指针。 |
| [IMAGE_ALLOCATOR_MODE](capi-image-common-h.md#image_allocator_mode) allocator | 辅助图使用的内存类型。有关可用选项的详细信息，请参阅[IMAGE_ALLOCATOR_MODE](capi-image-common-h.md#image_allocator_mode)。 |
| [OH_AuxiliaryPictureNative](capi-image-nativemodule-oh-auxiliarypicturenative.md) **auxiliaryPicture | 输出参数，用于接收新创建的OH_AuxiliaryPictureNative对象地址。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | <ul><br>         <li>IMAGE_SUCCESS：执行成功。</li><br>         <li>202：非系统应用程序调用该接口则返回此错误码。</li><br>         <li>IMAGE_INVALID_PARAMETER：info或auxiliaryPicture为空指针、allocator无效、辅助图大小无效或类型不支持、dataLength小于所需大小。</li><br>         <li>IMAGE_SOURCE_UNSUPPORTED_ALLOCATOR_TYPE：不支持的内存类型。<br>         例如使用共享内存创建增益图，仅DMA支持HDR元数据。</li><br>         <li>IMAGE_ALLOC_FAILED：内存分配失败。</li><br>         </ul> |
<!--DelEnd-->
### OH_AuxiliaryPictureNative_WritePixels()

```c
Image_ErrorCode OH_AuxiliaryPictureNative_WritePixels(OH_AuxiliaryPictureNative *auxiliaryPicture, uint8_t *source, size_t bufferSize)
```

**描述**

读取缓冲区的图像像素数据，并将结果写入辅助图中。

使用约束：auxiliaryPicture和source均不能为空指针，bufferSize需与待写入像素数据大小匹配。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AuxiliaryPictureNative](capi-image-nativemodule-oh-auxiliarypicturenative.md) *auxiliaryPicture | 被操作的OH_AuxiliaryPictureNative指针。 |
| uint8_t *source | 将被写入的图像像素数据。 |
| size_t bufferSize | 图像像素数据长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_BAD_PARAMETER：参数错误。<br>         IMAGE_ALLOC_FAILED：内存分配失败。<br>         IMAGE_COPY_FAILED：内存拷贝失败。 |

### OH_AuxiliaryPictureNative_ReadPixels()

```c
Image_ErrorCode OH_AuxiliaryPictureNative_ReadPixels(OH_AuxiliaryPictureNative *auxiliaryPicture, uint8_t *destination, size_t *bufferSize)
```

**描述**

读取辅助图的像素数据，结果写入缓冲区。

使用约束：auxiliaryPicture、destination和bufferSize均不能为空指针，bufferSize需表示destination可写入的缓冲区大小；接口执行成功后，bufferSize会更新为实际读取的数据大小。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AuxiliaryPictureNative](capi-image-nativemodule-oh-auxiliarypicturenative.md) *auxiliaryPicture | 被操作的OH_AuxiliaryPictureNative指针。 |
| uint8_t *destination | 缓冲区，获取的辅助图像素数据写入到该内存区域内。 |
| size_t *bufferSize | 缓冲区大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_BAD_PARAMETER：参数错误。<br>         IMAGE_ALLOC_FAILED：内存分配失败。<br>         IMAGE_COPY_FAILED：内存拷贝失败。 |

### OH_AuxiliaryPictureNative_GetType()

```c
Image_ErrorCode OH_AuxiliaryPictureNative_GetType(OH_AuxiliaryPictureNative *auxiliaryPicture, Image_AuxiliaryPictureType *type)
```

**描述**

获取辅助图类型。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AuxiliaryPictureNative](capi-image-nativemodule-oh-auxiliarypicturenative.md) *auxiliaryPicture | 被操作的OH_AuxiliaryPictureNative指针。 |
| [Image_AuxiliaryPictureType](capi-picture-native-h.md#image_auxiliarypicturetype) *type | 辅助图类型。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_BAD_PARAMETER：参数错误。 |

### OH_AuxiliaryPictureNative_GetInfo()

```c
Image_ErrorCode OH_AuxiliaryPictureNative_GetInfo(OH_AuxiliaryPictureNative *auxiliaryPicture, OH_AuxiliaryPictureInfo **info)
```

**描述**

获取辅助图信息。

资源管理：接口成功返回的OH_AuxiliaryPictureInfo对象由调用方管理，使用完成后应调用OH_AuxiliaryPictureInfo_Release()释放。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AuxiliaryPictureNative](capi-image-nativemodule-oh-auxiliarypicturenative.md) *auxiliaryPicture | 被操作的OH_AuxiliaryPictureNative指针。 |
| [OH_AuxiliaryPictureInfo](capi-image-nativemodule-oh-auxiliarypictureinfo.md) **info | 辅助图信息。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_BAD_PARAMETER：参数错误。 |

### OH_AuxiliaryPictureNative_SetInfo()

```c
Image_ErrorCode OH_AuxiliaryPictureNative_SetInfo(OH_AuxiliaryPictureNative *auxiliaryPicture, OH_AuxiliaryPictureInfo *info)
```

**描述**

设置辅助图信息。

资源管理：接口会读取并保存OH_AuxiliaryPictureInfo中的信息值，接口返回后调用方仍需自行管理该OH_AuxiliaryPictureInfo对象的生命周期。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AuxiliaryPictureNative](capi-image-nativemodule-oh-auxiliarypicturenative.md) *auxiliaryPicture | 将操作的OH_AuxiliaryPictureNative指针。 |
| [OH_AuxiliaryPictureInfo](capi-image-nativemodule-oh-auxiliarypictureinfo.md) *info | 将要设置的辅助图信息。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_BAD_PARAMETER：参数错误。 |

### OH_AuxiliaryPictureNative_GetMetadata()

```c
Image_ErrorCode OH_AuxiliaryPictureNative_GetMetadata(OH_AuxiliaryPictureNative *auxiliaryPicture, Image_MetadataType metadataType, OH_PictureMetadata **metadata)
```

**描述**

获取辅助图的元数据。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AuxiliaryPictureNative](capi-image-nativemodule-oh-auxiliarypicturenative.md) *auxiliaryPicture | 将操作的OH_AuxiliaryPictureNative指针。 |
| [Image_MetadataType](capi-image-common-h.md#image_metadatatype) metadataType | 元数据类型。 |
| [OH_PictureMetadata](capi-image-nativemodule-oh-picturemetadata.md) **metadata | 获取的元数据。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_BAD_PARAMETER：参数错误。<br>         IMAGE_UNSUPPORTED_METADATA：不支持的元数据类型，或者元数据类型与辅助图片类型不匹配。 |

### OH_AuxiliaryPictureNative_SetMetadata()

```c
Image_ErrorCode OH_AuxiliaryPictureNative_SetMetadata(OH_AuxiliaryPictureNative *auxiliaryPicture, Image_MetadataType metadataType, OH_PictureMetadata *metadata)
```

**描述**

设置辅助图的元数据。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AuxiliaryPictureNative](capi-image-nativemodule-oh-auxiliarypicturenative.md) *auxiliaryPicture | 将操作的OH_AuxiliaryPictureNative指针。 |
| [Image_MetadataType](capi-image-common-h.md#image_metadatatype) metadataType | 元数据类型。 |
| [OH_PictureMetadata](capi-image-nativemodule-oh-picturemetadata.md) *metadata | 将要设置的元数据。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_BAD_PARAMETER：参数错误。<br>         IMAGE_UNSUPPORTED_METADATA：不支持的元数据类型，或者元数据类型与辅助图片类型不匹配。 |

### OH_AuxiliaryPictureNative_AcquirePixelmap()

```c
Image_ErrorCode OH_AuxiliaryPictureNative_AcquirePixelmap(OH_AuxiliaryPictureNative *auxiliaryPicture, OH_PixelmapNative **pixelmap)
```

**描述**

获取辅助图的OH_PixelmapNative对象。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AuxiliaryPictureNative](capi-image-nativemodule-oh-auxiliarypicturenative.md) *auxiliaryPicture | 指向OH_AuxiliaryPictureNative对象的指针。 |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) **pixelmap | 输出参数，用于接收获取到的OH_PixelmapNative对象地址。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | <ul><br>         <li>IMAGE_SUCCESS：执行成功。</li><br>         <li>IMAGE_INVALID_PARAMETER：auxiliaryPicture或pixelmap为空指针。</li><br>         <li>IMAGE_GET_IMAGE_DATA_FAILED：无法获取辅助图或像素数据。</li><br>         <li>IMAGE_ALLOC_FAILED：内存分配失败。</li><br>         </ul> |

### OH_AuxiliaryPictureNative_Release()

```c
Image_ErrorCode OH_AuxiliaryPictureNative_Release(OH_AuxiliaryPictureNative *picture)
```

**描述**

释放OH_AuxiliaryPictureNative指针。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AuxiliaryPictureNative](capi-image-nativemodule-oh-auxiliarypicturenative.md) *picture | 将操作的OH_AuxiliaryPictureNative指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_BAD_PARAMETER：参数错误。 |

### OH_AuxiliaryPictureInfo_Create()

```c
Image_ErrorCode OH_AuxiliaryPictureInfo_Create(OH_AuxiliaryPictureInfo **info)
```

**描述**

创建一个OH_AuxiliaryPictureInfo对象。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AuxiliaryPictureInfo](capi-image-nativemodule-oh-auxiliarypictureinfo.md) **info | 将操作的OH_AuxiliaryPictureInfo指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_BAD_PARAMETER：参数错误。 |

### OH_AuxiliaryPictureInfo_GetType()

```c
Image_ErrorCode OH_AuxiliaryPictureInfo_GetType(OH_AuxiliaryPictureInfo *info, Image_AuxiliaryPictureType *type)
```

**描述**

获取OH_AuxiliaryPictureInfo中的辅助图类型。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AuxiliaryPictureInfo](capi-image-nativemodule-oh-auxiliarypictureinfo.md) *info | 将操作的OH_AuxiliaryPictureInfo指针。 |
| [Image_AuxiliaryPictureType](capi-picture-native-h.md#image_auxiliarypicturetype) *type | 获取的辅助图类型。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_BAD_PARAMETER：参数错误。 |

### OH_AuxiliaryPictureInfo_SetType()

```c
Image_ErrorCode OH_AuxiliaryPictureInfo_SetType(OH_AuxiliaryPictureInfo *info, Image_AuxiliaryPictureType type)
```

**描述**

设置OH_AuxiliaryPictureInfo中的辅助图类型。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AuxiliaryPictureInfo](capi-image-nativemodule-oh-auxiliarypictureinfo.md) *info | 将操作的OH_AuxiliaryPictureInfo指针。 |
| [Image_AuxiliaryPictureType](capi-picture-native-h.md#image_auxiliarypicturetype) type | 将要设置的辅助图类型。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_BAD_PARAMETER：参数错误。 |

### OH_AuxiliaryPictureInfo_GetSize()

```c
Image_ErrorCode OH_AuxiliaryPictureInfo_GetSize(OH_AuxiliaryPictureInfo *info, Image_Size *size)
```

**描述**

获取OH_AuxiliaryPictureInfo中的图片尺寸。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AuxiliaryPictureInfo](capi-image-nativemodule-oh-auxiliarypictureinfo.md) *info | 将操作的OH_AuxiliaryPictureInfo指针。 |
| [Image_Size](capi-image-nativemodule-image-size.md) *size | 获取的图片尺寸。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_BAD_PARAMETER：参数错误。 |

### OH_AuxiliaryPictureInfo_SetSize()

```c
Image_ErrorCode OH_AuxiliaryPictureInfo_SetSize(OH_AuxiliaryPictureInfo *info, Image_Size *size)
```

**描述**

设置OH_AuxiliaryPictureInfo中的图片尺寸。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AuxiliaryPictureInfo](capi-image-nativemodule-oh-auxiliarypictureinfo.md) *info | 将操作的OH_AuxiliaryPictureInfo指针。 |
| [Image_Size](capi-image-nativemodule-image-size.md) *size | 将要设置的图片尺寸。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_BAD_PARAMETER：参数错误。 |

### OH_AuxiliaryPictureInfo_GetRowStride()

```c
Image_ErrorCode OH_AuxiliaryPictureInfo_GetRowStride(OH_AuxiliaryPictureInfo *info, uint32_t *rowStride)
```

**描述**

获取OH_AuxiliaryPictureInfo中的行跨距。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AuxiliaryPictureInfo](capi-image-nativemodule-oh-auxiliarypictureinfo.md) *info | 将操作的OH_AuxiliaryPictureInfo指针。 |
| uint32_t *rowStride | 跨距，内存中每行像素所占的空间。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_BAD_PARAMETER：参数错误。 |

### OH_AuxiliaryPictureInfo_SetRowStride()

```c
Image_ErrorCode OH_AuxiliaryPictureInfo_SetRowStride(OH_AuxiliaryPictureInfo *info, uint32_t rowStride)
```

**描述**

设置OH_AuxiliaryPictureInfo中的行跨距。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AuxiliaryPictureInfo](capi-image-nativemodule-oh-auxiliarypictureinfo.md) *info | 将操作的OH_AuxiliaryPictureInfo指针。 |
| uint32_t rowStride | 跨距，内存中每行像素所占的空间。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_BAD_PARAMETER：参数错误。 |

### OH_AuxiliaryPictureInfo_GetPixelFormat()

```c
Image_ErrorCode OH_AuxiliaryPictureInfo_GetPixelFormat(OH_AuxiliaryPictureInfo *info, PIXEL_FORMAT *pixelFormat)
```

**描述**

获取OH_AuxiliaryPictureInfo中的像素格式。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AuxiliaryPictureInfo](capi-image-nativemodule-oh-auxiliarypictureinfo.md) *info | 将操作的OH_AuxiliaryPictureInfo指针。 |
| [PIXEL_FORMAT](capi-pixelmap-native-h.md#pixel_format) *pixelFormat | 获取的像素格式。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_BAD_PARAMETER：参数错误。 |

### OH_AuxiliaryPictureInfo_SetPixelFormat()

```c
Image_ErrorCode OH_AuxiliaryPictureInfo_SetPixelFormat(OH_AuxiliaryPictureInfo *info, PIXEL_FORMAT pixelFormat)
```

**描述**

设置OH_AuxiliaryPictureInfo中的像素格式。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AuxiliaryPictureInfo](capi-image-nativemodule-oh-auxiliarypictureinfo.md) *info | 将操作的OH_AuxiliaryPictureInfo指针。 |
| [PIXEL_FORMAT](capi-pixelmap-native-h.md#pixel_format) pixelFormat | 将要设置的像素格式。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_BAD_PARAMETER：参数错误。 |

### OH_AuxiliaryPictureInfo_Release()

```c
Image_ErrorCode OH_AuxiliaryPictureInfo_Release(OH_AuxiliaryPictureInfo *info)
```

**描述**

释放OH_AuxiliaryPictureInfo指针。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AuxiliaryPictureInfo](capi-image-nativemodule-oh-auxiliarypictureinfo.md) *info | 将操作的OH_AuxiliaryPictureInfo指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_BAD_PARAMETER：参数错误。 |

<!--Del-->
### OH_DecomposeOptions

```c
typedef struct OH_DecomposeOptions OH_DecomposeOptions
```

**描述**

OH_DecomposeOptions是native层封装的HDR分解选项参数结构体，用于指定HDR分解所用的参数，包括增益图（GainMap）尺寸（全尺寸或1/2缩小）以及分解后SDR PixelMap和增益图的像素格式。

**起始版本：** 26.0.0

### OH_DecomposeOptions_Create()

```c
Image_ErrorCode OH_DecomposeOptions_Create(OH_DecomposeOptions **outOwnedOptions)
```

**描述**

创建OH_DecomposeOptions实例。创建的实例需通过[OH_DecomposeOptions_Release](#oh_decomposeoptions_release)释放。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_DecomposeOptions](#oh_decomposeoptions) **outOwnedOptions | 指向被创建的OH_DecomposeOptions指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_INVALID_PARAMETER：参数错误，例如outOwnedOptions为nullptr。<br>         IMAGE_ALLOC_FAILED：内存分配失败。<br>         202：非系统应用程序调用该接口则返回此错误码。 |

### OH_DecomposeOptions_SetIsFullSizeGainmap()

```c
Image_ErrorCode OH_DecomposeOptions_SetIsFullSizeGainmap(OH_DecomposeOptions *options, bool isFullSizeGainmap)
```

**描述**

设置是否生成全尺寸增益图（指增益图和主图尺寸一致）。若不自行设置，默认值为false，即增益图的尺寸是主图的一半。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_DecomposeOptions](#oh_decomposeoptions) *options | 指向OH_DecomposeOptions对象的指针。 |
| bool isFullSizeGainmap | 是否生成全尺寸增益图。设置为true时生成全尺寸增益图，设置为false时生成1/2缩小的增益图。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_INVALID_PARAMETER：参数错误，例如options为nullptr。<br>         202：非系统应用程序调用该接口则返回此错误码。 |

### OH_DecomposeOptions_GetIsFullSizeGainmap()

```c
Image_ErrorCode OH_DecomposeOptions_GetIsFullSizeGainmap(OH_DecomposeOptions *options, bool *isFullSizeGainmap)
```

**描述**

获取是否生成全尺寸增益图（指增益图和主图尺寸一致）。如果isFullSizeGainmap为true，则增益图和主图尺寸一致；否则，增益图为主图尺寸的一半。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_DecomposeOptions](#oh_decomposeoptions) *options | 指向OH_DecomposeOptions对象的指针。 |
| bool *isFullSizeGainmap | 指向bool值的指针，用于接收是否生成全尺寸增益图的设置。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_INVALID_PARAMETER：参数错误，例如options或isFullSizeGainmap为nullptr。<br>         202：非系统应用程序调用该接口则返回此错误码。 |

### OH_DecomposeOptions_SetDesiredPixelFormat()

```c
Image_ErrorCode OH_DecomposeOptions_SetDesiredPixelFormat(OH_DecomposeOptions *options, int32_t desiredPixelFormat)
```

**描述**

设置HDR分解后的SDR PixelMap和增益图的像素格式。若不设置，默认值为RGBA_8888。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_DecomposeOptions](#oh_decomposeoptions) *options | 指向OH_DecomposeOptions对象的指针。 |
| int32_t desiredPixelFormat | 分解后SDR PixelMap和增益图的像素格式，支持RGBA_8888、NV12和NV21格式。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_INVALID_PARAMETER：参数错误，例如options为nullptr。<br>         IMAGE_UNSUPPORTED_OPERATION：不支持的像素格式。<br>         202：非系统应用程序调用该接口则返回此错误码。 |

### OH_DecomposeOptions_GetDesiredPixelFormat()

```c
Image_ErrorCode OH_DecomposeOptions_GetDesiredPixelFormat(OH_DecomposeOptions *options, int32_t *desiredPixelFormat)
```

**描述**

获取HDR分解后的SDR PixelMap和增益图的像素格式。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_DecomposeOptions](#oh_decomposeoptions) *options | 指向OH_DecomposeOptions对象的指针。 |
| int32_t *desiredPixelFormat | 指向int32_t的指针，用于接收像素格式设置。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_INVALID_PARAMETER：参数错误，例如options或desiredPixelFormat为nullptr。<br>         202：非系统应用程序调用该接口则返回此错误码。 |

### OH_DecomposeOptions_Release()

```c
Image_ErrorCode OH_DecomposeOptions_Release(OH_DecomposeOptions *options)
```

**描述**

释放OH_DecomposeOptions指针。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_DecomposeOptions](#oh_decomposeoptions) *options | 指向OH_DecomposeOptions对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_INVALID_PARAMETER：参数错误，例如options为nullptr。<br>         202：非系统应用程序调用该接口则返回此错误码。 |

### OH_PictureNative_DecomposeToPicture()

```c
Image_ErrorCode OH_PictureNative_DecomposeToPicture(OH_PixelmapNative *hdrPixelmap, OH_DecomposeOptions *options, OH_PictureNative **outOwnedPicture)
```

**描述**

将HDR PixelMap分解为包含SDR PixelMap和增益图（gainmap）的Picture对象。创建的Picture实例需通过[OH_PictureNative_Release](#oh_picturenative_release)释放。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *hdrPixelmap | 被分解的HDR PixelMap指针，像素格式需为RGBA_F16、RGBA_1010102、YCBCR_P010或YCRCB_P010。 |
| [OH_DecomposeOptions](#oh_decomposeoptions) *options | HDR分解配置选项，此参数为必填。 |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) **outOwnedPicture | 指向被创建的Picture对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。 <br>         IMAGE_INVALID_PARAMETER：参数错误，例如hdrPixelmap、options或outOwnedPicture为nullptr。<br>         IMAGE_UNSUPPORTED_OPERATION：hdrPixelmap的像素格式不是RGBA_F16、RGBA_1010102、YCBCR_P010或YCRCB_P010。<br>         IMAGE_DECOMPOSE_FAILED：HDR分解处理失败。<br>         IMAGE_ALLOC_FAILED：内存分配失败。<br>         202：非系统应用程序调用该接口则返回此错误码。 |
<!--DelEnd-->


