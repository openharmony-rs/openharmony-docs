# ArkUI_ActiveChildrenInfo
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiang-shouxing-->
<!--Designer: @xiang-shouxing-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

```
typedef struct ArkUI_ActiveChildrenInfo ArkUI_ActiveChildrenInfo
```

## Overview

Defines a struct for active child node information.

**Since**: 14

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_type.h](capi-native-type-h.md)

**Related APIs**
| API                                                                             | Description|
|---------------------------------------------------------------------------------| -- |
| [OH_ArkUI_NodeUtils_GetActiveChildrenInfo](capi-native-node-h.md#oh_arkui_nodeutils_getactivechildreninfo) | Obtains all active child nodes of the specified node.|
| [OH_ArkUI_ActiveChildrenInfo_GetNodeByIndex](capi-native-type-h.md#oh_arkui_activechildreninfo_getnodebyindex) | Obtains the child node at the specified index in the specified **ActiveChildrenInfo** instance.|
| [OH_ArkUI_ActiveChildrenInfo_GetCount](capi-native-type-h.md#oh_arkui_activechildreninfo_getcount) | Obtains the number of nodes in the specified **ActiveChildrenInfo** instance.|
| [OH_ArkUI_ActiveChildrenInfo_Destroy](capi-native-type-h.md#oh_arkui_activechildreninfo_destroy) | Destroys an **ActiveChildrenInfo** instance.|
