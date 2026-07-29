# ArkUI_SnapshotOptions
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct ArkUI_SnapshotOptions ArkUI_SnapshotOptions
```

## 概述

定义截图的配置选项结构体，用于在执行组件截图时配置截图行为，适用于需要按业务需求控制截图输出效果的场景。

使用本结构体时，应先调用[OH_ArkUI_CreateSnapshotOptions](capi-common-attributes-h.md#oh_arkui_createsnapshotoptions)创建截图选项对象，并通过[OH_ArkUI_SnapshotOptions_SetScale](capi-common-attributes-h.md#oh_arkui_snapshotoptions_setscale)、[OH_ArkUI_SnapshotOptions_SetColorMode](capi-common-attributes-h.md#oh_arkui_snapshotoptions_setcolormode)和[OH_ArkUI_SnapshotOptions_SetDynamicRangeMode](capi-common-attributes-h.md#oh_arkui_snapshotoptions_setdynamicrangemode)配置截图参数；再将该对象作为snapshotOptions参数传入[OH_ArkUI_GetNodeSnapshot](capi-native-node-h.md#oh_arkui_getnodesnapshot)；不再使用时，必须调用[OH_ArkUI_DestroySnapshotOptions](capi-common-attributes-h.md#oh_arkui_destroysnapshotoptions)释放资源。

**起始版本：** 15

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [common_attributes.h](capi-common-attributes-h.md)

