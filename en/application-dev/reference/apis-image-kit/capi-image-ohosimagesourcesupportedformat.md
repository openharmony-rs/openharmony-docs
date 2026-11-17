# OhosImageSourceSupportedFormat
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=a71c0a82e5ac85b488b13af278b7bfd23da513e9 translatedAt=2026-11-06T02:04:42.121Z pushedAt=2026-11-12T06:17:06.570Z nl=1 -->

```c
struct OhosImageSourceSupportedFormat {...}
```

## Overview

The struct describes the format string supported by an image source. It is used in [OhosImageSourceSupportedFormatList](capi-image-ohosimagesourcesupportedformatlist.md) and [OH_ImageSource_GetSupportedFormats](capi-image-source-mdk-h.md#oh_imagesource_getsupportedformats).

**Since**: 10

**Related module**: [Image](capi-image.md)

**Header file**: [image_source_mdk.h](capi-image-source-mdk-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| char* format = nullptr | Head address of the format string supported by the image source supported formats. This setting is only applicable to the C++ compilation environment. |
| size_t size = 0 | Size of the format string supported by the image source. This setting is only applicable to the C++ compilation environment. |
| char* format | Head address of the format string supported by the image source. This setting is only applicable to the C compilation environment. |
| size_t size | Size of the format string supported by the image source. This setting is only applicable to the C compilation environment. |