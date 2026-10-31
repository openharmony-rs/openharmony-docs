# ArkUI_LightEffectOptions

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=39ca26def5c22dc659f3dc0b76ef62a29421e77a translatedAt=2026-08-19T08:24:12.100Z pushedAt=2026-08-20T02:45:21.735Z -->

```c
typedef struct ArkUI_LightEffectOptions ArkUI_LightEffectOptions
```

## Overview

Defines a light sensing interaction effect configuration object for immersive materials, which is used to configure the light sensing response effect generated when users interact with immersive materials. For details about the design logic, see [native_material.h](capi-native-material-h.md). An immersive material is a visual material style with a sense of depth and layering, and the light sensing interaction effect refers to the light and shadow visual feedback generated when users interact with components. After creation, the configuration object must be set to the immersive material object through [OH_ArkUI_NativeModule_ImmersiveMaterial_SetLightEffect](capi-native-material-h.md#oh_arkui_nativemodule_immersivematerial_setlighteffect) to take effect.

If no light sensing interaction color is specified, the default light sensing interaction color is white (**0xffffffff**).

**Since**: 26.0.0

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_material.h](capi-native-material-h.md)