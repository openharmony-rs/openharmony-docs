# buffer_common.h

## 概述

提供NativeBuffer模块的公共类型定义。

**库：** libnative_buffer.so

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeBuffer

**起始版本：** 12

**相关模块：** [OH_NativeBuffer](capi-oh-nativebuffer.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_NativeBuffer_ColorXY](capi-oh-nativebuffer-oh-nativebuffer-colorxy.md) | OH_NativeBuffer_ColorXY | 表示基色的X和Y坐标。 |
| [OH_NativeBuffer_Smpte2086](capi-oh-nativebuffer-oh-nativebuffer-smpte2086.md) | OH_NativeBuffer_Smpte2086 | 表示smpte2086静态元数据。 |
| [OH_NativeBuffer_Cta861](capi-oh-nativebuffer-oh-nativebuffer-cta861.md) | OH_NativeBuffer_Cta861 | 表示CTA-861.3静态元数据。 |
| [OH_NativeBuffer_StaticMetadata](capi-oh-nativebuffer-oh-nativebuffer-staticmetadata.md) | OH_NativeBuffer_StaticMetadata | 表示HDR静态元数据。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_NativeBuffer_ColorSpace](#oh_nativebuffer_colorspace) | OH_NativeBuffer_ColorSpace | OH_NativeBuffer的颜色空间。Move from native_buffer.h to native_common.h |
| [OH_NativeBuffer_MetadataKey](#oh_nativebuffer_metadatakey) | OH_NativeBuffer_MetadataKey | 表示OH_NativeBuffer的描述信息的键值，如HDR元数据，ROI元数据等。 |
| [OH_NativeBuffer_Format](#oh_nativebuffer_format) | OH_NativeBuffer_Format | OH_NativeBuffer格式的枚举。 |
| [OH_NativeBuffer_TransformType](#oh_nativebuffer_transformtype) | OH_NativeBuffer_TransformType | OH_NativeBuffer转换类型的枚举。 |

## 枚举类型说明

### OH_NativeBuffer_ColorSpace

```c
enum OH_NativeBuffer_ColorSpace
```

**描述**

OH_NativeBuffer的颜色空间。Move from native_buffer.h to native_common.h

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeBuffer

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| OH_COLORSPACE_NONE | 无颜色空间。 |
| OH_COLORSPACE_BT601_EBU_FULL | 色域范围为BT601_P，传递函数为BT709，转换矩阵为BT601_P，数据范围为RANGE_FULL。 |
| OH_COLORSPACE_BT601_SMPTE_C_FULL | 色域范围为BT601_N，传递函数为BT709，转换矩阵为BT601_N，数据范围为RANGE_FULL。 |
| OH_COLORSPACE_BT709_FULL | 色域范围为BT709，传递函数为BT709，转换矩阵为BT709，数据范围为RANGE_FULL。 |
| OH_COLORSPACE_BT2020_HLG_FULL | 色域范围为BT2020，传递函数为HLG，转换矩阵为BT2020，数据范围为RANGE_FULL。 |
| OH_COLORSPACE_BT2020_PQ_FULL | 色域范围为BT2020，传递函数为PQ，转换矩阵为BT2020，数据范围为RANGE_FULL。 |
| OH_COLORSPACE_BT601_EBU_LIMIT | 色域范围为BT601_P，传递函数为BT709，转换矩阵为BT601_P，数据范围为RANGE_LIMITED。 |
| OH_COLORSPACE_BT601_SMPTE_C_LIMIT | 色域范围为BT601_N，传递函数为BT709，转换矩阵为BT601_N，数据范围为RANGE_LIMITED。 |
| OH_COLORSPACE_BT709_LIMIT | 色域范围为BT709，传递函数为BT709，转换矩阵为BT709，数据范围为RANGE_LIMITED。 |
| OH_COLORSPACE_BT2020_HLG_LIMIT | 色域范围为BT2020，传递函数为HLG，转换矩阵为BT2020，数据范围为RANGE_LIMITED。 |
| OH_COLORSPACE_BT2020_PQ_LIMIT | 色域范围为BT2020，传递函数为PQ，转换矩阵为BT2020，数据范围为RANGE_LIMITED。 |
| OH_COLORSPACE_SRGB_FULL | 色域范围为SRGB，传递函数为SRGB，转换矩阵为BT601_N，数据范围为RANGE_FULL。 |
| OH_COLORSPACE_P3_FULL | 色域范围为P3_D65，传递函数为SRGB，转换矩阵为P3，数据范围为RANGE_FULL。 |
| OH_COLORSPACE_P3_HLG_FULL | 色域范围为P3_D65，传递函数为HLG，转换矩阵为P3，数据范围为RANGE_FULL。 |
| OH_COLORSPACE_P3_PQ_FULL | 色域范围为P3_D65，传递函数为PQ，转换矩阵为P3，数据范围为RANGE_FULL。 |
| OH_COLORSPACE_ADOBERGB_FULL | 色域范围为ADOBERGB，传递函数为ADOBERGB，转换矩阵为ADOBERGB，数据范围为RANGE_FULL。 |
| OH_COLORSPACE_SRGB_LIMIT | 色域范围为SRGB，传递函数为SRGB，转换矩阵为BT601_N，数据范围为RANGE_LIMITED。 |
| OH_COLORSPACE_P3_LIMIT | 色域范围为P3_D65，传递函数为SRGB，转换矩阵为P3，数据范围为RANGE_LIMITED。 |
| OH_COLORSPACE_P3_HLG_LIMIT | 色域范围为P3_D65，传递函数为HLG，转换矩阵为P3，数据范围为RANGE_LIMITED。 |
| OH_COLORSPACE_P3_PQ_LIMIT | 色域范围为P3_D65，传递函数为PQ，转换矩阵为P3，数据范围为RANGE_LIMITED。 |
| OH_COLORSPACE_ADOBERGB_LIMIT | 色域范围为ADOBERGB，传递函数为ADOBERGB，转换矩阵为ADOBERGB，数据范围为RANGE_LIMITED。 |
| OH_COLORSPACE_LINEAR_SRGB | 色域范围为SRGB，传递函数为LINEAR。 |
| OH_COLORSPACE_LINEAR_BT709 | 等同于 OH_COLORSPACE_LINEAR_SRGB。 |
| OH_COLORSPACE_LINEAR_P3 | 色域范围为P3_D65，传递函数为LINEAR。 |
| OH_COLORSPACE_LINEAR_BT2020 | 色域范围为BT2020，传递函数为LINEAR。 |
| OH_COLORSPACE_DISPLAY_SRGB | 等同于OH_COLORSPACE_SRGB_FULL。 |
| OH_COLORSPACE_DISPLAY_P3_SRGB | 等同于OH_COLORSPACE_P3_FULL。 |
| OH_COLORSPACE_DISPLAY_P3_HLG | 等同于OH_COLORSPACE_P3_HLG_FULL。 |
| OH_COLORSPACE_DISPLAY_P3_PQ | 等同于OH_COLORSPACE_P3_PQ_FULL。 |
| OH_COLORSPACE_DISPLAY_BT2020_SRGB | 色域范围为BT2020，传递函数为SRGB，转换矩阵为BT2020，数据范围为RANGE_FULL。 |
| OH_COLORSPACE_DISPLAY_BT2020_HLG | 等同于 OH_COLORSPACE_BT2020_HLG_FULL。 |
| OH_COLORSPACE_DISPLAY_BT2020_PQ | 等同于OH_COLORSPACE_BT2020_PQ_FULL。 |
| OH_COLORSPACE_BT2020_LOG_FULL |  |
| OH_COLORSPACE_BT2020_LOG_LIMIT |  |

### OH_NativeBuffer_MetadataKey

```c
enum OH_NativeBuffer_MetadataKey
```

**描述**

表示OH_NativeBuffer的描述信息的键值，如HDR元数据，ROI元数据等。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeBuffer

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| OH_HDR_METADATA_TYPE | value: OH_NativeBuffer_MetadataType |
| OH_HDR_STATIC_METADATA | value: OH_NativeBuffer_StaticMetadata |
| OH_HDR_DYNAMIC_METADATA | byte stream of SEI in video stream |
| OH_REGION_OF_INTEREST_METADATA |  |

### OH_NativeBuffer_Format

```c
enum OH_NativeBuffer_Format
```

**描述**

OH_NativeBuffer格式的枚举。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeBuffer

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| NATIVEBUFFER_PIXEL_FMT_CLUT8 = 0 |  |
| NATIVEBUFFER_PIXEL_FMT_CLUT1 |  |
| NATIVEBUFFER_PIXEL_FMT_CLUT4 |  |
| NATIVEBUFFER_PIXEL_FMT_RGBA_5658,                 /// < RGBA5658 format */ |  |
| NATIVEBUFFER_PIXEL_FMT_RGBX_4444,                 /// < RGBX4444 format */ |  |
| NATIVEBUFFER_PIXEL_FMT_RGBA_4444,                 /// < RGBA4444 format */ |  |
| NATIVEBUFFER_PIXEL_FMT_RGB_444,                   /// < RGB444 format */ |  |
| NATIVEBUFFER_PIXEL_FMT_RGBX_5551,                 /// < RGBX5551 format */ |  |
| NATIVEBUFFER_PIXEL_FMT_RGBA_5551,                 /// < RGBA5551 format */ |  |
| NATIVEBUFFER_PIXEL_FMT_RGB_555,                   /// < RGB555 format */ |  |
| NATIVEBUFFER_PIXEL_FMT_RGBX_8888,                 /// < RGBX8888 format */ |  |
| NATIVEBUFFER_PIXEL_FMT_RGBA_8888,                 /// < RGBA8888 format */ |  |
| NATIVEBUFFER_PIXEL_FMT_RGB_888,                   /// < RGB888 format */ |  |
| NATIVEBUFFER_PIXEL_FMT_BGR_565,                   /// < BGR565 format */ |  |
| NATIVEBUFFER_PIXEL_FMT_BGRX_4444,                 /// < BGRX4444 format */ |  |
| NATIVEBUFFER_PIXEL_FMT_BGRA_4444,                 /// < BGRA4444 format */ |  |
| NATIVEBUFFER_PIXEL_FMT_BGRX_5551,                 /// < BGRX5551 format */ |  |
| NATIVEBUFFER_PIXEL_FMT_BGRA_5551,                 /// < BGRA5551 format */ |  |
| NATIVEBUFFER_PIXEL_FMT_BGRX_8888,                 /// < BGRX8888 format */ |  |
| NATIVEBUFFER_PIXEL_FMT_BGRA_8888,                 /// < BGRA8888 format */ |  |
| /** |  |
| NATIVEBUFFER_PIXEL_FMT_YUV_422_I |  |
| NATIVEBUFFER_PIXEL_FMT_YCBCR_422_SP |  |
| NATIVEBUFFER_PIXEL_FMT_YCRCB_422_SP |  |
| NATIVEBUFFER_PIXEL_FMT_YCBCR_420_SP |  |
| NATIVEBUFFER_PIXEL_FMT_YCRCB_420_SP |  |
| NATIVEBUFFER_PIXEL_FMT_YCBCR_422_P |  |
| NATIVEBUFFER_PIXEL_FMT_YCRCB_422_P |  |
| NATIVEBUFFER_PIXEL_FMT_YCBCR_420_P |  |
| NATIVEBUFFER_PIXEL_FMT_YCRCB_420_P |  |
| NATIVEBUFFER_PIXEL_FMT_YUYV_422_PKG |  |
| NATIVEBUFFER_PIXEL_FMT_UYVY_422_PKG |  |
| NATIVEBUFFER_PIXEL_FMT_YVYU_422_PKG |  |
| NATIVEBUFFER_PIXEL_FMT_VYUY_422_PKG |  |
| NATIVEBUFFER_PIXEL_FMT_RGBA_1010102 |  |
| NATIVEBUFFER_PIXEL_FMT_YCBCR_P010 |  |
| NATIVEBUFFER_PIXEL_FMT_YCRCB_P010 |  |
| NATIVEBUFFER_PIXEL_FMT_RAW10 |  |
| NATIVEBUFFER_PIXEL_FMT_BLOB |  |
| NATIVEBUFFER_PIXEL_FMT_RGBA16_FLOAT |  |
| NATIVEBUFFER_PIXEL_FMT_Y8 = 40 |  |
| NATIVEBUFFER_PIXEL_FMT_Y16 = 41 |  |
| NATIVEBUFFER_PIXEL_FMT_VENDER_MASK = 0X7FFF0000 |  |
| } OH_NativeBuffer_Format; |  |

### OH_NativeBuffer_TransformType

```c
enum OH_NativeBuffer_TransformType
```

**描述**

OH_NativeBuffer转换类型的枚举。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeBuffer

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| NATIVEBUFFER_ROTATE_90,               /**< 旋转90度 */ | NATIVEBUFFER_ROTATE_NONE = 0,         /**< 不旋转 |
| NATIVEBUFFER_ROTATE_180,              /**< 旋转180度 */ | NATIVEBUFFER_ROTATE_90,               /**< 旋转90度 |
| NATIVEBUFFER_ROTATE_270,              /**< 旋转270度 */ | NATIVEBUFFER_ROTATE_180,              /**< 旋转180度 |
| NATIVEBUFFER_FLIP_H,                  /**< 水平翻转 */ | NATIVEBUFFER_ROTATE_270,              /**< 旋转270度 |
| NATIVEBUFFER_FLIP_V,                  /**< 垂直翻转 */ | NATIVEBUFFER_FLIP_H,                  /**< 水平翻转 |
| NATIVEBUFFER_FLIP_H_ROT90,            /**< 水平翻转并旋转90度 */ | NATIVEBUFFER_FLIP_V,                  /**< 垂直翻转 |
| NATIVEBUFFER_FLIP_V_ROT90,            /**< 垂直翻转并旋转90度 */ | NATIVEBUFFER_FLIP_H_ROT90,            /**< 水平翻转并旋转90度 |
| NATIVEBUFFER_FLIP_H_ROT180,           /**< 水平翻转并旋转180度 */ | NATIVEBUFFER_FLIP_V_ROT90,            /**< 垂直翻转并旋转90度 |
| NATIVEBUFFER_FLIP_V_ROT180,           /**< 垂直翻转并旋转180度 */ | NATIVEBUFFER_FLIP_H_ROT180,           /**< 水平翻转并旋转180度 |
| NATIVEBUFFER_FLIP_H_ROT270,           /**< 水平翻转并旋转270度 */ | NATIVEBUFFER_FLIP_V_ROT180,           /**< 垂直翻转并旋转180度 |
| NATIVEBUFFER_FLIP_V_ROT270,           /**< 垂直翻转并旋转270度 */ | NATIVEBUFFER_FLIP_H_ROT270,           /**< 水平翻转并旋转270度 |
| } OH_NativeBuffer_TransformType; | NATIVEBUFFER_FLIP_V_ROT270,           /**< 垂直翻转并旋转270度 |


