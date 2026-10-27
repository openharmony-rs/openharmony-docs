# FastScrollMode

```TypeScript
declare enum FastScrollMode
```

Enumerates the fast scroll modes for scrolling to a specified index.

**Since:** 26.1.0

<!--Device-unnamed-declare enum FastScrollMode--><!--Device-unnamed-declare enum FastScrollMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NONE

```TypeScript
NONE = 0
```

No fast scroll optimization. All intermediate items are created and measured before the animation starts.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-FastScrollMode-NONE = 0--><!--Device-FastScrollMode-NONE = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SKIP_CREATE_AND_MEASURE

```TypeScript
SKIP_CREATE_AND_MEASURE = 2
```

Fast scroll optimization with skipping intermediate item creation and measurement. Intermediate items are neither created nor measured. This mode provides maximum performance optimization. However, this mode is not suitable for the scenarios where the list has multiple columns and both ListItem and ListItemGroup exist. In this scenario, use SKIP_MEASURE.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-FastScrollMode-SKIP_CREATE_AND_MEASURE = 2--><!--Device-FastScrollMode-SKIP_CREATE_AND_MEASURE = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SKIP_MEASURE

```TypeScript
SKIP_MEASURE = 1
```

Fast scroll optimization with skipping intermediate item measurement. Intermediate items are created but not measured. This mode is suitable for scenarios where the list has multiple columns and both ListItem and ListItemGroup exist. In this case, ListItem occupies only one column in a row, but ListItemGroup occupies an entire row. Therefore, the List needs to create all intermediate items to obtain the types of these items and calculate the row position of the target index.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-FastScrollMode-SKIP_MEASURE = 1--><!--Device-FastScrollMode-SKIP_MEASURE = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
