# OH_NativeBuffer_Plane

```c
typedef struct OH_NativeBuffer_Plane {...} OH_NativeBuffer_Plane
```

## Overview

Holds info for a single image plane.

**Since**: 12

**Related module**: [OH_NativeBuffer](capi-oh-nativebuffer.md)

**Header file**: [native_buffer.h](capi-native-buffer-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint64_t offset | Offset in bytes of plane. |
| uint32_t rowStride | Distance in bytes from the first value of one row of the image to the first value of the next row. |
| uint32_t columnStride | Distance in bytes from the first value of one column of the image to the first value of the next column. |


