# ColumnOptions

Sets the spacing between child components of the **Column** component.

> **NOTE:** 
> 
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18.
> While historical version information is preserved for anonymous objects, there may be cases where the outer element
> 's

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: string | number
```

Vertical spacing between two adjacent child components. This parameter has no effect if the value specified is a negative number, or if [justifyContent](@ColumnAttribute#justifyContent) is set to **FlexAlign.SpaceBetween**, **FlexAlign.SpaceAround**, or **FlexAlign.SpaceEvenly** Unit: vp, Invalid values are treated as the default value. **NOTE:** The value of **space** can be a number greater than or equal to 0 or a string that can be converted to a number. Default value: **0**.

**Type:** string &#124; number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
