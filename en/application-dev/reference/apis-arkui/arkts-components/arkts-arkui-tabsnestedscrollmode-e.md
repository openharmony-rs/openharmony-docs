# TabsNestedScrollMode

Enumerates the nested scrolling modes of the **Tabs** component and its parent container.

**Since:** 24

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SELF_ONLY

```TypeScript
SELF_ONLY = 0
```

The scrolling is contained within the **Tabs** component, and no scroll chaining occurs, that is, the parent component does not scroll when the component scrolling reaches the boundary.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SELF_FIRST

```TypeScript
SELF_FIRST = 1
```

The **Tabs** component scrolls first, and when it hits the boundary, the parent component scrolls. When the parent container hits the boundary, its edge effect is displayed. If no edge effect is specified for the parent container, the edge effect of the **Tabs** component is displayed instead.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
