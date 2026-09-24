# ColumnOptionsV2

```TypeScript
interface ColumnOptionsV2
```

Sets the spacing between child components of the **Column** component. The spacing type **SpaceType** can be number, string, or Resource.

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: SpaceType
```

Vertical spacing between elements in the column layout.

If **space** is a negative number or [justifyContent](arkts-arkui-column-comp-attribute.md#justifycontent) is set to **FlexAlign.SpaceBetween**, **FlexAlign.SpaceAround**, or **FlexAlign.SpaceEvenly**, **space** does not take effect.

Value range: [0, +∞)

Default value: **0**

Unit: vp

Invalid value: The default value is used.

**NOTE:** 

The value of **space** is a number greater than or equal to 0, a string that can be converted to a non-negative number, or a Resource type that can be converted to a number.

**Type:** [SpaceType](arkts-arkui-column-comp-spacetype-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
