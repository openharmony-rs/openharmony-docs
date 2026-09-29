# GridLayoutOptions

```TypeScript
declare interface GridLayoutOptions
```

Defines the grid layout options. In this API, **irregularIndexes** and **onGetIrregularSizeByIndex** can be used for grids where either **rowsTemplate** or **columnsTemplate** is set. These properties allow you to specify an index array and set the number of rows and columns to be occupied by a grid item at the specified index. For details about the usage, see [Example 3](../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#example-3-implementing-a-scrollable-grid-with-grid-items-spanning-rows-and-columns). On the other hand, **onGetRectByIndex** can be used for grids where both **rowsTemplate** and **columnsTemplate** are set. It allows you to specify the position and size for the grid item at the specified index. For details about the usage, see [Example 1](../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#example-1-creating-a-fixed-row-and-column-grid-layout).

To improve the performance of **Grid** in scenarios such as jumps and column quantity changes, you are advised to use **GridLayoutOptions** whenever possible. Even if there are no special cross-row or cross-column nodes in **Grid**, performance during jumps can still be enhanced by using 'Grid(this.scroller, {regularSize: [1, 1]})'.

**Since:** 10

<!--Device-unnamed-declare interface GridLayoutOptions--><!--Device-unnamed-declare interface GridLayoutOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onGetIrregularSizeByIndex

```TypeScript
onGetIrregularSizeByIndex?: (index: number) => [number, number]
```

Number of rows and columns occupied by the grid item with an irregular size. This parameter is used together with **irregularIndexes**. In versions earlier than API version 12, the vertical scrolling grid does not support grid items spanning multiple rows, and the horizontal scrolling grid does not support grid items spanning multiple columns.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridLayoutOptions-onGetIrregularSizeByIndex?: (index: number) => [number, number]--><!--Device-GridLayoutOptions-onGetIrregularSizeByIndex?: (index: number) => [number, number]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes |  |

## onGetRectByIndex

```TypeScript
onGetRectByIndex?: (index: number) => [number, number, number, number]
```

Position and size of the grid item with the specified index, in the format of [rowStart,columnStart,rowSpan,columnSpan], <br>where **rowStart** indicates the row start position, **columnStart** indicates the column start position, <br>**rowSpan** indicates the number of rows occupied by the grid item, and **columnSpan** indicates the number of columns occupied by the grid item. Their values are unitless. <br>The values of **rowStart** and **columnStart** are natural numbers greater than or equal to 0. If a negative value is set, the default value **0** is used. <br>The values of **rowSpan** and **columnSpan** are natural numbers greater than or equal to 1. If a decimal is set, it is rounded down. If the decimal set is less than 1, the value **1** is used. <br>**NOTE:** <br>Case 1: If a grid item finds that the start position specified for it is already occupied, it searches for an available start position from left to right and from top to bottom, starting from position [0,0]. <br>Case 2: If any space other than the start position specified for a grid item is occupied, the grid item is displayed within the available space left.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GridLayoutOptions-onGetRectByIndex?: (index: number) => [number, number, number, number]--><!--Device-GridLayoutOptions-onGetRectByIndex?: (index: number) => [number, number, number, number]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes |  |

## irregularIndexes

```TypeScript
irregularIndexes?: number[]
```

Size of **GridItem** at the specified index in **Grid**. The size is irregular. When **onGetIrregularSizeByIndex** is not set, the grid item specified in this parameter occupies an entire row of the grid that scrolls vertically or an entire column of the grid that scrolls horizontally.

**Type:** number[]

**Default:** number[] no irregular grid item

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridLayoutOptions-irregularIndexes?: number[]--><!--Device-GridLayoutOptions-irregularIndexes?: number[]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## regularSize

```TypeScript
regularSize: [number, number]
```

Number of rows and columns occupied by a grid item with regular size. The only supported value is **[1, 1]**, meaning that the grid item occupies one row and one column.

**Type:** [number, number]

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridLayoutOptions-regularSize: [number, number]--><!--Device-GridLayoutOptions-regularSize: [number, number]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
