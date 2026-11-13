# OhosImageSourceSupportedFormatList
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=a71c0a82e5ac85b488b13af278b7bfd23da513e9 translatedAt=2026-11-06T02:06:03.172Z pushedAt=2026-11-12T06:19:17.602Z nl=1 -->

```c
struct OhosImageSourceSupportedFormatList {...}
```

## Overview

The struct defines the format string list supported by an image source. It is obtained by calling [OH_ImageSource_GetSupportedFormats](capi-image-source-mdk-h.md#oh_imagesource_getsupportedformats).

**Since**: 10

**Related module**: [Image](capi-image.md)

**Header file**: [image_source_mdk.h](capi-image-source-mdk-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| struct [OhosImageSourceSupportedFormat](capi-image-ohosimagesourcesupportedformat.md)** supportedFormatList = nullptr | Head address of the format string list supported by the image source. This setting is only applicable to the C++ compilation environment. |
| size_t size = 0 | Size of the format string list supported by the image source. This setting is only applicable to the C++ compilation environment. |
| struct [OhosImageSourceSupportedFormat](capi-image-ohosimagesourcesupportedformat.md)** supportedFormatList | Head address of the format string list supported by the image source. This setting is only applicable to the C compilation environment. |
| size_t size | Size of the format string list supported by the image source. This setting is only applicable to the C compilation environment. |

