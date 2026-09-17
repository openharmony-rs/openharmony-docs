# OhosImageSourceDelayTimeList

```c
struct OhosImageSourceDelayTimeList {...}
```

## Overview

Defines the delay time list of the image source. It is obtained by calling [OH_ImageSource_GetDelayTime](capi-image-source-mdk-h.md#oh_imagesource_getdelaytime).

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


