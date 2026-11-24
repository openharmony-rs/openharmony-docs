# DisplaySoloist_ExpectedRateRange

```c
typedef struct DisplaySoloist_ExpectedRateRange {...} DisplaySoloist_ExpectedRateRange
```

## Overview

Defines the expected frame rate range struct, which is used to set the expected frame rate range of DisplaySoloist (variable frame rate drawing on an independent thread). The set expected frame rate range serves as a reference for system scheduling, and the system tries to adjust the drawing frame rate within this range.

<!--Device-typedef struct DisplaySoloist_ExpectedRateRange {...} DisplaySoloist_ExpectedRateRange--><!--Device-typedef struct DisplaySoloist_ExpectedRateRange {...} DisplaySoloist_ExpectedRateRange-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.HyperGraphicManager

**Since**: 12

**Related module**: [NativeDisplaySoloist](capi-arkgraphics2d-nativedisplaysoloist.md)

**Header file**: [native_display_soloist.h](capi-native-display-soloist-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t min | Expected minimum frame rate. Unit: fps. Value range: [0, maximum refresh rate supported by the device].<br><!--Device-int32_t min--><!--Device-int32_t min-End--> |
| int32_t max | Expected maximum frame rate. Unit: fps. Value range: [min, maximum refresh rate supported by the device].<br><!--Device-int32_t max--><!--Device-int32_t max-End--> |
| int32_t expected | Expected target frame rate. Unit: fps. Value range: [min, max].<br><!--Device-int32_t expected--><!--Device-int32_t expected-End--> |


