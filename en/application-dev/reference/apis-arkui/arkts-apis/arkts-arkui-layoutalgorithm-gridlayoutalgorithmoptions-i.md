# GridLayoutAlgorithmOptions

```TypeScript
interface GridLayoutAlgorithmOptions
```

Sets the column count template, column spacing, and row spacing of the grid layout algorithm.

**Since:** 24

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## columnsGap

```TypeScript
columnsGap?: LengthMetrics
```

Spacing between columns. Value range: a non-negative number.

Default value: **LengthMetrics.vp(0)**

Invalid values are treated as the default value.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Default:** LengthMetrics.vp(0)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## columnsTemplate

```TypeScript
columnsTemplate?: string | ItemFillPolicy
```

Column template of the current grid layout, defining the width and number of columns. The string type must conform to the template format, for example, **'1fr'** indicates a single-column layout, **'1fr 1fr 1fr'** indicates a three-column equal-width layout, and **'1fr 2fr'** indicates a two-column layout where the second column is twice as wide as the first. When **ItemFillPolicy** is used, adaptive column count can be achieved.

Default value: **'1fr'**

Invalid values are treated as the default value.

**Type:** string &#124; [ItemFillPolicy](arkts-arkui-itemfillpolicy-i.md)

**Default:** '1fr'

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## rowsGap

```TypeScript
rowsGap?: LengthMetrics
```

Spacing between rows. Value range: a non-negative number.

Default value: **LengthMetrics.vp(0)**

Invalid values are treated as the default value.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Default:** LengthMetrics.vp(0)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
