# ArkUI_NumberValue
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=40f125e411d86aec90278a3bd36a99ed8142a85d translatedAt=2026-11-23T07:07:42.656Z pushedAt=2026-11-25T01:16:37.507Z nl=1 -->

```c
typedef union {...} ArkUI_NumberValue
```

## Overview

Defines a numeric type used by ArkUI on the native side, including floating-point, signed integer, and unsigned integer types.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [common_type.h](capi-common-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| float f32 | Variable of floating-point type, used to store floating-point values.|
| int32_t i32 | Variable of signed integer type, used to store signed integer values.|
| uint32_t u32 | Variable of unsigned integer type, used to store unsigned integer values.|
