# ImmersiveStyle

```TypeScript
enum ImmersiveStyle
```

Enumerates the material styles. The enum values suffixed with EC are set on [EffectComponent](../arkts-components/arkts-arkui-effectcomponent-comp-sys.md), and those suffixed with EC_SUB are set on the child components of EffectComponent. The two work together to achieve merged optimization of material effect rendering. The material blur set on EffectComponent will ultimately take effect on its child components. Different material styles correspond to different material parameters, mainly including the blur level and highlight effect of the material. For details, see [ImmersiveStyle](arkts-arkui-uimaterial-immersivestyle-e.md).

**Since:** 26.0.0

<!--Device-uiMaterial-enum ImmersiveStyle--><!--Device-uiMaterial-enum ImmersiveStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## REGULAR_EC

```TypeScript
REGULAR_EC = 7
```

Regular style. The material layer has a moderate thickness, providing moderate transparency and blur effects.

Applicable to EffectComponent.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ImmersiveStyle-REGULAR_EC = 7--><!--Device-ImmersiveStyle-REGULAR_EC = 7-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## REGULAR_EC_SUB

```TypeScript
REGULAR_EC_SUB = 12
```

Regular style. The material layer has a moderate thickness, providing moderate transparency and blur effects.

Applicable to the child components of EffectComponent.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ImmersiveStyle-REGULAR_EC_SUB = 12--><!--Device-ImmersiveStyle-REGULAR_EC_SUB = 12-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## THICK_EC

```TypeScript
THICK_EC = 8
```

Thick style, providing a strong blur effect.

Applicable to EffectComponent.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ImmersiveStyle-THICK_EC = 8--><!--Device-ImmersiveStyle-THICK_EC = 8-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## THICK_EC_SUB

```TypeScript
THICK_EC_SUB = 13
```

Thick style, providing a strong blur effect.

Applicable to the child components of EffectComponent.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ImmersiveStyle-THICK_EC_SUB = 13--><!--Device-ImmersiveStyle-THICK_EC_SUB = 13-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## THIN_EC

```TypeScript
THIN_EC = 6
```

Thin style. The material layer is thin, providing a relatively strong transparency effect.

Applicable to EffectComponent.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ImmersiveStyle-THIN_EC = 6--><!--Device-ImmersiveStyle-THIN_EC = 6-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## THIN_EC_SUB

```TypeScript
THIN_EC_SUB = 11
```

Thin style. The material layer is thin, providing a relatively strong transparency effect.

Applicable to the child components of EffectComponent.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ImmersiveStyle-THIN_EC_SUB = 11--><!--Device-ImmersiveStyle-THIN_EC_SUB = 11-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## ULTRA_THICK_EC

```TypeScript
ULTRA_THICK_EC = 9
```

Ultra-thick style, providing a very strong blur effect.

Applicable to EffectComponent.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ImmersiveStyle-ULTRA_THICK_EC = 9--><!--Device-ImmersiveStyle-ULTRA_THICK_EC = 9-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## ULTRA_THICK_EC_SUB

```TypeScript
ULTRA_THICK_EC_SUB = 14
```

Ultra-thick style, providing a very strong blur effect.

Applicable to the child components of EffectComponent.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ImmersiveStyle-ULTRA_THICK_EC_SUB = 14--><!--Device-ImmersiveStyle-ULTRA_THICK_EC_SUB = 14-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## ULTRA_THIN_EC

```TypeScript
ULTRA_THIN_EC = 5
```

Ultra-thin style. The material layer is ultra-thin, providing a strong transparency effect.

Applicable to [EffectComponent](../arkts-components/arkts-arkui-effectcomponent-comp-sys.md). It must be used together with the corresponding EC_SUB suffix enum to achieve merged optimization of material effect rendering.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ImmersiveStyle-ULTRA_THIN_EC = 5--><!--Device-ImmersiveStyle-ULTRA_THIN_EC = 5-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## ULTRA_THIN_EC_SUB

```TypeScript
ULTRA_THIN_EC_SUB = 10
```

Ultra-thin style. The material layer is ultra-thin, providing a strong transparency effect.

Applicable to the child components of EffectComponent.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ImmersiveStyle-ULTRA_THIN_EC_SUB = 10--><!--Device-ImmersiveStyle-ULTRA_THIN_EC_SUB = 10-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
