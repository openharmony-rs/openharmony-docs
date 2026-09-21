# ArkUI_ExpectedFrameRateRange
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=4d06e6d604d64a9b64c2360f42cbd3fd13c9290b translatedAt=2026-09-20T08:46:51.846Z pushedAt=2026-09-20T09:03:15.957Z -->

```c
typedef struct {...} ArkUI_ExpectedFrameRateRange
```

## Overview

Sets the expected frame rate for an animation. This struct defines the frame rate range through **min**, **max**, and **expected**. The system attempts to meet the expected frame rate as much as possible.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_animate.h](capi-native-animate-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t min | Expected minimum frame rate, in fps. Rule: The value of **min** must be less than or equal to that of **max**, and must be less than or equal to that of **expected**. That is, **min** &le; **expected** &le; **max**. If this condition is not met, the expected frame rate range does not take effect. |
| uint32_t max | Expected maximum frame rate, in fps. Rule: The value of **max** must be greater than or equal to that of **min**, and must be greater than or equal to that of **expected**. That is, **min** &le; **expected** &le; **max**. |
| uint32_t expected | Expected optimal frame rate, in fps. Rule: The value of **expected** must be within the range of [**min**, **max**]. |


