# buffer_common.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @Flix-fangyang; @BruceXu; @ding-panyun-->
<!--Designer: @conan13234-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

## Overview

This file declares the common types used in the **NativeBuffer** module.

**File to include**: <native_buffer/buffer_common.h>

**Library**: libnative_buffer.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 12

**Related module**: [OH_NativeBuffer](capi-oh-nativebuffer.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_NativeBuffer_ColorXY](capi-oh-nativebuffer-oh-nativebuffer-colorxy.md) | OH_NativeBuffer_ColorXY | Describes the X and Y coordinates of the primary color.|
| [OH_NativeBuffer_Smpte2086](capi-oh-nativebuffer-oh-nativebuffer-smpte2086.md) | OH_NativeBuffer_Smpte2086 | Describes the SMPTE ST 2086 static metadata.|
| [OH_NativeBuffer_Cta861](capi-oh-nativebuffer-oh-nativebuffer-cta861.md) | OH_NativeBuffer_Cta861 | Describes the CTA-861.3 static metadata.|
| [OH_NativeBuffer_StaticMetadata](capi-oh-nativebuffer-oh-nativebuffer-staticmetadata.md) | OH_NativeBuffer_StaticMetadata | Describes the HDR static metadata.|

### Enumerated value

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_NativeBuffer_ColorSpace](#oh_nativebuffer_colorspace) | OH_NativeBuffer_ColorSpace | Defines an enum for the color spaces of an **OH_NativeBuffer** instance.|
| [OH_NativeBuffer_MetadataType](#oh_nativebuffer_metadatatype) | OH_NativeBuffer_MetadataType | Defines an enum for the **OH_NativeBuffer** image standards.|
| [OH_NativeBuffer_MetadataKey](#oh_nativebuffer_metadatakey) | OH_NativeBuffer_MetadataKey | Defines an enum for the key values of **OH_NativeBuffer** description information, such as HDR metadata and ROI metadata.|
| [OH_NativeBuffer_Format](#oh_nativebuffer_format) | OH_NativeBuffer_Format | Defines an enum for the **OH_NativeBuffer** formats.|
| [OH_NativeBuffer_TransformType](#oh_nativebuffer_transformtype) | OH_NativeBuffer_TransformType | Defines an enum for the conversion types of **OH_NativeBuffer**.|

## Enum Description

### OH_NativeBuffer_ColorSpace

```c
enum OH_NativeBuffer_ColorSpace
```

**Description**

Defines an enum for the color spaces of an **OH_NativeBuffer** instance.

This enum is moved from **native_buffer.h** to this header file since API version 12.

Before API version 12, use this enum only if **native_buffer.h** is referenced. From API version 12 onwards, this enum can be used properly whether **native_buffer.h** or **buffer_common.h** is referenced.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 11

| Value| Description|
| -- | -- |
| OH_COLORSPACE_NONE | No color space is available.|
| OH_COLORSPACE_BT601_EBU_FULL | The color gamut is BT601_P, the transfer function is BT709, the conversion matrix is BT601_P, and the data range is RANGE_FULL.|
| OH_COLORSPACE_BT601_SMPTE_C_FULL | The color gamut is BT601_N, the transfer function is BT709, the conversion matrix is BT601_N, and the data range is RANGE_FULL.|
| OH_COLORSPACE_BT709_FULL | The color gamut is BT709, the transfer function is BT709, the conversion matrix is BT709, and the data range is RANGE_FULL.|
| OH_COLORSPACE_BT2020_HLG_FULL | The color gamut is BT2020, the transfer function is HLG, the conversion matrix is BT2020, and the data range is RANGE_FULL.|
| OH_COLORSPACE_BT2020_PQ_FULL | The color gamut is BT2020, the transfer function is PQ, the conversion matrix is BT2020, and the data range is RANGE_FULL.|
| OH_COLORSPACE_BT601_EBU_LIMIT | The color gamut is BT601_P, the transfer function is BT709, the conversion matrix is BT601_P, and the data range is RANGE_LIMITED.|
| OH_COLORSPACE_BT601_SMPTE_C_LIMIT | The color gamut is BT601_N, the transfer function is BT709, the conversion matrix is BT601_N, and the data range is RANGE_LIMITED.|
| OH_COLORSPACE_BT709_LIMIT | The color gamut is BT709, the transfer function is BT709, the conversion matrix is BT709, and the data range is RANGE_LIMITED.|
| OH_COLORSPACE_BT2020_HLG_LIMIT | The color gamut is BT2020, the transfer function is HLG, the conversion matrix is BT2020, and the data range is RANGE_LIMITED.|
| OH_COLORSPACE_BT2020_PQ_LIMIT | The color gamut is BT2020, the transfer function is PQ, the conversion matrix is BT2020, and the data range is RANGE_LIMITED.|
| OH_COLORSPACE_SRGB_FULL | The color gamut is SRGB, the transfer function is SRGB, the conversion matrix is BT601_N, and the data range is RANGE_FULL.|
| OH_COLORSPACE_P3_FULL | The color gamut is P3_D65, the transfer function is SRGB, the conversion matrix is P3, and the data range is RANGE_FULL.|
| OH_COLORSPACE_P3_HLG_FULL | The color gamut is P3_D65, the transfer function is HLG, the conversion matrix is P3, and the data range is RANGE_FULL.|
| OH_COLORSPACE_P3_PQ_FULL | The color gamut is P3_D65, the transfer function is PQ, the conversion matrix is P3, and the data range is RANGE_FULL.|
| OH_COLORSPACE_ADOBERGB_FULL | The color gamut is ADOBERGB, the transfer function is ADOBERGB, the conversion matrix is ADOBERGB, and the data range is RANGE_FULL.|
| OH_COLORSPACE_SRGB_LIMIT | The color gamut is SRGB, the transfer function is SRGB, the conversion matrix is BT601_N, and the data range is RANGE_LIMITED.|
| OH_COLORSPACE_P3_LIMIT | The color gamut is P3_D65, the transfer function is SRGB, the conversion matrix is P3, and the data range is RANGE_LIMITED.|
| OH_COLORSPACE_P3_HLG_LIMIT | The color gamut is P3_D65, the transfer function is HLG, the conversion matrix is P3, and the data range is RANGE_LIMITED.|
| OH_COLORSPACE_P3_PQ_LIMIT | The color gamut is P3_D65, the transfer function is PQ, the conversion matrix is P3, and the data range is RANGE_LIMITED.|
| OH_COLORSPACE_ADOBERGB_LIMIT | The color gamut is ADOBERGB, the transfer function is ADOBERGB, the conversion matrix is ADOBERGB, and the data range is RANGE_LIMITED.|
| OH_COLORSPACE_LINEAR_SRGB | The color gamut is SRGB, and the transfer function is LINEAR.|
| OH_COLORSPACE_LINEAR_BT709 | It is equivalent to **OH_COLORSPACE_LINEAR_SRGB**.|
| OH_COLORSPACE_LINEAR_P3 | The color gamut is P3_D65, and the transfer function is LINEAR.|
| OH_COLORSPACE_LINEAR_BT2020 | The color gamut is BT2020, and the transfer function is LINEAR.|
| OH_COLORSPACE_DISPLAY_SRGB | It is equivalent to **OH_COLORSPACE_SRGB_FULL**.|
| OH_COLORSPACE_DISPLAY_P3_SRGB | It is equivalent to **OH_COLORSPACE_P3_FULL**.|
| OH_COLORSPACE_DISPLAY_P3_HLG | It is equivalent to **OH_COLORSPACE_P3_HLG_FULL**.|
| OH_COLORSPACE_DISPLAY_P3_PQ | It is equivalent to **OH_COLORSPACE_P3_PQ_FULL**.|
| OH_COLORSPACE_DISPLAY_BT2020_SRGB | The color gamut is BT2020, the transfer function is SRGB, the conversion matrix is BT2020, and the data range is RANGE_FULL.|
| OH_COLORSPACE_DISPLAY_BT2020_HLG | It is equivalent to **OH_COLORSPACE_BT2020_HLG_FULL**.|
| OH_COLORSPACE_DISPLAY_BT2020_PQ | It is equivalent to **OH_COLORSPACE_BT2020_PQ_FULL**.|

### OH_NativeBuffer_MetadataType

```c
enum OH_NativeBuffer_MetadataType
```

**Description**

Defines an enum for the **OH_NativeBuffer** image standards.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 12

| Value| Description|
| -- | -- |
| OH_VIDEO_HDR_HLG | Video HLG.|
| OH_VIDEO_HDR_HDR10 | Video HDR10.|
| OH_VIDEO_HDR_VIVID | Video HDR Vivid.|
| OH_IMAGE_HDR_VIVID_DUAL | Image HDR Vivid Dual.<br>**Since**: 22|
| OH_IMAGE_HDR_VIVID_SINGLE | Image HDR Vivid Single.<br>**Since**: 22|
| OH_IMAGE_HDR_ISO_DUAL | Image HDR ISO Dual.<br>**Since**: 23|
| OH_IMAGE_HDR_ISO_SINGLE | Image HDR ISO Single.<br>**Since**: 23|
| OH_VIDEO_NONE = -1 |  No metadata.<br>**Since**: 13|

### OH_NativeBuffer_MetadataKey

```c
enum OH_NativeBuffer_MetadataKey
```

**Description**

Defines an enum for the key values of **OH_NativeBuffer** description information, such as HDR metadata and ROI metadata.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 12

| Value| Description|
| -- | -- |
| OH_HDR_METADATA_TYPE | Metadata type. For details about the available options, see [OH_NativeBuffer_MetadataType](capi-buffer-common-h.md#oh_nativebuffer_metadatatype). **size** indicates the size of **OH_NativeBuffer_MetadataType**.|
| OH_HDR_STATIC_METADATA | Static metadata. For details about the available options, see [OH_NativeBuffer_StaticMetadata](capi-oh-nativebuffer-oh-nativebuffer-staticmetadata.md). **size** indicates the size of **OH_NativeBuffer_StaticMetadata**.|
| OH_HDR_DYNAMIC_METADATA | Dynamic metadata. For details about the available options, see the SEI byte stream in the video stream. The value range of **size** is 1-3000.|
| OH_REGION_OF_INTEREST_METADATA | ROI metadata of video encoding and decoding. The configuration format is as follows: Top1,Left1-Bottom1,Right1=QpOffset1;Top2,Left2-Bottom2,Right2=QpOffset2;<br>Each ROI box consists of the position information (**Top,Left-Bottom,Right**) and encoding quality offset information (**QpOffset**), and ends with a semicolon (;).<br>The encoding quality offset information of the ROI box can be defaulted. The default value is **-3**. The configuration example when the default value is used is as follows: **Top1,Left1-Bottom1,Right1;Top2,Left2-Bottom2,Right2;**<br>A maximum of six ROIs can be configured for each group of ROI metadata, and the total area of the ROIs cannot exceed 1/5 of the image.<br>This enumerated value can be called only through the [OH_NativeBuffer_SetMetadataValue()](capi-native-buffer-h.md#oh_nativebuffer_setmetadatavalue) API.<br>**Since**: 22|

### OH_NativeBuffer_Format

```c
enum OH_NativeBuffer_Format
```

**Description**

Defines an enum for the **OH_NativeBuffer** formats.

This enum is moved from **native_buffer.h** to this header file since API version 22.

Before API version 22, use this enum only if **native_buffer.h** is referenced. From API version 22 onwards, this enum can be used properly whether **native_buffer.h** or **buffer_common.h** is referenced.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 10

| Value| Description|
| -- | -- |
| NATIVEBUFFER_PIXEL_FMT_CLUT8 = 0 | CLUT8.<br>**Since**: 12|
| NATIVEBUFFER_PIXEL_FMT_CLUT1 | CLUT1.<br>**Since**: 12|
| NATIVEBUFFER_PIXEL_FMT_CLUT4 | CLUT4.<br>**Since**: 12|
| NATIVEBUFFER_PIXEL_FMT_RGB_565 = 3 | RGB565.|
| NATIVEBUFFER_PIXEL_FMT_RGBA_5658 | RGBA5658.|
| NATIVEBUFFER_PIXEL_FMT_RGBX_4444 | RGBX4444.|
| NATIVEBUFFER_PIXEL_FMT_RGBA_4444 | RGBA4444.|
| NATIVEBUFFER_PIXEL_FMT_RGB_444 | RGB444.|
| NATIVEBUFFER_PIXEL_FMT_RGBX_5551 | RGBX5551.|
| NATIVEBUFFER_PIXEL_FMT_RGBA_5551 | RGBA5551.|
| NATIVEBUFFER_PIXEL_FMT_RGB_555 | RGB555.|
| NATIVEBUFFER_PIXEL_FMT_RGBX_8888 | RGBX8888.|
| NATIVEBUFFER_PIXEL_FMT_RGBA_8888 | RGBA8888.|
| NATIVEBUFFER_PIXEL_FMT_RGB_888 | RGB888.|
| NATIVEBUFFER_PIXEL_FMT_BGR_565 | BGR565.|
| NATIVEBUFFER_PIXEL_FMT_BGRX_4444 | BGRX4444.|
| NATIVEBUFFER_PIXEL_FMT_BGRA_4444 | BGRA4444.|
| NATIVEBUFFER_PIXEL_FMT_BGRX_5551 | BGRX5551.|
| NATIVEBUFFER_PIXEL_FMT_BGRA_5551 | BGRA5551.|
| NATIVEBUFFER_PIXEL_FMT_BGRX_8888 | BGRX8888.|
| NATIVEBUFFER_PIXEL_FMT_BGRA_8888 | BGRA8888.|
| NATIVEBUFFER_PIXEL_FMT_YUV_422_I | YUV422 interleaved.<br>**Since**: 12|
| NATIVEBUFFER_PIXEL_FMT_YCBCR_422_SP | YCbCr422 semi-planar format.<br>**Since**: 12|
| NATIVEBUFFER_PIXEL_FMT_YCRCB_422_SP | YCrCb422 semi-planar.<br>**Since**: 12|
| NATIVEBUFFER_PIXEL_FMT_YCBCR_420_SP | YCbCr420 semi-planar.<br>**Since**: 12|
| NATIVEBUFFER_PIXEL_FMT_YCRCB_420_SP | YCrCb420 semi-planar.<br>**Since**: 12|
| NATIVEBUFFER_PIXEL_FMT_YCBCR_422_P | YCbCr422 planar.<br>**Since**: 12|
| NATIVEBUFFER_PIXEL_FMT_YCRCB_422_P | YCrCb422 planar.<br>**Since**: 12|
| NATIVEBUFFER_PIXEL_FMT_YCBCR_420_P | YCbCr420 planar.<br>**Since**: 12|
| NATIVEBUFFER_PIXEL_FMT_YCRCB_420_P | YCrCb420 planar.<br>**Since**: 12|
| NATIVEBUFFER_PIXEL_FMT_YUYV_422_PKG | YUYV422 packed.<br>**Since**: 12|
| NATIVEBUFFER_PIXEL_FMT_UYVY_422_PKG | UYVY422 packed.<br>**Since**: 12|
| NATIVEBUFFER_PIXEL_FMT_YVYU_422_PKG | YVYU422 packed.<br>**Since**: 12|
| NATIVEBUFFER_PIXEL_FMT_VYUY_422_PKG | VYUY422 packed.<br>**Since**: 12|
| NATIVEBUFFER_PIXEL_FMT_RGBA_1010102 | RGBA_1010102 packed.<br>**Since**: 12|
| NATIVEBUFFER_PIXEL_FMT_YCBCR_P010 | YCBCR420 semi-planar 10-bit packed.<br>**Since**: 12|
| NATIVEBUFFER_PIXEL_FMT_YCRCB_P010 | YCRCB420 semi-planar 10-bit packed.<br>**Since**: 12|
| NATIVEBUFFER_PIXEL_FMT_RAW10 | Raw 10-bit packed.<br>**Since**: 12|
| NATIVEBUFFER_PIXEL_FMT_BLOB | BLOB.<br>**Since**: 15|
| NATIVEBUFFER_PIXEL_FMT_RGBA16_FLOAT | RGBA16 float.<br>**Since**: 15|
| NATIVEBUFFER_PIXEL_FMT_Y8 = 40 | Y8.<br>**Since**: 20|
| NATIVEBUFFER_PIXEL_FMT_Y16 = 41 | Y16.<br>**Since**: 20|
| NATIVEBUFFER_PIXEL_FMT_VENDER_MASK = 0X7FFF0000 | Vender mask.<br>**Since**: 12|
| NATIVEBUFFER_PIXEL_FMT_BUTT = 0X7FFFFFFF | Invalid format.|

### OH_NativeBuffer_TransformType

```c
enum OH_NativeBuffer_TransformType
```

**Description**

Defines an enum for the conversion types of **OH_NativeBuffer**.

This enum is moved from **native_buffer.h** to this header file since API version 22.

Before API version 22, use this enum only if **native_buffer.h** is referenced. From API version 22 onwards, this enum can be used properly whether **native_buffer.h** or **buffer_common.h** is referenced.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 12

| Value| Description|
| -- | -- |
| NATIVEBUFFER_ROTATE_NONE = 0 | No rotation.|
| NATIVEBUFFER_ROTATE_90 | Rotates by 90 degrees.|
| NATIVEBUFFER_ROTATE_180 | Rotates by 180 degrees.|
| NATIVEBUFFER_ROTATE_270 | Rotates by 270 degrees.|
| NATIVEBUFFER_FLIP_H | Flips horizontally.|
| NATIVEBUFFER_FLIP_V | Flips vertically.|
| NATIVEBUFFER_FLIP_H_ROT90 | Flips horizontally and rotates by 90 degrees.|
| NATIVEBUFFER_FLIP_V_ROT90 | Flips vertically and rotates by 90 degrees.|
| NATIVEBUFFER_FLIP_H_ROT180 | Flips horizontally and rotates by 180 degrees.|
| NATIVEBUFFER_FLIP_V_ROT180 | Flips vertically and rotates by 180 degrees.|
| NATIVEBUFFER_FLIP_H_ROT270 | Flips horizontally and rotates by 270 degrees.|
| NATIVEBUFFER_FLIP_V_ROT270 | Flips vertically and rotates by 270 degrees.|
