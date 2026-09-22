# ArkUI_PointF

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=bdfa874a4b1a414190d4f3f309d53e78218cd5fb translatedAt=2026-08-19T08:27:33.698Z pushedAt=2026-08-20T06:30:41.447Z -->

```c
typedef struct {...} ArkUI_PointF
```

## Overview

Defines a two-dimensional coordinate point, used to describe coordinate information such as the component position or offset. The coordinates are stored as floating-point numbers.

**Since**: 24

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_type_visual.h](capi-native-type-visual-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| float x | X-coordinate, in px. Value range: (-∞, +∞). |
| float y | Y-coordinate, in px. Value range: (-∞, +∞). |