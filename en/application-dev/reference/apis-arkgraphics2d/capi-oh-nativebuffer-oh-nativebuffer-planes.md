# OH_NativeBuffer_Planes

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @Felix-fangyang-->
<!--Designer: @conan13234-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=094ced2c1714888f81b48ee277d1e52615f35dc2 translatedAt=2026-08-24T09:18:32.344Z pushedAt=2026-08-25T07:20:57.344Z -->

```c
typedef struct {...} OH_NativeBuffer_Planes
```

## Overview

This struct describes the plane information of images in an **OH_NativeBuffer** instance.

**Since**: 12

**Related module**: [OH_NativeBuffer](capi-oh-nativebuffer.md)

**Header file**: [native_buffer.h](capi-native-buffer-h.md)

## Summary

### Member Variables

| Name                                                        | Description                  |
| ------------------------------------------------------------ | ---------------------- |
| uint32_t planeCount                                          | Number of planes.      |
| [OH_NativeBuffer_Plane](capi-oh-nativebuffer-oh-nativebuffer-plane.md) planes[4] | Array holding the plane information of each image.|