# Image_PositionArea
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=efcee9a5da162db2b8fec2a8a54e6f913d17880b translatedAt=2026-11-06T02:01:15.022Z pushedAt=2026-11-12T05:59:30.759Z nl=1 -->

```c
typedef struct Image_PositionArea {...} Image_PositionArea
```

## Overview

The struct describes the area of image pixels to be read from or written to.

**Since**: 22

**Related module**: [Image_NativeModule](capi-image-nativemodule.md)

**Header file**: [image_common.h](capi-image-common-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint8_t *pixels | Image pixel data to read or write. For non-YUV pixels, only data in **BGRA_8888** format is supported. |
| size_t pixelsSize | Length of the pixel data, in bytes.|
| uint32_t offset | Offset for reading or writing data, in bytes.|
| uint32_t stride | Stride of the region, that is, the number of bytes occupied by each row of pixels. The value of **stride** must be greater than or equal to the value of **region.size.width** multiplied by 4.|
| [Image_Region](capi-image-nativemodule-image-region.md) region | Area for reading or writing. The region's width plus the X coordinate must not exceed the original image's width, and the region's height plus the Y coordinate must not exceed the original image's height.|


