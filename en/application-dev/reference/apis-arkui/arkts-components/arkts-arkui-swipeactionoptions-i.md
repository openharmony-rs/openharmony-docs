# SwipeActionOptions

The top layer of the @builder function corresponding to start and end must be a single component. Otherwise, undefined behavior occurs. If the top layer of the @builder function is a statement such as if/else or ForEach, ensure that these statements can generate a single component.

The swipe gesture works only in the list item area. If a swipe causes a child component to extend beyond the list item area, the portion outside the area does not respond to the swipe.

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onOffsetChange

```TypeScript
onOffsetChange?: (offset: number) => void
```

Callback invoked when the location of the list item changes, in vp, when it is swiped left or right (in vertical list layout) or up or down (in horizontal list layout).

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

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

**Type:** [SwipeEdgeEffect](arkts-arkui-swipeedgeeffect-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end?: CustomBuilder | SwipeActionItem
```

Swipe action item displayed on the right of the list item when the item is swiped left (in vertical list layout) or below the list item when the item is swiped up (in horizontal list layout).

**Type:** [CustomBuilder](arkts-arkui-custombuilder-t.md) &#124; [SwipeActionItem](arkts-arkui-swipeactionitem-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start?: CustomBuilder | SwipeActionItem
```

Swipe action item displayed on the left of the list item when the item is swiped right (in vertical list layout) or above the list item when the item is swiped down (in horizontal list layout).

**Type:** [CustomBuilder](arkts-arkui-custombuilder-t.md) &#124; [SwipeActionItem](arkts-arkui-swipeactionitem-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
