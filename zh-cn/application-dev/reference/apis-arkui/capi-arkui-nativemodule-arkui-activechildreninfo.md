# ArkUI_ActiveChildrenInfo
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct ArkUI_ActiveChildrenInfo ArkUI_ActiveChildrenInfo
```

## 概述

定义ArkUI_ActiveChildrenInfo结构体信息，用于表示节点当前处于活跃状态的子节点信息，支持查询活跃子节点数量、按下标获取子节点，并在使用完毕后释放资源。

**起始版本：** 14

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_type.h](capi-native-type-h.md)

**相关接口：** 
| 名称                                                                              | 描述 |
|---------------------------------------------------------------------------------|------|
| [OH_ArkUI_NodeUtils_GetActiveChildrenInfo](capi-native-node-h.md#oh_arkui_nodeutils_getactivechildreninfo) | 获取某个节点当前处于活跃状态的子节点信息，适用于查询节点当前可访问的活跃子节点集合。 |
| [OH_ArkUI_ActiveChildrenInfo_GetNodeByIndex](capi-native-type-h.md#oh_arkui_activechildreninfo_getnodebyindex) | 获取ArkUI_ActiveChildrenInfo结构体中下标为index的子节点，适用于按下标遍历活跃子节点。 |
| [OH_ArkUI_ActiveChildrenInfo_GetCount](capi-native-type-h.md#oh_arkui_activechildreninfo_getcount) | 获取ArkUI_ActiveChildrenInfo结构体内的节点数量，适用于遍历活跃子节点前确定数量。 |
| [OH_ArkUI_ActiveChildrenInfo_Destroy](capi-native-type-h.md#oh_arkui_activechildreninfo_destroy) | 销毁ArkUI_ActiveChildrenInfo实例，释放获取活跃子节点信息时分配的资源。 |
