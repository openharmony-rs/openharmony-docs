# ReplaceEffectType

```TypeScript
declare enum ReplaceEffectType
```

Enumerates symbol replacement effect types.

**Since:** 20

<!--Device-unnamed-declare enum ReplaceEffectType--><!--Device-unnamed-declare enum ReplaceEffectType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SEQUENTIAL

```TypeScript
SEQUENTIAL = 0
```

Sequential replacement: The current symbol disappears before a new symbol appears. This is the default symbol replacement effect type.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

<!--Device-ReplaceEffectType-SEQUENTIAL = 0--><!--Device-ReplaceEffectType-SEQUENTIAL = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CROSS_FADE

```TypeScript
CROSS_FADE = 1
```

Cross-fade transition effect: The current symbol fades out while a new symbol fades in simultaneously.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

<!--Device-ReplaceEffectType-CROSS_FADE = 1--><!--Device-ReplaceEffectType-CROSS_FADE = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SLASH_OVERLAY

```TypeScript
SLASH_OVERLAY = 2
```

Slash overlay effect: The current symbol is replaced with a symbol featuring diagonal slash, typically indicating disabled state.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

<!--Device-ReplaceEffectType-SLASH_OVERLAY = 2--><!--Device-ReplaceEffectType-SLASH_OVERLAY = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
