# OhosImageSourceSupportedFormatList

```c
struct OhosImageSourceSupportedFormatList {...}
```

## Overview

Defines the format string list supported by the image source. It is obtained by calling {@link OH_ImageSource_GetSupportedFormats}.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 10

**Related module**: [Image](capi-image.md)

**Header file**: [image_source_mdk.h](capi-image-source-mdk-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| struct [OhosImageSourceSupportedFormat**](capi-image-ohosimagesourcesupportedformat.md) supportedFormatList = nullptr |  |
| size_t size = 0;
#else |  |
| struct [OhosImageSourceSupportedFormat**](capi-image-ohosimagesourcesupportedformat.md) supportedFormatList |  |
| size_t size;
#endif |  |


