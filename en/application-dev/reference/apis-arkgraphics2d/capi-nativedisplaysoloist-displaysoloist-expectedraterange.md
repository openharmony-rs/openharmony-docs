# DisplaySoloist_ExpectedRateRange

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @wh_qwe-->
<!--Designer: @wh_qwe-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=ccdbec13380fdf227c4a20f5bde9cc05c16badee translatedAt=2026-08-24T09:15:51.719Z pushedAt=2026-08-31T11:52:35.166Z -->

```c
typedef struct {...} DisplaySoloist_ExpectedRateRange
```

## Overview

Defines the expected frame rate range struct, which is used to set the expected frame rate range of DisplaySoloist (variable frame rate drawing on an independent thread). The set expected frame rate range serves as a reference for system scheduling, and the system tries to adjust the drawing frame rate within this range.

**Since**: 12

**Related module**: [NativeDisplaySoloist](capi-nativedisplaysoloist.md)

**Header file**: [native_display_soloist.h](capi-native-display-soloist-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t min | Expected minimum frame rate. Unit: fps. Value range: [0, maximum refresh rate supported by the device]. |
| int32_t max | Expected maximum frame rate. Unit: fps. Value range: [min, maximum refresh rate supported by the device]. |
| int32_t expected | Expected target frame rate. Unit: fps. Value range: [min, max]. |