# RowOptionsV2

```TypeScript
interface RowOptionsV2
```

Sets the spacing between child components of the **Row** component. The spacing type **SpaceType** can be of the number, string, or Resource type.

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: SpaceType
```

Spacing between child components in the horizontal layout.

Value range: greater than or equal to 0.

Since API version 9, this parameter does not take effect when **justifyContent** is set to **FlexAlign.SpaceBetween**, **FlexAlign.SpaceAround**, or **FlexAlign.SpaceEvenly**.

Default value: **0**

Unit: vp

Invalid value: the default value is used.

**NOTE:** 

The value of **space** is a number greater than or equal to 0, a string that can be converted to a non-negative number, or a Resource type data that can be converted to a number. A negative number is treated as an invalid value and the default value 0 is used.

**Type:** [SpaceType](arkts-arkui-column-comp-spacetype-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
