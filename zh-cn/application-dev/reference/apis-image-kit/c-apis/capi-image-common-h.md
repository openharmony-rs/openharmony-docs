# image_common.h

## 概述

声明图像接口使用的公共枚举和结构体。

**库：** libimage_common.so

**系统能力：** SystemCapability.Multimedia.Image.Core

**起始版本：** 12

**相关模块：** [Image_NativeModule](capi-image-kit-image-nativemodule.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [Image_Size](capi-image-nativemodule-image-size.md) | Image_Size | 图像大小结构体。 |
| [Image_Region](capi-image-nativemodule-image-region.md) | Image_Region | 待解码的图像源区域结构体。区域坐标以图像左上角像素为原点（即(0, 0)），X轴正方向向右，Y轴正方向向下。 |
| [OH_PictureMetadata](capi-image-nativemodule-oh-picturemetadata.md) | OH_PictureMetadata | OH_PictureMetadata用于承载Picture元数据。<br>有多种方式创建和获取OH_PictureMetadata：<br>\| 函数 \| 描述 \|\| -- \| -- \|\| [OH_PictureMetadata_Create()](capi-image-common-h.md#oh_picturemetadata_create()) \| 创建OH_PictureMetadata指针。 \|\| [OH_PictureMetadata_Clone()](capi-image-common-h.md#oh_picturemetadata_clone()) \| 拷贝元数据。 \|\| OH_PictureNative_GetMetadata() \| 获取主图的元数据。 \|\| OH_AuxiliaryPictureNative_GetMetadata() \| 获取辅助图的元数据。 \|< br>使用[OH_PictureMetadata_Release()](capi-image-common-h.md#oh_picturemetadata_release())函数释放OH_PictureMetadata对象。<br>资源管理：通过[OH_PictureMetadata_Create()](capi-image-common-h.md#oh_picturemetadata_create())、 [OH_PictureMetadata_Clone()](capi-image-common-h.md#oh_picturemetadata_clone())、OH_PictureNative_GetMetadata()或 OH_AuxiliaryPictureNative_GetMetadata()获取到的OH_PictureMetadata对象由调用方管理，使用完成后应调用 [OH_PictureMetadata_Release()](capi-image-common-h.md#oh_picturemetadata_release())释放。通过OH_PictureNative_SetMetadata()或 OH_AuxiliaryPictureNative_SetMetadata()设置元数据时，接口不会释放传入的OH_PictureMetadata对象。<br> OH_PictureMetadata结构体内容和操作方式如下：<br>\| 字段类型 \| 字段名称 \| 字段描述 \| 字段获取函数 \| 字段设置函数 \|\| -- \| -- \| -- \| -- \| -- \|\| [Image_String](capi-image-nativemodule-image-string.md) \| property \| 元数据属性。 \| [OH_PictureMetadata_GetProperty()](capi-image-common-h.md#oh_picturemetadata_getproperty())、 [OH_PictureMetadata_GetPropertyWithNull()](capi-image-common-h.md#oh_picturemetadata_getpropertywithnull()) \| [OH_PictureMetadata_SetProperty()](capi-image-common-h.md#oh_picturemetadata_setproperty()) \|\| OH_PictureMetadata \| metadata \| 元数据对象副本。 \| [OH_PictureMetadata_Clone()](capi-image-common-h.md#oh_picturemetadata_clone()) \| - \| |
| [Image_String](capi-image-nativemodule-image-string.md) | Image_String | 字符串结构，用于描述字符串数据地址和数据长度。Image_MimeType是Image_String的别名，用于表示MIME类型。<br>作为输入参数使用时，调用方负责保证data和size有效；作为输出参数使用时， data的分配和释放方式以具体接口说明为准。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [Image_ErrorCode](#image_errorcode) | Image_ErrorCode | 错误码。 |
| [Image_MetadataType](#image_metadatatype) | Image_MetadataType | 定义元数据类型。 |
| [IMAGE_ALLOCATOR_MODE](#image_allocator_mode) | IMAGE_ALLOCATOR_MODE | Pixelmap的内存分配类型。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [Image_ErrorCode OH_PictureMetadata_Create(Image_MetadataType metadataType, OH_PictureMetadata **metadata)](#oh_picturemetadata_create) | 创建OH_PictureMetadata指针。 <br>使用约束：metadata不能为空指针。接口返回失败时，输出参数内容不应使用。 <br>资源管理：接口成功返回的OH_PictureMetadata对象由调用方管理，使用完成后应调用[OH_PictureMetadata_Release](capi-image-common-h.md#oh_picturemetadata_release)释放。 |
| [Image_ErrorCode OH_PictureMetadata_GetProperty(OH_PictureMetadata *metadata, Image_String *key, Image_String *value)](#oh_picturemetadata_getproperty) | 根据key获取Metadata的单条属性。该接口获取到的value.data缺少字符串结束符'\0'，请谨慎使用。 <br>使用约束：metadata、key、key->data和value均不能为空指针，key->size必须大于0。接口返回失败时，不应读取value.data。 <br>资源管理：接口执行成功后，value.data由接口分配，调用方使用完成后应使用delete[]释放。该接口返回的value.data不以字符串结束符'\0'结尾，如需按C字符串处理，建议使用 [OH_PictureMetadata_GetPropertyWithNull](capi-image-common-h.md#oh_picturemetadata_getpropertywithnull)。 |
| [Image_ErrorCode OH_PictureMetadata_GetPropertyWithNull(OH_PictureMetadata *metadata, Image_String *key, Image_String *value)](#oh_picturemetadata_getpropertywithnull) | 获取图片元数据的属性值。输出的value.data以字符串结束符'\0'结尾。 <br>使用场景：适用于读取字符串形式的元数据属性值。与[OH_PictureMetadata_GetProperty](capi-image-common-h.md#oh_picturemetadata_getproperty)相比，本接口返回的value.data以'\0'结尾，更适合直接按C字符串处理。 <br>使用约束：metadata、key、key->data和value均不能为空指针，key->size必须大于0。接口返回失败时，不应读取value.data。 <br>资源管理：接口执行成功后，value.data由接口分配，调用方使用完成后应使用delete[]释放。 |
| [Image_ErrorCode OH_PictureMetadata_SetProperty(OH_PictureMetadata *metadata, Image_String *key, Image_String *value)](#oh_picturemetadata_setproperty) | 根据key修改Metadata的单条属性。 <br>使用约束：metadata、key、key->data、value和value->data均不能为空指针，key->size和value->size必须大于0。 <br>资源管理：接口会读取传入的key和value内容，不持有调用方传入的Image_String指针。接口返回后，调用方仍需自行管理key和value的生命周期。 |
| [Image_ErrorCode OH_PictureMetadata_SetBlobData(OH_PictureMetadata *metadata, uint8_t *blob, uint32_t blobSize)](#oh_picturemetadata_setblobdata) | 使用二进制数据替换当前元数据。 |
| [Image_ErrorCode OH_PictureMetadata_GetBlobDataSize(OH_PictureMetadata *metadata, uint32_t *blobSize)](#oh_picturemetadata_getblobdatasize) | 获取元数据中blob数据的大小。 |
| [Image_ErrorCode OH_PictureMetadata_GetBlobData(OH_PictureMetadata *metadata, uint8_t *blob, uint32_t blobSize)](#oh_picturemetadata_getblobdata) | 以二进制数据的形式获取元数据。 |
| [Image_ErrorCode OH_PictureMetadata_Release(OH_PictureMetadata *metadata)](#oh_picturemetadata_release) | 释放OH_PictureMetadata指针。 <br>使用约束：metadata不能为空指针。 <br>资源管理：调用该接口后，metadata指向的OH_PictureMetadata对象会被释放，不应继续使用。 |
| [Image_ErrorCode OH_PictureMetadata_Clone(OH_PictureMetadata *oldMetadata, OH_PictureMetadata **newMetadata)](#oh_picturemetadata_clone) | 拷贝元数据。 <br>使用约束：oldMetadata和newMetadata均不能为空指针；接口返回失败时，输出参数内容不应使用。 <br>资源管理：接口成功返回的newMetadata由调用方管理，使用完成后应调用[OH_PictureMetadata_Release](capi-image-common-h.md#oh_picturemetadata_release)释放。 |

## 枚举类型说明

### Image_ErrorCode

```c
enum Image_ErrorCode
```

**描述：**

错误码。

<!--Device-enum Image_ErrorCode--><!--Device-enum Image_ErrorCode-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| IMAGE_SUCCESS = 0 | 操作成功。<br><!--Device-IMAGE_SUCCESS = 0--><!--Device-IMAGE_SUCCESS = 0-End--> |
| IMAGE_BAD_PARAMETER = 401 | 无效参数。<br><!--Device-IMAGE_BAD_PARAMETER = 401--><!--Device-IMAGE_BAD_PARAMETER = 401-End--> |
| OH_IMAGE_ERROR_NOT_SYSTEM_APPLICATION = 202 | &nbsp;权限校验失败。非系统应用调用系统接口。<br>**起始版本：** 26.0.1<br><!--Device-OH_IMAGE_ERROR_NOT_SYSTEM_APPLICATION = 202--><!--Device-OH_IMAGE_ERROR_NOT_SYSTEM_APPLICATION = 202-End--> |
| IMAGE_UNSUPPORTED_MIME_TYPE = 7600101 | 不支持的MIME类型。<br><!--Device-IMAGE_UNSUPPORTED_MIME_TYPE = 7600101--><!--Device-IMAGE_UNSUPPORTED_MIME_TYPE = 7600101-End--> |
| IMAGE_UNKNOWN_MIME_TYPE = 7600102 | 未知的MIME类型。<br><!--Device-IMAGE_UNKNOWN_MIME_TYPE = 7600102--><!--Device-IMAGE_UNKNOWN_MIME_TYPE = 7600102-End--> |
| IMAGE_TOO_LARGE = 7600103 | 过大的数据或图片。<br><!--Device-IMAGE_TOO_LARGE = 7600103--><!--Device-IMAGE_TOO_LARGE = 7600103-End--> |
| IMAGE_GET_IMAGE_DATA_FAILED = 7600104 | &nbsp;Failed to get image data.<br>**起始版本：** 23<br><!--Device-IMAGE_GET_IMAGE_DATA_FAILED = 7600104--><!--Device-IMAGE_GET_IMAGE_DATA_FAILED = 7600104-End--> |
| IMAGE_PIXELMAP_RELEASED = 7600105 | &nbsp;PixelMap has been released.<br>**起始版本：** 26.0.0<br><!--Device-IMAGE_PIXELMAP_RELEASED = 7600105--><!--Device-IMAGE_PIXELMAP_RELEASED = 7600105-End--> |
| IMAGE_DMA_NOT_EXIST = 7600173 | &nbsp;DMA memory does not exist<br><!--Device-IMAGE_DMA_NOT_EXIST = 7600173--><!--Device-IMAGE_DMA_NOT_EXIST = 7600173-End--> |
| IMAGE_DMA_OPERATION_FAILED = 7600174 | &nbsp;DMA operation failed<br><!--Device-IMAGE_DMA_OPERATION_FAILED = 7600174--><!--Device-IMAGE_DMA_OPERATION_FAILED = 7600174-End--> |
| IMAGE_UNSUPPORTED_OPERATION = 7600201 | 不支持的操作。<br><!--Device-IMAGE_UNSUPPORTED_OPERATION = 7600201--><!--Device-IMAGE_UNSUPPORTED_OPERATION = 7600201-End--> |
| IMAGE_UNSUPPORTED_METADATA = 7600202 | 不支持的metadata。<br><!--Device-IMAGE_UNSUPPORTED_METADATA = 7600202--><!--Device-IMAGE_UNSUPPORTED_METADATA = 7600202-End--> |
| IMAGE_UNSUPPORTED_CONVERSION = 7600203 | 不支持的转换。<br><!--Device-IMAGE_UNSUPPORTED_CONVERSION = 7600203--><!--Device-IMAGE_UNSUPPORTED_CONVERSION = 7600203-End--> |
| IMAGE_INVALID_REGION = 7600204 | 无效区域。<br><!--Device-IMAGE_INVALID_REGION = 7600204--><!--Device-IMAGE_INVALID_REGION = 7600204-End--> |
| IMAGE_UNSUPPORTED_MEMORY_FORMAT = 7600205 | &nbsp;unsupported memory format<br>**起始版本：** 13<br><!--Device-IMAGE_UNSUPPORTED_MEMORY_FORMAT = 7600205--><!--Device-IMAGE_UNSUPPORTED_MEMORY_FORMAT = 7600205-End--> |
| IMAGE_INVALID_PARAMETER = 7600206 | 无效参数。<br>**起始版本：** 19<br><!--Device-IMAGE_INVALID_PARAMETER = 7600206--><!--Device-IMAGE_INVALID_PARAMETER = 7600206-End--> |
| IMAGE_UNSUPPORTED_DATA_FORMAT = 7600207 | &nbsp;Unsupported data format<br>**起始版本：** 22<br><!--Device-IMAGE_UNSUPPORTED_DATA_FORMAT = 7600207--><!--Device-IMAGE_UNSUPPORTED_DATA_FORMAT = 7600207-End--> |
| OH_IMAGE_ERROR_DECOMPOSE_FAILED = 7600208 | &nbsp;图像分解失败。<br>**起始版本：** 26.0.1<br><!--Device-OH_IMAGE_ERROR_DECOMPOSE_FAILED = 7600208--><!--Device-OH_IMAGE_ERROR_DECOMPOSE_FAILED = 7600208-End--> |
| IMAGE_ALLOC_FAILED = 7600301 | 申请内存失败。<br><!--Device-IMAGE_ALLOC_FAILED = 7600301--><!--Device-IMAGE_ALLOC_FAILED = 7600301-End--> |
| IMAGE_COPY_FAILED = 7600302 | 内存拷贝失败。<br><!--Device-IMAGE_COPY_FAILED = 7600302--><!--Device-IMAGE_COPY_FAILED = 7600302-End--> |
| IMAGE_LOCK_UNLOCK_FAILED = 7600303 | &nbsp;memory lock or unlock failed<br>**起始版本：** 15<br><!--Device-IMAGE_LOCK_UNLOCK_FAILED = 7600303--><!--Device-IMAGE_LOCK_UNLOCK_FAILED = 7600303-End--> |
| IMAGE_INIT_FAILED = 7600304 | &nbsp;Initialization failed<br>**起始版本：** 22<br><!--Device-IMAGE_INIT_FAILED = 7600304--><!--Device-IMAGE_INIT_FAILED = 7600304-End--> |
| IMAGE_CREATE_PIXELMAP_FAILED = 7600305 | &nbsp;Create PixelMap failed<br>**起始版本：** 22<br><!--Device-IMAGE_CREATE_PIXELMAP_FAILED = 7600305--><!--Device-IMAGE_CREATE_PIXELMAP_FAILED = 7600305-End--> |
| IMAGE_DATA_CONVERSION_FAILED = 7600306 | &nbsp;Data conversion failed.<br>**起始版本：** 26.0.0<br><!--Device-IMAGE_DATA_CONVERSION_FAILED = 7600306--><!--Device-IMAGE_DATA_CONVERSION_FAILED = 7600306-End--> |
| IMAGE_ALLOCATOR_MODE_UNSUPPORTED = 7600501 | &nbsp;unsupported allocator mode, e.g., use share memory to create a HDR image as only DMA supported hdr metadata.<br>**起始版本：** 20<br><!--Device-IMAGE_ALLOCATOR_MODE_UNSUPPORTED = 7600501--><!--Device-IMAGE_ALLOCATOR_MODE_UNSUPPORTED = 7600501-End--> |
| IMAGE_UNKNOWN_ERROR = 7600901 | 未知错误。<br><!--Device-IMAGE_UNKNOWN_ERROR = 7600901--><!--Device-IMAGE_UNKNOWN_ERROR = 7600901-End--> |
| IMAGE_BAD_SOURCE = 7700101 | 解码数据源异常。<br><!--Device-IMAGE_BAD_SOURCE = 7700101--><!--Device-IMAGE_BAD_SOURCE = 7700101-End--> |
| IMAGE_SOURCE_UNSUPPORTED_MIME_TYPE = 7700102 | 图片解码中不支持的MIME类型。<br>**起始版本：** 15<br><!--Device-IMAGE_SOURCE_UNSUPPORTED_MIME_TYPE = 7700102--><!--Device-IMAGE_SOURCE_UNSUPPORTED_MIME_TYPE = 7700102-End--> |
| IMAGE_SOURCE_TOO_LARGE = 7700103 | 图像过大。<br>**起始版本：** 15<br><!--Device-IMAGE_SOURCE_TOO_LARGE = 7700103--><!--Device-IMAGE_SOURCE_TOO_LARGE = 7700103-End--> |
| IMAGE_SOURCE_UNSUPPORTED_ALLOCATOR_TYPE = 7700201 | 不支持的分配器类型。例如，DMA支持HDR元数据，可以使用共享内存解码HDR图像。<br>**起始版本：** 15<br><!--Device-IMAGE_SOURCE_UNSUPPORTED_ALLOCATOR_TYPE = 7700201--><!--Device-IMAGE_SOURCE_UNSUPPORTED_ALLOCATOR_TYPE = 7700201-End--> |
| IMAGE_SOURCE_UNSUPPORTED_METADATA = 7700202 | 不支持的元数据类型。如不支持的属性名或属性值非法。<br>**起始版本：** 23<br><!--Device-IMAGE_SOURCE_UNSUPPORTED_METADATA = 7700202--><!--Device-IMAGE_SOURCE_UNSUPPORTED_METADATA = 7700202-End--> |
| IMAGE_SOURCE_UNSUPPORTED_OPTIONS = 7700203 | 不支持的选项。例如，无法将图像转换为所需的像素格式。<br>**起始版本：** 15<br><!--Device-IMAGE_SOURCE_UNSUPPORTED_OPTIONS = 7700203--><!--Device-IMAGE_SOURCE_UNSUPPORTED_OPTIONS = 7700203-End--> |
| IMAGE_SOURCE_INVALID_PARAMETER = 7700204 | 无效参数。<br>**起始版本：** 19<br><!--Device-IMAGE_SOURCE_INVALID_PARAMETER = 7700204--><!--Device-IMAGE_SOURCE_INVALID_PARAMETER = 7700204-End--> |
| IMAGE_DECODE_FAILED = 7700301 | 解码失败。<br><!--Device-IMAGE_DECODE_FAILED = 7700301--><!--Device-IMAGE_DECODE_FAILED = 7700301-End--> |
| IMAGE_SOURCE_ALLOC_FAILED = 7700302 | 内存申请失败。<br>**起始版本：** 15<br><!--Device-IMAGE_SOURCE_ALLOC_FAILED = 7700302--><!--Device-IMAGE_SOURCE_ALLOC_FAILED = 7700302-End--> |
| IMAGE_PACKER_INVALID_PARAMETER = 7800202 | ImagePacker的无效参数。<br>**起始版本：** 19<br><!--Device-IMAGE_PACKER_INVALID_PARAMETER = 7800202--><!--Device-IMAGE_PACKER_INVALID_PARAMETER = 7800202-End--> |
| IMAGE_ENCODE_FAILED = 7800301 | 编码失败。<br><!--Device-IMAGE_ENCODE_FAILED = 7800301--><!--Device-IMAGE_ENCODE_FAILED = 7800301-End--> |
| IMAGE_RECEIVER_INVALID_PARAMETER = 7900201 | ImageReceiver的无效参数。<br>**起始版本：** 20<br><!--Device-IMAGE_RECEIVER_INVALID_PARAMETER = 7900201--><!--Device-IMAGE_RECEIVER_INVALID_PARAMETER = 7900201-End--> |

### Image_MetadataType

```c
enum Image_MetadataType
```

**描述：**

定义元数据类型。

<!--Device-enum Image_MetadataType--><!--Device-enum Image_MetadataType-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**起始版本：** 13

| 枚举项 | 描述 |
| -- | -- |
| EXIF_METADATA = 1 | EXIF元数据。<br>**起始版本：** 13<br><!--Device-EXIF_METADATA = 1--><!--Device-EXIF_METADATA = 1-End--> |
| FRAGMENT_METADATA = 2 | 水印裁剪图元数据。<br>**起始版本：** 13<br><!--Device-FRAGMENT_METADATA = 2--><!--Device-FRAGMENT_METADATA = 2-End--> |
| GIF_METADATA = 5 | GIF图片元数据。<br>**起始版本：** 20<br><!--Device-GIF_METADATA = 5--><!--Device-GIF_METADATA = 5-End--> |

### IMAGE_ALLOCATOR_MODE

```c
enum IMAGE_ALLOCATOR_MODE
```

**描述：**

Pixelmap的内存分配类型。

<!--Device-enum IMAGE_ALLOCATOR_MODE--><!--Device-enum IMAGE_ALLOCATOR_MODE-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**起始版本：** 20

| 枚举项 | 描述 |
| -- | -- |
| IMAGE_ALLOCATOR_MODE_AUTO = 0 | 系统决定内存分配类型。系统会根据图像类型、图像大小、平台能力等选择内存类型。<br>**起始版本：** 20<br><!--Device-IMAGE_ALLOCATOR_MODE_AUTO = 0--><!--Device-IMAGE_ALLOCATOR_MODE_AUTO = 0-End--> |
| IMAGE_ALLOCATOR_MODE_DMA = 1 | 使用DMA（Direct Memory Access，直接内存访问）的内存类型，适用于对解码及渲染性能有较高要求的场景。 根据设备硬件的差异可能会在每行像素的末尾产生用于内存对齐的空白填充字节。<br>**起始版本：** 20<br><!--Device-IMAGE_ALLOCATOR_MODE_DMA = 1--><!--Device-IMAGE_ALLOCATOR_MODE_DMA = 1-End--> |
| IMAGE_ALLOCATOR_MODE_SHARED_MEMORY = 2 | 使用共享内存（Shared Memory）的内存类型。<br>**起始版本：** 20<br><!--Device-IMAGE_ALLOCATOR_MODE_SHARED_MEMORY = 2--><!--Device-IMAGE_ALLOCATOR_MODE_SHARED_MEMORY = 2-End--> |


## 函数说明

### OH_PictureMetadata_Create()

```c
Image_ErrorCode OH_PictureMetadata_Create(Image_MetadataType metadataType, OH_PictureMetadata **metadata)
```

**描述：**

创建OH_PictureMetadata指针。 <br>使用约束：metadata不能为空指针。接口返回失败时，输出参数内容不应使用。 <br>资源管理：接口成功返回的OH_PictureMetadata对象由调用方管理，使用完成后应调用[OH_PictureMetadata_Release](capi-image-common-h.md#oh_picturemetadata_release)释放。

<!--Device-Image_ErrorCode OH_PictureMetadata_Create(Image_MetadataType metadataType, OH_PictureMetadata **metadata)--><!--Device-Image_ErrorCode OH_PictureMetadata_Create(Image_MetadataType metadataType, OH_PictureMetadata **metadata)-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Image_MetadataType](capi-image-common-h.md#image_metadatatype) metadataType | 元数据的类型。 |
| [OH_PictureMetadata](capi-image-nativemodule-oh-picturemetadata.md) **metadata | 指向OH_PictureMetadata对象的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。<br>IMAGE_BAD_PARAMETER：参数错误。 |

### OH_PictureMetadata_GetProperty()

```c
Image_ErrorCode OH_PictureMetadata_GetProperty(OH_PictureMetadata *metadata, Image_String *key, Image_String *value)
```

**描述：**

根据key获取Metadata的单条属性。该接口获取到的value.data缺少字符串结束符'\0'，请谨慎使用。 <br>使用约束：metadata、key、key->data和value均不能为空指针，key->size必须大于0。接口返回失败时，不应读取value.data。 <br>资源管理：接口执行成功后，value.data由接口分配，调用方使用完成后应使用delete[]释放。该接口返回的value.data不以字符串结束符'\0'结尾，如需按C字符串处理，建议使用 [OH_PictureMetadata_GetPropertyWithNull](capi-image-common-h.md#oh_picturemetadata_getpropertywithnull)。

<!--Device-Image_ErrorCode OH_PictureMetadata_GetProperty(OH_PictureMetadata *metadata, Image_String *key, Image_String *value)--><!--Device-Image_ErrorCode OH_PictureMetadata_GetProperty(OH_PictureMetadata *metadata, Image_String *key, Image_String *value)-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PictureMetadata](capi-image-nativemodule-oh-picturemetadata.md) *metadata | 指向OH_PictureMetadata对象的指针。 |
| [Image_String](capi-image-nativemodule-image-string.md) *key | 属性的键。 |
| [Image_String](capi-image-nativemodule-image-string.md) *value | 属性的值。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。<br>IMAGE_BAD_PARAMETER：参数错误。<br>IMAGE_UNSUPPORTED_METADATA：不支持的元数据类型，或元数据类型与辅助图片类型不匹配。 |

### OH_PictureMetadata_GetPropertyWithNull()

```c
Image_ErrorCode OH_PictureMetadata_GetPropertyWithNull(OH_PictureMetadata *metadata, Image_String *key, Image_String *value)
```

**描述：**

获取图片元数据的属性值。输出的value.data以字符串结束符'\0'结尾。 <br>使用场景：适用于读取字符串形式的元数据属性值。与[OH_PictureMetadata_GetProperty](capi-image-common-h.md#oh_picturemetadata_getproperty)相比，本接口返回的value.data以'\0'结尾，更适合直接按C字符串处理。 <br>使用约束：metadata、key、key->data和value均不能为空指针，key->size必须大于0。接口返回失败时，不应读取value.data。 <br>资源管理：接口执行成功后，value.data由接口分配，调用方使用完成后应使用delete[]释放。

<!--Device-Image_ErrorCode OH_PictureMetadata_GetPropertyWithNull(OH_PictureMetadata *metadata, Image_String *key, Image_String *value)--><!--Device-Image_ErrorCode OH_PictureMetadata_GetPropertyWithNull(OH_PictureMetadata *metadata, Image_String *key, Image_String *value)-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PictureMetadata](capi-image-nativemodule-oh-picturemetadata.md) *metadata | 将被操作的PictureMetadata指针。 |
| [Image_String](capi-image-nativemodule-image-string.md) *key | 属性键指针。 |
| [Image_String](capi-image-nativemodule-image-string.md) *value | 属性值指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。<br>IMAGE_INVALID_PARAMETER：metadata、key或value为空。<br>IMAGE_UNSUPPORTED_METADATA：不支持的元数据类型，或元数据类型与辅助图片类型不匹配。 |

### OH_PictureMetadata_SetProperty()

```c
Image_ErrorCode OH_PictureMetadata_SetProperty(OH_PictureMetadata *metadata, Image_String *key, Image_String *value)
```

**描述：**

根据key修改Metadata的单条属性。 <br>使用约束：metadata、key、key->data、value和value->data均不能为空指针，key->size和value->size必须大于0。 <br>资源管理：接口会读取传入的key和value内容，不持有调用方传入的Image_String指针。接口返回后，调用方仍需自行管理key和value的生命周期。

<!--Device-Image_ErrorCode OH_PictureMetadata_SetProperty(OH_PictureMetadata *metadata, Image_String *key, Image_String *value)--><!--Device-Image_ErrorCode OH_PictureMetadata_SetProperty(OH_PictureMetadata *metadata, Image_String *key, Image_String *value)-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PictureMetadata](capi-image-nativemodule-oh-picturemetadata.md) *metadata | 指向OH_PictureMetadata对象的指针。 |
| [Image_String](capi-image-nativemodule-image-string.md) *key | 属性的键。 |
| [Image_String](capi-image-nativemodule-image-string.md) *value | 属性的值。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。<br>IMAGE_BAD_PARAMETER：参数错误。<br>IMAGE_UNSUPPORTED_METADATA：不支持的元数据类型，或元数据类型与辅助图片类型不匹配。 |

### OH_PictureMetadata_SetBlobData()

```c
Image_ErrorCode OH_PictureMetadata_SetBlobData(OH_PictureMetadata *metadata, uint8_t *blob, uint32_t blobSize)
```

**描述：**

使用二进制数据替换当前元数据。

<!--Device-Image_ErrorCode OH_PictureMetadata_SetBlobData(OH_PictureMetadata *metadata, uint8_t *blob, uint32_t blobSize)--><!--Device-Image_ErrorCode OH_PictureMetadata_SetBlobData(OH_PictureMetadata *metadata, uint8_t *blob, uint32_t blobSize)-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PictureMetadata](capi-image-nativemodule-oh-picturemetadata.md) *metadata | 指向OH_PictureMetadata对象的指针。 |
| uint8_t *blob | 指向二进制数据的指针。 |
| uint32_t blobSize | 二进制数据的大小。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | <ul> <br><li>IMAGE_SUCCESS：执行成功。</li> <br><li>IMAGE_INVALID_PARAMETER：metadata或blob为空指针、blobSize为0。</li> <br><li>IMAGE_UNSUPPORTED_METADATA：不支持的元数据类型。</li> <br><li>IMAGE_UNSUPPORTED_OPERATION：未能设置二进制数据。</li> <br></ul> |

### OH_PictureMetadata_GetBlobDataSize()

```c
Image_ErrorCode OH_PictureMetadata_GetBlobDataSize(OH_PictureMetadata *metadata, uint32_t *blobSize)
```

**描述：**

获取元数据中blob数据的大小。

<!--Device-Image_ErrorCode OH_PictureMetadata_GetBlobDataSize(OH_PictureMetadata *metadata, uint32_t *blobSize)--><!--Device-Image_ErrorCode OH_PictureMetadata_GetBlobDataSize(OH_PictureMetadata *metadata, uint32_t *blobSize)-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PictureMetadata](capi-image-nativemodule-oh-picturemetadata.md) *metadata | 指向OH_PictureMetadata对象的指针。 |
| uint32_t *blobSize | 指向二进制数据大小的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | <ul> <br><li>IMAGE_SUCCESS：执行成功。</li> <br><li>IMAGE_INVALID_PARAMETER：metadata或blobSize为空指针。</li> <br><li>IMAGE_UNSUPPORTED_METADATA：不支持的元数据类型。</li> <br></ul> |

### OH_PictureMetadata_GetBlobData()

```c
Image_ErrorCode OH_PictureMetadata_GetBlobData(OH_PictureMetadata *metadata, uint8_t *blob, uint32_t blobSize)
```

**描述：**

以二进制数据的形式获取元数据。

<!--Device-Image_ErrorCode OH_PictureMetadata_GetBlobData(OH_PictureMetadata *metadata, uint8_t *blob, uint32_t blobSize)--><!--Device-Image_ErrorCode OH_PictureMetadata_GetBlobData(OH_PictureMetadata *metadata, uint8_t *blob, uint32_t blobSize)-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PictureMetadata](capi-image-nativemodule-oh-picturemetadata.md) *metadata | 指向OH_PictureMetadata对象的指针。 |
| uint8_t *blob | 指向获取到的二进制数据的指针。 |
| uint32_t blobSize | 二进制数据的大小。该值必须大于或等于通过OH_PictureMetadata_GetBlobDataSize方法获取的值。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | <ul> <br><li>IMAGE_SUCCESS：执行成功。</li> <br><li>IMAGE_INVALID_PARAMETER：metadata或blob为空指针、blobSize为0或小于要求。</li> <br><li>IMAGE_UNSUPPORTED_METADATA：不支持的元数据类型。</li> <br><li>IMAGE_UNSUPPORTED_OPERATION：无法获取二进制数据。</li> <br></ul> |

### OH_PictureMetadata_Release()

```c
Image_ErrorCode OH_PictureMetadata_Release(OH_PictureMetadata *metadata)
```

**描述：**

释放OH_PictureMetadata指针。 <br>使用约束：metadata不能为空指针。 <br>资源管理：调用该接口后，metadata指向的OH_PictureMetadata对象会被释放，不应继续使用。

<!--Device-Image_ErrorCode OH_PictureMetadata_Release(OH_PictureMetadata *metadata)--><!--Device-Image_ErrorCode OH_PictureMetadata_Release(OH_PictureMetadata *metadata)-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PictureMetadata](capi-image-nativemodule-oh-picturemetadata.md) *metadata | 被操作的OH_PictureMetadata指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。<br>IMAGE_BAD_PARAMETER：参数错误。 |

### OH_PictureMetadata_Clone()

```c
Image_ErrorCode OH_PictureMetadata_Clone(OH_PictureMetadata *oldMetadata, OH_PictureMetadata **newMetadata)
```

**描述：**

拷贝元数据。 <br>使用约束：oldMetadata和newMetadata均不能为空指针；接口返回失败时，输出参数内容不应使用。 <br>资源管理：接口成功返回的newMetadata由调用方管理，使用完成后应调用[OH_PictureMetadata_Release](capi-image-common-h.md#oh_picturemetadata_release)释放。

<!--Device-Image_ErrorCode OH_PictureMetadata_Clone(OH_PictureMetadata *oldMetadata, OH_PictureMetadata **newMetadata)--><!--Device-Image_ErrorCode OH_PictureMetadata_Clone(OH_PictureMetadata *oldMetadata, OH_PictureMetadata **newMetadata)-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PictureMetadata](capi-image-nativemodule-oh-picturemetadata.md) *oldMetadata | 被操作的OH_PictureMetadata指针。 |
| [OH_PictureMetadata](capi-image-nativemodule-oh-picturemetadata.md) **newMetadata | 拷贝得到的OH_PictureMetadata指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | IMAGE_SUCCESS：执行成功。<br>IMAGE_BAD_PARAMETER：参数错误。<br>IMAGE_ALLOC_FAILED：内存分配失败。<br>IMAGE_COPY_FAILED：内存拷贝失败。 |


