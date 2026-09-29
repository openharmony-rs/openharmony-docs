# LazyForEachReleaseStrategy

```TypeScript
declare enum LazyForEachReleaseStrategy
```

Selects the resource release strategy of **LazyForEach**.

**Since:** 26.0.0

<!--Device-unnamed-declare enum LazyForEachReleaseStrategy--><!--Device-unnamed-declare enum LazyForEachReleaseStrategy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## BATCH

```TypeScript
BATCH = 0
```

**BATCH** is the resource release strategy used by default. This strategy releases the resources of all discarded nodes in the current frame. If node reuse exists, the node reuse rate can be maximized. However, if a node has a deep component hierarchy or a large number of child components, releasing the resources of a single node takes a long time. Releasing a large number of nodes in the current frame may cause an oversized frame and affect performance.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyForEachReleaseStrategy-BATCH = 0--><!--Device-LazyForEachReleaseStrategy-BATCH = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## PROGRESSIVE

```TypeScript
PROGRESSIVE = 1
```

**PROGRESSIVE** is a strategy that automatically adjusts node release based on the node release time and the remaining time of the current frame. If the remaining time of the current frame is insufficient to release the remaining nodes, the release is postponed to subsequent frames, avoiding oversized frames and optimizing performance. In this case, **LazyForEach** continues to hold the nodes, which may reduce the reuse rate. When a large number of nodes are generated and cannot be released in time, memory usage increases accordingly. Developers need to pay attention to the impact on performance and memory and select a proper resource release strategy.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyForEachReleaseStrategy-PROGRESSIVE = 1--><!--Device-LazyForEachReleaseStrategy-PROGRESSIVE = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
