# OH_ArkUI_ShadowOptions

```c
typedef struct OH_ArkUI_ShadowOptions OH_ArkUI_ShadowOptions
```

## Overview

Defines shadow options for setting the shadow effect of a component, including attributes such as the shadow color, offset, blur radius, shadow type, and whether to fill.<br> Call [OH_ArkUI_ShadowOptions_Create](capi-native-type-visual-h.md#oh_arkui_shadowoptions_create) to create the corresponding shadow option object.<br> Call [OH_ArkUI_ShadowOptions_Destroy](capi-native-type-visual-h.md#oh_arkui_shadowoptions_destroy) to destroy the shadow option object.<br> After the object is created, call the <b>OH_ArkUI_ShadowOptions_SetXXX</b> series APIs to set the specific styles to take effect, for example, call [OH_ArkUI_ShadowOptions_SetRadius](capi-native-type-visual-h.md#oh_arkui_shadowoptions_setradius) to set the shadow blur radius. If the object fails to be created (a null pointer is returned), calling the <b>SetXXX</b> series APIs will not take effect.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_type_visual.h](capi-native-type-visual-h.md)

