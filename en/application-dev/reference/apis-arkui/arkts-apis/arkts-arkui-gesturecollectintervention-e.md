# GestureCollectIntervention

Define the gesture and events collection intervention operations.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CONTINUE

```TypeScript
CONTINUE = 0
```

Continue the normal collection process. No intervention will be applied.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DISCARD_LOWER

```TypeScript
DISCARD_LOWER = 1
```

Discard all pending lower-priority gestures and events. This includes gestures from left sibling nodes and ancestor nodes (parent and above). Only the already collected gestures from the current node and higher-priority nodes will be retained.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DISCARD_HIGHER

```TypeScript
DISCARD_HIGHER = 2
```

Discard already collected higher-priority gestures and events. This removes gestures from right sibling nodes that have been collected. The collection will continue with lower-priority gestures (left siblings and ancestors).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DISCARD_SELF

```TypeScript
DISCARD_SELF = 3
```

Discard gestures and events from the current node itself. The current node's gestures and events will be excluded from the gesture tree. Gestures from sibling nodes (both left and right) and ancestor nodes will still be collected.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DISCARD_LOWER_PRIORITY_SIBLINGS

```TypeScript
DISCARD_LOWER_PRIORITY_SIBLINGS = 4
```

Discard gestures and events from left sibling nodes that are pending collection. Gestures and events from the current node and already collected right sibling nodes will be retained. The collection will continue with ancestor nodes.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
