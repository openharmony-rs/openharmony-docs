# ArkUI_ExpectedFrameRateRange

```c
typedef struct ArkUI_ExpectedFrameRateRange {...} ArkUI_ExpectedFrameRateRange
```

## Overview

Defines the expected frame rate range of the animation.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_animate.h](capi-native-animate-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t min | Expected minimum frame rate, in fps. |
| uint32_t max | Expected maximum frame rate, in fps. |
| uint32_t expected | Expected optimal frame rate, in fps. |


