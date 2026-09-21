# OH_ImageBufferData

```c
typedef struct OH_ImageBufferData {...} OH_ImageBufferData
```

## Overview

{@link OH_ImageBufferData} is the image data struct encapsulated at the native layer. To obtain an {@link OH_ImageBufferData}<br>object, call {@link OH_ImageNative_GetBufferData}.<br> The struct stores the shallow copy of the original image data. Once the original data is released, no read or write operations should be performed on the pointers within this struct; otherwise, undefined behavior will occur.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 23

**Related module**: [Image_NativeModule](capi-image-nativemodule.md)

**Header file**: [image_native.h](capi-image-native-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t *rowStride | rowStride of each component. |
| int32_t *pixelStride | pixelStride of each component. |
| int32_t numStride | number of strides. |
| size_t bufferSize | byte length of the buffer |
| OH_NativeBuffer *nativeBuffer | native buffer of the image. |


