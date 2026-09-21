# BarGridColumnOptions

```TypeScript
interface BarGridColumnOptions
```

Implements a **BarGridColumnOptions** object for setting the visible area of the tab bar in grid mode, including the column margin and gutter, as well as the number of columns occupied by tabs under small, medium, and large screen sizes.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## gutter

```TypeScript
gutter?: Dimension
```

Column gutter (that is, gap between columns) in grid mode. It cannot be set in percentage.

Default value: **24.0**

Unit: vp

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lg

```TypeScript
lg?: number
```

Number of columns occupied by a tab on a screen whose width is greater than or equal to 840 vp but less than 1024 vp.

The value must be a non-negative even number. The default value is **-1**, indicating that the tab takes up the entire width of the tab bar.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## margin

```TypeScript
margin?: Dimension
```

Column margin in grid mode. It cannot be set in percentage.

Default value: **24.0**

Unit: vp

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## md

```TypeScript
md?: number
```

Number of columns occupied by a tab on a screen whose width is greater than or equal to 600 vp but less than 800 vp.

The value must be a non-negative even number. The default value is **-1**, indicating that the tab takes up the entire width of the tab bar.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## sm

```TypeScript
sm?: number
```

Number of columns occupied by a tab on a screen whose width is greater than or equal to 320 vp but less than 600 vp.

The value must be a non-negative even number. The default value is **-1**, indicating that the tab takes up the entire width of the tab bar.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
