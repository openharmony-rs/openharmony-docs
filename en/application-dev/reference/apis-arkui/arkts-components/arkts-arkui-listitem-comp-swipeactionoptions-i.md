# SwipeActionOptions

```TypeScript
declare interface SwipeActionOptions
```

In the **@builder** functions corresponding to **start** and **end**, the top-level component must be a single component. If the top level is a rendering control statement such as **if**\/**else** or **ForEach**, ensure that it can generate only a single component. Otherwise, undefined behavior may occur.

The swipe gesture works only in the list item area. If a child component is swiped out of the list item area, the portion outside the list item does not respond to the swipe gesture. Therefore, in multi-column mode, you are advised not to set the swipe-out component too wide.

**Since:** 9

<!--Device-unnamed-declare interface SwipeActionOptions--><!--Device-unnamed-declare interface SwipeActionOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onOffsetChange

```TypeScript
onOffsetChange?: (offset: number) => void
```

Callback invoked when the location of the list item changes, in vp, when it is swiped left or right (in vertical list layout) or up or down (in horizontal list layout).

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SwipeActionOptions-onOffsetChange?: (offset: number) => void--><!--Device-SwipeActionOptions-onOffsetChange?: (offset: number) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | Yes |  |

## edgeEffect

```TypeScript
edgeEffect?: SwipeEdgeEffect
```

Scroll effect.

**Type:** [SwipeEdgeEffect](arkts-arkui-listitem-comp-swipeedgeeffect-e.md)

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SwipeActionOptions-edgeEffect?: SwipeEdgeEffect--><!--Device-SwipeActionOptions-edgeEffect?: SwipeEdgeEffect-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end?: CustomBuilder | SwipeActionItem
```

Swipe action item displayed on the right of the list item when the item is swiped left (in vertical list layout) or below the list item when the item is swiped up (in horizontal list layout).

**Type:** [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) &#124; [SwipeActionItem](arkts-arkui-listitem-comp-swipeactionitem-i.md)

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SwipeActionOptions-end?: CustomBuilder | SwipeActionItem--><!--Device-SwipeActionOptions-end?: CustomBuilder | SwipeActionItem-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start?: CustomBuilder | SwipeActionItem
```

Swipe action item displayed on the left of the list item when the item is swiped right (in vertical list layout) or above the list item when the item is swiped down (in horizontal list layout).

**Type:** [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) &#124; [SwipeActionItem](arkts-arkui-listitem-comp-swipeactionitem-i.md)

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SwipeActionOptions-start?: CustomBuilder | SwipeActionItem--><!--Device-SwipeActionOptions-start?: CustomBuilder | SwipeActionItem-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
