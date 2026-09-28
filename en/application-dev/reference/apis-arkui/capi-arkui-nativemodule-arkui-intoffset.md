# ArkUI_IntOffset
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fenglinbailu-->
<!--Designer: @fenglinbailu-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=45ec2d938cfede23d9ca90fe41c0d1f3e7b2b01d translatedAt=2026-09-20T08:54:35.190Z pushedAt=2026-09-20T10:49:04.525Z -->

```c
typedef struct {...} ArkUI_IntOffset
```

## Overview

Defines an offset, which describes the position of the current component relative to its parent component.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_type.h](capi-native-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t x | Horizontal offset, in px. A positive value means the component moves right, and a negative value means it moves left. |
| int32_t y | Vertical offset, in px. A positive value means the component moves down, and a negative value means it moves up. |


