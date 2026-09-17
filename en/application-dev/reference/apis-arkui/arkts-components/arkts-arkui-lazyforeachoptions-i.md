# LazyForEachOptions

Defines the options for LazyForEach.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## customComponentFreezeMode

```TypeScript
customComponentFreezeMode?: LazyForEachCustomComponentFreezeMode
```

Freeze mode for cached custom nodes that have been removed from the component tree. Default value: LazyForEachCustomComponentFreezeMode.AUTO.

**Type:** [LazyForEachCustomComponentFreezeMode](arkts-arkui-lazyforeachcustomcomponentfreezemode-e.md)

**Default:** LazyForEachCustomComponentFreezeMode.AUTO

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## memoryOptimizationStrategy

```TypeScript
memoryOptimizationStrategy?: LazyForEachMemOptStrategy
```

Memory optimization strategy for LazyForEach.

**Type:** [LazyForEachMemOptStrategy](arkts-arkui-lazyforeachmemoptstrategy-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## releaseStrategy

```TypeScript
releaseStrategy?: LazyForEachReleaseStrategy
```

Resource release strategy for LazyForEach discarded nodes. Default value: LazyForEachReleaseStrategy.BATCH.

**Type:** [LazyForEachReleaseStrategy](arkts-arkui-lazyforeachreleasestrategy-e.md)

**Default:** LazyForEachReleaseStrategy.BATCH

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
