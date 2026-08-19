# OH_PictureMetadata

```c
typedef struct OH_PictureMetadata OH_PictureMetadata
```

## 概述

OH_PictureMetadata用于承载Picture元数据。<br>有多种方式创建和获取OH_PictureMetadata：<br>\| 函数 \| 描述 \|\| -- \| -- \|\|[OH_PictureMetadata_Create()](capi-image-common-h.md#oh_picturemetadata_create()) \| 创建OH_PictureMetadata指针。 \|\| [OH_PictureMetadata_Clone()](capi-image-common-h.md#oh_picturemetadata_clone()) \| 拷贝元数据。 \|\|{@link OH_PictureNative_GetMetadata()} \| 获取主图的元数据。 \|\| {@link OH_AuxiliaryPictureNative_GetMetadata()} \| 获取辅助图的元数据。 \|<br>使用[OH_PictureMetadata_Release()](capi-image-common-h.md#oh_picturemetadata_release())函数释放OH_PictureMetadata对象。<br>资源管理：通过[OH_PictureMetadata_Create()](capi-image-common-h.md#oh_picturemetadata_create())、[OH_PictureMetadata_Clone()](capi-image-common-h.md#oh_picturemetadata_clone())、{@link OH_PictureNative_GetMetadata()}或{@link OH_AuxiliaryPictureNative_GetMetadata()}获取到的OH_PictureMetadata对象由调用方管理，使用完成后应调用[OH_PictureMetadata_Release()](capi-image-common-h.md#oh_picturemetadata_release())释放。通过{@link OH_PictureNative_SetMetadata()}或{@link OH_AuxiliaryPictureNative_SetMetadata()}设置元数据时，接口不会释放传入的OH_PictureMetadata对象。<br>OH_PictureMetadata结构体内容和操作方式如下：<br>\| 字段类型 \| 字段名称 \| 字段描述 \| 字段获取函数 \| 字段设置函数 \|\| -- \| -- \| -- \| -- \| -- \|\|[Image_String](capi-image-nativemodule-image-string.md) \| property \| 元数据属性。 \| [OH_PictureMetadata_GetProperty()](capi-image-common-h.md#oh_picturemetadata_getproperty())、[OH_PictureMetadata_GetPropertyWithNull()](capi-image-common-h.md#oh_picturemetadata_getpropertywithnull()) \| [OH_PictureMetadata_SetProperty()](capi-image-common-h.md#oh_picturemetadata_setproperty()) \|\| OH_PictureMetadata \|metadata \| 元数据对象副本。 \| [OH_PictureMetadata_Clone()](capi-image-common-h.md#oh_picturemetadata_clone()) \| - \|

**起始版本：** 13

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [image_common.h](capi-image-common-h.md)

