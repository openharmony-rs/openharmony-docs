# LazyForEachMemOptStrategy

```TypeScript
declare enum LazyForEachMemOptStrategy
```

Enumerates the memory optimization strategies of **LazyForEach**.

**Since:** 26.0.0

<!--Device-unnamed-declare enum LazyForEachMemOptStrategy--><!--Device-unnamed-declare enum LazyForEachMemOptStrategy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

No memory optimization strategy.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyForEachMemOptStrategy-DEFAULT = 0--><!--Device-LazyForEachMemOptStrategy-DEFAULT = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ENABLE_AUTO_CACHE_OPTIMIZATION

```TypeScript
ENABLE_AUTO_CACHE_OPTIMIZATION = 1 << 0
```

Automatic memory optimization strategy. When the number of list items carried by **LazyForEach** is large (for example, hundreds or more) or the structure of a single child component is complex (for example, containing multiple nested layers or dozens of child nodes), resulting in high memory usage (which can be detected through a performance analysis tool), it is recommended to use this strategy to reduce memory usage.

When the application moves to the background, when the component where **LazyForEach** resides is invisible (the [visibility](arkts-arkui-common-comp-commonmethod-c.md#visibility) attribute is set to a value other than Visible, or the component area is 0, regardless of occlusion), or when the device is low on memory ([MemoryLevel](../../apis-ability-kit/arkts-apis/arkts-ability-abilityconstant-memorylevel-e.md) reaches **MEMORY_LEVEL_LOW** or **MEMORY_LEVEL_CRITICAL**), for devices with memory greater than 6 GB, some nodes in the [preload area](../../../ui/rendering-control/arkts-rendering-control-overview.md#basic-concepts) are released until the number of nodes in both the upper and lower preload areas does not exceed 2; for devices with memory less than or equal to 6 GB, all nodes in the preload area are released.

When the application returns to the foreground, when the component where **LazyForEach** resides becomes visible again, or when **LazyForEach** scrolls, the nodes in the preload area are restored.

Releasing and restoring nodes triggers the [custom component lifecycle](../../../ui/state-management/arkts-page-custom-components-lifecycle.md).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyForEachMemOptStrategy-ENABLE_AUTO_CACHE_OPTIMIZATION = 1 << 0--><!--Device-LazyForEachMemOptStrategy-ENABLE_AUTO_CACHE_OPTIMIZATION = 1 << 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
