# ArkUI_ImmersiveMaterial

```c
typedef struct ArkUI_ImmersiveMaterial ArkUI_ImmersiveMaterial
```

## 概述

定义Native侧的沉浸式材质对象，根据设备算力等级提供适配的视觉效果。<br>沉浸式材质的等级根据设备算力等级而不同。<br>材质等级由[ArkUI_MaterialLevel](capi-native-material-h.md#arkui_materiallevel)定义，可通过[OH_ArkUI_NativeModule_GetGlobalMaterialLevel](capi-native-material-h.md#oh_arkui_nativemodule_getglobalmateriallevel)获取。<br>在高算力和中算力设备上，会影响沉浸式材质渲染层的滤镜效果和阴影（{@link NODE_SHADOW}或{@link NODE_CUSTOM_SHADOW}）效果。在低算力设备上，会影响背景颜色{@link NODE_BACKGROUND_COLOR}、边框颜色{@link NODE_BORDER_COLOR}、边框宽度{@link NODE_BORDER_WIDTH}和阴影（{@link NODE_SHADOW}或{@link NODE_CUSTOM_SHADOW}）效果。

**起始版本：** 26.0.0

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_material.h](capi-native-material-h.md)

