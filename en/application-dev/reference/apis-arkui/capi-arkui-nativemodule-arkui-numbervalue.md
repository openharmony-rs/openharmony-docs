# ArkUI_NumberValue
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=b716ee352b9e655afb79b3f046265840f2170607 translatedAt=2026-09-20T09:22:28.521Z pushedAt=2026-09-21T12:33:30.520Z -->

```c
typedef union {...} ArkUI_NumberValue
```

## Overview

Defines a numeric type used by ArkUI on the native side, including floating-point, signed integer, and unsigned integer types.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_type.h](capi-native-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| float f32 | Variable of floating-point type, used to store floating-point values.|
| int32_t i32 | Variable of signed integer type, used to store signed integer values.|
| uint32_t u32 | Variable of unsigned integer type, used to store unsigned integer values.|
