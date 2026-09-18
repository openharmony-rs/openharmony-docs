# TouchTestStrategy

Event dispatch strategy.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

Custom dispatch has no effect; the system dispatches events based on the hit status of the current node.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## FORWARD_COMPETITION

```TypeScript
FORWARD_COMPETITION = 1
```

The event is dispatched to a specified child node, and the system determines whether to dispatch events to other sibling nodes.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## FORWARD

```TypeScript
FORWARD = 2
```

The event is dispatched to a specified child node, and the system will not dispatch events to other sibling nodes.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
