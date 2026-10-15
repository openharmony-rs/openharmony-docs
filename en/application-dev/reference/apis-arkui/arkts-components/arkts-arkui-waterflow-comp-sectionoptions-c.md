# SectionOptions

```TypeScript
declare class SectionOptions
```

Describes the configuration of the water flow item section.

**Since:** 12

<!--Device-unnamed-declare class SectionOptions--><!--Device-unnamed-declare class SectionOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onGetItemMainSizeByIndex

```TypeScript
onGetItemMainSizeByIndex?: GetItemMainSizeByIndex
```

Used to obtain the main axis size of the **FlowItem** at the specified index during the layout of the **WaterFlow** component. For a vertical **WaterFlow**, it is the height; for a horizontal **WaterFlow**, it is the width, in vp. When not set, the **WaterFlow** determines the main axis size based on the regular measurement result of the **FlowItem**.

**NOTE:** 

1. When both **onGetItemMainSizeByIndex** and the width and height attributes of the **FlowItem** are used,
the main axis size is subject to the result returned by **onGetItemMainSizeByIndex**, which overrides the main axis length of the **FlowItem**.
2. Using **onGetItemMainSizeByIndex** can improve the efficiency of jumping to a specified position or index
in the **WaterFlow**. Avoid mixing groups with and without **onGetItemMainSizeByIndex** set, which may cause layout exceptions.
3. When **onGetItemMainSizeByIndex** returns a negative number, the main axis size of the **FlowItem** is 0.
4. If the main axis size of the **FlowItem** changes dynamically with the data,
ensure that the value returned by **onGetItemMainSizeByIndex** is consistent with the data source. When using [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), call [onDataChange](arkts-arkui-lazyforeach-comp-datachangelistener-i.md#ondatachange), [onDataReloaded](arkts-arkui-lazyforeach-comp-datachangelistener-i.md#ondatareloaded), or [onDatasetChange](arkts-arkui-lazyforeach-comp-datachangelistener-i.md#ondatasetchange) to notify the framework that the data has changed after the data changes. When using [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md), modify the state array according to the data update rules of Repeat.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SectionOptions-onGetItemMainSizeByIndex?: GetItemMainSizeByIndex--><!--Device-SectionOptions-onGetItemMainSizeByIndex?: GetItemMainSizeByIndex-End-->

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

<!--Device-SectionOptions-columnsGap?: Dimension--><!--Device-SectionOptions-columnsGap?: Dimension-End-->

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

<!--Device-SectionOptions-crossCount?: number--><!--Device-SectionOptions-crossCount?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemsCount

```TypeScript
itemsCount: number
```

Number of **FlowItem** components in the group, which must be a non-negative number. If the **itemsCount** of any group received by the **splice**, **push**, or **update** method is less than 0, the method does not take effect (returns false). Avoid using a group with **itemsCount** of 0, which may cause layout calculation exceptions.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SectionOptions-itemsCount: number--><!--Device-SectionOptions-itemsCount: number-End-->

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

<!--Device-SectionOptions-margin?: Margin | Dimension--><!--Device-SectionOptions-margin?: Margin | Dimension-End-->

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

<!--Device-SectionOptions-rowsGap?: Dimension--><!--Device-SectionOptions-rowsGap?: Dimension-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
