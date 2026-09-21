# ArkUI_ImmersiveMaterial*
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=a306693f0f46e5633c549769b8338f6bd7c191f4 translatedAt=2026-09-20T08:54:14.175Z pushedAt=2026-09-20T10:48:11.151Z -->

```c
typedef struct ArkUI_ImmersiveMaterial* ArkUI_ImmersiveMaterialHandle
```

## Overview

Defines the pointer to an immersive material object, which is used to implement immersive visual effects.

You can call [OH_ArkUI_NativeModule_ImmersiveMaterial_Create](./capi-native-material-h.md#oh_arkui_nativemodule_immersivematerial_create) to create an immersive material object. When the object is no longer used, you must call [OH_ArkUI_NativeModule_ImmersiveMaterial_Destroy](./capi-native-material-h.md#oh_arkui_nativemodule_immersivematerial_destroy) to destroy it to release resources, avoiding memory leakage.

**Since**: 26.0.0

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_material.h](capi-native-material-h.md)
