# ScrollEffectType

```TypeScript
declare enum ScrollEffectType
```

Provides the scroll blur effect type of the title bar.

**Since:** 26.0.0

<!--Device-unnamed-declare enum ScrollEffectType--><!--Device-unnamed-declare enum ScrollEffectType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## COMMON_BLUR

```TypeScript
COMMON_BLUR = 0
```

Common blur style, which evenly blurs the background. The blurred background is displayed or hidden with the transparency gradient.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ScrollEffectType-COMMON_BLUR = 0--><!--Device-ScrollEffectType-COMMON_BLUR = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## GRADUAL_BLUR

```TypeScript
GRADUAL_BLUR = 1
```

Gradual blur style, which evenly blurs the title background with clear boundaries. The color or status of the title bar content is switched before and after scrolling, and changes linearly with the gesture during scrolling.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ScrollEffectType-GRADUAL_BLUR = 1--><!--Device-ScrollEffectType-GRADUAL_BLUR = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
