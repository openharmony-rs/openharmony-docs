# SwipeActionItem

```TypeScript
declare interface SwipeActionItem
```

Used to configure the **start** or **end** swipe-out item in [SwipeActionOptions](arkts-arkui-listitem-comp-swipeactionoptions-i.md), including the action item displayed when swiping out, the distance threshold of the long-distance action area, and the callbacks for entering and exiting the long-distance action area, triggering the action when the finger is lifted, and state changes.

When used as a **start** swipe-out item, it is displayed on the left of the **ListItem** when the **List** is in vertical layout, and above the **ListItem** when the **List** is in horizontal layout. When used as an end swipe-out item, it is displayed on the right of the **ListItem** when the **List** is in vertical layout, and below the **ListItem** when the **List** is in horizontal layout.

**Since:** 10

<!--Device-unnamed-declare interface SwipeActionItem--><!--Device-unnamed-declare interface SwipeActionItem-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onAction

```TypeScript
onAction?: () => void
```

Callback invoked when the list item is released while in the delete area.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SwipeActionItem-onAction?: () => void--><!--Device-SwipeActionItem-onAction?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onEnterActionArea

```TypeScript
onEnterActionArea?: () => void
```

Callback invoked each time the list item enters the delete area.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SwipeActionItem-onEnterActionArea?: () => void--><!--Device-SwipeActionItem-onEnterActionArea?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onExitActionArea

```TypeScript
onExitActionArea?: () => void
```

Callback invoked each time the list item exits the delete area.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SwipeActionItem-onExitActionArea?: () => void--><!--Device-SwipeActionItem-onExitActionArea?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onStateChange

```TypeScript
onStateChange?: (state: SwipeActionState) => void
```

Callback invoked when the swipe state of the list item changes.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SwipeActionItem-onStateChange?: (state: SwipeActionState) => void--><!--Device-SwipeActionItem-onStateChange?: (state: SwipeActionState) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| state | [SwipeActionState](arkts-arkui-listitem-comp-swipeactionstate-e.md) | Yes |  |

## actionAreaDistance

```TypeScript
actionAreaDistance?: Length
```

Swipe distance threshold for deleting the list item. This threshold applies after the swipe action component is fully swiped into view and triggers the deletion action.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Default:** 56vp

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SwipeActionItem-actionAreaDistance?: Length--><!--Device-SwipeActionItem-actionAreaDistance?: Length-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## builder

```TypeScript
builder?: CustomBuilder
```

Swipe action item displayed when the list item is swiped left or right (in vertical list layout) or up or down (in horizontal list layout).

**Type:** [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SwipeActionItem-builder?: CustomBuilder--><!--Device-SwipeActionItem-builder?: CustomBuilder-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## builderComponent

```TypeScript
builderComponent?: ComponentContent
```

Swipe action item displayed when the list item is swiped left or right (in vertical list layout) or up or down (in horizontal list layout).

**Type:** ComponentContent

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SwipeActionItem-builderComponent?: ComponentContent--><!--Device-SwipeActionItem-builderComponent?: ComponentContent-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
