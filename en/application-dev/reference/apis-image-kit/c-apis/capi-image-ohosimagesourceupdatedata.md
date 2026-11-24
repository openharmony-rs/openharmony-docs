# OhosImageSourceUpdateData

```c
struct OhosImageSourceUpdateData {...}
```

## Overview

Defines the update data of the image source. It is obtained by calling [OH_ImageSource_UpdateData](capi-image-source-mdk-h.md#oh_imagesource_updatedata).

<!--Device-struct OhosImageSourceUpdateData {...}--><!--Device-struct OhosImageSourceUpdateData {...}-End-->

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 10

**Related module**: [Image](capi-image-kit-image.md)

**Header file**: [image_source_mdk.h](capi-image-source-mdk-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t* buffer = nullptr | Image source update data buffer.<br>**Since**: 10<br><!--Device-uint8_t* buffer = nullptr--><!--Device-uint8_t* buffer = nullptr-End--> |
| size_t bufferSize = 0 | Image source update data buffer size.<br>**Since**: 10<br><!--Device-size_t bufferSize = 0--><!--Device-size_t bufferSize = 0-End--> |
| uint32_t offset = 0 | Image source offset of update data buffer.<br>**Since**: 10<br><!--Device-uint32_t offset = 0--><!--Device-uint32_t offset = 0-End--> |
| uint32_t updateLength = 0 | Image source update data length in update data buffer.<br>**Since**: 10<br><!--Device-uint32_t updateLength = 0--><!--Device-uint32_t updateLength = 0-End--> |
| int8_t isCompleted = 0 | Image source update data is completed in this session.<br>**Since**: 10<br><!--Device-int8_t isCompleted = 0--><!--Device-int8_t isCompleted = 0-End--> |
| uint8_t* buffer | Image source update data buffer.<br>**Since**: 10<br><!--Device-uint8_t* buffer--><!--Device-uint8_t* buffer-End--> |
| size_t bufferSize | Image source update data buffer size.<br>**Since**: 10<br><!--Device-size_t bufferSize--><!--Device-size_t bufferSize-End--> |
| uint32_t offset | Image source offset of update data buffer.<br>**Since**: 10<br><!--Device-uint32_t offset--><!--Device-uint32_t offset-End--> |
| uint32_t updateLength | Image source update data length in update data buffer.<br>**Since**: 10<br><!--Device-uint32_t updateLength--><!--Device-uint32_t updateLength-End--> |
| int8_t isCompleted | Image source update data is completed in this session.<br>**Since**: 10<br><!--Device-int8_t isCompleted--><!--Device-int8_t isCompleted-End--> |


