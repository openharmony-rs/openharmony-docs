# GridLayoutAlgorithmOptions

Sets the number of columns, column spacing, and row spacing of the grid layout algorithm.

@interface GridLayoutAlgorithmOptions

**Since:** 24

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## columnsGap

```TypeScript
columnsGap?: LengthMetrics
```

Spacing between columns.

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

Number of columns in the grid layout.

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

Spacing between rows.

Default value: **LengthMetrics.vp(0)**

Invalid values are treated as the default value.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Default:** LengthMetrics.vp(0)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
