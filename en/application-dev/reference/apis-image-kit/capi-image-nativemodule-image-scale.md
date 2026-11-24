# Image_Scale

<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=89b25106c383363d09662827798c5567932548f5 translatedAt=2026-11-06T02:01:50.316Z pushedAt=2026-11-12T05:59:42.423Z nl=1 -->

```c
typedef struct Image_Scale {...} Image_Scale
```

## Overview

The struct describes the image scale factor.

**Since**: 22

**Related module**: [Image_NativeModule](capi-image-nativemodule.md)

**Header file**: [image_common.h](capi-image-common-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| float x | Scaling factor of the width.<br>The value cannot be 0. A positive value is recommended; otherwise, a flip effect will occur. |
| float y | Scaling factor of the height.<br>The value cannot be 0. A positive value is recommended; otherwise, a flip effect will occur. |


