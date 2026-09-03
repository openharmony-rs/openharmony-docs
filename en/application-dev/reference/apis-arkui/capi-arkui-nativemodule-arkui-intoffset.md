# ArkUI_IntOffset

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fenglinbailu-->
<!--Designer: @fenglinbailu-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=75a7d62c0702c21a06ca0119552a942305a023cc translatedAt=2026-08-19T08:23:42.739Z pushedAt=2026-08-20T02:10:10.762Z -->

```c
typedef struct {...} ArkUI_IntOffset
```

## Overview

Defines the offset of the current component relative to its parent component.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_type.h](capi-native-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t x | Horizontal offset, in px. A positive value means the component moves right, and a negative value means it moves left. |
| int32_t y | Vertical offset, in px. A positive value means the component moves down, and a negative value means it moves up. |