# ArkUI_ImmersiveMaterial
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct ArkUI_ImmersiveMaterial ArkUI_ImmersiveMaterial
```

## Overview

Defines an immersive material object on the native side.

Immersive materials are classified into different levels based on device computing power.

A material level is defined by [ArkUI_MaterialLevel](./capi-native-material-h.md#arkui_materiallevel) and can be obtained through [OH_ArkUI_NativeModule_GetGlobalMaterialLevel](./capi-native-material-h.md#oh_arkui_nativemodule_getglobalmateriallevel).

On devices with high- and mid-level computing power, the filter and shadow ([NODE_SHADOW](./capi-native-node-h-nodeattributetype-animator.md#node_shadow) or [NODE_CUSTOM_SHADOW](./capi-native-node-h-nodeattributetype-animator.md#node_custom_shadow)) of the material layer are affected. On devices with low computing power, the background color ([NODE_BACKGROUND_COLOR](./capi-native-node-h-nodeattributetype-common.md#node_background_color)), border color ([NODE_BORDER_COLOR](./capi-native-node-h-nodeattributetype-layoutattributes.md#node_border_color)), border width ([NODE_BORDER_WIDTH](./capi-native-node-h-nodeattributetype-layoutattributes.md#node_border_width)), and shadow ([NODE_SHADOW](./capi-native-node-h-nodeattributetype-animator.md#node_shadow) or [NODE_CUSTOM_SHADOW](./capi-native-node-h-nodeattributetype-animator.md#node_custom_shadow)) are affected.

**Since**: 26.0.0

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_material.h](capi-native-material-h.md)
