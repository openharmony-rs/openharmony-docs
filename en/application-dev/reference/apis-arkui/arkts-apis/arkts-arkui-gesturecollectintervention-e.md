# GestureCollectIntervention

```TypeScript
declare enum GestureCollectIntervention
```

Enumerates the intervention types for gesture and event collection, applicable to scenarios where gestures need to be retained or discarded by priority during gesture and event collection.

**Since:** 26.0.0

<!--Device-unnamed-declare enum GestureCollectIntervention--><!--Device-unnamed-declare enum GestureCollectIntervention-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CONTINUE

```TypeScript
CONTINUE = 0
```

Continues the normal gesture and event collection flow. No intervention is performed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-GestureCollectIntervention-CONTINUE = 0--><!--Device-GestureCollectIntervention-CONTINUE = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DISCARD_LOWER

```TypeScript
DISCARD_LOWER = 1
```

Discards all low-priority gestures and events to be collected. The gestures of the left sibling node and ancestor nodes (parent nodes and above) are discarded. Only the gestures already collected on the current node and higher- priority nodes are retained.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-GestureCollectIntervention-DISCARD_LOWER = 1--><!--Device-GestureCollectIntervention-DISCARD_LOWER = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DISCARD_HIGHER

```TypeScript
DISCARD_HIGHER = 2
```

Discards all collected high-priority gestures and events. The gestures of the right sibling node and the current node are discarded. Continues processing the collection flow for lower-priority gestures (left sibling and ancestor nodes).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-GestureCollectIntervention-DISCARD_HIGHER = 2--><!--Device-GestureCollectIntervention-DISCARD_HIGHER = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DISCARD_SELF

```TypeScript
DISCARD_SELF = 3
```

Discards the gestures and events of the current node. The gestures and events of the current node are excluded from the gesture tree. The gestures of the sibling nodes (left and right) and the ancestor nodes are still collected.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-GestureCollectIntervention-DISCARD_SELF = 3--><!--Device-GestureCollectIntervention-DISCARD_SELF = 3-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DISCARD_LOWER_PRIORITY_SIBLINGS

```TypeScript
DISCARD_LOWER_PRIORITY_SIBLINGS = 4
```

Discards the gestures and events to be collected from the left sibling node. The gestures and events of the current node and the collected gestures and events of the right sibling node are retained. Continues processing the collection flow for the parent and ancestor nodes.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-GestureCollectIntervention-DISCARD_LOWER_PRIORITY_SIBLINGS = 4--><!--Device-GestureCollectIntervention-DISCARD_LOWER_PRIORITY_SIBLINGS = 4-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
