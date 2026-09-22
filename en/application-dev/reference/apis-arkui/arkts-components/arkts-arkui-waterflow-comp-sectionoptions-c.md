# SectionOptions

```TypeScript
declare class SectionOptions
```

Describes the configuration of the water flow item section.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onGetItemMainSizeByIndex

```TypeScript
onGetItemMainSizeByIndex?: GetItemMainSizeByIndex
```

Callback used to obtain the main axis size, in vp, of the water flow item at a specified index during the layout process of the **WaterFlow** component. For a vertical **WaterFlow** component, this size refers to the height, and for a horizontal **WaterFlow** component, it refers to the width.

**NOTE:** 

1. When both **onGetItemMainSizeByIndex** and the width or height attribute of **FlowItem** are used,
the main-axis size is determined by the return value of **onGetItemMainSizeByIndex**, which will override the main-axis length of **FlowItem**.
2. Using **onGetItemMainSizeByIndex** can improve the efficiency of jumping to a specific position
or index in the **WaterFlow** component. Avoid mixing the use of **onGetItemMainSizeByIndex** with sections that do not have it set, as this can cause layout exceptions.
3. If **onGetItemMainSizeByIndex** returns a negative number, the height of the water flow item is 0.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## columnsGap

```TypeScript
columnsGap?: Dimension
```

Column gap of the section. If this parameter is not set, the [columnsGap](arkts-arkui-waterflow-comp-attribute.md#columnsgap) of the **WaterFlow** component is used by default. If an invalid value is set, 0 vp is used.

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## crossCount

```TypeScript
crossCount?: number
```

Number of columns (in vertical layout) or rows (in horizontal layout).

Default value: **1**

If the value is less than 1, the default value is used.

**Type:** number

**Default:** 1 one column in vertical layout, or one row in horizontal layout

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemsCount

```TypeScript
itemsCount: number
```

Number of **FlowItem** components in a section. The value must be a non-negative number. If the **splice**, **push**, or **update** APIs receive a section whose **itemsCount** is set to a negative number, these APIs will not be executed. Do not use a section whose **itemsCount** is **0**. Otherwise, the layout calculation may be abnormal.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## margin

```TypeScript
margin?: Margin | Dimension
```

Margins of the section. A value of the **Length** type specifies the margins on all the four sides.

Default value: **0**

Unit: vp

When **margin** is set to a percentage, the width of the **WaterFlow** component is used as the base value for the top, bottom, left, and right margins.

**Type:** [Margin](../arkts-apis/arkts-arkui-margin-t.md) &#124; [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Default:** {top: 0, right: 0, bottom: 0, left: 0}

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## rowsGap

```TypeScript
rowsGap?: Dimension
```

Row gap of the section. If this parameter is not set, the [rowsGap](arkts-arkui-waterflow-comp-attribute.md#rowsgap) of the **WaterFlow** component is used by default. If an invalid value is set, 0 vp is used.

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
