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

定义ArkUI_ActiveChildrenInfo结构体，用于保存内部活跃状态为`true`的FrameNode子节点信息，支持查询子节点数量和按下标获取子节点。该结构体实例由OH_ArkUI_NodeUtils_GetActiveChildrenInfo生成，使用完毕后必须调用OH_ArkUI_ActiveChildrenInfo_Destroy销毁。

**起始版本：** 14

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_type.h](capi-native-type-h.md)

**相关接口：** 
| 名称                                                                              | 描述 |
|---------------------------------------------------------------------------------|------|
| [OH_ArkUI_NodeUtils_GetActiveChildrenInfo](capi-native-node-h.md#oh_arkui_nodeutils_getactivechildreninfo) | 获取内部活跃状态为`true`的FrameNode子节点，并生成ArkUI_ActiveChildrenInfo实例。Span不会被计入子节点统计。获取成功后，可查询子节点数量并按下标读取子节点；实例使用完毕后必须调用OH_ArkUI_ActiveChildrenInfo_Destroy销毁。 |
| [OH_ArkUI_ActiveChildrenInfo_GetNodeByIndex](capi-native-type-h.md#oh_arkui_activechildreninfo_getnodebyindex) | 获取ArkUI_ActiveChildrenInfo结构体中下标为index的子节点，适用于按下标遍历活跃子节点。 |
| [OH_ArkUI_ActiveChildrenInfo_GetCount](capi-native-type-h.md#oh_arkui_activechildreninfo_getcount) | 获取ArkUI_ActiveChildrenInfo结构体内的子节点数量，适用于遍历活跃子节点前确定数量。 |
| [OH_ArkUI_ActiveChildrenInfo_Destroy](capi-native-type-h.md#oh_arkui_activechildreninfo_destroy) | 销毁ArkUI_ActiveChildrenInfo实例，释放获取活跃子节点信息时分配的资源。 |
