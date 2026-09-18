# FocusWrapMode

Enumerates focus wrapping modes for cross-axis directional navigation.

**Since:** 20

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

Cross-axis directional navigation does not wrap focus.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## WRAP_WITH_ARROW

```TypeScript
WRAP_WITH_ARROW = 1
```

Cross-axis directional navigation wraps focus.

In irregular grid layouts, when moving focus along the cross axis, the system prioritizes focusable items within the same row.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
