# OhosImageSourceSupportedFormat

```c
struct OhosImageSourceSupportedFormat {...}
```

## Overview

Defines image source supported format string. {@link OhosImageSourceSupportedFormatList} and {@link OH_ImageSource_GetSupportedFormats}

**System capability**: SystemCapability.Multimedia.Image.ImageSource

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


