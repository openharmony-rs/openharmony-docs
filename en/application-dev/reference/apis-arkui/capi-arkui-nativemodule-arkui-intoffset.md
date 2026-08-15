# ArkUI_IntOffset

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fenglinbailu-->
<!--Designer: @lanshouren-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=f8ecdb82f3ec053eb7dde21e27a6f047d194898a translatedAt=2026-07-17T09:25:05.689Z pushedAt=2026-07-17T11:06:10.105Z -->

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