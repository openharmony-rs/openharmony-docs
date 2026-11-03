# OhosImageSource

```c
struct OhosImageSource {...}
```

## Overview

Defines the input resource of the image source. It is obtained by calling [OH_ImageSource_Create](capi-image-source-mdk-h.md#oh_imagesource_create). Only one type of resource is accepted at a time.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 10

**Deprecated**: 11

**Related module**: [Image](capi-others-image.md)

**Header file**: [image_source_mdk.h](capi-image-source-mdk-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char* uri = nullptr | Pointer to the image source URI. Only a file URI or Base64 URI is accepted.<br>**Since**: 10 |
| size_t uriSize = 0 | Length of the image source URI.<br>**Since**: 10 |
| int32_t fd = -1 | Descriptor of the image source.<br>**Since**: 10 |
| uint8_t* buffer = nullptr | Pointer to the image source buffer. Only a formatted packet buffer or Base64 buffer is accepted.<br>**Since**: 10 |
| size_t bufferSize = 0 | Size of the image source buffer.<br>**Since**: 10 |
| char* uri | Pointer to the image source URI. Only a file URI or Base64 URI is accepted.<br>**Since**: 10 |
| size_t uriSize | Length of the image source URI.<br>**Since**: 10 |
| int32_t fd | Descriptor of the image source.<br>**Since**: 10 |
| uint8_t* buffer | Pointer to the image source buffer. Only a formatted packet buffer or Base64 buffer is accepted.<br>**Since**: 10 |
| size_t bufferSize | Size of the image source buffer.<br>**Since**: 10 |


