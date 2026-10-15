# SwipeActionState

```TypeScript
declare enum SwipeActionState
```

Enumerates swipe states of list items.

**Since:** 11

<!--Device-unnamed-declare enum SwipeActionState--><!--Device-unnamed-declare enum SwipeActionState-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ACTIONING

```TypeScript
ACTIONING
```

Long-distance state, in which the list item is deleted after it enters the long-distance deletion area.

**NOTE:** 

This state can be entered only when the final value of **actionAreaDistance** is greater than 0 and less than the size of the list item in the swipe direction minus the size of the swipe-out component in the swipe direction, and the position where the finger is released after swiping is greater than or equal to this value.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SwipeActionState-ACTIONING--><!--Device-SwipeActionState-ACTIONING-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## COLLAPSED

```TypeScript
COLLAPSED
```

Collapsed state, in which the action items are hidden.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SwipeActionState-COLLAPSED--><!--Device-SwipeActionState-COLLAPSED-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## EXPANDED

```TypeScript
EXPANDED
```

Expanded state, in which the action items are displayed.

**NOTE:** 

The swipe action items must be set for the list item.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SwipeActionState-EXPANDED--><!--Device-SwipeActionState-EXPANDED-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
