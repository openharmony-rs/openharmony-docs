# OH_NativeBuffer_Plane
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @Felix-fangyang-->
<!--Designer: @conan13234-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=eb202bbb7c66b7aa5aaa1b04a6221f6189d3d8ff translatedAt=2026-11-04T10:34:28.899Z pushedAt=2026-11-04T10:36:42.099Z nl=1 -->

```c
typedef struct {...} OH_NativeBuffer_Plane
```
## Overview

This struct describes the plane information of an image.

**Since**: 12

**Related module**: [OH_NativeBuffer](capi-oh-nativebuffer.md)

**Header file**: [native_buffer.h](capi-native-buffer-h.md)

## Summary

### Member Variables

| Name                 | Description                                                      |
| --------------------- | ---------------------------------------------------------- |
| uint64_t offset       | Offset of the image plane, in bytes.                            |
| uint32_t rowStride    | Distance from the first value in an image row to the first value in the next row, in bytes.|
| uint32_t columnStride | Distance from the first value in an image column to the first value in the next column, in bytes.|

