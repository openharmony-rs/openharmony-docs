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

## 概述

定义Native侧的沉浸式材质对象。

沉浸式材质根据设备算力等级分为不同等级。

材质等级由[ArkUI_MaterialLevel](./capi-native-material-h.md#arkui_materiallevel)定义，可通过[OH_ArkUI_NativeModule_GetGlobalMaterialLevel](./capi-native-material-h.md#oh_arkui_nativemodule_getglobalmateriallevel)获取。

在高算力和中算力设备上，会影响材质层的滤镜效果和阴影（[NODE_SHADOW](./capi-native-node-h-nodeattributetype-animator.md#node_shadow)或[NODE_CUSTOM_SHADOW](./capi-native-node-h-nodeattributetype-animator.md#node_custom_shadow)）效果。在低算力设备上，会影响背景颜色[NODE_BACKGROUND_COLOR](./capi-native-node-h-nodeattributetype-common.md#node_background_color)、边框颜色[NODE_BORDER_COLOR](./capi-native-node-h-nodeattributetype-layoutattributes.md#node_border_color)、边框宽度[NODE_BORDER_WIDTH](./capi-native-node-h-nodeattributetype-layoutattributes.md#node_border_width)和阴影（[NODE_SHADOW](./capi-native-node-h-nodeattributetype-animator.md#node_shadow)或[NODE_CUSTOM_SHADOW](./capi-native-node-h-nodeattributetype-animator.md#node_custom_shadow)）效果。

**起始版本：** 26.0.0

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_material.h](capi-native-material-h.md)
