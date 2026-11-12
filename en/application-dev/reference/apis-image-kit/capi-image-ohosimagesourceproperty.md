# OhosImageSourceProperty
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=a71c0a82e5ac85b488b13af278b7bfd23da513e9 translatedAt=2026-11-06T02:03:45.295Z pushedAt=2026-11-12T06:14:48.758Z nl=1 -->

```c
struct OhosImageSourceProperty {...}
```

## Overview

The struct describes the property string (in key-value format) of an image source. It is used in [OH_ImageSource_GetImageProperty](capi-image-source-mdk-h.md#oh_imagesource_getimageproperty) and [OH_ImageSource_ModifyImageProperty](capi-image-source-mdk-h.md#oh_imagesource_modifyimageproperty).

**Since**: 10

**Related module**: [Image](capi-image.md)

**Header file**: [image_source_mdk.h](capi-image-source-mdk-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| char* value = nullptr | Header address of the property key-value string of an image source. This setting is only applicable to the C++ compilation environment. |
| size_t size = 0 | Size of the property key-value string of an image source. This setting is only applicable to the C++ compilation environment. |
| char* value | Header address of the property key-value string of an image source. This setting is only applicable to the C compilation environment. |
| size_t size | Size of the property key-value string of an image source. This setting is only applicable to the C compilation environment. |

