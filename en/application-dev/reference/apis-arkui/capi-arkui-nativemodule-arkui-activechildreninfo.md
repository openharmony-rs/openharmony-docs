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

## Overview

Defines active child node information of the current node. You can query the number of active child nodes, obtain child nodes by subscript, and release resources after use.

**Since**: 14

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_type.h](capi-native-type-h.md)

**Related APIs**
| Name                                                                             | Description|
|---------------------------------------------------------------------------------|------|
| [OH_ArkUI_NodeUtils_GetActiveChildrenInfo](capi-native-node-h.md#oh_arkui_nodeutils_getactivechildreninfo) | Obtains the information about the active child node of a node. This API is applicable to querying the set of active child nodes that can be accessed by the node.|
| [OH_ArkUI_ActiveChildrenInfo_GetNodeByIndex](capi-native-type-h.md#oh_arkui_activechildreninfo_getnodebyindex) | Obtains the child node whose subscript is index in **ArkUI_ActiveChildrenInfo**. This API is applicable to traversing active child nodes by subscript.|
| [OH_ArkUI_ActiveChildrenInfo_GetCount](capi-native-type-h.md#oh_arkui_activechildreninfo_getcount) | Obtains the number of nodes in **ArkUI_ActiveChildrenInfo**. This API is applicable to determining the number of active child nodes before traversal.|
| [OH_ArkUI_ActiveChildrenInfo_Destroy](capi-native-type-h.md#oh_arkui_activechildreninfo_destroy) | Destroys an **ArkUI_ActiveChildrenInfo** instance and releases the resources allocated when obtaining active child node information.|
