# ArkUI_LightEffectOptions*
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef ArkUI_LightEffectOptions* ArkUI_LightEffectOptionsHandle
```

## Overview

Defines the pointer to a light sensing interaction effect configuration object. You can use this pointer to set and manage the parameters of the light sensing interaction effect.

You must create a light sensing interaction effect configuration object by calling [OH_ArkUI_NativeModule_LightEffectOptions_Create](./capi-native-material-h.md#oh_arkui_nativemodule_lighteffectoptions_create). When the object is no longer used, you must call [OH_ArkUI_NativeModule_LightEffectOptions_Destroy](./capi-native-material-h.md#oh_arkui_nativemodule_lighteffectoptions_destroy) to destroy it to release resources. The two APIs must be used in pairs. If the object is not destroyed by calling **Destroy**, resource leakage may occur.

**Since**: 26.0.0

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_material.h](capi-native-material-h.md)
