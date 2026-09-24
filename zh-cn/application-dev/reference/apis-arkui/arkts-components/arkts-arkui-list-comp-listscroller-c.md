# ListScroller

```TypeScript
declare class ListScroller extends Scroller
```

List组件的滚动控制器，通过它控制List组件的滚动，仅支持一对一绑定到List组件。

> **说明：** 
> 
> ListScroller继承自[Scroller](arkts-arkui-scroll-comp-scroller-c.md)，具有[Scroller](arkts-arkui-scroll-comp-scroller-c.md)的全部方法。

## 导入对象

```ts
listScroller: ListScroller = new ListScroller();
```

**继承/实现关系：** ListScroller extends [Scroller](arkts-arkui-scroll-comp-scroller-c.md)

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## closeAllSwipeActions

```TypeScript
closeAllSwipeActions(options?: CloseSwipeActionOptions): void
```

将[EXPANDED](arkts-arkui-listitem-comp-swipeactionstate-e.md)状态的[ListItem](arkts-arkui-listitem-comp.md#list_item)收起，并设置回调事件。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [CloseSwipeActionOptions](arkts-arkui-list-comp-closeswipeactionoptions-i.md) | 否 | 收起[EXPANDED](arkts-arkui-listitem-comp-swipeactionstate-e.md)状态的[ListItem](arkts-arkui-listitem-comp.md#list_item)的回调事件集合。不传入时不设置回调事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100004](../errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Controller not bound to a component. |

## getItemRectInGroup

```TypeScript
getItemRectInGroup(index: number, indexInGroup: number): RectResult
```

获取[ListItemGroup](arkts-arkui-listitemgroup-comp.md#list_item_group)中的[ListItem](arkts-arkui-listitem-comp.md#list_item)的大小和相对于List的位置。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | ListItemGroup在List中的索引值。 |
| indexInGroup | number | 是 | ListItem在ListItemGroup中的索引值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RectResult](arkts-arkui-common-comp-rectresult-i.md) | ListItemGroup中的ListItem的大小和相对于List的位置。<br>单位：vp。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100004](../errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Controller not bound to a component. |

## getVisibleListContentInfo

```TypeScript
getVisibleListContentInfo(x: number, y: number): VisibleListContentInfo
```

根据坐标获取子组件的索引信息。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | x轴坐标，单位为vp。 |
| y | number | 是 | y轴坐标，单位为vp。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [VisibleListContentInfo](arkts-arkui-list-comp-visiblelistcontentinfo-i.md) | 入参坐标处的子组件的索引信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100004](../errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Controller not bound to a component. |

## scrollToItemInGroup

```TypeScript
scrollToItemInGroup(index: number, indexInGroup:number, smooth?: boolean, align?: ScrollAlign): void
```

滑动到指定的ListItemGroup中指定的ListItem。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 要滑动到的目标元素所在的ListItemGroup在当前容器中的索引值。<br>**说明：** <br>index值设置成负值或者大于当前容器子组件的最大索引值，视为异常值，本次跳转不生效。 |
| indexInGroup | number | 是 | 要滑动到的目标元素在index指定的ListItemGroup中的索引值。<br>**说明：** <br>indexInGroup值设置成负值或者大于index指定的ListItemGroup容器子组件的最大索引值，视为异常值，本次跳转不生效。 |
| smooth | boolean | 否 | 设置该次滑动是否有动效，true表示有动效，false表示没有动效。<br>默认值：false<br>**说明：** <br>开启动效时，会对经过的所有item进行加载和布局计算，当大量加载item时会导致性能问题。 |
| align | [ScrollAlign](arkts-arkui-scroll-comp-scrollalign-e.md) | 否 | 指定滑动到的元素与当前容器的对齐方式。<br>默认值：ScrollAlign.START。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100004](../errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Controller not bound to a component. |
