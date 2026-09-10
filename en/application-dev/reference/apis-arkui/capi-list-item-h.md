# list_item.h

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @rongShao-Z; @wind_-->
<!--Designer: @yangcan18-->
<!--Tester: @leiyuqian-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=c49fd674e4d037d5cc12381f25673ba96011cc7b translatedAt=2026-08-21T10:45:42.405Z pushedAt=2026-08-21T12:03:54.027Z -->

## Overview

Defines the enumerations and APIs related to the swipe operation of the **ListItem** component, including setting a swipe action item, the swipe distance threshold for deleting the list item, and the swipe state change callback. It can be used to implement interactive scenarios such as displaying an operation menu when a list item is swiped or deleting a list item through a swipe distance.

**File to include:** <arkui/node_attributes/list_item.h>

**Library:** libace_ndk.z.so

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 12

**Related module:** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Structs

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md) | ArkUI_ListItemSwipeActionItem | Defines the configuration of an item in the **swipeAction** API of the **ListItem** component. |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md) | ArkUI_ListItemSwipeActionOption | Defines the configuration of the **swipeAction** API of the **ListItem** component. |

### Enums

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [ArkUI_ListItemSwipeActionState](#arkui_listitemswipeactionstate) | ArkUI_ListItemSwipeActionState | Enumerates the swipe states of a list item in the [swipeAction](./arkui-ts/ts-container-listitem.md#swipeaction9) API of the [ListItem](./arkui-ts/ts-container-listitem.md#listitem10) component. |
| [ArkUI_ListItemSwipeEdgeEffect](#arkui_listitemswipeedgeeffect) | ArkUI_ListItemSwipeEdgeEffect | Enumerates the edge swipe effects of the [swipeAction](./arkui-ts/ts-container-listitem.md#swipeaction9) API of the [ListItem](./arkui-ts/ts-container-listitem.md#listitem10) component. |
| [ArkUI_ListItemSwipeActionDirection](#arkui_listitemswipeactiondirection) | ArkUI_ListItemSwipeActionDirection | Enumerates the swipe action menu display directions for the **ListItem** component. |

### Functions

| Name | Description |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem\* OH_ArkUI_ListItemSwipeActionItem_Create()](#oh_arkui_listitemswipeactionitem_create) | Creates an item configuration set by the **swipeAction** API of the **ListItem** component. |
| [void OH_ArkUI_ListItemSwipeActionItem_Dispose(ArkUI_ListItemSwipeActionItem\* item)](#oh_arkui_listitemswipeactionitem_dispose) | Disposes of the **ListItemSwipeActionItem** instance created by **OH_ArkUI_ListItemSwipeActionItem_Create**. |
| [void OH_ArkUI_ListItemSwipeActionItem_SetContent(ArkUI_ListItemSwipeActionItem\* item, ArkUI_NodeHandle node)](#oh_arkui_listitemswipeactionitem_setcontent) | Sets the layout content of **ListItemSwipeActionItem**. |
| [void OH_ArkUI_ListItemSwipeActionItem_SetActionAreaDistance(ArkUI_ListItemSwipeActionItem\* item, float distance)](#oh_arkui_listitemswipeactionitem_setactionareadistance) | Sets the swipe distance threshold for deleting the list item. |
| [float OH_ArkUI_ListItemSwipeActionItem_GetActionAreaDistance(ArkUI_ListItemSwipeActionItem\* item)](#oh_arkui_listitemswipeactionitem_getactionareadistance) | Obtains the swipe distance threshold for deleting the list item. |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionArea(ArkUI_ListItemSwipeActionItem\* item, void (\*callback)())](#oh_arkui_listitemswipeactionitem_setonenteractionarea) | Sets the callback invoked each time the list item enters the delete area. |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionAreaWithUserData(ArkUI_ListItemSwipeActionItem\* item, void\* userData, void (\*callback)(void\* userData))](#oh_arkui_listitemswipeactionitem_setonenteractionareawithuserdata) | Sets the callback invoked each time the list item enters the delete area. The callback event will carry user-defined data. |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnAction(ArkUI_ListItemSwipeActionItem\* item, void (\*callback)())](#oh_arkui_listitemswipeactionitem_setonaction) | Sets the callback invoked each time the list item is deleted while in the delete area. |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnActionWithUserData(ArkUI_ListItemSwipeActionItem\* item, void\* userData, void (\*callback)(void\* userData))](#oh_arkui_listitemswipeactionitem_setonactionwithuserdata) | Sets the callback invoked each time the list item is deleted while in the delete area. The callback event will carry user-defined data. |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionArea(ArkUI_ListItemSwipeActionItem\* item, void (\*callback)())](#oh_arkui_listitemswipeactionitem_setonexitactionarea) | Sets the callback invoked when the list item exits the delete area. |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionAreaWithUserData(ArkUI_ListItemSwipeActionItem\* item, void\* userData, void (\*callback)(void\* userData))](#oh_arkui_listitemswipeactionitem_setonexitactionareawithuserdata) | Sets the callback invoked when the list item exits the delete area. The callback event will carry user-defined data. |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnStateChange(ArkUI_ListItemSwipeActionItem\* item, void (\*callback)(ArkUI_ListItemSwipeActionState swipeActionState))](#oh_arkui_listitemswipeactionitem_setonstatechange) | Sets the callback invoked when the swipe state of the list item changes. |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnStateChangeWithUserData(ArkUI_ListItemSwipeActionItem\* item, void\* userData, void (\*callback)(ArkUI_ListItemSwipeActionState swipeActionState, void\* userData))](#oh_arkui_listitemswipeactionitem_setonstatechangewithuserdata) | Sets the callback invoked when the swipe state of the list item changes. The callback event will carry user-defined data. |
| [ArkUI_ListItemSwipeActionOption\* OH_ArkUI_ListItemSwipeActionOption_Create()](#oh_arkui_listitemswipeactionoption_create) | Creates a configuration option set by the **swipeAction** API of the **ListItem** component. |
| [void OH_ArkUI_ListItemSwipeActionOption_Dispose(ArkUI_ListItemSwipeActionOption\* option)](#oh_arkui_listitemswipeactionoption_dispose) | Disposes of the **ListItemSwipeActionOption** instance created by **OH_ArkUI_ListItemSwipeActionOption_Create**. |
| [void OH_ArkUI_ListItemSwipeActionOption_SetStart(ArkUI_ListItemSwipeActionOption\* option, ArkUI_ListItemSwipeActionItem\* item)](#oh_arkui_listitemswipeactionoption_setstart) | Sets the layout content of **ListItemSwipeActionItem** on the left (in vertical layout) or top (in horizontal layout). |
| [void OH_ArkUI_ListItemSwipeActionOption_SetEnd(ArkUI_ListItemSwipeActionOption\* option, ArkUI_ListItemSwipeActionItem\* item)](#oh_arkui_listitemswipeactionoption_setend) | Sets the layout content of **ListItemSwipeActionItem** on the right (in vertical layout) or bottom (in horizontal layout). |
| [void OH_ArkUI_ListItemSwipeActionOption_SetEdgeEffect(ArkUI_ListItemSwipeActionOption\* option, ArkUI_ListItemSwipeEdgeEffect edgeEffect)](#oh_arkui_listitemswipeactionoption_setedgeeffect) | Sets the edge swipe effect. |
| [int32_t OH_ArkUI_ListItemSwipeActionOption_GetEdgeEffect(ArkUI_ListItemSwipeActionOption\* option)](#oh_arkui_listitemswipeactionoption_getedgeeffect) | Obtains the edge swipe effect. |
| [void OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChange(ArkUI_ListItemSwipeActionOption\* option, void (\*callback)(float offset))](#oh_arkui_listitemswipeactionoption_setonoffsetchange) | Sets the callback invoked when the swipe operation offset changes. |
| [void OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChangeWithUserData(ArkUI_ListItemSwipeActionOption\* option, void\* userData, void (\*callback)(float offset, void\* userData))](#oh_arkui_listitemswipeactionoption_setonoffsetchangewithuserdata) | Sets the callback invoked when the swipe operation offset changes. The callback event will carry user-defined data. |
| [int32_t OH_ArkUI_ListItemSwipeAction_Expand(ArkUI_NodeHandle node, ArkUI_ListItemSwipeActionDirection direction)](#oh_arkui_listitemswipeaction_expand) | Expands the swipe-out menu of the specified list item. |
| [int32_t OH_ArkUI_ListItemSwipeAction_Collapse(ArkUI_NodeHandle node)](#oh_arkui_listitemswipeaction_collapse) | Collapses the swipe-out menu of the specified list item. |

## Enum Description

### ArkUI_ListItemSwipeActionState

```c
enum ArkUI_ListItemSwipeActionState
```

**Description**

Enumerates the swipe states of a list item in the [swipeAction](./arkui-ts/ts-container-listitem.md#swipeaction9) API of the [ListItem](./arkui-ts/ts-container-listitem.md#listitem10) component. A swipe action is performed horizontally in a vertical list and vertically in a horizontal list. The default value is **ARKUI_LIST_ITEM_SWIPE_ACTION_STATE_COLLAPSED**.

**Since:** 12

| Value | Description |
| -- | -- |
| ARKUI_LIST_ITEM_SWIPE_ACTION_STATE_COLLAPSED = 0 | Collapsed. The action items are hidden. |
| ARKUI_LIST_ITEM_SWIPE_ACTION_STATE_EXPANDED = 1 | Expanded. The action items are displayed. |
| ARKUI_LIST_ITEM_SWIPE_ACTION_STATE_ACTIONING = 2 | Long swipe state, indicating that the list item is in the delete operation after entering the area of the swipe distance for deleting the list item. |

### ArkUI_ListItemSwipeEdgeEffect

```c
enum ArkUI_ListItemSwipeEdgeEffect
```

**Description**

Defines the edge swipe effects of the [swipeAction](./arkui-ts/ts-container-listitem.md#swipeaction9) API of the **ListItem** component. The default value is **ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_SPRING**. The swipe-out component refers to the action item content displayed during a swipe action.

**Since:** 12

| Value | Description |
| -- | -- |
| ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_SPRING = 0 | The list item can continue to swipe after the swipe distance exceeds the size of the swipe-out component. |
| ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_NONE = 1 | The swipe distance of the list item cannot exceed the size of the swipe-out component. |

### ArkUI_ListItemSwipeActionDirection

```c
enum ArkUI_ListItemSwipeActionDirection
```

**Description**

Enumerates the swipe action menu display directions for the **ListItem** component.

**Since:** 21

| Value | Description |
| -- | -- |
| ARKUI_LIST_ITEM_SWIPE_ACTION_DIRECTION_START = 0 | When the list direction is vertical, this value indicates the left side of the list item in LTR mode and the right side in RTL mode. When the list direction is horizontal, this value indicates the top side of the list item. |
| ARKUI_LIST_ITEM_SWIPE_ACTION_DIRECTION_END = 1 | When the list direction is vertical, this value indicates the right side of the list item in LTR mode and the left side in RTL mode. When the list direction is horizontal, this value indicates the bottom side of the list item. |

## Function Description

### OH_ArkUI_ListItemSwipeActionItem_Create()

```c
ArkUI_ListItemSwipeActionItem* OH_ArkUI_ListItemSwipeActionItem_Create()
```

**Description**

Creates an item configuration set by the **swipeAction** API of the **ListItem** component.

**Since:** 12

**Returns**

| Type                                 | Description |
|------------------------------------| -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)\* | Pointer to the **ListItemSwipeActionItem** configuration instance, which is used to set the layout content of a swipe action item, the swipe distance threshold for deleting the list item, and the swipe state change callback. |

### OH_ArkUI_ListItemSwipeActionItem_Dispose()

```c
void OH_ArkUI_ListItemSwipeActionItem_Dispose(ArkUI_ListItemSwipeActionItem* item)
```

**Description**

Disposes of the **ListItemSwipeActionItem** instance created by **OH_ArkUI_ListItemSwipeActionItem_Create**. Call this API to release the instance after use to avoid memory leaks.

**Since:** 12

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)\* item | Pointer to the **ListItemSwipeActionItem** instance to dispose of. |

### OH_ArkUI_ListItemSwipeActionItem_SetContent()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetContent(ArkUI_ListItemSwipeActionItem* item, ArkUI_NodeHandle node)
```

**Description**

Sets the layout content of **ListItemSwipeActionItem**.

**Since:** 12

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)\* item | Pointer to the **ListItemSwipeActionItem** instance. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Content node of the swipe action item. If not set, the swipe action item has no content to display. |

### OH_ArkUI_ListItemSwipeActionItem_SetActionAreaDistance()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetActionAreaDistance(ArkUI_ListItemSwipeActionItem* item, float distance)
```

**Description**

Sets the swipe distance threshold for deleting the list item, that is, the distance for triggering list item deletion by swipe. When the swipe-out component is fully swiped out and the user continues swiping, and the threshold is greater than 0 and less than the size of the list item in the swipe direction minus the size of the swipe-out component in the swipe direction, the list item enters the delete area once the continued swipe distance reaches or exceeds the threshold.

**Since:** 12

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)\* item | Pointer to the **ListItemSwipeActionItem** instance. |
| float distance | Swipe distance threshold for deleting the list item, in vp. The default value is **56vp**. If the value is less than or equal to 0, or greater than or equal to the size of the list item in the swipe direction minus the size of the swipe-out component in the swipe direction, the delete area will not be formed. When the list item enters the delete area, the callback set by **OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionArea** or **OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionAreaWithUserData** will be triggered; when the list item exits the delete area, the callback set by **OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionArea** or **OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionAreaWithUserData** will be triggered. It is recommended to use this parameter together with the callback set by **OH_ArkUI_ListItemSwipeActionItem_SetOnAction** or **OH_ArkUI_ListItemSwipeActionItem_SetOnActionWithUserData**. |

### OH_ArkUI_ListItemSwipeActionItem_GetActionAreaDistance()

```c
float OH_ArkUI_ListItemSwipeActionItem_GetActionAreaDistance(ArkUI_ListItemSwipeActionItem* item)
```

**Description**

Obtains the swipe distance threshold for deleting the list item.

**Since:** 12

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)\* item | Pointer to the **ListItemSwipeActionItem** instance. |

**Returns**

| Type | Description |
| -- | -- |
| float | Swipe distance threshold for deleting the list item, in vp. The default value **56vp** is returned when it is not explicitly set, and **-1.0f** is returned when an exception occurs. |

### OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionArea()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionArea(ArkUI_ListItemSwipeActionItem* item, void (*callback)())
```

**Description**

Sets the callback invoked each time the list item enters the delete area. This callback is triggered only when the swipe distance threshold for deleting the list item is valid and a delete area is formed.

**Since:** 12

**Parameters**

| Name                                     | Description |
|-----------------------------------------| -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)\* item | Pointer to the **ListItemSwipeActionItem** instance. |
| void (\*callback)()                       | Pointer to the callback event. |

### OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionAreaWithUserData()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionAreaWithUserData(ArkUI_ListItemSwipeActionItem* item, void* userData, void (*callback)(void* userData))
```

**Description**

Sets the callback invoked each time the list item enters the delete area. The callback event will carry user-defined data. It is triggered only when the swipe distance threshold for deleting the list item is valid and a delete area is formed.

**Since:** 12

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)\* item | Pointer to the **ListItemSwipeActionItem** instance. |
| void\* userData | Pointer to the user-defined data. |
| void (\*callback)(void\* userData) | Pointer to the callback event. |

### OH_ArkUI_ListItemSwipeActionItem_SetOnAction()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnAction(ArkUI_ListItemSwipeActionItem* item, void (*callback)())
```

**Description**

Sets the callback invoked each time the [list item](./arkui-ts/ts-container-listitem.md) is deleted while in the delete area. The callback is triggered only when the distance threshold for deleting the list item is within the valid range (greater than 0 and less than the size of the list item in the swipe direction minus the size of the swipe-out component in the swipe direction), and the release position after swiping exceeds or reaches threshold.

**Since:** 12

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)\* item | Pointer to the **ListItemSwipeActionItem** instance. |
| void (\*callback)() | Pointer to the callback event. |

### OH_ArkUI_ListItemSwipeActionItem_SetOnActionWithUserData()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnActionWithUserData(ArkUI_ListItemSwipeActionItem* item, void* userData, void (*callback)(void* userData))
```

**Description**

Sets the callback invoked each time the list item is deleted while in the delete area. The callback event will carry user-defined data. The callback is triggered only when the distance threshold for deleting the list item is within the valid range (greater than 0 and less than the size of the list item in the swipe direction minus the size of the swipe-out component in the swipe direction), and the release position after swiping exceeds or reaches the threshold.

**Since:** 12

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)\* item | Pointer to the **ListItemSwipeActionItem** instance. |
| void\* userData | Pointer to the user-defined data. |
| void (\*callback)(void\* userData) | Pointer to the callback event. |

### OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionArea()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionArea(ArkUI_ListItemSwipeActionItem* item, void (*callback)())
```

**Description**

Sets the callback invoked each time the list item exits the delete area. This callback is triggered only when the swipe distance threshold for deleting the list item is valid and a delete area is formed.

**Since:** 12

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)\* item | Pointer to the **ListItemSwipeActionItem** instance. |
| void (\*callback)() | Pointer to the callback event. |

### OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionAreaWithUserData()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionAreaWithUserData(ArkUI_ListItemSwipeActionItem* item, void* userData, void (*callback)(void* userData))
```

**Description**

Sets the callback invoked each time the list item exits the delete area. The callback event will carry user-defined data. It is triggered only when the swipe distance threshold for deleting the list item is valid and a delete area is formed.

**Since:** 12

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)\* item | Pointer to the **ListItemSwipeActionItem** instance. |
| void\* userData | Pointer to the user-defined data. |
| void (\*callback)(void\* userData) | Pointer to the callback event. |

### OH_ArkUI_ListItemSwipeActionItem_SetOnStateChange()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnStateChange(ArkUI_ListItemSwipeActionItem* item, void (*callback)(ArkUI_ListItemSwipeActionState swipeActionState))
```

**Description**

Sets the callback invoked when the swipe state of the list item changes. The swipe state of a list item switches among the collapsed, expanded, and long swipe distance. For details about the states, see [ArkUI_ListItemSwipeActionState](#arkui_listitemswipeactionstate).

**Since:** 12

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)\* item | Pointer to the **ListItemSwipeActionItem** instance. |
| void (\*callback)(ArkUI_ListItemSwipeActionState swipeActionState) | Pointer to the callback event. The input parameter is **swipeActionState**, which indicates the swipe state of the list item. |

### OH_ArkUI_ListItemSwipeActionItem_SetOnStateChangeWithUserData()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnStateChangeWithUserData(ArkUI_ListItemSwipeActionItem* item, void* userData, void (*callback)(ArkUI_ListItemSwipeActionState swipeActionState, void* userData))
```

**Description**

Sets the callback invoked when the swipe state of the list item changes. The callback event will carry user-defined data. The swipe state of a list item switches among the collapsed, expanded, and long swipe distance. For details about the states, see [ArkUI_ListItemSwipeActionState](#arkui_listitemswipeactionstate).

**Since:** 12

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)\* item | Pointer to the **ListItemSwipeActionItem** instance. |
| void\* userData | Pointer to the user-defined data. |
| void (\*callback)(ArkUI_ListItemSwipeActionState swipeActionState, void\* userData) | Pointer to the callback event. The input parameter is **swipeActionState**, which indicates the swipe state of the list item. |

### OH_ArkUI_ListItemSwipeActionOption_Create()

```c
ArkUI_ListItemSwipeActionOption* OH_ArkUI_ListItemSwipeActionOption_Create()
```

**Description**

Creates a configuration option set by the **swipeAction** API of the **ListItem** component.

**Since:** 12

**Returns**

| Type                                   | Description |
|--------------------------------------| -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)\* | Pointer to the **ListItemSwipeActionOption** instance, used to set the layout content, edge swipe effect, and offset change callback of the **ListItem** component's swipe action items on the start side and end side. |

### OH_ArkUI_ListItemSwipeActionOption_Dispose()

```c
void OH_ArkUI_ListItemSwipeActionOption_Dispose(ArkUI_ListItemSwipeActionOption* option)
```

**Description**

Disposes of the **ListItemSwipeActionOption** instance created by **OH_ArkUI_ListItemSwipeActionOption_Create**. Call this API to release the instance after use to avoid memory leaks.

**Since:** 12

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)\* option | Pointer to the **ListItemSwipeActionOption** instance to dispose of. |

### OH_ArkUI_ListItemSwipeActionOption_SetStart()

```c
void OH_ArkUI_ListItemSwipeActionOption_SetStart(ArkUI_ListItemSwipeActionOption* option, ArkUI_ListItemSwipeActionItem* item)
```

**Description**

Sets the layout content of **ListItemSwipeActionItem** on the left (in vertical layout) or top (in horizontal layout). This layout content can be expanded programmatically through the **OH_ArkUI_ListItemSwipeAction_Expand** API.

**Since:** 12

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)\* option | Pointer to the **ListItemSwipeActionOption** instance. |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)\* item | Pointer to the **ListItemSwipeActionItem** instance to be set on the start side. If not set, no swipe action item is displayed on the start side of **ListItem**. |

### OH_ArkUI_ListItemSwipeActionOption_SetEnd()

```c
void OH_ArkUI_ListItemSwipeActionOption_SetEnd(ArkUI_ListItemSwipeActionOption* option, ArkUI_ListItemSwipeActionItem* item)
```

**Description**

Sets the layout content of **ListItemSwipeActionItem** on the right side (vertical layout) or bottom side (horizontal layout). This layout content can be programmatically expanded through the **OH_ArkUI_ListItemSwipeAction_Expand** API.

**Since:** 12

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)\* option | Pointer to the **ListItemSwipeActionOption** instance. |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)\* item | Pointer to the **ListItemSwipeActionItem** instance to be set on the end side. If not set, no swipe action item is displayed on the end side of **ListItem**. |

### OH_ArkUI_ListItemSwipeActionOption_SetEdgeEffect()

```c
void OH_ArkUI_ListItemSwipeActionOption_SetEdgeEffect(ArkUI_ListItemSwipeActionOption* option, ArkUI_ListItemSwipeEdgeEffect edgeEffect)
```

**Description**

Sets the edge swipe effect. Use **ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_SPRING** when the swipe distance is allowed to exceed the size of the swipe-out component; use **ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_NONE** when the swipe distance must not exceed the size of the swipe-out component.

**Since:** 12

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)\* option | Pointer to the **ListItemSwipeActionOption** instance. |
| [ArkUI_ListItemSwipeEdgeEffect](#arkui_listitemswipeedgeeffect) edgeEffect | Edge swipe effect. |

### OH_ArkUI_ListItemSwipeActionOption_GetEdgeEffect()

```c
int32_t OH_ArkUI_ListItemSwipeActionOption_GetEdgeEffect(ArkUI_ListItemSwipeActionOption* option)
```

**Description**

Obtains the edge swipe effect.

**Since:** 12

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)\* option | Pointer to the **ListItemSwipeActionOption** instance. |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | Edge swipe effect. The value can be [ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_SPRING](#arkui_listitemswipeedgeeffect) (**0**) or [ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_NONE](#arkui_listitemswipeedgeeffect) (**1**). The default return value is [ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_SPRING](#arkui_listitemswipeedgeeffect), and **-1** is returned in the case of an exception. |

### OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChange()

```c
void OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChange(ArkUI_ListItemSwipeActionOption* option, void (*callback)(float offset))
```

**Description**

Sets the callback invoked when the offset of a swipe action changes.

**Since:** 12

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)\* option | Pointer to the **ListItemSwipeActionOption** instance. |
| void (\*callback)(float offset) | Pointer to the callback event. **offset** indicates the swipe offset, in vp. This callback may be triggered frequently during the swipe process. Avoid performing time-consuming operations in it. |

### OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChangeWithUserData()

```c
void OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChangeWithUserData(ArkUI_ListItemSwipeActionOption* option, void* userData, void (*callback)(float offset, void* userData))
```

**Description**

Sets the callback invoked when the offset of a swipe action changes. The callback event will carry user-defined data.

**Since:** 12

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)\* option | Pointer to the **ListItemSwipeActionOption** instance. |
| void\* userData | User-defined data. |
| void (\*callback)(float offset, void\* userData) | Pointer to the callback event. **offset** indicates the swipe offset, in vp. This callback may be triggered frequently during the swipe process. Avoid performing time-consuming operations in it. |

### OH_ArkUI_ListItemSwipeAction_Expand()

```c
int32_t OH_ArkUI_ListItemSwipeAction_Expand(ArkUI_NodeHandle node, ArkUI_ListItemSwipeActionDirection direction)
```

**Description**

Expands the swipe-out menu (that is, the action item area displayed during a swipe action) of the specified list item. When **direction** is set to **ARKUI_LIST_ITEM_SWIPE_ACTION_DIRECTION_START**, the swipe-out menu set through **OH_ArkUI_ListItemSwipeActionOption_SetStart** is expanded. When **direction** is set to **ARKUI_LIST_ITEM_SWIPE_ACTION_DIRECTION_END**, the swipe-out menu set through **OH_ArkUI_ListItemSwipeActionOption_SetEnd** is expanded. The expanded swipe-out menu can be collapsed through **OH_ArkUI_ListItemSwipeAction_Collapse**. This API can also be called after the application responds to a user tap on a button such as "More" to expand the swipe-out menu programmatically.

**Since:** 21

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | **ListItem** node object. |
| [ArkUI_ListItemSwipeActionDirection](#arkui_listitemswipeactiondirection) direction | Expansion direction of the **ListItem** swipe-out menu. |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the type of the passed-in node object is incorrect. Check whether the passed-in node is a **ListItem** node.<br>         Returns [ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the passed-in node is not mounted to the component tree. Mount the node to the component tree before performing this operation. |

> **NOTE**
>
> - If the **List** component has the **NODE_LIST_CACHED_COUNT** attribute set to enable preloading, list items outside the **List** display area that have been preloaded support expansion. Otherwise, the nodes outside the **List** display area do not support expansion.

### OH_ArkUI_ListItemSwipeAction_Collapse()

```c
int32_t OH_ArkUI_ListItemSwipeAction_Collapse(ArkUI_NodeHandle node)
```

**Description**

Collapses the swipe-out menu (that is, the action item area displayed during a swipe action) of the specified list item that has been expanded by **OH_ArkUI_ListItemSwipeAction_Expand**. It can also be called programmatically when the user completes the swipe-out menu operation or switches to another list item.

> **NOTE**
>
> - If the **List** component has the **NODE_LIST_CACHED_COUNT** attribute set to enable preloading, list items outside the **List** display area that have been preloaded support collapsing; otherwise, the nodes outside the **List** display area do not support collapsing.

**Since:** 21

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | **ListItem** node object. |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the type of the passed-in node object is incorrect. Check whether the passed-in node is a **ListItem** node.<br>         Returns [ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the passed-in node is not mounted to the component tree. Mount the node to the component tree before performing this operation. | 