# buffer_common.h

## 概述

提供NativeBuffer模块的公共类型定义。

**库：** libnative_buffer.so

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeBuffer

**起始版本：** 12

**相关模块：** [OH_NativeBuffer](capi-arkgraphics2d-oh-nativebuffer.md)

## 汇总

### 结构体

| 名称 | 描述 |
| -- | -- |
| [OH_NativeBuffer_ColorXY](capi-oh-nativebuffer-oh-nativebuffer-colorxy.md) | 表示基色的X和Y坐标。 |
| [OH_NativeBuffer_Smpte2086](capi-oh-nativebuffer-oh-nativebuffer-smpte2086.md) | 表示smpte2086静态元数据。 |
| [OH_NativeBuffer_Cta861](capi-oh-nativebuffer-oh-nativebuffer-cta861.md) | 表示CTA-861.3静态元数据。 |
| [OH_NativeBuffer_StaticMetadata](capi-oh-nativebuffer-oh-nativebuffer-staticmetadata.md) | 表示HDR静态元数据。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_NativeBuffer_ColorSpace](#oh_nativebuffer_colorspace) | OH_NativeBuffer_ColorSpace | OH_NativeBuffer的颜色空间。 Move from native_buffer.h to native_common.h |
| [OH_NativeBuffer_MetadataType](#oh_nativebuffer_metadatatype) | OH_NativeBuffer_MetadataType | OH_NativeBuffer的图像标准。 |
| [OH_NativeBuffer_MetadataKey](#oh_nativebuffer_metadatakey) | OH_NativeBuffer_MetadataKey | 表示OH_NativeBuffer的描述信息的键值，如HDR元数据，ROI元数据等。 |
| [OH_NativeBuffer_Format](#oh_nativebuffer_format) | OH_NativeBuffer_Format | OH_NativeBuffer格式的枚举。 |
| [OH_NativeBuffer_TransformType](#oh_nativebuffer_transformtype) | OH_NativeBuffer_TransformType | OH_NativeBuffer转换类型的枚举。 |
| [OH_NativeBuffer_VideoDimensionType](#oh_nativebuffer_videodimensiontype) | OH_NativeBuffer_VideoDimensionType | 视频维度类型枚举。 |
| [OH_NativeBuffer_3D_MetadataKey](#oh_nativebuffer_3d_metadatakey) | OH_NativeBuffer_3D_MetadataKey | 表示NativeBuffer的3D元数据枚举属性。 |

## 枚举类型说明

### OH_NativeBuffer_ColorSpace

```c
enum OH_NativeBuffer_ColorSpace
```

**描述：**

OH_NativeBuffer的颜色空间。 Move from native_buffer.h to native_common.h

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
| OH_COLORSPACE_BT2020_LOG_FULL | COLORPRIMARIES_BT2020 \\| (TRANSFUNC_PRIV_LOG << 8) \\| (MATRIX_BT2020 << 16) \\| (RANGE_FULL << 21)<br>**起始版本：** 26.0.0 |
| OH_COLORSPACE_BT2020_LOG_LIMIT | COLORPRIMARIES_BT2020 \\| (TRANSFUNC_PRIV_LOG << 8) \\| (MATRIX_BT2020 << 16) \\| (RANGE_LIMITED << 21)<br>**起始版本：** 26.0.0 |

### OH_NativeBuffer_MetadataType

```c
enum OH_NativeBuffer_MetadataType
```

**描述：**

OH_NativeBuffer的图像标准。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeBuffer

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| OH_VIDEO_HDR_HLG | 视频HLG。 |
| OH_VIDEO_HDR_HDR10 | 视频HDR10。 |
| OH_VIDEO_HDR_VIVID | 视频HDR VIVID。 |
| OH_IMAGE_HDR_VIVID_DUAL | 图片HDR VIVID DUAL。<br>**起始版本：** 22 |
| OH_IMAGE_HDR_VIVID_SINGLE | 图片HDR VIVID SINGLE。<br>**起始版本：** 22 |
| OH_IMAGE_HDR_ISO_DUAL | 图片HDR ISO DUAL。<br>**起始版本：** 23 |
| OH_IMAGE_HDR_ISO_SINGLE | 图片HDR ISO SINGLE。<br>**起始版本：** 23 |
| OH_VIDEO_NONE = -1 | 无元数据。<br>**起始版本：** 13 |

### OH_NativeBuffer_MetadataKey

```c
enum OH_NativeBuffer_MetadataKey
```

**描述：**

表示OH_NativeBuffer的描述信息的键值，如HDR元数据，ROI元数据等。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeBuffer

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| OH_HDR_METADATA_TYPE | value：OH_NativeBuffer_MetadataType类型。 |
| OH_HDR_STATIC_METADATA | value：OH_NativeBuffer_StaticMetadata类型。 |
| OH_HDR_DYNAMIC_METADATA | 视频流中SEI的字节流。 |
| OH_REGION_OF_INTEREST_METADATA | 感兴趣区域（ROI）元数据用于在视频编码中配置ROI功能。值类型为字符串， 格式为"Top1,Left1-Bottom1,Right1[=Params1];Top2,Left2-Bottom2,Right2[=Params2];"。 每个"Top,Left-Bottom,Right"表示一个ROI的坐标信息。 "[=Params]"为可选内容。 "[=Params]"的格式因版本而异： 1. 26.0.0版本之前：仅支持一个表示量化参数偏移的int32_t值（例如"=QpOffset"）。 2. 26.0.0版本及之后：额外支持并推荐使用键值对格式， 使用逗号分隔的键值对（例如"=dqp:-6,slb:1"）。 支持的键： - "dqp"：量化参数偏移。 - "slb"：语义标签。取值必须与[OH_VideoMetadataRoiSemanticLabel](../../apis-avcodec-kit/c-apis/capi-native-avcodec-videobase-h.md#oh_videometadataroisemanticlabel)对应。 如果完全省略"=Params"，如"Top1,Left1-Bottom1,Right1;Top2,Left2-Bottom2,Right2=dqp:-6;"， 编码器将对第一个ROI使用默认参数进行ROI编码，并对第二个ROI使用指定参数。 请注意，可同时应用的ROI数量不得超过六个，且总面积不得超过图像总面积的五分之一。<br>**起始版本：** 22 |

### OH_NativeBuffer_Format

```c
enum OH_NativeBuffer_Format
```

**描述：**

OH_NativeBuffer格式的枚举。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeBuffer

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| NATIVEBUFFER_PIXEL_FMT_CLUT8 = 0 | CLUT8格式。<br>**起始版本：** 12 |
| NATIVEBUFFER_PIXEL_FMT_CLUT1 | CLUT1格式。<br>**起始版本：** 12 |
| NATIVEBUFFER_PIXEL_FMT_CLUT4 | CLUT4格式。<br>**起始版本：** 12 |
| NATIVEBUFFER_PIXEL_FMT_RGB_565 = 3 | RGB565格式。 |
| NATIVEBUFFER_PIXEL_FMT_RGBA_5658 | RGBA5658格式。 |
| NATIVEBUFFER_PIXEL_FMT_RGBX_4444 | RGBX4444格式。 |
| NATIVEBUFFER_PIXEL_FMT_RGBA_4444 | RGBA4444格式。 |
| NATIVEBUFFER_PIXEL_FMT_RGB_444 | RGB444格式。 |
| NATIVEBUFFER_PIXEL_FMT_RGBX_5551 | RGBX5551格式。 |
| NATIVEBUFFER_PIXEL_FMT_RGBA_5551 | RGBA5551格式。 |
| NATIVEBUFFER_PIXEL_FMT_RGB_555 | RGB555格式。 |
| NATIVEBUFFER_PIXEL_FMT_RGBX_8888 | RGBX8888格式。 |
| NATIVEBUFFER_PIXEL_FMT_RGBA_8888 | RGBA8888格式。 |
| NATIVEBUFFER_PIXEL_FMT_RGB_888 | RGB888格式。 |
| NATIVEBUFFER_PIXEL_FMT_BGR_565 | BGR565格式。 |
| NATIVEBUFFER_PIXEL_FMT_BGRX_4444 | BGRX4444格式。 |
| NATIVEBUFFER_PIXEL_FMT_BGRA_4444 | BGRA4444格式。 |
| NATIVEBUFFER_PIXEL_FMT_BGRX_5551 | BGRX5551格式。 |
| NATIVEBUFFER_PIXEL_FMT_BGRA_5551 | BGRA5551格式。 |
| NATIVEBUFFER_PIXEL_FMT_BGRX_8888 | BGRX8888格式。 |
| NATIVEBUFFER_PIXEL_FMT_BGRA_8888 | BGRA8888格式。 |
| NATIVEBUFFER_PIXEL_FMT_YUV_422_I | YUV422 interleaved 格式。<br>**起始版本：** 12 |
| NATIVEBUFFER_PIXEL_FMT_YCBCR_422_SP | YCBCR422 semi-planar 格式。<br>**起始版本：** 12 |
| NATIVEBUFFER_PIXEL_FMT_YCRCB_422_SP | YCRCB422 semi-planar 格式。<br>**起始版本：** 12 |
| NATIVEBUFFER_PIXEL_FMT_YCBCR_420_SP | YCBCR420 semi-planar 格式。<br>**起始版本：** 12 |
| NATIVEBUFFER_PIXEL_FMT_YCRCB_420_SP | YCRCB420 semi-planar 格式。<br>**起始版本：** 12 |
| NATIVEBUFFER_PIXEL_FMT_YCBCR_422_P | YCBCR422 planar 格式。<br>**起始版本：** 12 |
| NATIVEBUFFER_PIXEL_FMT_YCRCB_422_P | YCRCB422 planar 格式。<br>**起始版本：** 12 |
| NATIVEBUFFER_PIXEL_FMT_YCBCR_420_P | YCBCR420 planar 格式。<br>**起始版本：** 12 |
| NATIVEBUFFER_PIXEL_FMT_YCRCB_420_P | YCRCB420 planar 格式。<br>**起始版本：** 12 |
| NATIVEBUFFER_PIXEL_FMT_YUYV_422_PKG | YUYV422 packed 格式。<br>**起始版本：** 12 |
| NATIVEBUFFER_PIXEL_FMT_UYVY_422_PKG | UYVY422 packed 格式。<br>**起始版本：** 12 |
| NATIVEBUFFER_PIXEL_FMT_YVYU_422_PKG | YVYU422 packed 格式。<br>**起始版本：** 12 |
| NATIVEBUFFER_PIXEL_FMT_VYUY_422_PKG | VYUY422 packed 格式。<br>**起始版本：** 12 |
| NATIVEBUFFER_PIXEL_FMT_RGBA_1010102 | RGBA_1010102 packed 格式。<br>**起始版本：** 12 |
| NATIVEBUFFER_PIXEL_FMT_YCBCR_P010 | YCBCR420 semi-planar 10bit packed 格式。<br>**起始版本：** 12 |
| NATIVEBUFFER_PIXEL_FMT_YCRCB_P010 | YCRCB420 semi-planar 10bit packed 格式。<br>**起始版本：** 12 |
| NATIVEBUFFER_PIXEL_FMT_RAW10 | Raw 10bit packed 格式。<br>**起始版本：** 12 |
| NATIVEBUFFER_PIXEL_FMT_BLOB | BLOB格式。<br>**起始版本：** 15 |
| NATIVEBUFFER_PIXEL_FMT_RGBA16_FLOAT | RGBA16 float格式。<br>**起始版本：** 15 |
| NATIVEBUFFER_PIXEL_FMT_Y8 = 40 | Y8格式。<br>**起始版本：** 20 |
| NATIVEBUFFER_PIXEL_FMT_Y16 = 41 | Y16格式。<br>**起始版本：** 20 |
| NATIVEBUFFER_PIXEL_FMT_VENDER_MASK = 0X7FFF0000 | vender mask 格式。<br>**起始版本：** 12 |
| } OH_NativeBuffer_Format; | NATIVEBUFFER_PIXEL_FMT_BUTT = 0X7FFFFFFF          /** 无效格式 |

### OH_NativeBuffer_TransformType

```c
enum OH_NativeBuffer_TransformType
```

**描述：**

OH_NativeBuffer转换类型的枚举。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeBuffer

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| NATIVEBUFFER_ROTATE_NONE = 0 | 不旋转 |
| NATIVEBUFFER_ROTATE_90 | 旋转90度 |
| NATIVEBUFFER_ROTATE_180 | 旋转180度 |
| NATIVEBUFFER_ROTATE_270 | 旋转270度 |
| NATIVEBUFFER_FLIP_H | 水平翻转 |
| NATIVEBUFFER_FLIP_V | 垂直翻转 |
| NATIVEBUFFER_FLIP_H_ROT90 | 水平翻转并旋转90度 |
| NATIVEBUFFER_FLIP_V_ROT90 | 垂直翻转并旋转90度 |
| NATIVEBUFFER_FLIP_H_ROT180 | 水平翻转并旋转180度 |
| NATIVEBUFFER_FLIP_V_ROT180 | 垂直翻转并旋转180度 |
| NATIVEBUFFER_FLIP_H_ROT270 | 水平翻转并旋转270度 |
| NATIVEBUFFER_FLIP_V_ROT270 | 垂直翻转并旋转270度 |

### OH_NativeBuffer_VideoDimensionType

```c
enum OH_NativeBuffer_VideoDimensionType
```

**描述：**

视频维度类型枚举。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeBuffer

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| OH_VIDEO_DIM_TYPE_2D = 0 | 二维视频 |
| OH_VIDEO_DIM_TYPE_3D_SBS | 三维视频，格式：左右排列 |
| OH_VIDEO_DIM_TYPE_3D_TAB | 三维视频，格式：上下排列 |
| OH_VIDEO_DIM_TYPE_BUTT | 无效的视频维度类型 |

### OH_NativeBuffer_3D_MetadataKey

```c
enum OH_NativeBuffer_3D_MetadataKey
```

**描述：**

表示NativeBuffer的3D元数据枚举属性。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeBuffer

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| OH_VIDEO_DIM_TYPE | value: NativeBuffer的视频维度类型 |


