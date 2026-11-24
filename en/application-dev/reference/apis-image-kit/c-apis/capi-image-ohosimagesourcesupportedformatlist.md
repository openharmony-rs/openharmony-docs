# OhosImageSourceSupportedFormatList

```c
struct OhosImageSourceSupportedFormatList {...}
```

## Overview

Defines the format string list supported by the image source. It is obtained by calling [OH_ImageSource_GetSupportedFormats](capi-image-source-mdk-h.md#oh_imagesource_getsupportedformats).

<!--Device-struct OhosImageSourceSupportedFormatList {...}--><!--Device-struct OhosImageSourceSupportedFormatList {...}-End-->

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 10

**Related module**: [Image](capi-image-kit-image.md)

**Header file**: [image_source_mdk.h](capi-image-source-mdk-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| struct OhosImageSourceSupportedFormat** supportedFormatList = nullptr | Image source supported format string list head.<br>**Since**: 10<br><!--Device-struct OhosImageSourceSupportedFormat** supportedFormatList = nullptr--><!--Device-struct OhosImageSourceSupportedFormat** supportedFormatList = nullptr-End--> |
| size_t size = 0 | Image source supported format string list size.<br>**Since**: 10<br><!--Device-size_t size = 0--><!--Device-size_t size = 0-End--> |
| [struct OhosImageSourceSupportedFormat*](capi-image-ohosimagesourcesupportedformat.md)* supportedFormatList | Image source supported format string list head.<br>**Since**: 10<br><!--Device-struct OhosImageSourceSupportedFormat** supportedFormatList--><!--Device-struct OhosImageSourceSupportedFormat** supportedFormatList-End--> |
| size_t size | Image source supported format string list size.<br>**Since**: 10<br><!--Device-size_t size--><!--Device-size_t size-End--> |


