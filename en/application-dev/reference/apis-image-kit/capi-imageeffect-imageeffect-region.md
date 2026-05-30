# ImageEffect_Region
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct ImageEffect_Region {...} ImageEffect_Region
```

## Overview

The struct describes the image region.

**Since**: 12

**Related module**: [ImageEffect](capi-imageeffect.md)

**Header file**: [image_effect_filter.h](capi-image-effect-filter-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t x0 | Start coordinate of the X axis.|
| int32_t y0 | Start coordinate of the Y axis.|
| int32_t x1 | End coordinate of the X axis.|
| int32_t y1 | End coordinate of the Y axis.|
