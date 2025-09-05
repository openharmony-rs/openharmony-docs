# image_effect.h

<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zyj208-->
<!--Designer: @wangshoucheng-->
<!--Tester: @gengfei-->
<!--Adviser: @zengyawen-->

## 概述

声明效果器相关接口。<br> 效果器提供了滤镜的添加、删除、查询等功能。开发者可以通过效果器提供的接口将多个滤镜组合串联，从而实现较为复杂的效果调节功能。<br> 同时，效果器支持多种输入类型，如Pixelmap、URI、Surface、Picture。不同的输入类型在效果器内部都会转换为内存对象，通过滤镜的效果处理，获得处理结果。

**引用文件：** <multimedia/image_effect/image_effect.h>

**库：** libimage_effect.so

**系统能力：** SystemCapability.Multimedia.ImageEffect.Core

**起始版本：** 12

**相关模块：** [ImageEffect](capi-imageeffect.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) | OH_ImageEffect | 定义效果器结构类型。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_ImageEffect *OH_ImageEffect_Create(const char *name)](#oh_imageeffect_create) | 创建OH_ImageEffect实例，调用[OH_ImageEffect_Release](capi-image-effect-h.md#oh_imageeffect_release)进行资源释放。 |
| [OH_EffectFilter *OH_ImageEffect_AddFilter(OH_ImageEffect *imageEffect, const char *filterName)](#oh_imageeffect_addfilter) | 添加滤镜。 |
| [ImageEffect_ErrorCode OH_ImageEffect_AddFilterByFilter(OH_ImageEffect *imageEffect, OH_EffectFilter *filter)](#oh_imageeffect_addfilterbyfilter) | 添加指定滤镜。 |
| [OH_EffectFilter *OH_ImageEffect_InsertFilter(OH_ImageEffect *imageEffect, uint32_t index, const char *filterName)](#oh_imageeffect_insertfilter) | 插入滤镜。 |
| [ImageEffect_ErrorCode OH_ImageEffect_InsertFilterByFilter(OH_ImageEffect *imageEffect, uint32_t index, OH_EffectFilter *filter)](#oh_imageeffect_insertfilterbyfilter) | 按指定位置插入滤镜。 |
| [int32_t OH_ImageEffect_RemoveFilter(OH_ImageEffect *imageEffect, const char *filterName)](#oh_imageeffect_removefilter) | 移除滤镜。 |
| [ImageEffect_ErrorCode OH_ImageEffect_RemoveFilterByIndex(OH_ImageEffect *imageEffect, uint32_t index)](#oh_imageeffect_removefilterbyindex) | 移除指定位置滤镜。 |
| [OH_EffectFilter *OH_ImageEffect_ReplaceFilter(OH_ImageEffect *imageEffect, uint32_t index, const char *filterName)](#oh_imageeffect_replacefilter) | 替换滤镜。 |
| [ImageEffect_ErrorCode OH_ImageEffect_ReplaceFilterByFilter(OH_ImageEffect *imageEffect, uint32_t index, const char *filterName)](#oh_imageeffect_replacefilterbyfilter) | 替换指定位置滤镜。 |
| [int32_t OH_ImageEffect_GetFilterCount(OH_ImageEffect *imageEffect)](#oh_imageeffect_getfiltercount) | 查询已添加滤镜个数。 |
| [OH_EffectFilter *OH_ImageEffect_GetFilter(OH_ImageEffect *imageEffect, uint32_t index)](#oh_imageeffect_getfilter) | 查询已添加滤镜。 |
| [ImageEffect_ErrorCode OH_ImageEffect_Configure(OH_ImageEffect *imageEffect, const char *key, const ImageEffect_Any *value)](#oh_imageeffect_configure) | 设置配置信息。 |
| [ImageEffect_ErrorCode OH_ImageEffect_SetOutputSurface(OH_ImageEffect *imageEffect, OHNativeWindow *nativeWindow)](#oh_imageeffect_setoutputsurface) | 设置输出Surface。 |
| [ImageEffect_ErrorCode OH_ImageEffect_GetInputSurface(OH_ImageEffect *imageEffect, OHNativeWindow **nativeWindow)](#oh_imageeffect_getinputsurface) | 获取输入Surface。 |
| [ImageEffect_ErrorCode OH_ImageEffect_SetInputPixelmap(OH_ImageEffect *imageEffect, OH_PixelmapNative *pixelmap)](#oh_imageeffect_setinputpixelmap) | 设置输入的Pixelmap。 |
| [ImageEffect_ErrorCode OH_ImageEffect_SetOutputPixelmap(OH_ImageEffect *imageEffect, OH_PixelmapNative *pixelmap)](#oh_imageeffect_setoutputpixelmap) | 设置输出的Pixelmap。 |
| [ImageEffect_ErrorCode OH_ImageEffect_SetInputNativeBuffer(OH_ImageEffect *imageEffect, OH_NativeBuffer *nativeBuffer)](#oh_imageeffect_setinputnativebuffer) | 设置输入的NativeBuffer。 |
| [ImageEffect_ErrorCode OH_ImageEffect_SetOutputNativeBuffer(OH_ImageEffect *imageEffect, OH_NativeBuffer *nativeBuffer)](#oh_imageeffect_setoutputnativebuffer) | 设置输出的NativeBuffer。 |
| [ImageEffect_ErrorCode OH_ImageEffect_SetInputUri(OH_ImageEffect *imageEffect, const char *uri)](#oh_imageeffect_setinputuri) | 设置输入的URI。 |
| [ImageEffect_ErrorCode OH_ImageEffect_SetOutputUri(OH_ImageEffect *imageEffect, const char *uri)](#oh_imageeffect_setoutputuri) | 设置输出的URI。 |
| [ImageEffect_ErrorCode OH_ImageEffect_SetInputPicture(OH_ImageEffect *imageEffect, OH_PictureNative *picture)](#oh_imageeffect_setinputpicture) | 设置输入的Picture。 |
| [ImageEffect_ErrorCode OH_ImageEffect_SetOutputPicture(OH_ImageEffect *imageEffect, OH_PictureNative *picture)](#oh_imageeffect_setoutputpicture) | 设置输出的Picture。 |
| [ImageEffect_ErrorCode OH_ImageEffect_SetInputTextureId(OH_ImageEffect *imageEffect, int32_t textureId,int32_t colorSpace)](#oh_imageeffect_setinputtextureid) | 配置输入包含图片内容的纹理标识。 |
| [ImageEffect_ErrorCode OH_ImageEffect_SetOutputTextureId(OH_ImageEffect *imageEffect, int32_t textureId)](#oh_imageeffect_setoutputtextureid) | 配置输出包含渲染后的纹理标识。 |
| [ImageEffect_ErrorCode OH_ImageEffect_Start(OH_ImageEffect *imageEffect)](#oh_imageeffect_start) | 启动效果器。 |
| [ImageEffect_ErrorCode OH_ImageEffect_Stop(OH_ImageEffect *imageEffect)](#oh_imageeffect_stop) | 停止生效效果。 |
| [ImageEffect_ErrorCode OH_ImageEffect_Release(OH_ImageEffect *imageEffect)](#oh_imageeffect_release) | 释放OH_ImageEffect实例资源。 |
| [ImageEffect_ErrorCode OH_ImageEffect_Save(OH_ImageEffect *imageEffect, char **info)](#oh_imageeffect_save) | 序列化效果器。 |
| [OH_ImageEffect *OH_ImageEffect_Restore(const char *info)](#oh_imageeffect_restore) | 反序列化效果器。 |

## 函数说明

### OH_ImageEffect_Create()

```
OH_ImageEffect *OH_ImageEffect_Create(const char *name)
```

**描述**

创建OH_ImageEffect实例，调用[OH_ImageEffect_Release](capi-image-effect-h.md#oh_imageeffect_release)进行资源释放。

**系统能力：** SystemCapability.Multimedia.ImageEffect.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *name | 效果器名，用于标识效果器，由用户自定义，建议为非空的字符串。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) * | 返回一个指向OH_ImageEffect实例的指针，创建失败时返回空指针。 |

### OH_ImageEffect_AddFilter()

```
OH_EffectFilter *OH_ImageEffect_AddFilter(OH_ImageEffect *imageEffect, const char *filterName)
```

**描述**

添加滤镜。

**系统能力：** SystemCapability.Multimedia.ImageEffect.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | 效果器指针。 |
| const char *filterName | 滤镜名。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_EffectFilter](capi-imageeffect-oh-effectfilter.md) * | 返回一个指向OH_EffectFilter实例的指针，滤镜名无效时返回空指针。 |

### OH_ImageEffect_AddFilterByFilter()

```
ImageEffect_ErrorCode OH_ImageEffect_AddFilterByFilter(OH_ImageEffect *imageEffect, OH_EffectFilter *filter)
```

**描述**

添加指定滤镜。

**系统能力：** SystemCapability.Multimedia.ImageEffect.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | 效果器指针。 |
| [OH_EffectFilter](capi-imageeffect-oh-effectfilter.md) *filter | 滤镜指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ImageEffect_ErrorCode](capi-image-effect-errors-h.md#imageeffect_errorcode) | EFFECT_SUCCESS：方法调用成功。<br>         EFFECT_ERROR_PARAM_INVALID：入参为空指针。 |

### OH_ImageEffect_InsertFilter()

```
OH_EffectFilter *OH_ImageEffect_InsertFilter(OH_ImageEffect *imageEffect, uint32_t index, const char *filterName)
```

**描述**

插入滤镜。

**系统能力：** SystemCapability.Multimedia.ImageEffect.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | 效果器指针。 |
| uint32_t index | 插入滤镜位置索引。 |
| const char *filterName | 滤镜名。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_EffectFilter](capi-imageeffect-oh-effectfilter.md) * | 返回一个指向OH_EffectFilter实例的指针，参数无效时返回空指针。 |

### OH_ImageEffect_InsertFilterByFilter()

```
ImageEffect_ErrorCode OH_ImageEffect_InsertFilterByFilter(OH_ImageEffect *imageEffect, uint32_t index,OH_EffectFilter *filter)
```

**描述**

按指定位置插入滤镜。

**系统能力：** SystemCapability.Multimedia.ImageEffect.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | 效果器指针。 |
| uint32_t index | 插入滤镜位置索引。 |
| [OH_EffectFilter](capi-imageeffect-oh-effectfilter.md) *filter | 滤镜指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ImageEffect_ErrorCode](capi-image-effect-errors-h.md#imageeffect_errorcode) | EFFECT_SUCCESS：方法调用成功。<br>         EFFECT_ERROR_PARAM_INVALID：入参为空指针。 |

### OH_ImageEffect_RemoveFilter()

```
int32_t OH_ImageEffect_RemoveFilter(OH_ImageEffect *imageEffect, const char *filterName)
```

**描述**

移除滤镜。

**系统能力：** SystemCapability.Multimedia.ImageEffect.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | 效果器指针。 |
| const char *filterName | 滤镜名。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 所删除的滤镜个数。 |

### OH_ImageEffect_RemoveFilterByIndex()

```
ImageEffect_ErrorCode OH_ImageEffect_RemoveFilterByIndex(OH_ImageEffect *imageEffect, uint32_t index)
```

**描述**

移除指定位置滤镜。

**系统能力：** SystemCapability.Multimedia.ImageEffect.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | 效果器指针。 |
| uint32_t index | 移除滤镜位置索引。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ImageEffect_ErrorCode](capi-image-effect-errors-h.md#imageeffect_errorcode) | EFFECT_SUCCESS：方法调用成功。<br>         EFFECT_ERROR_PARAM_INVALID：入参为空指针。 |

### OH_ImageEffect_ReplaceFilter()

```
OH_EffectFilter *OH_ImageEffect_ReplaceFilter(OH_ImageEffect *imageEffect, uint32_t index, const char *filterName)
```

**描述**

替换滤镜。

**系统能力：** SystemCapability.Multimedia.ImageEffect.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | 效果器指针。 |
| const char *filterName | 滤镜名。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_EffectFilter](capi-imageeffect-oh-effectfilter.md) * | 返回一个指向OH_EffectFilter实例的指针，替换失败时返回空指针。 |

### OH_ImageEffect_ReplaceFilterByFilter()

```
ImageEffect_ErrorCode OH_ImageEffect_ReplaceFilterByFilter(OH_ImageEffect *imageEffect, uint32_t index,const char *filterName)
```

**描述**

替换指定位置滤镜。

**系统能力：** SystemCapability.Multimedia.ImageEffect.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | 效果器指针。 |
| uint32_t index | 替换滤镜位置索引。 |
| const char *filterName | 滤镜名。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ImageEffect_ErrorCode](capi-image-effect-errors-h.md#imageeffect_errorcode) | EFFECT_SUCCESS：方法调用成功。<br>         EFFECT_ERROR_PARAM_INVALID：入参为空指针。 |

### OH_ImageEffect_GetFilterCount()

```
int32_t OH_ImageEffect_GetFilterCount(OH_ImageEffect *imageEffect)
```

**描述**

查询已添加滤镜个数。

**系统能力：** SystemCapability.Multimedia.ImageEffect.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | 效果器指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 已添加的滤镜个数。 |

### OH_ImageEffect_GetFilter()

```
OH_EffectFilter *OH_ImageEffect_GetFilter(OH_ImageEffect *imageEffect, uint32_t index)
```

**描述**

查询已添加滤镜。

**系统能力：** SystemCapability.Multimedia.ImageEffect.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | 效果器指针。 |
| uint32_t index | 待查询滤镜位置索引。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_EffectFilter](capi-imageeffect-oh-effectfilter.md) * | 返回一个指向OH_EffectFilter实例的指针，参数无效时返回空指针。 |

### OH_ImageEffect_Configure()

```
ImageEffect_ErrorCode OH_ImageEffect_Configure(OH_ImageEffect *imageEffect, const char *key,const ImageEffect_Any *value)
```

**描述**

设置配置信息。

**系统能力：** SystemCapability.Multimedia.ImageEffect.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | 效果器指针。 |
| const char *key | 配置参数。 |
| [const ImageEffect_Any](capi-imageeffect-imageeffect-any.md) *value | 配置参数值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ImageEffect_ErrorCode](capi-image-effect-errors-h.md#imageeffect_errorcode) | EFFECT_SUCCESS：方法调用成功。<br>         EFFECT_ERROR_PARAM_INVALID：入参为空指针。<br>         EFFECT_KEY_ERROR：参数无效。<br>         EFFECT_PARAM_ERROR：参数值无效。 |

### OH_ImageEffect_SetOutputSurface()

```
ImageEffect_ErrorCode OH_ImageEffect_SetOutputSurface(OH_ImageEffect *imageEffect, OHNativeWindow *nativeWindow)
```

**描述**

设置输出Surface。

**系统能力：** SystemCapability.Multimedia.ImageEffect.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | 效果器指针。 |
| OHNativeWindow *nativeWindow | 指向OHNativeWindow实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ImageEffect_ErrorCode](capi-image-effect-errors-h.md#imageeffect_errorcode) | EFFECT_SUCCESS：方法调用成功。<br>         EFFECT_ERROR_PARAM_INVALID：入参为空指针。 |

### OH_ImageEffect_GetInputSurface()

```
ImageEffect_ErrorCode OH_ImageEffect_GetInputSurface(OH_ImageEffect *imageEffect, OHNativeWindow **nativeWindow)
```

**描述**

获取输入Surface。

**系统能力：** SystemCapability.Multimedia.ImageEffect.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | 效果器指针。 |
| OHNativeWindow **nativeWindow | 指向OHNativeWindow实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ImageEffect_ErrorCode](capi-image-effect-errors-h.md#imageeffect_errorcode) | EFFECT_SUCCESS：方法调用成功。<br>         EFFECT_ERROR_PARAM_INVALID：入参为空指针。 |

### OH_ImageEffect_SetInputPixelmap()

```
ImageEffect_ErrorCode OH_ImageEffect_SetInputPixelmap(OH_ImageEffect *imageEffect, OH_PixelmapNative *pixelmap)
```

**描述**

设置输入的Pixelmap。

**系统能力：** SystemCapability.Multimedia.ImageEffect.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | 效果器指针。 |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | 指向OH_PixelmapNative实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ImageEffect_ErrorCode](capi-image-effect-errors-h.md#imageeffect_errorcode) | EFFECT_SUCCESS：方法调用成功。<br>         EFFECT_ERROR_PARAM_INVALID：入参为空指针。 |

### OH_ImageEffect_SetOutputPixelmap()

```
ImageEffect_ErrorCode OH_ImageEffect_SetOutputPixelmap(OH_ImageEffect *imageEffect, OH_PixelmapNative *pixelmap)
```

**描述**

设置输出的Pixelmap。

**系统能力：** SystemCapability.Multimedia.ImageEffect.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | 效果器指针。 |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | 指向OH_PixelmapNative实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ImageEffect_ErrorCode](capi-image-effect-errors-h.md#imageeffect_errorcode) | EFFECT_SUCCESS：方法调用成功。<br>         EFFECT_ERROR_PARAM_INVALID：入参为空指针。<br>         EFFECT_PARAM_ERROR：如果参数异常导致方法调用失败。 |

### OH_ImageEffect_SetInputNativeBuffer()

```
ImageEffect_ErrorCode OH_ImageEffect_SetInputNativeBuffer(OH_ImageEffect *imageEffect, OH_NativeBuffer *nativeBuffer)
```

**描述**

设置输入的NativeBuffer。

**系统能力：** SystemCapability.Multimedia.ImageEffect.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | 效果器指针。 |
| [OH_NativeBuffer](../apis-arkgraphics2d/capi-oh-nativebuffer-oh-nativebuffer.md) *nativeBuffer | 指向OH_NativeBuffer实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ImageEffect_ErrorCode](capi-image-effect-errors-h.md#imageeffect_errorcode) | EFFECT_SUCCESS：方法调用成功。<br>         EFFECT_ERROR_PARAM_INVALID：入参为空指针。 |

### OH_ImageEffect_SetOutputNativeBuffer()

```
ImageEffect_ErrorCode OH_ImageEffect_SetOutputNativeBuffer(OH_ImageEffect *imageEffect, OH_NativeBuffer *nativeBuffer)
```

**描述**

设置输出的NativeBuffer。

**系统能力：** SystemCapability.Multimedia.ImageEffect.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | 效果器指针。 |
| [OH_NativeBuffer](../apis-arkgraphics2d/capi-oh-nativebuffer-oh-nativebuffer.md) *nativeBuffer | 指向OH_NativeBuffer实例的指针，允许为空，当输入为空时渲染结果返回到输入的OH_NativeBuffer对象上。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ImageEffect_ErrorCode](capi-image-effect-errors-h.md#imageeffect_errorcode) | EFFECT_SUCCESS：方法调用成功。<br>         EFFECT_ERROR_PARAM_INVALID：入参为空指针。<br>          EFFECT_PARAM_ERROR：如果参数异常导致方法调用失败。 |

### OH_ImageEffect_SetInputUri()

```
ImageEffect_ErrorCode OH_ImageEffect_SetInputUri(OH_ImageEffect *imageEffect, const char *uri)
```

**描述**

设置输入的URI。

**系统能力：** SystemCapability.Multimedia.ImageEffect.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | 效果器指针。 |
| const char *uri | 图片URI（只支持Jpeg，Heif）。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ImageEffect_ErrorCode](capi-image-effect-errors-h.md#imageeffect_errorcode) | EFFECT_SUCCESS：方法调用成功。<br>         EFFECT_ERROR_PARAM_INVALID：入参为空指针。 |

### OH_ImageEffect_SetOutputUri()

```
ImageEffect_ErrorCode OH_ImageEffect_SetOutputUri(OH_ImageEffect *imageEffect, const char *uri)
```

**描述**

设置输出的URI。

**系统能力：** SystemCapability.Multimedia.ImageEffect.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | 效果器指针。 |
| const char *uri | 图片URI。输出URI的格式和输入保持一致，如果不支持Heif编码能力，则进行Jpeg编码。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ImageEffect_ErrorCode](capi-image-effect-errors-h.md#imageeffect_errorcode) | EFFECT_SUCCESS：方法调用成功。<br>         EFFECT_ERROR_PARAM_INVALID：入参为空指针。 |

### OH_ImageEffect_SetInputPicture()

```
ImageEffect_ErrorCode OH_ImageEffect_SetInputPicture(OH_ImageEffect *imageEffect, OH_PictureNative *picture)
```

**描述**

设置输入的Picture。

**系统能力：** SystemCapability.Multimedia.ImageEffect.Core

**起始版本：** 13


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | 效果器指针。 |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *picture | 指向OH_PictureNative实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ImageEffect_ErrorCode](capi-image-effect-errors-h.md#imageeffect_errorcode) | EFFECT_SUCCESS：方法调用成功。<br>         EFFECT_ERROR_PARAM_INVALID：入参为空指针。 |

### OH_ImageEffect_SetOutputPicture()

```
ImageEffect_ErrorCode OH_ImageEffect_SetOutputPicture(OH_ImageEffect *imageEffect, OH_PictureNative *picture)
```

**描述**

设置输出的Picture。

**系统能力：** SystemCapability.Multimedia.ImageEffect.Core

**起始版本：** 13


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | 效果器指针。 |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *picture | 指向OH_PictureNative实例的指针，允许为空，当输入为空时渲染结果返回到输入的OH_PictureNative对象上。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ImageEffect_ErrorCode](capi-image-effect-errors-h.md#imageeffect_errorcode) | EFFECT_SUCCESS：方法调用成功。<br>         EFFECT_ERROR_PARAM_INVALID：入参为空指针。<br>         EFFECT_PARAM_ERROR：如果参数异常导致方法调用失败。 |

### OH_ImageEffect_SetInputTextureId()

```
ImageEffect_ErrorCode OH_ImageEffect_SetInputTextureId(OH_ImageEffect *imageEffect, int32_t textureId,int32_t colorSpace)
```

**描述**

配置输入包含图片内容的纹理标识。

**系统能力：** SystemCapability.Multimedia.ImageEffect.Core

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | OH_ImageEffect结构体实例指针。 |
| int32_t textureId | 包含图片内容的纹理标识，纹理标识必须是有效的且绑定了GL_TEXTURE_2D类型的纹理。 |
| int32_t colorSpace | 图片对应的色彩空间。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ImageEffect_ErrorCode](capi-image-effect-errors-h.md#imageeffect_errorcode) | EFFECT_SUCCESS：方法调用成功。<br>         EFFECT_ERROR_PARAM_INVALID：入参为空指针或参数超出有效范围。<br>         EFFECT_PARAM_ERROR：参数缺失或参数错误。 |

### OH_ImageEffect_SetOutputTextureId()

```
ImageEffect_ErrorCode OH_ImageEffect_SetOutputTextureId(OH_ImageEffect *imageEffect, int32_t textureId)
```

**描述**

配置输出包含渲染后的纹理标识。

**系统能力：** SystemCapability.Multimedia.ImageEffect.Core

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | OH_ImageEffect结构体实例指针。 |
| int32_t textureId | 包含图片渲染后内容的纹理标识，纹理标识必须是一个有效的纹理。<br> 如果纹理标识未被绑定纹理图片，纹理标识会自动绑定GL_TEXTURE_2D类型；<br> 如果纹理标识已经被绑定纹理且尺寸不合适，结果可能会被裁剪或部分填充到此纹理上。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ImageEffect_ErrorCode](capi-image-effect-errors-h.md#imageeffect_errorcode) | EFFECT_SUCCESS：方法调用成功。<br>         EFFECT_ERROR_PARAM_INVALID：入参为空指针或参数超出有效范围。<br>         EFFECT_PARAM_ERROR：参数缺失或参数错误。 |

### OH_ImageEffect_Start()

```
ImageEffect_ErrorCode OH_ImageEffect_Start(OH_ImageEffect *imageEffect)
```

**描述**

启动效果器。

**系统能力：** SystemCapability.Multimedia.ImageEffect.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | 效果器指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ImageEffect_ErrorCode](capi-image-effect-errors-h.md#imageeffect_errorcode) | EFFECT_SUCCESS：方法调用成功。<br>         EFFECT_ERROR_PARAM_INVALID：入参为空指针。<br>         EFFECT_INPUT_OUTPUT_NOT_SUPPORTED：待处理输入、输出图像数据类型不一致。<br>         EFFECT_COLOR_SPACE_NOT_MATCH：输入、输出图像色彩空间不配置。<br>         EFFECT_ALLOCATE_MEMORY_FAILED：内存申请失败。 |

### OH_ImageEffect_Stop()

```
ImageEffect_ErrorCode OH_ImageEffect_Stop(OH_ImageEffect *imageEffect)
```

**描述**

停止生效效果。

**系统能力：** SystemCapability.Multimedia.ImageEffect.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | 效果器指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ImageEffect_ErrorCode](capi-image-effect-errors-h.md#imageeffect_errorcode) | EFFECT_SUCCESS：方法调用成功。<br>         EFFECT_ERROR_PARAM_INVALID：入参为空指针。 |

### OH_ImageEffect_Release()

```
ImageEffect_ErrorCode OH_ImageEffect_Release(OH_ImageEffect *imageEffect)
```

**描述**

释放OH_ImageEffect实例资源。

**系统能力：** SystemCapability.Multimedia.ImageEffect.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | 效果器指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ImageEffect_ErrorCode](capi-image-effect-errors-h.md#imageeffect_errorcode) | EFFECT_SUCCESS：方法调用成功。<br>         EFFECT_ERROR_PARAM_INVALID：入参为空指针。 |

### OH_ImageEffect_Save()

```
ImageEffect_ErrorCode OH_ImageEffect_Save(OH_ImageEffect *imageEffect, char **info)
```

**描述**

序列化效果器。

**系统能力：** SystemCapability.Multimedia.ImageEffect.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | 效果器指针。 |
| char **info | 指向char数组的指针，返回序列化JSON字符串。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ImageEffect_ErrorCode](capi-image-effect-errors-h.md#imageeffect_errorcode) | EFFECT_SUCCESS：方法调用成功。<br>         EFFECT_ERROR_PARAM_INVALID：入参为空指针。 |

### OH_ImageEffect_Restore()

```
OH_ImageEffect *OH_ImageEffect_Restore(const char *info)
```

**描述**

反序列化效果器。

**系统能力：** SystemCapability.Multimedia.ImageEffect.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *info | 序列化JSON字符串。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) * | 反序列化成功时返回OH_ImageEffect实例，否则返回空指针。 |


