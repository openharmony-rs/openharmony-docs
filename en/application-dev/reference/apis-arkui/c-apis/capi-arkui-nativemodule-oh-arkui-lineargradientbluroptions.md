# OH_ArkUI_LinearGradientBlurOptions

```c
typedef struct OH_ArkUI_LinearGradientBlurOptions OH_ArkUI_LinearGradientBlurOptions
```

## Overview

Defines the options for the linear gradient blur effect.<br> The options include the blur radius, fraction stops, and direction. When created by [OH_ArkUI_NativeModule_LinearGradientBlurOptions_Create](capi-native-type-visual-h.md#oh_arkui_nativemodule_lineargradientbluroptions_create), the default values are: blurRadius = 0 (no blur), fractionStops = {0.0, 0.0, 0.0, 1.0} (two stops: blur value 0 at position 0 and blur value 0 at position 1, meaning no blur across the entire gradient), direction = [OH_ARKUI_LINEAR_GRADIENT_BLUR_DIRECTION_BOTTOM](capi-native-type-visual-h.md#oh_arkui_lineargradientblurdirection).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.2.0

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_type_visual.h](capi-native-type-visual-h.md)

