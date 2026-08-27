# list_item.h

## 概述

Provides shared list item-related type and function definitions for <b>NativeNode</b> APIs.

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md) | ArkUI_ListItemSwipeActionItem | Defines the configuration information of an item in the **ListItemSwipeActionOption**. |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md) | ArkUI_ListItemSwipeActionOption | Defines the configuration information of the **ListItemSwipeActionOption**. |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_ListItemSwipeActionState](#arkui_listitemswipeactionstate) | ArkUI_ListItemSwipeActionState | 定义{@link ListItem}组件{@link swipeAction}方法的列表项滑动状态。侧滑操作在垂直列表中沿水平方向进行，在水平列表中沿垂直方向进行。默认值为ARKUI_LIST_ITEM_SWIPE_ACTION_STATE_COLLAPSED。 |
| [ArkUI_ListItemSwipeActionDirection](#arkui_listitemswipeactiondirection) | ArkUI_ListItemSwipeActionDirection | ListItem划出菜单的展开方向。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem* OH_ArkUI_ListItemSwipeActionItem_Create()](#oh_arkui_listitemswipeactionitem_create) | 创建ListItem组件swipeAction方法设置的Item配置项。 |
| [void OH_ArkUI_ListItemSwipeActionItem_Dispose(ArkUI_ListItemSwipeActionItem* item)](#oh_arkui_listitemswipeactionitem_dispose) | 销毁由OH_ArkUI_ListItemSwipeActionItem_Create创建的ListItemSwipeActionItem实例，使用完毕后需调用本接口释放，避免内存泄漏。 |
| [void OH_ArkUI_ListItemSwipeActionItem_SetContent(ArkUI_ListItemSwipeActionItem* item, ArkUI_NodeHandle node)](#oh_arkui_listitemswipeactionitem_setcontent) | 设置ListItemSwipeActionItem的布局内容。 |
| [void OH_ArkUI_ListItemSwipeActionItem_SetActionAreaDistance(ArkUI_ListItemSwipeActionItem* item, float distance)](#oh_arkui_listitemswipeactionitem_setactionareadistance) | 设置组件长距离滑动删除距离阈值，即列表项侧滑删除的触发距离。当划出组件被完全滑出后继续滑动，且该阈值取值大于0并小于ListItem在滑动方向上的尺寸减去划出组件在滑动方向上的尺寸时，继续滑动距离超过或等于该阈值后ListItem进入长距删除区。 |
| [float OH_ArkUI_ListItemSwipeActionItem_GetActionAreaDistance(ArkUI_ListItemSwipeActionItem* item)](#oh_arkui_listitemswipeactionitem_getactionareadistance) | 获取组件长距离滑动删除距离阈值。 |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionArea(ArkUI_ListItemSwipeActionItem* item, void (\*callback)())](#oh_arkui_listitemswipeactionitem_setonenteractionarea) | 设置滑动条目进入长距删除区时调用的事件。仅当长距删除距离阈值有效并形成长距删除区时触发。 |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionAreaWithUserData(ArkUI_ListItemSwipeActionItem* item, void* userData, void (\*callback)(void* userData))](#oh_arkui_listitemswipeactionitem_setonenteractionareawithuserdata) | 设置滑动条目进入长距删除区时调用的事件，回调事件会传入用户自定义数据。仅当长距删除距离阈值有效并形成长距删除区时触发。 |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnAction(ArkUI_ListItemSwipeActionItem* item, void (\*callback)())](#oh_arkui_listitemswipeactionitem_setonaction) | 设置滑动条目进入长距删除区后抬手删除{@link ListItem}时调用的事件。仅在删除距离阈值处于有效取值范围（大于0且小于ListItem在滑动方向上的尺寸减去划出组件在滑动方向上的尺寸），且滑动后松手位置超过或等于该阈值时触发。 |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnActionWithUserData(ArkUI_ListItemSwipeActionItem* item, void* userData, void (\*callback)(void* userData))](#oh_arkui_listitemswipeactionitem_setonactionwithuserdata) | 设置滑动条目进入长距删除区后抬手删除ListItem时调用的事件，回调事件会传入用户自定义数据。仅在删除距离阈值处于有效取值范围（大于0且小于ListItem在滑动方向上的尺寸减去划出组件在滑动方向上的尺寸），且滑动后松手位置超过或等于该阈值时触发。 |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionArea(ArkUI_ListItemSwipeActionItem* item, void (\*callback)())](#oh_arkui_listitemswipeactionitem_setonexitactionarea) | 设置滑动条目退出长距删除区时调用的事件。仅当长距删除距离阈值有效并形成长距删除区时触发。 |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionAreaWithUserData(ArkUI_ListItemSwipeActionItem* item, void* userData, void (\*callback)(void* userData))](#oh_arkui_listitemswipeactionitem_setonexitactionareawithuserdata) | 设置滑动条目退出长距删除区时调用的事件，回调事件会传入用户自定义数据。仅当长距删除距离阈值有效并形成长距删除区时触发。 |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnStateChange(ArkUI_ListItemSwipeActionItem* item, void (\*callback)(ArkUI_ListItemSwipeActionState swipeActionState))](#oh_arkui_listitemswipeactionitem_setonstatechange) | 设置列表项滑动状态变化时触发的事件。列表项滑动状态会在收起、展开和长距离状态之间切换，具体状态见[ArkUI_ListItemSwipeActionState](capi-list-item-h.md#arkui_listitemswipeactionstate)。 |
| [void OH_ArkUI_ListItemSwipeActionItem_SetOnStateChangeWithUserData(ArkUI_ListItemSwipeActionItem* item, void* userData, void (\*callback)(ArkUI_ListItemSwipeActionState swipeActionState, void* userData))](#oh_arkui_listitemswipeactionitem_setonstatechangewithuserdata) | 设置列表项滑动状态变化时触发的事件，回调事件会传入用户自定义数据。列表项滑动状态会在收起、展开和长距离状态之间切换，具体状态见[ArkUI_ListItemSwipeActionState](capi-list-item-h.md#arkui_listitemswipeactionstate)。 |
| [ArkUI_ListItemSwipeActionOption* OH_ArkUI_ListItemSwipeActionOption_Create()](#oh_arkui_listitemswipeactionoption_create) | 创建ListItem组件swipeAction方法设置的配置项。 |
| [void OH_ArkUI_ListItemSwipeActionOption_Dispose(ArkUI_ListItemSwipeActionOption* option)](#oh_arkui_listitemswipeactionoption_dispose) | 销毁由OH_ArkUI_ListItemSwipeActionOption_Create创建的ListItemSwipeActionOption实例，使用完毕后需调用本接口释放，避免内存泄漏。 |
| [void OH_ArkUI_ListItemSwipeActionOption_SetStart(ArkUI_ListItemSwipeActionOption* option, ArkUI_ListItemSwipeActionItem* item)](#oh_arkui_listitemswipeactionoption_setstart) | 设置ListItemSwipeActionItem的左侧（垂直布局）或上方（横向布局）布局内容，该布局内容可通过OH_ArkUI_ListItemSwipeAction_Expand接口以编程方式展开。 |
| [void OH_ArkUI_ListItemSwipeActionOption_SetEnd(ArkUI_ListItemSwipeActionOption* option, ArkUI_ListItemSwipeActionItem* item)](#oh_arkui_listitemswipeactionoption_setend) | 设置ListItemSwipeActionItem的右侧（垂直布局）或下方（横向布局）布局内容，该布局内容可通过OH_ArkUI_ListItemSwipeAction_Expand接口以编程方式展开。 |
| [void OH_ArkUI_ListItemSwipeActionOption_SetEdgeEffect(ArkUI_ListItemSwipeActionOption* option, ArkUI_ListItemSwipeEdgeEffect edgeEffect)](#oh_arkui_listitemswipeactionoption_setedgeeffect) | 设置边缘滑动效果。需要允许滑动距离超过划出组件大小时，使用ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_SPRING；需要限制滑动距离不超过划出组件大小时，使用ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_NONE。 |
| [int32_t OH_ArkUI_ListItemSwipeActionOption_GetEdgeEffect(ArkUI_ListItemSwipeActionOption* option)](#oh_arkui_listitemswipeactionoption_getedgeeffect) | 获取边缘滑动效果。 |
| [void OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChange(ArkUI_ListItemSwipeActionOption* option, void (\*callback)(float offset))](#oh_arkui_listitemswipeactionoption_setonoffsetchange) | 滑动操作偏移量更改时调用的事件。 |
| [void OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChangeWithUserData(ArkUI_ListItemSwipeActionOption* option, void* userData, void (\*callback)(float offset, void* userData))](#oh_arkui_listitemswipeactionoption_setonoffsetchangewithuserdata) | 滑动操作偏移量更改时调用的事件，回调事件会传入用户自定义数据。 |
| [int32_t OH_ArkUI_ListItemSwipeAction_Expand(ArkUI_NodeHandle node, ArkUI_ListItemSwipeActionDirection direction)](#oh_arkui_listitemswipeaction_expand) | 展开指定ListItem的划出菜单（即侧滑操作时展示的操作项区域）。direction为ARKUI_LIST_ITEM_SWIPE_ACTION_DIRECTION_START时，展开通过OH_ArkUI_ListItemSwipeActionOption_SetStart设置的划出菜单；direction为ARKUI_LIST_ITEM_SWIPE_ACTION_DIRECTION_END时，展开通过OH_ArkUI_ListItemSwipeActionOption_SetEnd设置的划出菜单。展开后的划出菜单可通过OH_ArkUI_ListItemSwipeAction_Collapse接口收起。也可在应用响应用户点击"更多"等按钮后调用本接口，以编程方式展开划出菜单。 |
| [int32_t OH_ArkUI_ListItemSwipeAction_Collapse(ArkUI_NodeHandle node)](#oh_arkui_listitemswipeaction_collapse) | 收起由OH_ArkUI_ListItemSwipeAction_Expand展开的指定ListItem的划出菜单（即侧滑操作时展示的操作项区域），也可在用户完成划出菜单操作或切换其他列表项时以编程方式调用。 |

## 枚举类型说明

### ArkUI_ListItemSwipeActionState

```c
enum ArkUI_ListItemSwipeActionState
```

**描述**

定义{@link ListItem}组件{@link swipeAction}方法的列表项滑动状态。侧滑操作在垂直列表中沿水平方向进行，在水平列表中沿垂直方向进行。默认值为ARKUI_LIST_ITEM_SWIPE_ACTION_STATE_COLLAPSED。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_LIST_ITEM_SWIPE_ACTION_STATE_COLLAPSED = 0 | 收起状态，操作项处于隐藏状态。 |
| ARKUI_LIST_ITEM_SWIPE_ACTION_STATE_EXPANDED | 展开状态，操作项处于显示状态。 |
| ARKUI_LIST_ITEM_SWIPE_ACTION_STATE_ACTIONING | 长距离状态，表示ListItem进入长距删除区后处于删除操作中的状态。 |

### ArkUI_ListItemSwipeActionDirection

```c
enum ArkUI_ListItemSwipeActionDirection
```

**描述**

ListItem划出菜单的展开方向。

**起始版本：** 21

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_LIST_ITEM_SWIPE_ACTION_DIRECTION_START = 0 | 当列表方向为垂直时，LTR模式下表示ListItem的左边，RTL模式下表示ListItem的右边。当列表方向为水平时，表示ListItem的上边。 |
| ARKUI_LIST_ITEM_SWIPE_ACTION_DIRECTION_END = 1 | 当列表方向为垂直时，LTR模式下表示ListItem的右边，RTL模式下表示ListItem的左边。当列表方向为水平时，表示ListItem的下边。 |


## 函数说明

### OH_ArkUI_ListItemSwipeActionItem_Create()

```c
ArkUI_ListItemSwipeActionItem* OH_ArkUI_ListItemSwipeActionItem_Create()
```

**描述**

创建ListItem组件swipeAction方法设置的Item配置项。

**起始版本：** 12

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem*](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md) | 指向已创建的ListItemSwipeActionItem实例的指针。如果返回空指针，则表示  创建失败。可能的原因是地址空间已满。 |

### OH_ArkUI_ListItemSwipeActionItem_Dispose()

```c
void OH_ArkUI_ListItemSwipeActionItem_Dispose(ArkUI_ListItemSwipeActionItem* item)
```

**描述**

销毁由OH_ArkUI_ListItemSwipeActionItem_Create创建的ListItemSwipeActionItem实例，使用完毕后需调用本接口释放，避免内存泄漏。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | 要销毁的ListItemSwipeActionItem实例。 |

### OH_ArkUI_ListItemSwipeActionItem_SetContent()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetContent(ArkUI_ListItemSwipeActionItem* item, ArkUI_NodeHandle node)
```

**描述**

设置ListItemSwipeActionItem的布局内容。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | ListItemSwipeActionItem实例。 |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 侧滑操作项的内容节点。不设置时，侧滑操作项无可显示内容。 |

### OH_ArkUI_ListItemSwipeActionItem_SetActionAreaDistance()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetActionAreaDistance(ArkUI_ListItemSwipeActionItem* item, float distance)
```

**描述**

设置组件长距离滑动删除距离阈值，即列表项侧滑删除的触发距离。当划出组件被完全滑出后继续滑动，且该阈值取值大于0并小于ListItem在滑动方向上的尺寸减去划出组件在滑动方向上的尺寸时，继续滑动距离超过或等于该阈值后ListItem进入长距删除区。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | ListItemSwipeActionItem实例。 |
| float distance | 组件长距离滑动删除距离阈值，单位vp。默认值为56vp；取值小于等于0或大于等于ListItem在滑动方向上的尺寸减去划出组件在滑动方向上的尺寸时，不会形成长距删除区；进入长距删除区时会触发OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionArea或OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionAreaWithUserData设置的回调，退出长距删除区时会触发OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionArea或OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionAreaWithUserData设置的回调。建议配合OH_ArkUI_ListItemSwipeActionItem_SetOnAction或OH_ArkUI_ListItemSwipeActionItem_SetOnActionWithUserData回调使用。 |

### OH_ArkUI_ListItemSwipeActionItem_GetActionAreaDistance()

```c
float OH_ArkUI_ListItemSwipeActionItem_GetActionAreaDistance(ArkUI_ListItemSwipeActionItem* item)
```

**描述**

获取组件长距离滑动删除距离阈值。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | ListItemSwipeActionItem实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 组件长距离滑动删除距离阈值，单位vp。未显式设置时返回默认值56vp，异常时返回值：-1.0f。 |

### OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionArea()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionArea(ArkUI_ListItemSwipeActionItem* item, void (*callback)())
```

**描述**

设置滑动条目进入长距删除区时调用的事件。仅当长距删除距离阈值有效并形成长距删除区时触发。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_ListItemSwipeActionItem\* item | ListItemSwipeActionItem实例。 |
| void (\*callback)() | Callback event. |

### OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionAreaWithUserData()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnEnterActionAreaWithUserData(ArkUI_ListItemSwipeActionItem* item, void* userData, void (*callback)(void* userData))
```

**描述**

设置滑动条目进入长距删除区时调用的事件，回调事件会传入用户自定义数据。仅当长距删除距离阈值有效并形成长距删除区时触发。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_ListItemSwipeActionItem\* item | ListItemSwipeActionItem实例。 |
| void\* userData | 用户自定义数据。 |
| void (\*callback)(void\* userData) | Callback event. |

### OH_ArkUI_ListItemSwipeActionItem_SetOnAction()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnAction(ArkUI_ListItemSwipeActionItem* item, void (*callback)())
```

**描述**

设置滑动条目进入长距删除区后抬手删除{@link ListItem}时调用的事件。仅在删除距离阈值处于有效取值范围（大于0且小于ListItem在滑动方向上的尺寸减去划出组件在滑动方向上的尺寸），且滑动后松手位置超过或等于该阈值时触发。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_ListItemSwipeActionItem\* item | ListItemSwipeActionItem实例。 |
| void (\*callback)() | Callback event. |

### OH_ArkUI_ListItemSwipeActionItem_SetOnActionWithUserData()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnActionWithUserData(ArkUI_ListItemSwipeActionItem* item, void* userData, void (*callback)(void* userData))
```

**描述**

设置滑动条目进入长距删除区后抬手删除ListItem时调用的事件，回调事件会传入用户自定义数据。仅在删除距离阈值处于有效取值范围（大于0且小于ListItem在滑动方向上的尺寸减去划出组件在滑动方向上的尺寸），且滑动后松手位置超过或等于该阈值时触发。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_ListItemSwipeActionItem\* item | ListItemSwipeActionItem实例。 |
| void\* userData | 用户自定义数据。 |
| void (\*callback)(void\* userData) | Callback event. |

### OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionArea()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionArea(ArkUI_ListItemSwipeActionItem* item, void (*callback)())
```

**描述**

设置滑动条目退出长距删除区时调用的事件。仅当长距删除距离阈值有效并形成长距删除区时触发。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_ListItemSwipeActionItem\* item | ListItemSwipeActionItem实例。 |
| void (\*callback)() | Callback event. |

### OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionAreaWithUserData()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnExitActionAreaWithUserData(ArkUI_ListItemSwipeActionItem* item, void* userData, void (*callback)(void* userData))
```

**描述**

设置滑动条目退出长距删除区时调用的事件，回调事件会传入用户自定义数据。仅当长距删除距离阈值有效并形成长距删除区时触发。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_ListItemSwipeActionItem\* item | ListItemSwipeActionItem实例。 |
| void\* userData | 用户自定义数据。 |
| void (\*callback)(void\* userData) | Callback event. |

### OH_ArkUI_ListItemSwipeActionItem_SetOnStateChange()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnStateChange(ArkUI_ListItemSwipeActionItem* item, void (*callback)(ArkUI_ListItemSwipeActionState swipeActionState))
```

**描述**

设置列表项滑动状态变化时触发的事件。列表项滑动状态会在收起、展开和长距离状态之间切换，具体状态见[ArkUI_ListItemSwipeActionState](capi-list-item-h.md#arkui_listitemswipeactionstate)。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_ListItemSwipeActionItem\* item | ListItemSwipeActionItem实例。 |
| void (\*callback)(ArkUI_ListItemSwipeActionState swipeActionState) | Callback event.**swipeActionState** The changed state. |

### OH_ArkUI_ListItemSwipeActionItem_SetOnStateChangeWithUserData()

```c
void OH_ArkUI_ListItemSwipeActionItem_SetOnStateChangeWithUserData(ArkUI_ListItemSwipeActionItem* item, void* userData, void (*callback)(ArkUI_ListItemSwipeActionState swipeActionState, void* userData))
```

**描述**

设置列表项滑动状态变化时触发的事件，回调事件会传入用户自定义数据。列表项滑动状态会在收起、展开和长距离状态之间切换，具体状态见[ArkUI_ListItemSwipeActionState](capi-list-item-h.md#arkui_listitemswipeactionstate)。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_ListItemSwipeActionItem\* item | ListItemSwipeActionItem实例。 |
| void\* userData | 用户自定义数据。 |
| void (\*callback)(ArkUI_ListItemSwipeActionState swipeActionState | Callback event.**swipeActionState** The changed state. |

### OH_ArkUI_ListItemSwipeActionOption_Create()

```c
ArkUI_ListItemSwipeActionOption* OH_ArkUI_ListItemSwipeActionOption_Create()
```

**描述**

创建ListItem组件swipeAction方法设置的配置项。

**起始版本：** 12

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption*](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md) | ListItemSwipeActionOption配置项实例，用于设置ListItem侧滑操作项在起始侧和结束侧的布局内容、边缘滑动效果及偏移量变化回调。 |

### OH_ArkUI_ListItemSwipeActionOption_Dispose()

```c
void OH_ArkUI_ListItemSwipeActionOption_Dispose(ArkUI_ListItemSwipeActionOption* option)
```

**描述**

销毁由OH_ArkUI_ListItemSwipeActionOption_Create创建的ListItemSwipeActionOption实例，使用完毕后需调用本接口释放，避免内存泄漏。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)* option | 要销毁的ListItemSwipeActionOption实例。 |

### OH_ArkUI_ListItemSwipeActionOption_SetStart()

```c
void OH_ArkUI_ListItemSwipeActionOption_SetStart(ArkUI_ListItemSwipeActionOption* option, ArkUI_ListItemSwipeActionItem* item)
```

**描述**

设置ListItemSwipeActionItem的左侧（垂直布局）或上方（横向布局）布局内容，该布局内容可通过OH_ArkUI_ListItemSwipeAction_Expand接口以编程方式展开。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)* option | ListItemSwipeActionOption实例。 |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | 待设置到起始侧的ListItemSwipeActionItem实例。不设置时，ListItem起始侧不展示侧滑操作项。 |

### OH_ArkUI_ListItemSwipeActionOption_SetEnd()

```c
void OH_ArkUI_ListItemSwipeActionOption_SetEnd(ArkUI_ListItemSwipeActionOption* option, ArkUI_ListItemSwipeActionItem* item)
```

**描述**

设置ListItemSwipeActionItem的右侧（垂直布局）或下方（横向布局）布局内容，该布局内容可通过OH_ArkUI_ListItemSwipeAction_Expand接口以编程方式展开。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)* option | ListItemSwipeActionOption实例。 |
| [ArkUI_ListItemSwipeActionItem](capi-arkui-nativemodule-arkui-listitemswipeactionitem.md)* item | 待设置到结束侧的ListItemSwipeActionItem实例。不设置时，ListItem结束侧不展示侧滑操作项。 |

### OH_ArkUI_ListItemSwipeActionOption_SetEdgeEffect()

```c
void OH_ArkUI_ListItemSwipeActionOption_SetEdgeEffect(ArkUI_ListItemSwipeActionOption* option, ArkUI_ListItemSwipeEdgeEffect edgeEffect)
```

**描述**

设置边缘滑动效果。需要允许滑动距离超过划出组件大小时，使用ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_SPRING；需要限制滑动距离不超过划出组件大小时，使用ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_NONE。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)* option | ListItemSwipeActionOption实例。 |
| ArkUI_ListItemSwipeEdgeEffect edgeEffect | 边缘滑动效果。 |

### OH_ArkUI_ListItemSwipeActionOption_GetEdgeEffect()

```c
int32_t OH_ArkUI_ListItemSwipeActionOption_GetEdgeEffect(ArkUI_ListItemSwipeActionOption* option)
```

**描述**

获取边缘滑动效果。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListItemSwipeActionOption](capi-arkui-nativemodule-arkui-listitemswipeactionoption.md)* option | ListItemSwipeActionOption实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 边缘滑动效果。取值包括{@link ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_SPRING}（0）和      {@link ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_NONE}（1），默认返回值为{@link ARKUI_LIST_ITEM_SWIPE_EDGE_EFFECT_SPRING}，异常时返回-1。 |

### OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChange()

```c
void OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChange(ArkUI_ListItemSwipeActionOption* option, void (*callback)(float offset))
```

**描述**

滑动操作偏移量更改时调用的事件。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_ListItemSwipeActionOption\* option | ListItemSwipeActionOption实例。 |
| void (\*callback)(float offset) | Callback event.**offset** Slide offset. |

### OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChangeWithUserData()

```c
void OH_ArkUI_ListItemSwipeActionOption_SetOnOffsetChangeWithUserData(ArkUI_ListItemSwipeActionOption* option, void* userData, void (*callback)(float offset, void* userData))
```

**描述**

滑动操作偏移量更改时调用的事件，回调事件会传入用户自定义数据。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_ListItemSwipeActionOption\* option | ListItemSwipeActionOption实例。 |
| void\* userData | 用户自定义数据。 |
| void (\*callback)(float offset | Callback event.**offset** Slide offset. |

### OH_ArkUI_ListItemSwipeAction_Expand()

```c
int32_t OH_ArkUI_ListItemSwipeAction_Expand(ArkUI_NodeHandle node, ArkUI_ListItemSwipeActionDirection direction)
```

**描述**

展开指定ListItem的划出菜单（即侧滑操作时展示的操作项区域）。direction为ARKUI_LIST_ITEM_SWIPE_ACTION_DIRECTION_START时，展开通过OH_ArkUI_ListItemSwipeActionOption_SetStart设置的划出菜单；direction为ARKUI_LIST_ITEM_SWIPE_ACTION_DIRECTION_END时，展开通过OH_ArkUI_ListItemSwipeActionOption_SetEnd设置的划出菜单。展开后的划出菜单可通过OH_ArkUI_ListItemSwipeAction_Collapse接口收起。也可在应用响应用户点击"更多"等按钮后调用本接口，以编程方式展开划出菜单。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ListItem节点对象。 |
| [ArkUI_ListItemSwipeActionDirection](capi-list-item-h.md#arkui_listitemswipeactiondirection) direction | ListItem划出菜单的展开方向。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>{@link ARKUI_ERROR_CODE_NO_ERROR} 成功。      <br>{@link ARKUI_ERROR_CODE_PARAM_ERROR} 传入的节点对象类型错误，请检查传入的节点是否为ListItem节点。      <br>{@link ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE} 传入的节点未挂载到组件树上，请先将节点挂载到组件树上再执行该操作。 |

### OH_ArkUI_ListItemSwipeAction_Collapse()

```c
int32_t OH_ArkUI_ListItemSwipeAction_Collapse(ArkUI_NodeHandle node)
```

**描述**

收起由OH_ArkUI_ListItemSwipeAction_Expand展开的指定ListItem的划出菜单（即侧滑操作时展示的操作项区域），也可在用户完成划出菜单操作或切换其他列表项时以编程方式调用。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | ListItem节点对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。      <br>{@link ARKUI_ERROR_CODE_NO_ERROR} 成功。      <br>{@link ARKUI_ERROR_CODE_PARAM_ERROR} 传入的节点对象类型错误，请检查传入的节点是否为ListItem节点。      <br>{@link ARKUI_ERROR_CODE_NODE_NOT_ON_MAIN_TREE} 传入的节点未挂载到组件树上，请先将节点挂载到组件树上再执行该操作。 |


