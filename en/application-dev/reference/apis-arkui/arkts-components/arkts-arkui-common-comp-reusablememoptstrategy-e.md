# ReusableMemOptStrategy

```TypeScript
declare enum ReusableMemOptStrategy
```

Enumerates the memory optimization strategies of reusable custom components.

@enum { number }

**Since:** 26.0.0

<!--Device-unnamed-declare enum ReusableMemOptStrategy--><!--Device-unnamed-declare enum ReusableMemOptStrategy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

No memory optimization strategy.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ReusableMemOptStrategy-DEFAULT = 0--><!--Device-ReusableMemOptStrategy-DEFAULT = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ENABLE_AUTO_CACHE_OPTIMIZATION

```TypeScript
ENABLE_AUTO_CACHE_OPTIMIZATION = 1 << 0
```

Automatic memory optimization strategy. It is recommended to use this strategy in scenarios where the memory usage of reusable custom components needs to be reduced. <br>When any of the following conditions is met, all custom components of this type in the reuse pool are released: <br> - The app is switched to the background. <br> - The component where the reuse pool resides is invisible (the [visibility](arkts-arkui-common-comp-commonmethod-c.md#visibility) attribute is set to a value other than [Visible](../arkts-apis/arkts-arkui-visibility-e.md#visible), or the component area is 0, regardless of occlusion). <br> - The device is low on memory (the [MemoryLevel](../../apis-ability-kit/arkts-apis/arkts-ability-abilityconstant-memorylevel-e.md) reaches **MEMORY_LEVEL_LOW** or **MEMORY_LEVEL_CRITICAL**). <br>When the number of custom components of this type with the same **ReuseId** in the reuse pool exceeds the reuse pool capacity limit and does not increase within 5 seconds, the components within the limit are retained and the rest are released. The reuse pool capacity limit is set as follows: <br> - When the device memory is greater than 8 GB, the limit is 48. <br> - When the device memory is greater than 6 GB and less than or equal to 8 GB, the limit is 4. <br> - When the device memory is less than or equal to 6 GB, the limit is 2. <br>When nodes are released, the [custom component lifecycle](../../../ui/state-management/arkts-page-custom-components-lifecycle.md) is triggered.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ReusableMemOptStrategy-ENABLE_AUTO_CACHE_OPTIMIZATION = 1 << 0--><!--Device-ReusableMemOptStrategy-ENABLE_AUTO_CACHE_OPTIMIZATION = 1 << 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
