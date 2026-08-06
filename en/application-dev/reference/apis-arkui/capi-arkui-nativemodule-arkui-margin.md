# ArkUI_Margin

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fenglinbailu-->
<!--Designer: @lanshouren-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=f8ecdb82f3ec053eb7dde21e27a6f047d194898a translatedAt=2026-07-17T09:25:01.157Z pushedAt=2026-07-17T11:13:53.330Z -->

```c
typedef struct {...} ArkUI_Margin
```

## Overview

Describes the margins of a component, which is used to define the blank area between the component boundary and its parent container or adjacent components, affecting the actually occupied space and position of the component in the layout.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [water_flow.h](capi-water-flow-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| float top | Top margin, in vp.|
| float right | Right margin, in vp.|
| float bottom | Bottom margin, in vp.|
| float left | Left margin, in vp.|