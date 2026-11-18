# ArkUI_ImmersiveMaterial*
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=2495040792c8da8de232a60f3eafa9d33ca50fa6 translatedAt=2026-11-09T11:43:52.788Z pushedAt=2026-11-10T02:30:43.687Z nl=1 -->

```c
typedef struct ArkUI_ImmersiveMaterial* ArkUI_ImmersiveMaterialHandle
```

## Overview

Defines the pointer to an immersive material object, which is used to implement immersive visual effects.

You can call [OH_ArkUI_NativeModule_ImmersiveMaterial_Create](./capi-native-material-h.md#oh_arkui_nativemodule_immersivematerial_create) to create an immersive material object. When the object is no longer used, you must call [OH_ArkUI_NativeModule_ImmersiveMaterial_Destroy](./capi-native-material-h.md#oh_arkui_nativemodule_immersivematerial_destroy) to destroy it to release resources, avoiding memory leakage.

**Since**: 26.0.0

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_material.h](capi-native-material-h.md)
