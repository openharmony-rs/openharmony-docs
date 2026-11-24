# OhosImageComponent

```c
struct OhosImageComponent {...}
```

## Overview

Defines the image composition information.

<!--Device-struct OhosImageComponent {...}--><!--Device-struct OhosImageComponent {...}-End-->

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 10

**Related module**: [Image](capi-image-kit-image.md)

**Header file**: [image_mdk.h](capi-image-mdk-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t* byteBuffer | Buffer that stores the pixel data.<br><!--Device-uint8_t* byteBuffer--><!--Device-uint8_t* byteBuffer-End--> |
| size_t size | Size of the pixel data in the memory.<br><!--Device-size_t size--><!--Device-size_t size-End--> |
| int32_t componentType | Type of the pixel data.<br><!--Device-int32_t componentType--><!--Device-int32_t componentType-End--> |
| int32_t rowStride | Row stride of the pixel data.<br><!--Device-int32_t rowStride--><!--Device-int32_t rowStride-End--> |
| int32_t pixelStride | Pixel stride of the pixel data<br><!--Device-int32_t pixelStride--><!--Device-int32_t pixelStride-End--> |


