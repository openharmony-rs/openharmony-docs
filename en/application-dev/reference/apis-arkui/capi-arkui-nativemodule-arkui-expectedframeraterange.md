# ArkUI_ExpectedFrameRateRange

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e98b791a1f57fab5012a75ce7d9ff0a0466dd410 translatedAt=2026-07-17T02:52:43.932Z pushedAt=2026-07-17T06:57:33.684Z -->

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
| uint32_t min | Expected minimum frame rate, in fps. Rule: The value of **min** must be less than or equal to that of **max**, and must be less than or equal to that of **expected**. That is, min <= expected <= max.|
| uint32_t max | Expected maximum frame rate, in fps. Rule: The value of **max** must be greater than or equal to that of **min**, and must be greater than or equal to that of **expected**. That is, min <= expected <= max.|
| uint32_t expected | Expected optimal frame rate, in fps. Rule: The value of **expected** must be within the range of [**min**, **max**].|