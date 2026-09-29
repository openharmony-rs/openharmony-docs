# ReusableOptions

```TypeScript
declare interface ReusableOptions
```

Defines the parameters of a reusable custom component, which are used to configure the memory optimization strategy. They apply to scenarios where the memory usage of reusable custom components needs to be reduced.

@interface ReusableOptions

**Since:** 26.0.0

<!--Device-unnamed-declare interface ReusableOptions--><!--Device-unnamed-declare interface ReusableOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## memoryOptimizationStrategy

```TypeScript
memoryOptimizationStrategy?: ReusableMemOptStrategy
```

Memory optimization strategy for reusable custom components. This parameter is set when a reusable custom component is created and cannot be dynamically modified. When [ENABLE_AUTO_CACHE_OPTIMIZATION](arkts-arkui-common-comp-reusablememoptstrategy-e.md) is passed, automatic memory optimization is enabled, and components in the reuse pool are automatically released in scenarios such as the app being switched to the background, the component being invisible, or the device being low on memory. If this parameter is not passed, the default value [DEFAULT](arkts-arkui-common-comp-reusablememoptstrategy-e.md) (no memory optimization strategy) is used.

**Type:** [ReusableMemOptStrategy](arkts-arkui-common-comp-reusablememoptstrategy-e.md)

**Default:** ReusableMemOptStrategy.DEFAULT

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ReusableOptions-memoryOptimizationStrategy?: ReusableMemOptStrategy--><!--Device-ReusableOptions-memoryOptimizationStrategy?: ReusableMemOptStrategy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
