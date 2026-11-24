# OH_ImageBufferData

```c
typedef struct OH_ImageBufferData {...} OH_ImageBufferData
```

## Overview

[OH_ImageBufferData](capi-image-nativemodule-oh-imagebufferdata.md) is the image data struct encapsulated at the native layer. To obtain an [OH_ImageBufferData](capi-image-nativemodule-oh-imagebufferdata.md) object, call [OH_ImageNative_GetBufferData](capi-image-native-h.md#oh_imagenative_getbufferdata).<br> The struct stores the shallow copy of the original image data. Once the original data is released, no read or write operations should be performed on the pointers within this struct; otherwise, undefined behavior will occur.

<!--Device-struct OH_ImageBufferData {...}--><!--Device-struct OH_ImageBufferData {...}-End-->

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 23

**Related module**: [Image_NativeModule](capi-image-kit-image-nativemodule.md)

**Header file**: [image_native.h](capi-image-native-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t *rowStride | rowStride of each component.<br><!--Device-int32_t *rowStride--><!--Device-int32_t *rowStride-End--> |
| int32_t *pixelStride | pixelStride of each component.<br><!--Device-int32_t *pixelStride--><!--Device-int32_t *pixelStride-End--> |
| int32_t numStride | number of strides.<br><!--Device-int32_t numStride--><!--Device-int32_t numStride-End--> |
| size_t bufferSize | byte length of the buffer<br><!--Device-size_t bufferSize--><!--Device-size_t bufferSize-End--> |
| [OH_NativeBuffer](../../apis-arkgraphics2d/c-apis/capi-oh-nativebuffer-oh-nativebuffer.md) *nativeBuffer | native buffer of the image.<br><!--Device-OH_NativeBuffer *nativeBuffer--><!--Device-OH_NativeBuffer *nativeBuffer-End--> |


