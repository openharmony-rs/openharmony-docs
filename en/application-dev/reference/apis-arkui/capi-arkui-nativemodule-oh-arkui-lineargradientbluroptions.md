# OH_ArkUI_LinearGradientBlurOptions
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=37a41c7e4764d3e7f831e1f47fc28c3acf56e6c1 translatedAt=2026-11-03T08:41:13.450Z pushedAt=2026-11-03T09:07:57.483Z nl=1 -->

```c
typedef struct OH_ArkUI_LinearGradientBlurOptions OH_ArkUI_LinearGradientBlurOptions
```

## Overview

Defines the options for a linear gradient blur effect.

The options include the blur radius, gradient blur segments, and gradient direction. When created through [OH_ArkUI_NativeModule_LinearGradientBlurOptions_Create](capi-native-type-visual-h.md#oh_arkui_nativemodule_lineargradientbluroptions_create), the default values are: **blurRadius** = **0** (no blur), **fractionStops** = **{0.0, 0.0, 0.0, 1.0}** (two segments: the blur value at position 0 is 0, and the blur value at position 1 is 0, indicating no blur along the entire gradient direction), **direction** = [OH_ARKUI_LINEAR_GRADIENT_BLUR_DIRECTION_BOTTOM](capi-native-type-visual-h.md#oh_arkui_lineargradientblurdirection).

**Since:** 26.1.0

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_type_visual.h](capi-native-type-visual-h.md)
