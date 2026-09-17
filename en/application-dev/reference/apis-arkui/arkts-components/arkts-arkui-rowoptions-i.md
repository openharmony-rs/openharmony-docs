# RowOptions

Sets the spacing between child components of the **Row** component.

> **NOTE:** 
> 
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18.
> While starting version information is preserved for historical anonymous objects, there may be cases where the
> outer element's

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: string | number
```

Spacing between child components. Since API version 9, this parameter does not take effect when it is set to a negative number or when **justifyContent** is set to **FlexAlign.SpaceBetween**, **FlexAlign.SpaceAround** or **FlexAlign.SpaceEvenly**. Unit: vp. If an invalid value is set, the default value is used instead.  
> **NOTE:** 
> 
> The value of **space** can be a number greater than or equal to 0 or a string that can be converted to a number.
> Default value: **0**.

**Type:** string &#124; number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
