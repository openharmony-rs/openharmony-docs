# GridLayoutOptions

```TypeScript
declare interface GridLayoutOptions
```

Defines the grid layout options. In this API, **irregularIndexes** and **onGetIrregularSizeByIndex** can be used for grids where either **rowsTemplate** or **columnsTemplate** is set. These properties allow you to specify an index array and set the number of rows and columns to be occupied by a grid item at the specified index. For details about the usage, see [Example 3](../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#example-3-implementing-a-scrollable-grid-with-grid-items-spanning-rows-and-columns). On the other hand, **onGetRectByIndex** can be used for grids where both **rowsTemplate** and **columnsTemplate** are set. It allows you to specify the position and size for the grid item at the specified index. For details about the usage, see [Example 1](../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#example-1-creating-a-fixed-row-and-column-grid-layout).

To improve the performance of **Grid** in scenarios such as jumps and column quantity changes, you are advised to use **GridLayoutOptions** whenever possible. Even if there are no special cross-row or cross-column nodes in **Grid**, performance during jumps can still be enhanced by using 'Grid(this.scroller, {regularSize: [1, 1]})'.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onGetStartIndexByIndex

```TypeScript
onGetStartIndexByIndex?: OnGetStartIndexByIndexCallback
```

Called to return the StartLineInfo based on target index for the scrollToIndex operation.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## onGetStartIndexByOffset

```TypeScript
onGetStartIndexByOffset?: OnGetStartIndexByOffsetCallback
```

Called to return the StartLineInfo based on total offset for the fast or reverse sliding.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
