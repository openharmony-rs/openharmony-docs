# ArkUI_ImmersiveMaterial*

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=39ca26def5c22dc659f3dc0b76ef62a29421e77a translatedAt=2026-08-19T08:23:49.815Z pushedAt=2026-08-20T07:17:58.453Z -->

```c
typedef struct ArkUI_ImmersiveMaterial* ArkUI_ImmersiveMaterialHandle
```

## Overview

Defines the pointer to an immersive material object, which is used to implement immersive visual effects.

You can call [OH_ArkUI_NativeModule_ImmersiveMaterial_Create](./capi-native-material-h.md#oh_arkui_nativemodule_immersivematerial_create) to create an immersive material object. When the object is no longer used, you must call [OH_ArkUI_NativeModule_ImmersiveMaterial_Destroy](./capi-native-material-h.md#oh_arkui_nativemodule_immersivematerial_destroy) to destroy it to release resources, avoiding memory leakage.

**Since**: 26.0.0

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_material.h](capi-native-material-h.md)