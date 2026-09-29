# PresetFillType

```TypeScript
declare enum PresetFillType
```

Enumerates column count policies for different [breakpoints](../../../ui/arkts-layout-development-grid-layout.md#breakpoints).

**Since:** 22

<!--Device-unnamed-declare enum PresetFillType--><!--Device-unnamed-declare enum PresetFillType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## BREAKPOINT_DEFAULT

```TypeScript
BREAKPOINT_DEFAULT = 0
```

For **List** and **Swiper** components: displays 1 column when the component width falls within the sm and smaller breakpoint range, 2 columns within the md breakpoint range, and 3 columns within the lg and larger breakpoint range.

For **Grid**, **WaterFlow**, and **LazyVWaterFlowLayout** components: displays 2 columns when the component width falls within the sm and smaller breakpoint range, 3 columns within the md breakpoint range, and 5 columns within the lg and larger breakpoint range. **LazyVWaterFlowLayout** is supported since API version 26.0.0.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-PresetFillType-BREAKPOINT_DEFAULT = 0--><!--Device-PresetFillType-BREAKPOINT_DEFAULT = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## BREAKPOINT_SM1MD2LG3

```TypeScript
BREAKPOINT_SM1MD2LG3 = 1
```

Displays 1 column when the component width falls within the sm and smaller breakpoint range, 2 columns within the md breakpoint range, and 3 columns within the lg and larger breakpoint range.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-PresetFillType-BREAKPOINT_SM1MD2LG3 = 1--><!--Device-PresetFillType-BREAKPOINT_SM1MD2LG3 = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## BREAKPOINT_SM2MD3LG5

```TypeScript
BREAKPOINT_SM2MD3LG5 = 2
```

Displays 2 columns when the component width falls within the sm and smaller breakpoint range, 3 columns within the md breakpoint range, and 5 columns within the lg and larger breakpoint range.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-PresetFillType-BREAKPOINT_SM2MD3LG5 = 2--><!--Device-PresetFillType-BREAKPOINT_SM2MD3LG5 = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
