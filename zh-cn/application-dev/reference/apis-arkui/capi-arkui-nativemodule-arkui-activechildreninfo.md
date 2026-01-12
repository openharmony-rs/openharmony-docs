# ArkUI_ActiveChildrenInfo
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiang-shouxing-->
<!--Designer: @xiang-shouxing-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct ArkUI_ActiveChildrenInfo ArkUI_ActiveChildrenInfo
```

## 概述

定义ActiveChildrenInfo类信息。

**起始版本：** 14

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_type.h](capi-native-type-h.md)

**相关接口：** 
| 名称                                                                              | 描述 |
|---------------------------------------------------------------------------------| -- |
| [OH_ArkUI_NodeUtils_GetActiveChildrenInfo](capi-native-node-h.md#oh_arkui_nodeutils_getactivechildreninfo) | 获取某个节点所有活跃的子节点。 |
| [OH_ArkUI_ActiveChildrenInfo_GetNodeByIndex](capi-native-type-h.md#oh_arkui_activechildreninfo_getnodebyindex) | 获取ActiveChildrenInfo结构体的下标为index的子节点。 |
| [OH_ArkUI_ActiveChildrenInfo_GetCount](capi-native-type-h.md#oh_arkui_activechildreninfo_getcount) | 获取ActiveChildrenInfo结构体内的节点数量。 |
| [OH_ArkUI_ActiveChildrenInfo_Destroy](capi-native-type-h.md#oh_arkui_activechildreninfo_destroy) | 销毁ActiveChildrenInfo实例。 |