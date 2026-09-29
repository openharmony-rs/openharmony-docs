# ItemFillPolicy

```TypeScript
declare interface ItemFillPolicy
```

Defines a responsive layout policy applicable to the WaterFlow, Grid, List, Swiper, and LazyVWaterFlowLayout components. The LazyVWaterFlowLayout component is supported since API version 26.0.0.

**Since:** 22

<!--Device-unnamed-declare interface ItemFillPolicy--><!--Device-unnamed-declare interface ItemFillPolicy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fillType

```TypeScript
fillType?: ResponsiveFillType
```

Column count for different breakpoints. The default value is **BREAKPOINT_DEFAULT**.

**Type:** [ResponsiveFillType](arkts-arkui-responsivefilltype-t.md)

**Default:** ResponsiveFillType.BREAKPOINT_DEFAULT

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-ItemFillPolicy-fillType?: ResponsiveFillType--><!--Device-ItemFillPolicy-fillType?: ResponsiveFillType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
