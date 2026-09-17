# buffer_common.h

## Overview

Defines the common types for native buffer.

**Library**: libnative_buffer.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 9

**Related module**: [OH_NativeBuffer](capi-oh-nativebuffer.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_NativeBuffer_ColorXY](capi-oh-nativebuffer-oh-nativebuffer-colorxy.md) | OH_NativeBuffer_ColorXY | Indicates the color x and y. |
| [OH_NativeBuffer_Smpte2086](capi-oh-nativebuffer-oh-nativebuffer-smpte2086.md) | OH_NativeBuffer_Smpte2086 | Indicates the smpte2086 metadata. |
| [OH_NativeBuffer_Cta861](capi-oh-nativebuffer-oh-nativebuffer-cta861.md) | OH_NativeBuffer_Cta861 | Indicates the cta861.3 metadata. |
| [OH_NativeBuffer_StaticMetadata](capi-oh-nativebuffer-oh-nativebuffer-staticmetadata.md) | OH_NativeBuffer_StaticMetadata | Indicates the HDR static metadata. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_NativeBuffer_ColorSpace](#oh_nativebuffer_colorspace) | OH_NativeBuffer_ColorSpace | Indicates the color space of a native buffer. Move from native_buffer.h to native_common.h |
| [OH_NativeBuffer_MetadataType](#oh_nativebuffer_metadatatype) | OH_NativeBuffer_MetadataType | Indicates the HDR metadata type of a native buffer. |
| [OH_NativeBuffer_MetadataKey](#oh_nativebuffer_metadatakey) | OH_NativeBuffer_MetadataKey | Indicates the descriptive information of a native buffer, such as HDR metadata, ROI metadata, etc. |
| [OH_NativeBuffer_Format](#oh_nativebuffer_format) | OH_NativeBuffer_Format | Indicates the format of a native buffer. |
| [OH_NativeBuffer_TransformType](#oh_nativebuffer_transformtype) | OH_NativeBuffer_TransformType | Indicates the transform type of a native buffer. |
| [OH_NativeBuffer_VideoDimensionType](#oh_nativebuffer_videodimensiontype) | OH_NativeBuffer_VideoDimensionType | Indicates video dimension type. |
| [OH_NativeBuffer_3D_MetadataKey](#oh_nativebuffer_3d_metadatakey) | OH_NativeBuffer_3D_MetadataKey | Indicates the descriptive 3D information of a native buffer. |

## Enum type description

### OH_NativeBuffer_ColorSpace

```c
enum OH_NativeBuffer_ColorSpace
```

**Description**

Indicates the color space of a native buffer. Move from native_buffer.h to native_common.h

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 12

| Enum item | Description |
| -- | -- |
| OH_COLORSPACE_NONE | None color space |
| OH_COLORSPACE_BT601_EBU_FULL | COLORPRIMARIES_BT601_P \| (TRANSFUNC_BT709 << 8) \| (MATRIX_BT601_P << 16) \| (RANGE_FULL << 21) |
| OH_COLORSPACE_BT601_SMPTE_C_FULL | COLORPRIMARIES_BT601_N \| (TRANSFUNC_BT709 << 8) \| (MATRIX_BT601_N << 16) \| (RANGE_FULL << 21) |
| OH_COLORSPACE_BT709_FULL | COLORPRIMARIES_BT709 \| (TRANSFUNC_BT709 << 8) \| (MATRIX_BT709 << 16) \| (RANGE_FULL << 21) |
| OH_COLORSPACE_BT2020_HLG_FULL | COLORPRIMARIES_BT2020 \| (TRANSFUNC_HLG << 8) \| (MATRIX_BT2020 << 16) \| (RANGE_FULL << 21) |
| OH_COLORSPACE_BT2020_PQ_FULL | COLORPRIMARIES_BT2020 \| (TRANSFUNC_PQ << 8) \| (MATRIX_BT2020 << 16) \| (RANGE_FULL << 21) |
| OH_COLORSPACE_BT601_EBU_LIMIT | COLORPRIMARIES_BT601_P \| (TRANSFUNC_BT709 << 8) \| (MATRIX_BT601_P << 16) \| (RANGE_LIMITED << 21) |
| OH_COLORSPACE_BT601_SMPTE_C_LIMIT | COLORPRIMARIES_BT601_N \| (TRANSFUNC_BT709 << 8) \| (MATRIX_BT601_N << 16) \| (RANGE_LIMITED << 21) |
| OH_COLORSPACE_BT709_LIMIT | COLORPRIMARIES_BT709 \| (TRANSFUNC_BT709 << 8) \| (MATRIX_BT709 << 16) \| (RANGE_LIMITED << 21) |
| OH_COLORSPACE_BT2020_HLG_LIMIT | COLORPRIMARIES_BT2020 \| (TRANSFUNC_HLG << 8) \| (MATRIX_BT2020 << 16) \| (RANGE_LIMITED << 21) |
| OH_COLORSPACE_BT2020_PQ_LIMIT | COLORPRIMARIES_BT2020 \| (TRANSFUNC_PQ << 8) \| (MATRIX_BT2020 << 16) \| (RANGE_LIMITED << 21) |
| OH_COLORSPACE_SRGB_FULL | COLORPRIMARIES_SRGB \| (TRANSFUNC_SRGB << 8) \| (MATRIX_BT601_N << 16) \| (RANGE_FULL << 21) |
| OH_COLORSPACE_P3_FULL | COLORPRIMARIES_P3_D65 \| (TRANSFUNC_SRGB << 8) \| (MATRIX_P3 << 16) \| (RANGE_FULL << 21) |
| OH_COLORSPACE_P3_HLG_FULL | COLORPRIMARIES_P3_D65 \| (TRANSFUNC_HLG << 8) \| (MATRIX_P3 << 16) \| (RANGE_FULL << 21) |
| OH_COLORSPACE_P3_PQ_FULL | COLORPRIMARIES_P3_D65 \| (TRANSFUNC_PQ << 8) \| (MATRIX_P3 << 16) \| (RANGE_FULL << 21) |
| OH_COLORSPACE_ADOBERGB_FULL | COLORPRIMARIES_ADOBERGB \| (TRANSFUNC_ADOBERGB << 8) \| (MATRIX_ADOBERGB << 16) \| (RANGE_FULL << 21) |
| OH_COLORSPACE_SRGB_LIMIT | COLORPRIMARIES_SRGB \| (TRANSFUNC_SRGB << 8) \| (MATRIX_BT601_N << 16) \| (RANGE_LIMITED << 21) |
| OH_COLORSPACE_P3_LIMIT | COLORPRIMARIES_P3_D65 \| (TRANSFUNC_SRGB << 8) \| (MATRIX_P3 << 16) \| (RANGE_LIMITED << 21) |
| OH_COLORSPACE_P3_HLG_LIMIT | COLORPRIMARIES_P3_D65 \| (TRANSFUNC_HLG << 8) \| (MATRIX_P3 << 16) \| (RANGE_LIMITED << 21) |
| OH_COLORSPACE_P3_PQ_LIMIT | COLORPRIMARIES_P3_D65 \| (TRANSFUNC_PQ << 8) \| (MATRIX_P3 << 16) \| (RANGE_LIMITED << 21) |
| OH_COLORSPACE_ADOBERGB_LIMIT | COLORPRIMARIES_ADOBERGB \| (TRANSFUNC_ADOBERGB << 8) \| (MATRIX_ADOBERGB << 16) \| (RANGE_LIMITED << 21) |
| OH_COLORSPACE_LINEAR_SRGB | COLORPRIMARIES_SRGB \| (TRANSFUNC_LINEAR << 8) |
| OH_COLORSPACE_LINEAR_BT709 | equal to OH_COLORSPACE_LINEAR_SRGB |
| OH_COLORSPACE_LINEAR_P3 | COLORPRIMARIES_P3_D65 \| (TRANSFUNC_LINEAR << 8) |
| OH_COLORSPACE_LINEAR_BT2020 | COLORPRIMARIES_BT2020 \| (TRANSFUNC_LINEAR << 8) |
| OH_COLORSPACE_DISPLAY_SRGB | equal to OH_COLORSPACE_SRGB_FULL |
| OH_COLORSPACE_DISPLAY_P3_SRGB | equal to OH_COLORSPACE_P3_FULL |
| OH_COLORSPACE_DISPLAY_P3_HLG | equal to OH_COLORSPACE_P3_HLG_FULL |
| OH_COLORSPACE_DISPLAY_P3_PQ | equal to OH_COLORSPACE_P3_PQ_FULL |
| OH_COLORSPACE_DISPLAY_BT2020_SRGB | COLORPRIMARIES_BT2020 \| (TRANSFUNC_SRGB << 8) \| (MATRIX_BT2020 << 16) \| (RANGE_FULL << 21) |
| OH_COLORSPACE_DISPLAY_BT2020_HLG | equal to OH_COLORSPACE_BT2020_HLG_FULL |
| OH_COLORSPACE_DISPLAY_BT2020_PQ | equal to OH_COLORSPACE_BT2020_PQ_FULL |
| OH_COLORSPACE_BT2020_LOG_FULL |  |
| OH_COLORSPACE_BT2020_LOG_LIMIT |  |

### OH_NativeBuffer_MetadataType

```c
enum OH_NativeBuffer_MetadataType
```

**Description**

Indicates the HDR metadata type of a native buffer.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 12

| Enum item | Description |
| -- | -- |
| OH_VIDEO_HDR_HLG | HLG |
| OH_VIDEO_HDR_HDR10 | HDR10 |
| OH_VIDEO_HDR_VIVID | HDR VIVID |
| OH_IMAGE_HDR_VIVID_DUAL |  |
| OH_IMAGE_HDR_VIVID_SINGLE |  |
| OH_IMAGE_HDR_ISO_DUAL |  |
| OH_IMAGE_HDR_ISO_SINGLE |  |
| OH_VIDEO_NONE = -1 |  |

### OH_NativeBuffer_MetadataKey

```c
enum OH_NativeBuffer_MetadataKey
```

**Description**

Indicates the descriptive information of a native buffer, such as HDR metadata, ROI metadata, etc.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 12

| Enum item | Description |
| -- | -- |
| OH_HDR_METADATA_TYPE | value: OH_NativeBuffer_MetadataType |
| OH_HDR_STATIC_METADATA | value: OH_NativeBuffer_StaticMetadata |
| OH_HDR_DYNAMIC_METADATA | byte stream of SEI in video stream |
| OH_REGION_OF_INTEREST_METADATA |  |

### OH_NativeBuffer_Format

```c
enum OH_NativeBuffer_Format
```

**Description**

Indicates the format of a native buffer.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 10

| Enum item | Description |
| -- | -- |
| NATIVEBUFFER_PIXEL_FMT_CLUT8 = 0 |  |
| NATIVEBUFFER_PIXEL_FMT_CLUT1 |  |
| NATIVEBUFFER_PIXEL_FMT_CLUT4 |  |
| NATIVEBUFFER_PIXEL_FMT_RGB_565 = 3 | RGB565 format |
| NATIVEBUFFER_PIXEL_FMT_RGBA_5658 | RGBA5658 format |
| NATIVEBUFFER_PIXEL_FMT_RGBX_4444 | RGBX4444 format |
| NATIVEBUFFER_PIXEL_FMT_RGBA_4444 | RGBA4444 format |
| NATIVEBUFFER_PIXEL_FMT_RGB_444 | RGB444 format |
| NATIVEBUFFER_PIXEL_FMT_RGBX_5551 | RGBX5551 format |
| NATIVEBUFFER_PIXEL_FMT_RGBA_5551 | RGBA5551 format |
| NATIVEBUFFER_PIXEL_FMT_RGB_555 | RGB555 format |
| NATIVEBUFFER_PIXEL_FMT_RGBX_8888 | RGBX8888 format |
| NATIVEBUFFER_PIXEL_FMT_RGBA_8888 | RGBA8888 format |
| NATIVEBUFFER_PIXEL_FMT_RGB_888 | RGB888 format |
| NATIVEBUFFER_PIXEL_FMT_BGR_565 | BGR565 format |
| NATIVEBUFFER_PIXEL_FMT_BGRX_4444 | BGRX4444 format |
| NATIVEBUFFER_PIXEL_FMT_BGRA_4444 | BGRA4444 format |
| NATIVEBUFFER_PIXEL_FMT_BGRX_5551 | BGRX5551 format |
| NATIVEBUFFER_PIXEL_FMT_BGRA_5551 | BGRA5551 format |
| NATIVEBUFFER_PIXEL_FMT_BGRX_8888 | BGRX8888 format |
| NATIVEBUFFER_PIXEL_FMT_BGRA_8888 | BGRA8888 format |
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
| NATIVEBUFFER_PIXEL_FMT_BUTT = 0X7FFFFFFF | Invalid pixel format |

### OH_NativeBuffer_TransformType

```c
enum OH_NativeBuffer_TransformType
```

**Description**

Indicates the transform type of a native buffer.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 12

| Enum item | Description |
| -- | -- |
| NATIVEBUFFER_ROTATE_NONE = 0 | No rotation |
| NATIVEBUFFER_ROTATE_90 | Rotation by 90 degrees |
| NATIVEBUFFER_ROTATE_180 | Rotation by 180 degrees |
| NATIVEBUFFER_ROTATE_270 | Rotation by 270 degrees |
| NATIVEBUFFER_FLIP_H | Flip horizontally |
| NATIVEBUFFER_FLIP_V | Flip vertically |
| NATIVEBUFFER_FLIP_H_ROT90 | Flip horizontally and rotate 90 degrees |
| NATIVEBUFFER_FLIP_V_ROT90 | Flip vertically and rotate 90 degrees |
| NATIVEBUFFER_FLIP_H_ROT180 | Flip horizontally and rotate 180 degrees |
| NATIVEBUFFER_FLIP_V_ROT180 | Flip vertically and rotate 180 degrees |
| NATIVEBUFFER_FLIP_H_ROT270 | Flip horizontally and rotate 270 degrees |
| NATIVEBUFFER_FLIP_V_ROT270 | Flip vertically and rotate 270 degrees |

### OH_NativeBuffer_VideoDimensionType

```c
enum OH_NativeBuffer_VideoDimensionType
```

**Description**

Indicates video dimension type.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_VIDEO_DIM_TYPE_2D = 0 | 2-dimension video |
| OH_VIDEO_DIM_TYPE_3D_SBS | 3-dimension video, format: side by side |
| OH_VIDEO_DIM_TYPE_3D_TAB | 3-dimension video, format: top and bottom |
| OH_VIDEO_DIM_TYPE_BUTT | Invalid video dimension type |

### OH_NativeBuffer_3D_MetadataKey

```c
enum OH_NativeBuffer_3D_MetadataKey
```

**Description**

Indicates the descriptive 3D information of a native buffer.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_VIDEO_DIM_TYPE | value: the video dimension type of the native buffer |


