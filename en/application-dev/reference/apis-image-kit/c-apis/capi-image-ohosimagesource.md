# OhosImageSource

```c
struct OhosImageSource {...}
```

## Overview

Defines the input resource of the image source. It is obtained by calling [OH_ImageSource_Create](capi-image-source-mdk-h.md#oh_imagesource_create). Only one type of resource is accepted at a time.

**Since**: 10

**Deprecated**: 11

**Related module**: [Image](capi-image.md)

**Header file**: [image_source_mdk.h](capi-image-source-mdk-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char* uri = nullptr |  |
| size_t uriSize = 0 |  |
| int32_t fd = -1 |  |
| uint8_t* buffer = nullptr |  |
| size_t bufferSize = 0;
#else |  |
| char* uri |  |
| size_t uriSize |  |
| int32_t fd |  |
| uint8_t* buffer |  |
| size_t bufferSize;
#endif |  |


