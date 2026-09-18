# OhosImageSourceSupportedFormat

```c
struct OhosImageSourceSupportedFormat {...}
```

## Overview

Defines image source supported format string. [OhosImageSourceSupportedFormatList](capi-image-ohosimagesourcesupportedformatlist.md) and [OH_ImageSource_GetSupportedFormats](capi-image-source-mdk-h.md#oh_imagesource_getsupportedformats)

**Since**: 10

**Related module**: [Image](capi-image.md)

**Header file**: [image_source_mdk.h](capi-image-source-mdk-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char* format = nullptr |  |
| size_t size = 0;
#else |  |
| char* format |  |
| size_t size;
#endif |  |


