# OH_ImageBufferData
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=6390c7092d7c521347e2f8699be33d9cd3458eb0 translatedAt=2026-11-06T02:02:32.116Z pushedAt=2026-11-12T06:04:12.642Z nl=1 -->

```c
typedef struct {...} OH_ImageBufferData
```

## Overview

**OH_ImageBufferData** is an image data struct encapsulated at the native layer. To obtain an **OH_ImageBufferData** object, use the [OH_ImageNative_GetBufferData](capi-image-native-h.md#oh_imagenative_getbufferdata) function.<br> The struct stores a shallow copy of the original image data. After the original data is released, do not perform any read or write operations on the pointers in this struct; otherwise, undefined behavior may occur.

**Since**: 23

**Related module**: [Image_NativeModule](capi-image-nativemodule.md)

**Header file**: [image_native.h](capi-image-native-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t *rowStride | Array of row strides of image color components, in pixels.|
| int32_t *pixelStride | Array of pixel pitches of image color components, in pixels.|
| int32_t numStride | Array length.|
| size_t bufferSize | Buffer size, in bytes.|
| OH_NativeBuffer *nativeBuffer | Pointer to the **OH_NativeBuffer** object of the image.|


