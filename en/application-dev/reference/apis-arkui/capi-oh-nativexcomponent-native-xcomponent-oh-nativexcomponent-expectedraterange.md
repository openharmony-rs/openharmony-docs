# OH_NativeXComponent_ExpectedRateRange
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @pengzhiwen3-->
<!--Designer: @dutie123-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=26981b54dcb92d5646f17bc8dcf56ce1bdfdfcf7 translatedAt=2026-08-27T08:45:57.322Z pushedAt=2026-08-28T01:47:36.966Z -->

```c
typedef struct {...} OH_NativeXComponent_ExpectedRateRange
```

## Overview

Defines an expected frame rate range, used to set the expected frame rate range during **XComponent** rendering. It applies to scenarios that require precise control over animation or rendering frame rates, helping to strike a balance between visual smoothness and power consumption.

**Since**: 11

**Related module**: [OH_NativeXComponent Native XComponent](capi-oh-nativexcomponent-native-xcomponent.md)

**Header file**: [native_interface_xcomponent.h](capi-native-interface-xcomponent-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t min | Minimum value in the expected frame rate range. The value must be greater than or equal to 0 and less than or equal to **max**. Unit: frames per second. An invalid value does not take effect. Value range: [0, +∞). The value of **min** must be less than or equal to the value of **max**. |
| int32_t max | Maximum value in the expected frame rate range. The value must be greater than or equal to **min** and must not exceed the maximum frame rate supported by the device. Unit: frames per second. An invalid value does not take effect. Value range: [0, +∞). The value of **max** must be greater than or equal to the value of **min**. |
| int32_t expected | Expected frame rate. The value must meet the condition "**min** ≤ **expected** ≤ **max**. Unit: frames per second. Value range: [0, +∞), and the value must be within [**min**, **max**]. |


