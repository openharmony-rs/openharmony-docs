# list_item.h

## Overview

Provides shared list item-related type and function definitions for <b>NativeNode</b> APIs.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md) | ArkUI_ListItemSwipeActionItem | Defines the configuration information of an item in the **ListItemSwipeActionOption**. |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md) | ArkUI_ListItemSwipeActionOption | Defines the configuration information of the **ListItemSwipeActionOption**. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_ListItemSwipeActionState](#arkui_listitemswipeactionstate) | ArkUI_ListItemSwipeActionState | Enumerates the swipe action states of a {@link ListItem}. The default value is **<br>ARKUI_LIST_ITEM_SWIPE_ACTION_STATE_COLLAPSED**. |
| [ArkUI_ListItemSwipeEdgeEffect](#arkui_listitemswipeedgeeffect) | ArkUI_ListItemSwipeEdgeEffect | Enumerates the edge effects of the swipe action for the {@link ListItem} component. The default value is **<br>ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_SPRING**. |
| [ArkUI_ListItemSwipeActionDirection](#arkui_listitemswipeactiondirection) | ArkUI_ListItemSwipeActionDirection | Enumerates the directions to expand the swipe action of a {@link ListItem}. |

### Function

| Name | Description |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem* OH_ArkUI_ListItemSwipeActionItem_Create()](#oh_arkui_listitemswipeactionitem_create) | Creates a **ListItemSwipeActionItem** instance. |
| [void OH_ArkUI_ListItemSwipeActionItem_Dispose(ArkUI_ListItemSwipeActionItem* item)](#oh_arkui_listitemswipeactionitem_dispose) | Disposes of a **ListItemSwipeActionItem** instance. |
| [void OH_ArkUI_ListItemSwipeActionItem_SetContent(ArkUI_ListItemSwipeActionItem* item, ArkUI_NodeHandle node)](#oh_arkui_listitemswipeactionitem_setcontent) | Sets the layout content of the **ListItemSwipeActionItem**. |
| [void OH_ArkUI_ListItemSwipeActionItem_SetActionAreaDistance(ArkUI_ListItemSwipeActionItem* item, float distance)](#oh_arkui_listitemswipeactionitem_setactionareadistance) | Sets the threshold for the long-distance sliding deletion distance of the component. |
| [float OH_ArkUI_ListItemSwipeActionItem_GetActionAreaDistance(ArkUI_ListItemSwipeActionItem* item)](#oh_arkui_listitemswipeactionitem_getactionareadistance) | Obtains the threshold for the long-distance sliding deletion distance of the component. |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionArea(ArkUI_ListItemSwipeActionItem* item, void (\*callback)())](#oh_arkui_listitemswipeactionitem_setonenteractionarea) | Sets the event to be called when a sliding entry enters the deletion area. |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionAreaWithUserData(ArkUI_ListItemSwipeActionItem* item, void* userData, void (\*callback)(void* userData))](#oh_arkui_listitemswipeactionitem_setonenteractionareawithuserdata) | Sets the event triggered when a sliding entry enters the deletion area, with user data. |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnAction(ArkUI_ListItemSwipeActionItem* item, void (\*callback)())](#oh_arkui_listitemswipeactionitem_setonaction) | Sets the event to be called when a component enters the long-range deletion area and deletes a {@link ListItem}. |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnActionWithUserData(ArkUI_ListItemSwipeActionItem* item, void* userData, void (\*callback)(void* userData))](#oh_arkui_listitemswipeactionitem_setonactionwithuserdata) | Sets the event triggered when a component enters the long-range deletion area and deletes a {@link ListItem}, with user data. |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionArea(ArkUI_ListItemSwipeActionItem* item, void (\*callback)())](#oh_arkui_listitemswipeactionitem_setonexitactionarea) | Sets the event to be called when a sliding entry exits the deletion area. |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionAreaWithUserData(ArkUI_ListItemSwipeActionItem* item, void* userData, void (\*callback)(void* userData))](#oh_arkui_listitemswipeactionitem_setonexitactionareawithuserdata) | Sets the event triggered when a sliding entry exits the deletion area, with user data. |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnStateChange(ArkUI_ListItemSwipeActionItem* item, void (\*callback)(ArkUI_ListItemSwipeActionState swipeActionState))](#oh_arkui_listitemswipeactionitem_setonstatechange) | Sets the event triggered when the sliding state of a {@link ListItem} changes. |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnStateChangeWithUserData(ArkUI_ListItemSwipeActionItem* item, void* userData, void (\*callback)(ArkUI_ListItemSwipeActionState swipeActionState, void* userData))](#oh_arkui_listitemswipeactionitem_setonstatechangewithuserdata) | Sets the event triggered when the sliding state of a {@link ListItem} changes, with user data. |
| [ArkUI_ListItemSwipeActionOption* OH_ArkUI_ListItemSwipeActionOption_Create()](#oh_arkui_listitemswipeactionoption_create) | Creates a **ListItemSwipeActionOption** instance. |
| [void OH_ArkUI_ListItemSwipeActionOption_Dispose(ArkUI_ListItemSwipeActionOption* option)](#oh_arkui_listitemswipeactionoption_dispose) | Disposes of a **ListItemSwipeActionOption** instance. |
| [void OH_ArkUI_ListItemSwipeActionOption_SetStart(ArkUI_ListItemSwipeActionOption* option, ArkUI_ListItemSwipeActionItem* item)](#oh_arkui_listitemswipeactionoption_setstart) | Sets the layout content on the left (vertical layout) or top (horizontal layout) of the **ListItemSwipeActionItem**. |
| [void OH_ArkUI_ListItemSwipeActionOption_SetEnd(ArkUI_ListItemSwipeActionOption* option, ArkUI_ListItemSwipeActionItem* item)](#oh_arkui_listitemswipeactionoption_setend) | Sets the layout content on the right (vertical layout) or bottom (horizontal layout) of the **ListItemSwipeActionItem**. |
| [void OH_ArkUI_ListItemSwipeActionOption_SetEdgeEffect(ArkUI_ListItemSwipeActionOption* option, ArkUI_ListItemSwipeEdgeEffect edgeEffect)](#oh_arkui_listitemswipeactionoption_setedgeeffect) | Sets the sliding effect. |
| [int32_t OH_ArkUI_ListItemSwipeActionOption_GetEdgeEffect(ArkUI_ListItemSwipeActionOption* option)](#oh_arkui_listitemswipeactionoption_getedgeeffect) | Obtains the sliding effect. |
| [void OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChange(ArkUI_ListItemSwipeActionOption* option, void (\*callback)(float offset))](#oh_arkui_listitemswipeactionoption_setonoffsetchange) | Sets the event called when the sliding operation offset changes. |
| [void OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChangeWithUserData(ArkUI_ListItemSwipeActionOption* option, void* userData, void (\*callback)(float offset, void* userData))](#oh_arkui_listitemswipeactionoption_setonoffsetchangewithuserdata) | Sets the event triggered when the sliding operation offset changes, with user data. |
| [int32_t OH_ArkUI_ListItemSwipeAction_Expand(ArkUI_NodeHandle node, ArkUI_ListItemSwipeActionDirection direction)](#oh_arkui_listitemswipeaction_expand) | Expands the swipe action. |
| [int32_t OH_ArkUI_ListItemSwipeAction_Collapse(ArkUI_NodeHandle node)](#oh_arkui_listitemswipeaction_collapse) | Collapses the swipe action. |

## Enum type description

### ArkUI_ListItemSwipeActionState

```c
enum ArkUI_ListItemSwipeActionState
```

**Description**

Enumerates the swipe action states of a {@link ListItem}. The default value is **<br>ARKUI_LIST_ITEM_SWIPE_ACTION_STATE_COLLAPSED**.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_LIST_ITEM_SWIPE_ACTION_STATE_COLLAPSED = 0 | Collapsed state. When the list item slides in the direction opposite to the main axis, the operation item is hidden. |
| ARKUI_LIST_ITEM_SWIPE_ACTION_STATE_EXPANDED | Expanded state. When the list item slides in the direction opposite to the main axis, the operation item is displayed. |
| ARKUI_LIST_ITEM_SWIPE_ACTION_STATE_ACTIONING | Actioning state. This state is triggered when the list item enters the long-distance deletion area and is deleted. |

### ArkUI_ListItemSwipeEdgeEffect

```c
enum ArkUI_ListItemSwipeEdgeEffect
```

**Description**

Enumerates the edge effects of the swipe action for the {@link ListItem} component. The default value is **<br>ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_SPRING**.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_SPRING = 0 | The list item can continue to slide after the sliding distance exceeds the size of the operation item. |
| ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_NONE | The sliding distance of the list item cannot exceed the size of the operation item. |

### ArkUI_ListItemSwipeActionDirection

```c
enum ArkUI_ListItemSwipeActionDirection
```

**Description**

Enumerates the directions to expand the swipe action of a {@link ListItem}.

**Since**: 21

| Enum item | Description |
| -- | -- |
| ARKUI_LIST_ITEM_SWIPE_ACTION_DIRECTION_START = 0 | When the list direction is vertical, it indicates the left in LTR mode and right in RTL mode. When the list direction is horizontal, it indicates the top. |
| ARKUI_LIST_ITEM_SWIPE_ACTION_DIRECTION_END = 1 | When the list direction is vertical, it indicates the right in LTR mode and left in RTL mode. When the list direction is horizontal, it indicates the bottom. |


## Function description

### OH_ArkUI_ListItemSwipeActionItem_Create()

```c
ArkUI_ListItemSwipeActionItem* OH_ArkUI_ListItemSwipeActionItem_Create()
```

**Description**

Creates a **ListItemSwipeActionItem** instance.

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem*](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md) | Pointer to the created ListItemSwipeActionItem instance. If a null pointer is returned, it indicates a  creation failure. The possible cause is that the address space is full. |

### OH_ArkUI_ListItemSwipeActionItem_Dispose()

```c
void OH_ArkUI_ListItemSwipeActionItem_Dispose(ArkUI_ListItemSwipeActionItem* item)
```

**Description**

Disposes of a **ListItemSwipeActionItem** instance.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | Pointer to the **ListItemSwipeActionItem** instance to dispose of. |

### OH_ArkUI_ListItemSwipeActionItem_SetContent()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetContent(ArkUI_ListItemSwipeActionItem* item, ArkUI_NodeHandle node)
```

**Description**

Sets the layout content of the **ListItemSwipeActionItem**.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | Pointer to the **ListItemSwipeActionItem** instance. |
| ArkUI_NodeHandle node | Layout information. |

### OH_ArkUI_ListItemSwipeActionItem_SetActionAreaDistance()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetActionAreaDistance(ArkUI_ListItemSwipeActionItem* item, float distance)
```

**Description**

Sets the threshold for the long-distance sliding deletion distance of the component.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | Pointer to the **ListItemSwipeActionItem** instance. |
| float distance | Threshold for the long-distance sliding deletion distance of the component. |

### OH_ArkUI_ListItemSwipeActionItem_GetActionAreaDistance()

```c
float OH_ArkUI_ListItemSwipeActionItem_GetActionAreaDistance(ArkUI_ListItemSwipeActionItem* item)
```

**Description**

Obtains the threshold for the long-distance sliding deletion distance of the component.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | Pointer to the **ListItemSwipeActionItem** instance. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Threshold for the long-distance sliding deletion distance of the component. If -1.0f is returned, the  operation fails. The possible cause is that the item parameter is abnormal, such as a null pointer. |

### OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionArea()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionArea(ArkUI_ListItemSwipeActionItem* item, void (*callback)())
```

**Description**

Sets the event to be called when a sliding entry enters the deletion area.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_ListItemSwipeActionItem\* item | Pointer to the **ListItemSwipeActionItem** instance. |
| void (\*callback)() | Callback event. |

### OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionAreaWithUserData()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionAreaWithUserData(ArkUI_ListItemSwipeActionItem* item, void* userData, void (*callback)(void* userData))
```

**Description**

Sets the event triggered when a sliding entry enters the deletion area, with user data.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_ListItemSwipeActionItem\* item | Pointer to the **ListItemSwipeActionItem** instance. |
| void\* userData | User-defined data. |
| void (\*callback)(void\* userData) | Callback event. |

### OH_ArkUI_ListItemSwipeActionItem_SetOnAction()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnAction(ArkUI_ListItemSwipeActionItem* item, void (*callback)())
```

**Description**

Sets the event to be called when a component enters the long-range deletion area and deletes a {@link ListItem}.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_ListItemSwipeActionItem\* item | Pointer to the **ListItemSwipeActionItem** instance. |
| void (\*callback)() | Callback event. |

### OH_ArkUI_ListItemSwipeActionItem_SetOnActionWithUserData()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnActionWithUserData(ArkUI_ListItemSwipeActionItem* item, void* userData, void (*callback)(void* userData))
```

**Description**

Sets the event triggered when a component enters the long-range deletion area and deletes a {@link ListItem}, with user data.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_ListItemSwipeActionItem\* item | Pointer to the **ListItemSwipeActionItem** instance. |
| void\* userData | User-defined data. |
| void (\*callback)(void\* userData) | Callback event. |

### OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionArea()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionArea(ArkUI_ListItemSwipeActionItem* item, void (*callback)())
```

**Description**

Sets the event to be called when a sliding entry exits the deletion area.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_ListItemSwipeActionItem\* item | Pointer to the **ListItemSwipeActionItem** instance. |
| void (\*callback)() | Callback event. |

### OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionAreaWithUserData()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionAreaWithUserData(ArkUI_ListItemSwipeActionItem* item, void* userData, void (*callback)(void* userData))
```

**Description**

Sets the event triggered when a sliding entry exits the deletion area, with user data.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_ListItemSwipeActionItem\* item | Pointer to the **ListItemSwipeActionItem** instance. |
| void\* userData | User-defined data. |
| void (\*callback)(void\* userData) | Callback event. |

### OH_ArkUI_ListItemSwipeActionItem_SetOnStateChange()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnStateChange(ArkUI_ListItemSwipeActionItem* item, void (*callback)(ArkUI_ListItemSwipeActionState swipeActionState))
```

**Description**

Sets the event triggered when the sliding state of a {@link ListItem} changes.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_ListItemSwipeActionItem\* item | Pointer to the **ListItemSwipeActionItem** instance. |
| void (\*callback)(ArkUI_ListItemSwipeActionState swipeActionState) | Callback event. **swipeActionState** The changed state. |

### OH_ArkUI_ListItemSwipeActionItem_SetOnStateChangeWithUserData()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnStateChangeWithUserData(ArkUI_ListItemSwipeActionItem* item, void* userData, void (*callback)(ArkUI_ListItemSwipeActionState swipeActionState, void* userData))
```

**Description**

Sets the event triggered when the sliding state of a {@link ListItem} changes, with user data.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_ListItemSwipeActionItem\* item | Pointer to the **ListItemSwipeActionItem** instance. |
| void\* userData | User-defined data. |
| void (\*callback)(ArkUI_ListItemSwipeActionState swipeActionState | Callback event. **swipeActionState** The changed state. |

### OH_ArkUI_ListItemSwipeActionOption_Create()

```c
ArkUI_ListItemSwipeActionOption* OH_ArkUI_ListItemSwipeActionOption_Create()
```

**Description**

Creates a **ListItemSwipeActionOption** instance.

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption*](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md) | Pointer to the created ListItemSwipeActionOption instance. If a null pointer is returned, it indicates a  creation failure. The possible cause is that the address space is full. |

### OH_ArkUI_ListItemSwipeActionOption_Dispose()

```c
void OH_ArkUI_ListItemSwipeActionOption_Dispose(ArkUI_ListItemSwipeActionOption* option)
```

**Description**

Disposes of a **ListItemSwipeActionOption** instance.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)* option | Pointer to the **ListItemSwipeActionOption** instance to dispose of. |

### OH_ArkUI_ListItemSwipeActionOption_SetStart()

```c
void OH_ArkUI_ListItemSwipeActionOption_SetStart(ArkUI_ListItemSwipeActionOption* option, ArkUI_ListItemSwipeActionItem* item)
```

**Description**

Sets the layout content on the left (vertical layout) or top (horizontal layout) of the **ListItemSwipeActionItem**.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)* option | Pointer to the **ListItemSwipeActionOption** instance. |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | Layout information. |

### OH_ArkUI_ListItemSwipeActionOption_SetEnd()

```c
void OH_ArkUI_ListItemSwipeActionOption_SetEnd(ArkUI_ListItemSwipeActionOption* option, ArkUI_ListItemSwipeActionItem* item)
```

**Description**

Sets the layout content on the right (vertical layout) or bottom (horizontal layout) of the **ListItemSwipeActionItem**.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)* option | Pointer to the **ListItemSwipeActionOption** instance. |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | Layout information. |

### OH_ArkUI_ListItemSwipeActionOption_SetEdgeEffect()

```c
void OH_ArkUI_ListItemSwipeActionOption_SetEdgeEffect(ArkUI_ListItemSwipeActionOption* option, ArkUI_ListItemSwipeEdgeEffect edgeEffect)
```

**Description**

Sets the sliding effect.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)* option | Pointer to the **ListItemSwipeActionOption** instance. |
| [ArkUI_ListItemSwipeEdgeEffect](capi-list-item-h.md#arkui_listitemswipeedgeeffect) edgeEffect | Sliding effect. |

### OH_ArkUI_ListItemSwipeActionOption_GetEdgeEffect()

```c
int32_t OH_ArkUI_ListItemSwipeActionOption_GetEdgeEffect(ArkUI_ListItemSwipeActionOption* option)
```

**Description**

Obtains the sliding effect.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)* option | Pointer to the **ListItemSwipeActionOption** instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Sliding effect. The default return value is 0. If -1 is returned, the operation fails. The possible  cause is that the option parameter is abnormal, such as a null pointer. |

### OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChange()

```c
void OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChange(ArkUI_ListItemSwipeActionOption* option, void (*callback)(float offset))
```

**Description**

Sets the event called when the sliding operation offset changes.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_ListItemSwipeActionOption\* option | Pointer to the **ListItemSwipeActionOption** instance. |
| void (\*callback)(float offset) | Callback event. **offset** Slide offset. |

### OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChangeWithUserData()

```c
void OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChangeWithUserData(ArkUI_ListItemSwipeActionOption* option, void* userData, void (*callback)(float offset, void* userData))
```

**Description**

Sets the event triggered when the sliding operation offset changes, with user data.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_ListItemSwipeActionOption\* option | Pointer to the **ListItemSwipeActionOption** instance. |
| void\* userData | User-defined data. |
| void (\*callback)(float offset | Callback event. **offset** Slide offset. |

### OH_ArkUI_ListItemSwipeAction_Expand()

```c
int32_t OH_ArkUI_ListItemSwipeAction_Expand(ArkUI_NodeHandle node, ArkUI_ListItemSwipeActionDirection direction)
```

**Description**

Expands the swipe action.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | List item node. |
| [ArkUI_ListItemSwipeActionDirection](capi-list-item-h.md#arkui_listitemswipeactiondirection) direction | Direction to expand the swipe action. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <ul>      <li><br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>    <li><br>Returns {@link ARKUI_ERROR_CODE_PARAM_ERROR} if the component type of the node is incorrect.</li><br>    <li><br>Returns {@link ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE} if the node is not mounted to the component      tree.</li>      </ul> |

### OH_ArkUI_ListItemSwipeAction_Collapse()

```c
int32_t OH_ArkUI_ListItemSwipeAction_Collapse(ArkUI_NodeHandle node)
```

**Description**

Collapses the swipe action.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle node | List item node. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <ul>      <li><br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>    <li><br>Returns {@link ARKUI_ERROR_CODE_PARAM_ERROR} if the component type of the node is incorrect.</li><br>    <li><br>Returns {@link ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE} if the node is not mounted to the component      tree.</li>      </ul> |


