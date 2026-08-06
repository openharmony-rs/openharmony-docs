# GestureCollectIntervention

Define the gesture and events collection intervention operations.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare enum GestureCollectIntervention--><!--Device-unnamed-export declare enum GestureCollectIntervention-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CONTINUE

```TypeScript
CONTINUE = 0
```

Continue the normal collection process. No intervention will be applied.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureCollectIntervention-CONTINUE = 0--><!--Device-GestureCollectIntervention-CONTINUE = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DISCARD_LOWER

```TypeScript
DISCARD_LOWER = 1
```

Discard all pending lower-priority gestures and events. This includes gestures from left sibling nodes and ancestor nodes (parent and above). Only the already collected gestures from the current node and higher-priority nodes will be retained.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureCollectIntervention-DISCARD_LOWER = 1--><!--Device-GestureCollectIntervention-DISCARD_LOWER = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DISCARD_HIGHER

```TypeScript
DISCARD_HIGHER = 2
```

Discard already collected higher-priority gestures and events. This removes gestures from right sibling nodes that have been collected. The collection will continue with lower-priority gestures (left siblings and ancestors).

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureCollectIntervention-DISCARD_HIGHER = 2--><!--Device-GestureCollectIntervention-DISCARD_HIGHER = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DISCARD_SELF

```TypeScript
DISCARD_SELF = 3
```

Discard gestures and events from the current node itself. The current node's gestures and events will be excluded from the gesture tree. Gestures from sibling nodes (both left and right) and ancestor nodes will still be collected.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureCollectIntervention-DISCARD_SELF = 3--><!--Device-GestureCollectIntervention-DISCARD_SELF = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DISCARD_LOWER_PRIORITY_SIBLINGS

```TypeScript
DISCARD_LOWER_PRIORITY_SIBLINGS = 4
```

Discard gestures and events from left sibling nodes that are pending collection. Gestures and events from the current node and already collected right sibling nodes will be retained. The collection will continue with ancestor nodes.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureCollectIntervention-DISCARD_LOWER_PRIORITY_SIBLINGS = 4--><!--Device-GestureCollectIntervention-DISCARD_LOWER_PRIORITY_SIBLINGS = 4-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

