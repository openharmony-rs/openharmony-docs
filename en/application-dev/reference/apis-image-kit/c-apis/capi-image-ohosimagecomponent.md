# OhosImageComponent

```c
struct OhosImageComponent {...}
```

## Overview

Defines the image composition information.

**Since**: 10

**Related module**: [Image](capi-image.md)

**Header file**: [image_mdk.h](capi-image-mdk-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t* byteBuffer | Buffer that stores the pixel data. |
| size_t size | Size of the pixel data in the memory. |
| int32_t componentType | Type of the pixel data. |
| int32_t rowStride | Row stride of the pixel data. |
| int32_t pixelStride | Pixel stride of the pixel data |


