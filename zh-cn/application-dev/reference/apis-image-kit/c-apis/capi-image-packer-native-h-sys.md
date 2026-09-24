# image_packer_native.h（系统接口）

## 概述

图片编码API。

**库：** libimage_packer.so

**系统能力：** SystemCapability.Multimedia.Image.ImagePacker

**起始版本：** 12

**系统接口：** 此接口为系统接口。

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [Image_ErrorCode OH_PackingOptions_GetNeedsPackDfxData(OH_PackingOptions *options, bool *needsPackDfxData)（系统接口）](#oh_packingoptions_getneedspackdfxdata) | 获取OH_PackingOptions结构体中的needsPackDfxData参数。<br>**系统接口：** 此接口为系统接口。 |
| [Image_ErrorCode OH_PackingOptions_SetNeedsPackDfxData(OH_PackingOptions *options, bool needsPackDfxData)（系统接口）](#oh_packingoptions_setneedspackdfxdata) | 设置OH_PackingOptions结构体中的needsPackDfxData参数。<br>**系统接口：** 此接口为系统接口。 |
| [Image_ErrorCode OH_PackingOptions_SetC2paDataSize(OH_PackingOptions *options, uint32_t c2paDataSize)（系统接口）](#oh_packingoptions_setc2padatasize) | 设置OH_PackingOptions结构体中的C2PA数据大小，默认值为0，表示不预留空间。<br>**系统接口：** 此接口为系统接口。 |
| [Image_ErrorCode OH_PackingOptions_GetC2paDataSize(const OH_PackingOptions *options, uint32_t *c2paDataSize)（系统接口）](#oh_packingoptions_getc2padatasize) | 获取OH_PackingOptions结构体中的C2PA数据大小。<br>**系统接口：** 此接口为系统接口。 |

## 函数说明

### OH_PackingOptions_GetNeedsPackDfxData()

```c
Image_ErrorCode OH_PackingOptions_GetNeedsPackDfxData(OH_PackingOptions *options, bool *needsPackDfxData)
```

**描述：**

获取OH_PackingOptions结构体中的needsPackDfxData参数。

**系统能力：** SystemCapability.Multimedia.Image.ImagePacker

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PackingOptions](capi-image-nativemodule-oh-packingoptions.md) *options | 指向OH_PackingOptions结构体的指针。 |
| bool *needsPackDfxData | 图像DFX数据是否需要编码。true表示图像DFX数据需要编码，false表示图像DFX数据不需要编码。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | <ul>      <br><li>IMAGE_SUCCESS：执行成功。</li>      <br><li>202：非系统应用程序调用该接口则返回此错误码。</li>      <br><li>IMAGE_PACKER_INVALID_PARAMETER：options或needsPackDfxData为空指针。</li>      <br></ul> |

### OH_PackingOptions_SetNeedsPackDfxData()

```c
Image_ErrorCode OH_PackingOptions_SetNeedsPackDfxData(OH_PackingOptions *options, bool needsPackDfxData)
```

**描述：**

设置OH_PackingOptions结构体中的needsPackDfxData参数。

**系统能力：** SystemCapability.Multimedia.Image.ImagePacker

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PackingOptions](capi-image-nativemodule-oh-packingoptions.md) *options | 指向OH_PackingOptions结构体的指针。 |
| bool needsPackDfxData | 图像DFX数据是否需要编码。true表示图像DFX数据需要编码，false表示图像DFX数据不需要编码。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | <ul>      <br><li>IMAGE_SUCCESS：执行成功。</li>      <br><li>202：非系统应用程序调用该接口则返回此错误码。</li>      <br><li>IMAGE_PACKER_INVALID_PARAMETER：options为空指针。</li>      <br></ul> |

### OH_PackingOptions_SetC2paDataSize()

```c
Image_ErrorCode OH_PackingOptions_SetC2paDataSize(OH_PackingOptions *options, uint32_t c2paDataSize)
```

**描述：**

设置OH_PackingOptions结构体中的C2PA数据大小，默认值为0，表示不预留空间。

**系统能力：** SystemCapability.Multimedia.Image.ImagePacker

**起始版本：** 26.0.1

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PackingOptions](capi-image-nativemodule-oh-packingoptions.md) *options | [in] 指向OH_PackingOptions结构体的指针，不能为NULL。 |
| uint32_t c2paDataSize | [in] C2PA数据预留空间大小，单位为字节。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | <ul>           <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) 操作成功。</li>          <li>202 非系统应用程序调用该接口。</li>          <li>[IMAGE_PACKER_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) options为NULL。</li>          </ul> |

### OH_PackingOptions_GetC2paDataSize()

```c
Image_ErrorCode OH_PackingOptions_GetC2paDataSize(const OH_PackingOptions *options, uint32_t *c2paDataSize)
```

**描述：**

获取OH_PackingOptions结构体中的C2PA数据大小。

**系统能力：** SystemCapability.Multimedia.Image.ImagePacker

**起始版本：** 26.0.1

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_PackingOptions](capi-image-nativemodule-oh-packingoptions.md) *options | [in] 指向OH_PackingOptions结构体的指针，不能为NULL。 |
| uint32_t *c2paDataSize | [out] 指向C2PA数据大小的指针，单位为字节，不能为NULL。 如果函数执行失败，c2paDataSize指向的内容保持不变。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | <ul>           <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) 操作成功。</li>          <li>202 非系统应用程序调用该接口。</li>          <li>[IMAGE_PACKER_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) options或c2paDataSize为NULL。</li>          </ul> |


