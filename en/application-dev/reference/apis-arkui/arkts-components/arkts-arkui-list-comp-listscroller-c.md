# ListScroller

```TypeScript
declare class ListScroller extends Scroller
```

Implements the scroll controller of the **List** component. A **List** component is bound to a **ListScroller** on a one-to-one basis.

> **NOTE:** 
> 
> **ListScroller** inherits from [Scroller](arkts-arkui-scroll-comp-scroller-c.md) and has all methods of [Scroller](arkts-arkui-scroll-comp-scroller-c.md).

## Objects to Import

```ts
listScroller: ListScroller = new ListScroller();
```

**Inheritance/Implementation:** ListScroller extends [Scroller](arkts-arkui-scroll-comp-scroller-c.md)

**Since:** 11

<!--Device-unnamed-declare class ListScroller extends Scroller--><!--Device-unnamed-declare class ListScroller extends Scroller-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## closeAllSwipeActions

```TypeScript
closeAllSwipeActions(options?: CloseSwipeActionOptions): void
```

Collapses the [list items](arkts-arkui-listitem-comp.md) in the [EXPANDED](arkts-arkui-listitem-comp-swipeactionstate-e.md) state and sets callback events.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ListScroller-closeAllSwipeActions(options?: CloseSwipeActionOptions): void--><!--Device-ListScroller-closeAllSwipeActions(options?: CloseSwipeActionOptions): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [CloseSwipeActionOptions](arkts-arkui-list-comp-closeswipeactionoptions-i.md) | No | Set of callback events for collapsing the [ListItem](arkts-arkui-listitem-comp.md) in the [EXPANDED](arkts-arkui-listitem-comp-swipeactionstate-e.md) state. If this parameter is not passed, no callback events are set. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100004](../errorcode-router.md#100004-incorrect-route-name) | Controller not bound to a component. |

## getItemRectInGroup

```TypeScript
getItemRectInGroup(index: number, indexInGroup: number): RectResult
```

Obtains the size of a [list item](arkts-arkui-listitem-comp.md) in a [list item group](arkts-arkui-listitemgroup-comp.md) and its position relative to the list.

> **NOTE:** 
> 
> - The value of **index** must be the index of a child component visible in the display area. Otherwise, the value is considered invalid.
> - The child component for which **index** is set must be a list item group. Otherwise, the **index** value is considered invalid.
> - The value of **indexInGroup** must be the index of a list item in the list item group visible in the display area. Otherwise, the value is considered invalid.
> - When **index** or **indexInGroup** is set to an invalid value, the returned size and position are both **0**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ListScroller-getItemRectInGroup(index: number, indexInGroup: number): RectResult--><!--Device-ListScroller-getItemRectInGroup(index: number, indexInGroup: number): RectResult-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the list item group in the list. |
| indexInGroup | number | Yes | Index of the list item in the list item group. |

**Return value:**

| Type | Description |
| --- | --- |
| [RectResult](arkts-arkui-common-comp-rectresult-i.md) | Size of the list item in the list item group and its position relative to the list.<br>Unit: vp |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100004](../errorcode-router.md#100004-incorrect-route-name) | Controller not bound to a component. |

## getVisibleListContentInfo

```TypeScript
getVisibleListContentInfo(x: number, y: number): VisibleListContentInfo
```

Obtains the index information of the child component at the specified coordinates.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-ListScroller-getVisibleListContentInfo(x: number, y: number): VisibleListContentInfo--><!--Device-ListScroller-getVisibleListContentInfo(x: number, y: number): VisibleListContentInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X-coordinate, in vp. |
| y | number | Yes | Y-coordinate, in vp. |

**Return value:**

| Type | Description |
| --- | --- |
| [VisibleListContentInfo](arkts-arkui-list-comp-visiblelistcontentinfo-i.md) | Index information of a child component at the specified coordinates. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100004](../errorcode-router.md#100004-incorrect-route-name) | Controller not bound to a component. |

## scrollToItemInGroup

```TypeScript
scrollToItemInGroup(index: number, indexInGroup:number, smooth?: boolean, align?: ScrollAlign): void
```

Scrolls to the specified list item in the specified list item group.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ListScroller-scrollToItemInGroup(index: number, indexInGroup:number, smooth?: boolean, align?: ScrollAlign): void--><!--Device-ListScroller-scrollToItemInGroup(index: number, indexInGroup:number, smooth?: boolean, align?: ScrollAlign): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the target list item group in the current container.<br>**NOTE:** <br>If the value set is a negative value or greater than the maximum index of the items in the container, the value is deemed abnormal, and no scrolling will be performed. |
| indexInGroup | number | Yes | Index of the target list item in the list item group specified by **index**.<br>**NOTE:** <br>If the value set is a negative value or greater than the maximum index of the items in the list item group, the value is deemed abnormal, and no scrolling will be performed. |
| smooth | boolean | No | Whether the scroll animation is enabled. The options are **true** (enabled) and **false** (disabled).<br>Default value: **false** <br>**NOTE:** <br>When **smooth** is set to **true**, all passed items are loaded and counted in layout calculation. This may result in performance issues if a large number of items are involved. |
| align | [ScrollAlign](arkts-arkui-scroll-comp-scrollalign-e.md) | No | How the list item to scroll to is aligned with the container.<br>Default value: **ScrollAlign.START** |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100004](../errorcode-router.md#100004-incorrect-route-name) | Controller not bound to a component. |
