# Image_Scale

<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=0fd7a4a11ddfd226fa5fd7e273dd1b93d4f5d399 translatedAt=2026-11-10T08:06:20.676Z pushedAt=2026-11-10T11:47:29.830Z nl=1 -->

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
| float x | Scale factor of the width.<br>The value cannot be 0. A positive value is recommended; otherwise, a flip effect occurs. |
| float y | Scale factor of the height.<br>The value cannot be 0. A positive value is recommended; otherwise, a flip effect occurs. |


