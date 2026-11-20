# OH_NativeXComponent_ExpectedRateRange
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @pengzhiwen3-->
<!--Designer: @dutie123-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=33898b66eb6c0bf66810bb0d90faa36b55a4ad07 translatedAt=2026-11-18T09:13:09.115Z pushedAt=2026-11-20T02:10:24.123Z nl=1 -->

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
| int32_t min | Minimum value in the expected frame rate range. The value must be greater than or equal to 0 and less than or equal to the value of **max**. Unit: frames per second. An invalid value does not take effect. Value range: [0, Maximum frame rate supported by the device]. |
| int32_t max | Maximum value in the expected frame rate range. The value must be greater than or equal to the value of **min** and must not exceed the maximum frame rate supported by the device. Unit: frames per second. An invalid value does not take effect. Value range: [0, Maximum frame rate supported by the device]. |
| int32_t expected | Expected frame rate. Unit: frames per second. The value must satisfy **min** ≤ **expected** ≤ **max**. An invalid value does not take effect. |


