# ColumnOptionsV2

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
space?: SpaceType
```

Vertical spacing between two adjacent child components. This parameter has no effect if the value specified is a negative number, or if **justifyContent** is set to **FlexAlign.SpaceBetween**, **FlexAlign.SpaceAround**, or **FlexAlign.SpaceEvenly**. Unit: vp, Invalid values are treated as the default value. **NOTE:** The value of **space** can be a number greater than or equal to 0, a string that can be converted to a number, or a Resource type that can be converted to a number. Default value: **0**.

**Type:** [SpaceType](arkts-arkui-spacetype-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
