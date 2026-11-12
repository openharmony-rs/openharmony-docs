# OhosImageSourceUpdateData
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=a71c0a82e5ac85b488b13af278b7bfd23da513e9 translatedAt=2026-11-06T02:06:42.877Z pushedAt=2026-11-12T06:20:31.636Z nl=1 -->

```c
struct OhosImageSourceUpdateData {...}
```

## Overview

The struct describes the update data option of the image source. It is obtained by calling [OH_ImageSource_UpdateData](capi-image-source-mdk-h.md#oh_imagesource_updatedata).

**Since**: 10

**Related module**: [Image](capi-image.md)

**Header file**: [image_source_mdk.h](capi-image-source-mdk-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint8_t* buffer = nullptr | Buffer for the image source update data. This setting is applicable only to the C++ compilation environment. |
| size_t bufferSize = 0 | Size of the buffer for the image source update data. This setting is applicable only to the C++ compilation environment. |
| uint32_t offset = 0 | Start of the buffer for the image source update data. This setting is applicable only to the C++ compilation environment. |
| uint32_t updateLength = 0 | Length of the update data in the buffer for the image source update data. This setting is applicable only to the C++ compilation environment. |
| int8_t isCompleted = 0 | Whether the image source update data is completed in this section. This setting is applicable only to the C++ compilation environment. |
| uint8_t* buffer | Buffer for the image source update data. This setting is applicable only to the C compilation environment. |
| size_t bufferSize | Size of the buffer for the image source update data. This setting is applicable only to the C compilation environment. |
| uint32_t offset | Start of the buffer for the image source update data. This setting is applicable only to the C compilation environment. |
| uint32_t updateLength | Length of the update data in the buffer for the image source update data. This setting is applicable only to the C compilation environment. |
| int8_t isCompleted | Whether the image source update data is completed in this section. This setting is applicable only to the C compilation environment. |

