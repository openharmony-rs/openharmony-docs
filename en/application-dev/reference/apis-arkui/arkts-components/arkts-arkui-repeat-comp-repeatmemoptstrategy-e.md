# RepeatMemOptStrategy

```TypeScript
declare enum RepeatMemOptStrategy
```

Enumerates the memory optimization strategies of **Repeat**.

**Since:** 26.0.0

<!--Device-unnamed-declare enum RepeatMemOptStrategy--><!--Device-unnamed-declare enum RepeatMemOptStrategy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

No memory optimization strategy.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-RepeatMemOptStrategy-DEFAULT = 0--><!--Device-RepeatMemOptStrategy-DEFAULT = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ENABLE_AUTO_CACHE_OPTIMIZATION

```TypeScript
ENABLE_AUTO_CACHE_OPTIMIZATION = 1 << 0
```

Automatic memory optimization strategy. When the memory usage of **Repeat** child nodes needs to be reduced, it is recommended to use this strategy to lower memory usage.

When the application goes to the background, when the component where **Repeat** resides is invisible (the [visibility](arkts-arkui-common-comp-commonmethod-c.md#visibility) attribute is set to a value other than Visible, or the component area is 0, regardless of occlusion), or when the device memory is low (the [MemoryLevel](../../apis-ability-kit/arkts-apis/arkts-ability-abilityconstant-memorylevel-e.md) reaches **MEMORY_LEVEL_LOW** or **MEMORY_LEVEL_CRITICAL**), all nodes in the [cache pool](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md#node-update-and-reuse-mechanism) are released.

When the application returns to the foreground and the component where **Repeat** resides is displayed again, the nodes in the cache pool are restored.

When nodes are released and restored, the [custom component lifecycle](../../../ui/state-management/arkts-page-custom-components-lifecycle.md) is triggered.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-RepeatMemOptStrategy-ENABLE_AUTO_CACHE_OPTIMIZATION = 1 << 0--><!--Device-RepeatMemOptStrategy-ENABLE_AUTO_CACHE_OPTIMIZATION = 1 << 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
