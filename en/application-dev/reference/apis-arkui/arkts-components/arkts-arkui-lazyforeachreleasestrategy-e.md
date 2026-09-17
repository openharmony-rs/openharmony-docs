# LazyForEachReleaseStrategy

Enumerates the release strategies for LazyForEach discarded nodes.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## BATCH

```TypeScript
BATCH = 0
```

Release all discarded nodes during the next idle period.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## PROGRESSIVE

```TypeScript
PROGRESSIVE = 1
```

Release discarded nodes one by one during the next idle period based on the remaining time of the current frame. Unreleased nodes will continue to be released in subsequent idle periods based on the available idle time.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
