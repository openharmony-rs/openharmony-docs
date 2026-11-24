# OH_NativeBuffer_Plane

```c
typedef struct OH_NativeBuffer_Plane {...} OH_NativeBuffer_Plane
```

## Overview

Holds info for a single image plane.

<!--Device-typedef struct OH_NativeBuffer_Plane {...} OH_NativeBuffer_Plane--><!--Device-typedef struct OH_NativeBuffer_Plane {...} OH_NativeBuffer_Plane-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 12

**Related module**: [OH_NativeBuffer](capi-arkgraphics2d-oh-nativebuffer.md)

**Header file**: [native_buffer.h](capi-native-buffer-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint64_t offset | Offset in bytes of plane.<br><!--Device-uint64_t offset--><!--Device-uint64_t offset-End--> |
| uint32_t rowStride | Distance in bytes from the first value of one row of the image to the first value of the next row.<br><!--Device-uint32_t rowStride--><!--Device-uint32_t rowStride-End--> |
| uint32_t columnStride | Distance in bytes from the first value of one column of the image to the first value of the next column.<br><!--Device-uint32_t columnStride--><!--Device-uint32_t columnStride-End--> |


