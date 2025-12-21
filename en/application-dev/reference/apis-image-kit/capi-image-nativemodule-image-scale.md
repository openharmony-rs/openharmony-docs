# Image_Scale

<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

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
| float x | Scale factor of the width. It must not be **0**.|
| float y | Scale factor of the height. It must not be **0**.|
