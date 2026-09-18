# OhosImageSourceUpdateData

```c
struct OhosImageSourceUpdateData {...}
```

## Overview

Defines the update data of the image source. It is obtained by calling [OH_ImageSource_UpdateData](capi-image-source-mdk-h.md#oh_imagesource_updatedata).

**Since**: 10

**Related module**: [Image](capi-image.md)

**Header file**: [image_source_mdk.h](capi-image-source-mdk-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t* buffer = nullptr |  |
| size_t bufferSize = 0 |  |
| uint32_t offset = 0 |  |
| uint32_t updateLength = 0 |  |
| int8_t isCompleted = 0;
#else |  |
| uint8_t* buffer |  |
| size_t bufferSize |  |
| uint32_t offset |  |
| uint32_t updateLength |  |
| int8_t isCompleted;
#endif |  |


