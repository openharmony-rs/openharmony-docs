# image_common.h（系统接口）

## 概述

声明图像接口使用的公共枚举和结构体。

**库：** libimage_common.so

**系统能力：** SystemCapability.Multimedia.Image.Core

**起始版本：** 12

**系统接口：** 此接口为系统接口。

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [Image_ErrorCode OH_PictureMetadata_GetMetadataByType(OH_PictureMetadata **metadatas, uint32_t metadataCount, int32_t type, OH_PictureMetadata *metadata)（系统接口）](#oh_picturemetadata_getmetadatabytype) | 从OH_PictureMetadata数组中获取与指定类型匹配的PictureMetadata对象。**系统接口：** 此接口为系统接口。 |
| [Image_ErrorCode OH_PictureMetadatas_Release(OH_PictureMetadata **metadatas, uint32_t metadatasCount)（系统接口）](#oh_picturemetadatas_release) | 释放OH_PictureMetadata对象数组。**系统接口：** 此接口为系统接口。 |

## 函数说明

### OH_PictureMetadata_GetMetadataByType()

```c
Image_ErrorCode OH_PictureMetadata_GetMetadataByType(OH_PictureMetadata **metadatas, uint32_t metadataCount, int32_t type, OH_PictureMetadata *metadata)
```

**描述：**

从OH_PictureMetadata数组中获取与指定类型匹配的PictureMetadata对象。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PictureMetadata](capi-image-nativemodule-oh-picturemetadata.md) **metadatas | 指向OH_PictureMetadata数组的指针。 |
| uint32_t metadataCount | OH_PictureMetadata数组的长度。 |
| int32_t type | 要匹配的目标元数据类型。 |
| [OH_PictureMetadata](capi-image-nativemodule-oh-picturemetadata.md) *metadata | 指向OH_PictureMetadata输出对象的指针，用于存储匹配的内容。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | <ul>      <br><li>IMAGE_SUCCESS：执行成功。</li>      <br><li>202：非系统应用程序调用该接口则返回此错误码。</li>      <br><li>IMAGE_INVALID_PARAMETER：metadatas或metadata为空指针、数组长度为0。</li>      <br></ul> |

### OH_PictureMetadatas_Release()

```c
Image_ErrorCode OH_PictureMetadatas_Release(OH_PictureMetadata **metadatas, uint32_t metadatasCount)
```

**描述：**

释放OH_PictureMetadata对象数组。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PictureMetadata](capi-image-nativemodule-oh-picturemetadata.md) **metadatas | 指向OH_PictureMetadata数组的指针。 |
| uint32_t metadatasCount | OH_PictureMetadata数组的长度。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | <ul>      <br><li>IMAGE_SUCCESS：执行成功。</li>      <br><li>202：非系统应用程序调用该接口则返回此错误码。</li>      <br><li>IMAGE_INVALID_PARAMETER：metadatas为空指针、数组长度为0。</li>      <br></ul> |


