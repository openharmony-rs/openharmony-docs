# ColumnOptions

```TypeScript
interface ColumnOptions
```

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

Vertical spacing between child components in the column layout.

If **space** is a negative number or [justifyContent](arkts-arkui-column-comp-attribute.md#justifycontent) is set to **FlexAlign.SpaceBetween**, **FlexAlign.SpaceAround**, or **FlexAlign.SpaceEvenly**, **space** does not take effect.

Value range: [0, +∞)

Default value: **0**

Invalid value: handled as the default value.

Unit: vp

**NOTE:** 

The value of **space** is a number greater than or equal to 0, or a string that can be converted to a non-negative number.

**Type:** string &#124; number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
