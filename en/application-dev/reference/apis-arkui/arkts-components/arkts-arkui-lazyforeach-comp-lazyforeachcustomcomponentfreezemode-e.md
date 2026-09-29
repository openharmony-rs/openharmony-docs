# LazyForEachCustomComponentFreezeMode

```TypeScript
declare enum LazyForEachCustomComponentFreezeMode
```

Selects whether to enable custom component freezing.

> **NOTE:** 
> 
> This configuration is added only when a custom component is directly used under **LazyForEach**. It is not
> applicable in other cases.

**Since:** 26.0.0

<!--Device-unnamed-declare enum LazyForEachCustomComponentFreezeMode--><!--Device-unnamed-declare enum LazyForEachCustomComponentFreezeMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## AUTO

```TypeScript
AUTO = 0
```

Follows the **metadata** settings in the **module.json5** configuration file.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyForEachCustomComponentFreezeMode-AUTO = 0--><!--Device-LazyForEachCustomComponentFreezeMode-AUTO = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DISABLED

```TypeScript
DISABLED = 1
```

Does not enable custom component freezing.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyForEachCustomComponentFreezeMode-DISABLED = 1--><!--Device-LazyForEachCustomComponentFreezeMode-DISABLED = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ENABLED

```TypeScript
ENABLED = 2
```

Enables custom component freezing.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyForEachCustomComponentFreezeMode-ENABLED = 2--><!--Device-LazyForEachCustomComponentFreezeMode-ENABLED = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
