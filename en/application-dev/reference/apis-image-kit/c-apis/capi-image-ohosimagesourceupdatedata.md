# OhosImageSourceUpdateData

```c
struct OhosImageSourceUpdateData {...}
```

## Overview

Defines the update data of the image source. It is obtained by calling [OH_ImageSource_UpdateData](capi-image-source-mdk-h.md#oh_imagesource_updatedata).

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 10

**Related module**: [Image](capi-others-image.md)

**Header file**: [image_source_mdk.h](capi-image-source-mdk-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t* buffer = nullptr | Image source update data buffer.<br>**Since**: 10 |
| size_t bufferSize = 0 | Image source update data buffer size.<br>**Since**: 10 |
| uint32_t offset = 0 | Image source offset of update data buffer.<br>**Since**: 10 |
| uint32_t updateLength = 0 | Image source update data length in update data buffer.<br>**Since**: 10 |
| int8_t isCompleted = 0 | Image source update data is completed in this session.<br>**Since**: 10 |
| uint8_t* buffer | Image source update data buffer.<br>**Since**: 10 |
| size_t bufferSize | Image source update data buffer size.<br>**Since**: 10 |
| uint32_t offset | Image source offset of update data buffer.<br>**Since**: 10 |
| uint32_t updateLength | Image source update data length in update data buffer.<br>**Since**: 10 |
| int8_t isCompleted | Image source update data is completed in this session.<br>**Since**: 10 |


