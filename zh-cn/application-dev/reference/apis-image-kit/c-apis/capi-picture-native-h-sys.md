# picture_native.h（系统接口）

## 概述

提供获取picture数据和信息的API。

**库：** libpicture.so

**系统能力：** SystemCapability.Multimedia.Image.Core

**起始版本：** 13

**系统接口：** 此接口为系统接口。

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_DecomposeOptions（系统接口）](capi-image-nativemodule-oh-decomposeoptions-sys.md) | OH_DecomposeOptions | **OH_DecomposeOptions** is the HDR decomposition option struct encapsulated at the native layer. It is used to specify parameters used for HDR decomposition, such as the target pixel format.**系统接口：** 此接口为系统接口。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [Image_ErrorCode OH_AuxiliaryPictureNative_CreateUsingAllocator(uint8_t *data, uint32_t dataLength, OH_AuxiliaryPictureInfo *info, IMAGE_ALLOCATOR_MODE allocator, OH_AuxiliaryPictureNative **auxiliaryPicture)（系统接口）](#oh_auxiliarypicturenative_createusingallocator) | 创建一个具有指定内存类型的OH_AuxiliaryPictureNative对象。<ul><li>系统默认根据图像类型、图像大小、平台能力等因素选择内存类型。</li><li>处理该接口返回的辅助图时， 需要考虑stride的影响。</li><li>如果data为null或dataLength小于等于0，则不会初始化辅助图数据。</li></ul>**系统接口：** 此接口为系统接口。 |
| [Image_ErrorCode OH_DecomposeOptions_Create(OH_DecomposeOptions **outOwnedOptions)（系统接口）](#oh_decomposeoptions_create) | 创建OH_DecomposeOptions实例。创建的实例需通过[OH_DecomposeOptions_Release](capi-picture-native-h.md#oh_decomposeoptions_release)释放。**系统接口：** 此接口为系统接口。 |
| [Image_ErrorCode OH_DecomposeOptions_SetIsFullSizeGainmap(OH_DecomposeOptions *options, bool isFullSizeGainmap)（系统接口）](#oh_decomposeoptions_setisfullsizegainmap) | 设置是否生成全尺寸增益图（指增益图和主图尺寸一致）。若不自行设置，默认值为false，即增益图的尺寸是主图的一半。**系统接口：** 此接口为系统接口。 |
| [Image_ErrorCode OH_DecomposeOptions_GetIsFullSizeGainmap(OH_DecomposeOptions *options, bool *isFullSizeGainmap)（系统接口）](#oh_decomposeoptions_getisfullsizegainmap) | 获取是否生成全尺寸增益图（指增益图和主图尺寸一致）。如果isFullSizeGainmap为true，则增益图和主图尺寸一致；否则，增益图为主图尺寸的一半。**系统接口：** 此接口为系统接口。 |
| [Image_ErrorCode OH_DecomposeOptions_SetDesiredPixelFormat(OH_DecomposeOptions *options, int32_t desiredPixelFormat)（系统接口）](#oh_decomposeoptions_setdesiredpixelformat) | 设置HDR分解后的SDR PixelMap和增益图的像素格式。若不设置，默认值为RGBA_8888。**系统接口：** 此接口为系统接口。 |
| [Image_ErrorCode OH_DecomposeOptions_GetDesiredPixelFormat(OH_DecomposeOptions *options, int32_t *desiredPixelFormat)（系统接口）](#oh_decomposeoptions_getdesiredpixelformat) | 获取HDR分解后的SDR PixelMap和增益图的像素格式。**系统接口：** 此接口为系统接口。 |
| [Image_ErrorCode OH_DecomposeOptions_Release(OH_DecomposeOptions *options)（系统接口）](#oh_decomposeoptions_release) | 释放OH_DecomposeOptions指针。**系统接口：** 此接口为系统接口。 |
| [Image_ErrorCode OH_PictureNative_DecomposeToPicture(OH_PixelmapNative *hdrPixelmap, OH_DecomposeOptions *options, OH_PictureNative **outOwnedPicture)（系统接口）](#oh_picturenative_decomposetopicture) | 将HDR PixelMap分解为包含SDR PixelMap和增益图（gainmap）的Picture对象。创建的Picture实例需通过[OH_PictureNative_Release](capi-picture-native-h.md#oh_picturenative_release)释放。**系统接口：** 此接口为系统接口。 |

## 函数说明

### OH_AuxiliaryPictureNative_CreateUsingAllocator()

```c
Image_ErrorCode OH_AuxiliaryPictureNative_CreateUsingAllocator(uint8_t *data, uint32_t dataLength, OH_AuxiliaryPictureInfo *info, IMAGE_ALLOCATOR_MODE allocator, OH_AuxiliaryPictureNative **auxiliaryPicture)
```

**描述：**

创建一个具有指定内存类型的OH_AuxiliaryPictureNative对象。<ul><li>系统默认根据图像类型、图像大小、平台能力等因素选择内存类型。</li><li>处理该接口返回的辅助图时， 需要考虑stride的影响。</li><li>如果data为null或dataLength小于等于0，则不会初始化辅助图数据。</li></ul>

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint8_t *data | 指向图像数据的指针。 |
| uint32_t dataLength | 图像数据的长度。 |
| [OH_AuxiliaryPictureInfo](capi-image-nativemodule-oh-auxiliarypictureinfo.md) *info | 指向辅助图基本信息的指针。 |
| IMAGE_ALLOCATOR_MODE allocator | 辅助图使用的内存类型。有关可用选项的详细信息，请参阅{@link IMAGE_ALLOCATOR_MODE}。 |
| [OH_AuxiliaryPictureNative](capi-image-nativemodule-oh-auxiliarypicturenative.md) **auxiliaryPicture | 输出参数，用于接收新创建的OH_AuxiliaryPictureNative对象地址。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | <ul>      <br><li>IMAGE_SUCCESS：执行成功。</li>      <br><li>202：非系统应用程序调用该接口则返回此错误码。</li>      <br><li>IMAGE_INVALID_PARAMETER：info或auxiliaryPicture为空指针、allocator无效、辅助图大小无效或类型不支持、dataLength小于所需大小。</li>      <br><li>IMAGE_SOURCE_UNSUPPORTED_ALLOCATOR_TYPE：不支持的内存类型。      <br>例如使用共享内存创建增益图，仅DMA支持HDR元数据。</li>      <br><li>IMAGE_ALLOC_FAILED：内存分配失败。</li>      <br></ul> |

### OH_DecomposeOptions_Create()

```c
Image_ErrorCode OH_DecomposeOptions_Create(OH_DecomposeOptions **outOwnedOptions)
```

**描述：**

创建OH_DecomposeOptions实例。创建的实例需通过[OH_DecomposeOptions_Release](capi-picture-native-h.md#oh_decomposeoptions_release)释放。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_DecomposeOptions](capi-image-nativemodule-oh-decomposeoptions.md) **outOwnedOptions | 指向被创建的OH_DecomposeOptions指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | IMAGE_SUCCESS：执行成功。      <br>IMAGE_INVALID_PARAMETER：参数错误，例如outOwnedOptions为nullptr。      <br>IMAGE_ALLOC_FAILED：内存分配失败。      <br>202：非系统应用程序调用该接口则返回此错误码。 |

### OH_DecomposeOptions_SetIsFullSizeGainmap()

```c
Image_ErrorCode OH_DecomposeOptions_SetIsFullSizeGainmap(OH_DecomposeOptions *options, bool isFullSizeGainmap)
```

**描述：**

设置是否生成全尺寸增益图（指增益图和主图尺寸一致）。若不自行设置，默认值为false，即增益图的尺寸是主图的一半。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_DecomposeOptions](capi-image-nativemodule-oh-decomposeoptions.md) *options | 指向OH_DecomposeOptions对象的指针。 |
| bool isFullSizeGainmap | 是否生成全尺寸增益图。设置为true时生成全尺寸增益图，设置为false时生成1/2缩小的增益图。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | IMAGE_SUCCESS：执行成功。      <br>IMAGE_INVALID_PARAMETER：参数错误，例如options为nullptr。      <br>202：非系统应用程序调用该接口则返回此错误码。      @systemapi |

### OH_DecomposeOptions_GetIsFullSizeGainmap()

```c
Image_ErrorCode OH_DecomposeOptions_GetIsFullSizeGainmap(OH_DecomposeOptions *options, bool *isFullSizeGainmap)
```

**描述：**

获取是否生成全尺寸增益图（指增益图和主图尺寸一致）。如果isFullSizeGainmap为true，则增益图和主图尺寸一致；否则，增益图为主图尺寸的一半。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_DecomposeOptions](capi-image-nativemodule-oh-decomposeoptions.md) *options | 指向OH_DecomposeOptions对象的指针。 |
| bool *isFullSizeGainmap | 指向bool值的指针，用于接收是否生成全尺寸增益图的设置。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | IMAGE_SUCCESS：执行成功。      <br>IMAGE_INVALID_PARAMETER：参数错误，例如options或isFullSizeGainmap为nullptr。      <br>202：非系统应用程序调用该接口则返回此错误码。      @systemapi |

### OH_DecomposeOptions_SetDesiredPixelFormat()

```c
Image_ErrorCode OH_DecomposeOptions_SetDesiredPixelFormat(OH_DecomposeOptions *options, int32_t desiredPixelFormat)
```

**描述：**

设置HDR分解后的SDR PixelMap和增益图的像素格式。若不设置，默认值为RGBA_8888。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_DecomposeOptions](capi-image-nativemodule-oh-decomposeoptions.md) *options | 指向OH_DecomposeOptions对象的指针。 |
| int32_t desiredPixelFormat | 分解后SDR PixelMap和增益图的像素格式，支持RGBA_8888、NV12和NV21格式。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | IMAGE_SUCCESS：执行成功。      <br>IMAGE_INVALID_PARAMETER：参数错误，例如options为nullptr。      <br>IMAGE_UNSUPPORTED_OPERATION：不支持的像素格式。      <br>202：非系统应用程序调用该接口则返回此错误码。      @systemapi |

### OH_DecomposeOptions_GetDesiredPixelFormat()

```c
Image_ErrorCode OH_DecomposeOptions_GetDesiredPixelFormat(OH_DecomposeOptions *options, int32_t *desiredPixelFormat)
```

**描述：**

获取HDR分解后的SDR PixelMap和增益图的像素格式。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_DecomposeOptions](capi-image-nativemodule-oh-decomposeoptions.md) *options | 指向OH_DecomposeOptions对象的指针。 |
| int32_t *desiredPixelFormat | 指向int32_t的指针，用于接收像素格式设置。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | IMAGE_SUCCESS：执行成功。      <br>IMAGE_INVALID_PARAMETER：参数错误，例如options或desiredPixelFormat为nullptr。      <br>202：非系统应用程序调用该接口则返回此错误码。      @systemapi |

### OH_DecomposeOptions_Release()

```c
Image_ErrorCode OH_DecomposeOptions_Release(OH_DecomposeOptions *options)
```

**描述：**

释放OH_DecomposeOptions指针。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_DecomposeOptions](capi-image-nativemodule-oh-decomposeoptions.md) *options | 指向OH_DecomposeOptions对象的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | IMAGE_SUCCESS：执行成功。      <br>IMAGE_INVALID_PARAMETER：参数错误，例如options为nullptr。      <br>202：非系统应用程序调用该接口则返回此错误码。      @systemapi |

### OH_PictureNative_DecomposeToPicture()

```c
Image_ErrorCode OH_PictureNative_DecomposeToPicture(OH_PixelmapNative *hdrPixelmap, OH_DecomposeOptions *options, OH_PictureNative **outOwnedPicture)
```

**描述：**

将HDR PixelMap分解为包含SDR PixelMap和增益图（gainmap）的Picture对象。创建的Picture实例需通过[OH_PictureNative_Release](capi-picture-native-h.md#oh_picturenative_release)释放。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_PixelmapNative *hdrPixelmap | 被分解的HDR PixelMap指针，像素格式需为RGBA_F16、RGBA_1010102、YCBCR_P010或YCRCB_P010。 |
| [OH_DecomposeOptions](capi-image-nativemodule-oh-decomposeoptions.md) *options | HDR分解配置选项，此参数为必填。 |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) **outOwnedPicture | 指向被创建的Picture对象指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | IMAGE_SUCCESS：执行成功。      <br>IMAGE_INVALID_PARAMETER：参数错误，例如hdrPixelmap、options或outOwnedPicture为nullptr。      <br>IMAGE_UNSUPPORTED_OPERATION：hdrPixelmap的像素格式不是RGBA_F16、RGBA_1010102、YCBCR_P010或YCRCB_P010。      <br>IMAGE_DECOMPOSE_FAILED：HDR分解处理失败。      <br>IMAGE_ALLOC_FAILED：内存分配失败。      <br>202：非系统应用程序调用该接口则返回此错误码。 |


