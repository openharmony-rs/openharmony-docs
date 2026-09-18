# CompetitionStrategy

Defines whether the dispatched event is a competitive gesture. In the competitive scenario, only one of the original node and target node of the gesture responds. In the non‑competitive scenario, both nodes can respond simultaneously.

**Since:** 24

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

Indicates that the dispatched event is a non‑competitive gesture.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## COMPETITION

```TypeScript
COMPETITION = 1
```

Indicates that the dispatched event is a competitive gesture.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
