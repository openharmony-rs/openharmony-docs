# ArkUI_LightEffectOptions*

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=39ca26def5c22dc659f3dc0b76ef62a29421e77a translatedAt=2026-08-19T08:24:14.761Z pushedAt=2026-08-20T02:47:07.044Z -->

```c
typedef ArkUI_LightEffectOptions* ArkUI_LightEffectOptionsHandle
```

## Overview

Defines the pointer to a light sensing interaction effect configuration object. You can use this pointer to set and manage the parameters of the light sensing interaction effect of immersive materials.

You must create a light sensing interaction effect configuration object by calling [OH_ArkUI_NativeModule_LightEffectOptions_Create](./capi-native-material-h.md#oh_arkui_nativemodule_lighteffectoptions_create). After using the object, you must call [OH_ArkUI_NativeModule_LightEffectOptions_Destroy](./capi-native-material-h.md#oh_arkui_nativemodule_lighteffectoptions_destroy) to destroy it and release resources. Continuing to use the pointer after the destruction will lead to undefined behavior. The two APIs must be used in pairs. Failing to call **Destroy** to destroy the object will cause a resource leak.

**Since**: 26.0.0

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_material.h](capi-native-material-h.md)