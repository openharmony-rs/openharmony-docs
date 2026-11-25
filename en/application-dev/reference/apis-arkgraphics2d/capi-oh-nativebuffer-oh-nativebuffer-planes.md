# OH_NativeBuffer_Planes
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @Felix-fangyang-->
<!--Designer: @conan13234-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=1f370dd3425411b659f906071e53860b94f0e2f1 translatedAt=2026-11-04T10:34:40.526Z pushedAt=2026-11-04T10:35:59.643Z nl=1 -->

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

