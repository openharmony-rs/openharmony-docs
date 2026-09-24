# GridRowDirection

```TypeScript
declare enum GridRowDirection
```

Grid element arrangement direction.

> **NOTE:** 
> 
> - Grid elements can be arranged only in the **Row** or **RowReverse** direction, but not in the **Column** or
> **ColumnReverse** direction.
> 
> - The location and size of a grid child component can only be calculated through **span** and **offset**. When the
> **span** values of multiple child components exceed the specified number of columns, they automatically wrap to a
> new row.
> 
> - When the **span** of a single element exceeds the maximum number of columns, the **span** is set to the maximum number of columns by default.
> 
> - When the **offset** of a new row plus the **span** of the child component exceeds the total number of columns,the next child component is placed on a new row.
> 
> - Example: Item1: GridCol({ span: 6 }), Item2: GridCol({ span: 8, offset:11 }).
> 
> ![figures/gridRowOffsetToNextLine.png](../../../reference/apis-arkui/arkui-ts/figures/gridRowOffsetToNextLine.png)

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Row

```TypeScript
Row
```

Grid elements are arranged in the row direction. This is suitable for regular LTR (left-to-right) layout scenarios.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## RowReverse

```TypeScript
RowReverse
```

Grid elements are arranged in the reverse row direction. This is suitable for RTL (right-to-left) language layouts or scenarios that require reverse arrangement.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
