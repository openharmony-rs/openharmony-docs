# GridRowDirection

Grid element arrangement direction.

> **NOTE:** 
> 
> - Grid elements can be arranged only in the **Row** or **RowReverse** direction, but not in the **Column** or
> **ColumnReverse** direction.
> 
> - The location and size of a grid child component can be calculated only based on **span** and **offset**. If the
> **span** values of child components add up to a number greater than the allowed number of columns, the grid will
> automatically wrap lines.
> 
> - If the **span** value of a single child component exceeds the maximum number of columns, the maximum number of columns is used.
> 
> - If a child component takes up more than the total number of columns according to its **offset** and **span**settings, it will be placed in a new row.
> 
> - Example: Item1: GridCol({ span: 6 }), Item2: GridCol({ span: 8, offset:11 })
> 
> 
> 
> ![figures/gridRowOffsetToNextLine.png](../../../reference/apis-arkui/arkui-ts/figures/gridRowOffsetToNextLine.png)

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Row

```TypeScript
Row
```

Grid elements are arranged in the row direction.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## RowReverse

```TypeScript
RowReverse
```

Grid elements are arranged in the reverse row direction.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
