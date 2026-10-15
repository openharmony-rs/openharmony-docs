# BarGridColumnOptions

```TypeScript
interface BarGridColumnOptions
```

Defines an object for setting the grid layout of the tab bar, including the column margin and gutter in grid mode, and the number of columns occupied by tabs on small, medium, and large screens.

**Since:** 10

<!--Device-unnamed-interface BarGridColumnOptions--><!--Device-unnamed-interface BarGridColumnOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## gutter

```TypeScript
gutter?: Dimension
```

Column gutter in grid mode. Percentage setting is not supported. Value range: [0, +∞). Default value: **24.0**

Unit: vp

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-BarGridColumnOptions-gutter?: Dimension--><!--Device-BarGridColumnOptions-gutter?: Dimension-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lg

```TypeScript
lg?: number
```

Number of columns occupied by tabs on a large screen. A non-negative even number or -1 (-1 indicates that the tabs occupy the full width of the tab bar). A large screen is greater than or equal to 840 vp but less than 1024 vp.

Default value: **-1**

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-BarGridColumnOptions-lg?: number--><!--Device-BarGridColumnOptions-lg?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## margin

```TypeScript
margin?: Dimension
```

Column margin in grid mode. Percentage setting is not supported. Value range: [0, +∞). Default value: **24.0**

Unit: vp

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-BarGridColumnOptions-margin?: Dimension--><!--Device-BarGridColumnOptions-margin?: Dimension-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## md

```TypeScript
md?: number
```

Number of columns occupied by tabs on a medium screen. A non-negative even number or -1 (-1 indicates that the tabs occupy the full width of the tab bar). A medium screen is greater than or equal to 600 vp but less than 800 vp.

Default value: **-1**

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-BarGridColumnOptions-md?: number--><!--Device-BarGridColumnOptions-md?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## sm

```TypeScript
sm?: number
```

Number of columns occupied by tabs on a small screen. A non-negative even number or -1 (-1 indicates that the tabs occupy the full width of the tab bar). A small screen is greater than or equal to 320 vp but less than 600 vp.

Default value: **-1**

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-BarGridColumnOptions-sm?: number--><!--Device-BarGridColumnOptions-sm?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
