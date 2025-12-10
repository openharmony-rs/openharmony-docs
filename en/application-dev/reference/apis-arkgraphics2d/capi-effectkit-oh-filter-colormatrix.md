# OH_Filter_ColorMatrix

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanamaru-->
<!--Designer: @gaoweihua-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->

```
struct OH_Filter_ColorMatrix {...}
```

## Overview

Describes a matrix used to create an effect filter.

**Since**: 12

**Related module**: [effectKit](capi-effectkit.md)

**Header file**: [effect_types.h](capi-effect-types-h.md)

## Summary

### Member Variables

| Name         | Description                              |
| ------------- | ---------------------------------- |
| float val[20] | Custom color matrix. The value is a 5 x 4 array.|
