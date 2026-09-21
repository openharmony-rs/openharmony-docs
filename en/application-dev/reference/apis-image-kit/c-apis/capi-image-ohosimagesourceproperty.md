# OhosImageSourceProperty

```c
struct OhosImageSourceProperty {...}
```

## Overview

Defines the property string (in key-value format) of the image source. It is used in {@link OH_ImageSource_GetImageProperty} and {@link OH_ImageSource_ModifyImageProperty}.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 10

**Related module**: [Image](capi-image.md)

**Header file**: [image_source_mdk.h](capi-image-source-mdk-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char* value = nullptr |  |
| size_t size = 0;
#else |  |
| char* value |  |
| size_t size;
#endif |  |


