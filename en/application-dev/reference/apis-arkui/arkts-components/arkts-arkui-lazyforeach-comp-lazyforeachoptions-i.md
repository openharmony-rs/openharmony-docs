# LazyForEachOptions

```TypeScript
declare interface LazyForEachOptions
```

Configures the resource release strategy and memory optimization strategy of **LazyForEach**, and whether to enable custom component freezing.

> **NOTE:** 
> 
> 1. When using **LazyForEachOptions**, ensure that the **keyGenerator** function has been defined; otherwise,compilation will fail.
> 
> 2. Custom component freezing: When a custom component is directly used under **LazyForEach**, this configuration determines whether to enable the freezing feature of the custom component. Once enabled, when the custom component is outside the visible area, the framework pauses the processing logic such as state variable updates of the component to reduce resource consumption; when the component re-enters the visible area, normal processing resumes.
> 
> 3. Resource release strategy: **LazyForEach** manages the nodes in the on-screen area and the preloading area. When a node slides out of the preloading area and leaves the management scope of **LazyForEach**, **LazyForEach** no longer manages the node, and the node resources are released. The **BATCH** mode is used by default, in which
> **LazyForEach** releases all nodes to be released in the current frame. The **PROGRESSIVE** mode releases resources
> one by one, and when releasing the resources of each node, it checks whether the time of the current frame is
> sufficient; if not, the release is postponed to subsequent frames. Under this strategy, **LazyForEach** may hold
> node resources, and the nodes in the cache pool cannot be replenished in time, which reduces the reuse rate in
> scenarios where nodes are obtained quickly. Developers should select an appropriate resource release strategy based
> on the application scenario.

**Since:** 26.0.0

<!--Device-unnamed-declare interface LazyForEachOptions--><!--Device-unnamed-declare interface LazyForEachOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## customComponentFreezeMode

```TypeScript
customComponentFreezeMode?: LazyForEachCustomComponentFreezeMode
```

Whether to enable custom component freezing. It takes effect only when a custom component is directly used under **LazyForEach**, and does not apply to other cases. Default value: [AUTO](arkts-arkui-lazyforeach-comp-lazyforeachcustomcomponentfreezemode-e.md).

**Type:** [LazyForEachCustomComponentFreezeMode](arkts-arkui-lazyforeach-comp-lazyforeachcustomcomponentfreezemode-e.md)

**Default:** LazyForEachCustomComponentFreezeMode.AUTO

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyForEachOptions-customComponentFreezeMode?: LazyForEachCustomComponentFreezeMode--><!--Device-LazyForEachOptions-customComponentFreezeMode?: LazyForEachCustomComponentFreezeMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## memoryOptimizationStrategy

```TypeScript
memoryOptimizationStrategy?: LazyForEachMemOptStrategy
```

Memory optimization strategy of **LazyForEach**. This parameter is set when **LazyForEach** is created and does not support dynamic modification.

Default value: [DEFAULT](arkts-arkui-lazyforeach-comp-lazyforeachmemoptstrategy-e.md)

**Type:** [LazyForEachMemOptStrategy](arkts-arkui-lazyforeach-comp-lazyforeachmemoptstrategy-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyForEachOptions-memoryOptimizationStrategy?: LazyForEachMemOptStrategy--><!--Device-LazyForEachOptions-memoryOptimizationStrategy?: LazyForEachMemOptStrategy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## releaseStrategy

```TypeScript
releaseStrategy?: LazyForEachReleaseStrategy
```

Resource release strategy for **LazyForEach**. Default value: [BATCH](arkts-arkui-lazyforeach-comp-lazyforeachreleasestrategy-e.md).

**Type:** [LazyForEachReleaseStrategy](arkts-arkui-lazyforeach-comp-lazyforeachreleasestrategy-e.md)

**Default:** LazyForEachReleaseStrategy.BATCH

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyForEachOptions-releaseStrategy?: LazyForEachReleaseStrategy--><!--Device-LazyForEachOptions-releaseStrategy?: LazyForEachReleaseStrategy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
