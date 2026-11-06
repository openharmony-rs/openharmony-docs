# OH_NativeBuffer_Plane

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @Felix-fangyang-->
<!--Designer: @conan13234-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=e8f70545487753bf02035ac39cc6f1df5bb66337 translatedAt=2026-08-24T09:18:23.953Z pushedAt=2026-08-25T07:20:47.325Z -->

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