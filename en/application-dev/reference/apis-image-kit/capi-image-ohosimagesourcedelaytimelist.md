# OhosImageSourceDelayTimeList
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=a71c0a82e5ac85b488b13af278b7bfd23da513e9 translatedAt=2026-11-06T02:03:40.643Z pushedAt=2026-11-12T06:11:03.852Z nl=1 -->

```c
struct OhosImageSourceDelayTimeList {...}
```

## Overview

The struct describes the delay time list of an image source. The delay time list is obtained by calling [OH_ImageSource_GetDelayTime](capi-image-source-mdk-h.md#oh_imagesource_getdelaytime).

**Since**: 10

**Related module**: [Image](capi-image.md)

**Header file**: [image_source_mdk.h](capi-image-source-mdk-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t* delayTimeList | Pointer to the starting address of the delay time list of an image source.|
| size_t size = 0 | Size of the delay time list of an image source. This setting is only applicable to the C++ compilation environment. |
| size_t size | Size of the delay time list of an image source. This setting is only applicable to the C compilation environment. |

