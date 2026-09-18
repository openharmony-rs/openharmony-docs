# OH_NativeBuffer_Planes

```c
typedef struct OH_NativeBuffer_Planes {...} OH_NativeBuffer_Planes
```

## Overview

Holds all image planes.

**Since**: 12

**Related module**: [OH_NativeBuffer](capi-oh-nativebuffer.md)

**Header file**: [native_buffer.h](capi-native-buffer-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t planeCount | Number of distinct planes. |
| [OH_NativeBuffer_Plane](capi-oh-nativebuffer-oh-nativebuffer-plane.md) planes[4] | Array of image planes. |


