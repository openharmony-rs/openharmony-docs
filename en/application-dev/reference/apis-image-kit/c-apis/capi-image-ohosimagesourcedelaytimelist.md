# OhosImageSourceDelayTimeList

```c
struct OhosImageSourceDelayTimeList {...}
```

## Overview

Defines the delay time list of the image source. It is obtained by calling {@link OH_ImageSource_GetDelayTime}.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 10

**Related module**: [Image](capi-image.md)

**Header file**: [image_source_mdk.h](capi-image-source-mdk-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t* delayTimeList |  |
| size_t size = 0;
#else |  |
| int32_t* delayTimeList |  |
| size_t size;
#endif |  |


