# NestedScrollMode

```TypeScript
declare enum NestedScrollMode
```

Sets the nested mode of a nested scrollable component.

**Since:** 10

<!--Device-unnamed-declare enum NestedScrollMode--><!--Device-unnamed-declare enum NestedScrollMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## PARALLEL

```TypeScript
PARALLEL
```

The component and its parent component scroll at the same time. When both the component and its parent component hit the boundary, the edge effect of the component is displayed. If no edge effect is specified for the component, the edge effect of the parent component is displayed instead.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-NestedScrollMode-PARALLEL--><!--Device-NestedScrollMode-PARALLEL-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## PARENT_FIRST

```TypeScript
PARENT_FIRST
```

The parent component scrolls first, and when it hits the boundary, the component scrolls. When the component hits the boundary, its edge effect is displayed. If no edge effect is specified for the component, the edge effect of the parent component is displayed instead.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-NestedScrollMode-PARENT_FIRST--><!--Device-NestedScrollMode-PARENT_FIRST-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SELF_FIRST

```TypeScript
SELF_FIRST
```

The component scrolls first, and when it hits the boundary, the parent component scrolls. When the parent component hits the boundary, its edge effect is displayed. If no edge effect is specified for the parent component, the edge effect of the child component is displayed instead.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-NestedScrollMode-SELF_FIRST--><!--Device-NestedScrollMode-SELF_FIRST-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SELF_ONLY

```TypeScript
SELF_ONLY
```

The scrolling is contained within the component, and no scroll chaining occurs, that is, the parent component does not scroll when the component scrolling reaches the boundary.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-NestedScrollMode-SELF_ONLY--><!--Device-NestedScrollMode-SELF_ONLY-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
