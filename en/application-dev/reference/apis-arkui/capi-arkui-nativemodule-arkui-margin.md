# ArkUI_Margin

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fenglinbailu-->
<!--Designer: @fenglinbailu-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=75a7d62c0702c21a06ca0119552a942305a023cc translatedAt=2026-08-19T08:24:30.974Z pushedAt=2026-08-20T02:48:00.814Z -->

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