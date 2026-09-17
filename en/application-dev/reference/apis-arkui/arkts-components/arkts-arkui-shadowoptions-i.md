# ShadowOptions

Provides the shadow attributes, including the blur radius, color, and offset along the x-axis and y-axis.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: Color | string | Resource | ColoringStrategy
```

Color of the shadow.

The default color is black.

**NOTE:** 

Since API version 11, this API supports **ColoringStrategy**, which cannot be used with ArkTS widgets or the textShadow attribute.

With **ColoringStrategy**, the average color or primary color can be obtained, and the obtained color is applied to the shadow drawing area.

The **'average'** string can be used to trigger the mode for obtaining the average color, and the **'primary'** string for obtaining the primary color.

**Type:** [Color](../arkts-apis/arkts-arkui-color-e.md) &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) &#124; [ColoringStrategy](../arkts-apis/arkts-arkui-coloringstrategy-e.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fill

```TypeScript
fill?: boolean
```

Whether to fill the inside of the component with shadow. **true**: Fill the inside of the component with shadow.

**false**: Do not fill the inside of the component with shadow.

Default value: **false**.

**NOTE:** 

This attribute does not take effect in textShadow.

**Type:** boolean

**Default:** false

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offsetX

```TypeScript
offsetX?: number | Resource
```

Offset of the shadow along the x-axis.

Default value: **0**

Unit: px

**NOTE:** 

To use a value in the unit of vp, you can use [vp2px](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#vp2px) to convert the value.

If **offsetX** is of the Resource type, its value must be of the number type.

**Type:** number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offsetY

```TypeScript
offsetY?: number | Resource
```

Offset of the shadow along the y-axis.

Default value: **0**

Unit: px

**NOTE:** 

To use a value in the unit of vp, you can use [vp2px](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#vp2px) to convert the value.

If **offsetY** is of the Resource type, its value must be of the number type.

**Type:** number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius: number | Resource
```

Blur radius of the shadow.

Value range: [0, +∞)

Unit: px

**NOTE:** 

A value less than 0 evaluates to the value **0**.

To use a value in the unit of vp, you can use [vp2px](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#vp2px) to convert the value.

If **radius** is of the Resource type, its value must be of the number type.

**Type:** number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type?: ShadowType
```

Shadow type.

Default value: **COLOR**

**Type:** [ShadowType](arkts-arkui-shadowtype-e.md)

**Default:** ShadowType.COLOR

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
