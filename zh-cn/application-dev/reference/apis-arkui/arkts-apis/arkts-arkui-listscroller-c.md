# ListScroller

List组件的滚动控制器，通过它控制List组件的滚动，仅支持一对一绑定到List组件。

> **说明：**
>
> ListScroller继承自[Scroller](arkts-arkui-scroll-scroller-c.md#Scroller)，具有[Scroller](arkts-arkui-scroll-scroller-c.md#Scroller)的全部方法。

**继承/实现关系：** ListScroller extends [Scroller](arkts-arkui-scroll-scroller-c.md#Scroller)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## closeAllSwipeActions

```TypeScript
closeAllSwipeActions(options?: CloseSwipeActionOptions): void
```

将[EXPANDED](arkts-arkui-listitem-swipeactionstate-e.md#SwipeActionState)状态的[ListItem](arkts-arkui-listitem.md)收起，并设置回调事件。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | CloseSwipeActionOptions | 否 | 收起[EXPANDED](arkts-arkui-listitem-swipeactionstate-e.md#SwipeActionState)状态的[ListItem](arkts-arkui-listitem.md)的回调事<br/>件集合。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [100004](../../errorcode-universal.md#100004-Controller) | Controller not bound to a component. |

## getItemRectInGroup

```TypeScript
getItemRectInGroup(index: number, indexInGroup: number): RectResult
```

获取[ListItemGroup](arkts-arkui-listitemgroup.md)中的[ListItem](arkts-arkui-listitem.md)的大小和相对于List的位置。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | ListItemGroup在List中的索引值。 |
| indexInGroup | number | 是 | ListItemGroup在List中的索引值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RectResult | ListItemGroup中的ListItem的大小和相对于List的位置。<br/>单位：vp。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [100004](../../errorcode-universal.md#100004-Controller) | Controller not bound to a component. |

## getVisibleListContentInfo

```TypeScript
getVisibleListContentInfo(x: number, y: number): VisibleListContentInfo
```

根据坐标获取子组件的索引信息。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | x轴坐标，单位为vp。 |
| y | number | 是 | y轴坐标，单位为vp。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| VisibleListContentInfo | 入参坐标处的子组件的索引信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [100004](../../errorcode-universal.md#100004-Controller) | Controller not bound to a component. |

## scrollToItemInGroup

```TypeScript
scrollToItemInGroup(index: number, indexInGroup:number, smooth?: boolean, align?: ScrollAlign): void
```

滑动到指定的ListItemGroup中指定的ListItem。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 要滑动到的目标元素所在的ListItemGroup在当前容器中的索引值。<br/>**说明：**<br/>index值设置成负值或者大于当前容器子组件的最大索引值，<br/>视为异常值，本次跳转不生效。 |
| indexInGroup | number | 是 | 要滑动到的目标元素所在的ListItemGroup在当前容器中的索引值。<br/>**说明：**<br/>index值设置成负值或者大于当前容器子组件的最大索引值，<br/>视为异常值，本次跳转不生效。 |
| smooth | boolean | 否 | 设置该次滑动是否有动效，true表示有动效，false表示没有动效。<br/>默认值：false<br/>**说明：**<br/>开启动效时，会对经过的所有item进行加载<br/>和布局计算，当大量加载item时会导致性能问题。 |
| align | ScrollAlign | 否 | 指定滑动到的元素与当前容器的对齐方式。<br/>默认值：ScrollAlign.START。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [100004](../../errorcode-universal.md#100004-Controller) | Controller not bound to a component. |

