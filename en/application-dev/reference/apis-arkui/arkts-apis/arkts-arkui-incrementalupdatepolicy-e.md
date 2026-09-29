# IncrementalUpdatePolicy

```TypeScript
declare enum IncrementalUpdatePolicy
```

Incremental update policy for text rendering.

**Since:** 26.0.0

<!--Device-unnamed-declare enum IncrementalUpdatePolicy--><!--Device-unnamed-declare enum IncrementalUpdatePolicy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NONE

```TypeScript
NONE = 0
```

Disables incremental update and uses full layout rendering.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-IncrementalUpdatePolicy-NONE = 0--><!--Device-IncrementalUpdatePolicy-NONE = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## PARAGRAPH_CACHE

```TypeScript
PARAGRAPH_CACHE = 1
```

Enables incremental update and uses paragraph-level cache. This policy takes effect only when the styled string object bound to the text remains unchanged. If the styled string object changes, the cache cannot be hit.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-IncrementalUpdatePolicy-PARAGRAPH_CACHE = 1--><!--Device-IncrementalUpdatePolicy-PARAGRAPH_CACHE = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
