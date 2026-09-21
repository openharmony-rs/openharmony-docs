# SwipeActionItem

```TypeScript
declare interface SwipeActionItem
```

Describes the swipe action item. For a list in vertical layout, it refers to the delete option displayed on the left (or right) of the list item when the list item is swiped right (or left).

For a list in horizontal layout, it refers to the delete option displayed below (or above) the list item when the list item is swiped up (or down).

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onAction

```TypeScript
onAction?: () => void
```

Callback invoked when the list item is released while in the delete area.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onEnterActionArea

```TypeScript
onEnterActionArea?: () => void
```

Callback invoked each time the list item enters the delete area.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onExitActionArea

```TypeScript
onExitActionArea?: () => void
```

Callback invoked each time the list item exits the delete area.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onStateChange

```TypeScript
onStateChange?: (state: SwipeActionState) => void
```

Callback invoked when the swipe state of the list item changes.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full
