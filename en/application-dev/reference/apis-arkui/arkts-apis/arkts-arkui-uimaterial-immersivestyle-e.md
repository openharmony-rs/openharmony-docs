# ImmersiveStyle

```TypeScript
enum ImmersiveStyle
```

Enumerates the material styles. The enum values suffixed with EC are set on [EffectComponent](../arkts-components/arkts-arkui-effectcomponent-comp-sys.md), and those suffixed with EC_SUB are set on the child components of EffectComponent. The two work together to achieve merged optimization of material effect rendering. The material blur set on EffectComponent will ultimately take effect on its child components. Different material styles correspond to different material parameters, mainly including the blur level and highlight effect of the material. For details, see [ImmersiveStyle](arkts-arkui-uimaterial-immersivestyle-e.md).

**Since:** 26.0.0

<!--Device-uiMaterial-enum ImmersiveStyle--><!--Device-uiMaterial-enum ImmersiveStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## REGULAR

```TypeScript
REGULAR = 2
```

Regular style, which means the material layer is of regular thickness.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ImmersiveStyle-REGULAR = 2--><!--Device-ImmersiveStyle-REGULAR = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## THICK

```TypeScript
THICK = 3
```

Thick style, which provides a strong blur effect.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ImmersiveStyle-THICK = 3--><!--Device-ImmersiveStyle-THICK = 3-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## THIN

```TypeScript
THIN = 1
```

Thin style, which provides a strong transparent effect.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ImmersiveStyle-THIN = 1--><!--Device-ImmersiveStyle-THIN = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ULTRA_THICK

```TypeScript
ULTRA_THICK = 4
```

Ultra-thick style, which provides a very strong blur effect.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ImmersiveStyle-ULTRA_THICK = 4--><!--Device-ImmersiveStyle-ULTRA_THICK = 4-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ULTRA_THIN

```TypeScript
ULTRA_THIN = 0
```

Ultra-thin style, which provides a very strong transparent effect.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ImmersiveStyle-ULTRA_THIN = 0--><!--Device-ImmersiveStyle-ULTRA_THIN = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
