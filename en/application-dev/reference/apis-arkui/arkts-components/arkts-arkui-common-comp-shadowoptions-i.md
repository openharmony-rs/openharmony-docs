# ShadowOptions

```TypeScript
declare interface ShadowOptions
```

Provides the shadow attributes, including the blur radius, color, and offset along the x-axis and y-axis.

**Since:** 7

<!--Device-unnamed-declare interface ShadowOptions--><!--Device-unnamed-declare interface ShadowOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: Color | string | Resource | ColoringStrategy
```

Shadow color.

The default value is black.

**NOTE:** 

Starting from API version 11, this interface supports using ColoringStrategy to implement smart color picking. The smart color picking feature is not supported in ArkTS cards or [textShadow](arkts-arkui-text-comp-attribute.md#textshadow).

Currently, only average color picking and primary color picking are supported. The smart color picking area is the shadow drawing area.

The 'average' string can be used to trigger the smart average color picking mode, and the 'primary' string can be used to trigger the smart primary color mode.

**Type:** [Color](../arkts-apis/arkts-arkui-color-e.md) &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) &#124; [ColoringStrategy](../arkts-apis/arkts-arkui-coloringstrategy-e.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ShadowOptions-color?: Color | string | Resource | ColoringStrategy--><!--Device-ShadowOptions-color?: Color | string | Resource | ColoringStrategy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fill

```TypeScript
fill?: boolean
```

Whether the shadow is filled internally. The value true indicates that the shadow is filled internally, and false indicates that the shadow is filled externally.

Default value: false.

**NOTE:** 

This field does not take effect in [textShadow](arkts-arkui-text-comp-attribute.md#textshadow).

**Type:** boolean

**Default:** false

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ShadowOptions-fill?: boolean--><!--Device-ShadowOptions-fill?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offsetX

```TypeScript
offsetX?: number | Resource
```

X-axis offset of the shadow.

Default value: 0

Unit: px

**NOTE:** 

To use a value in vp, call [vp2px](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#vp2px) to convert it.

If offsetX is of the Resource type, the value passed in must be of the number type.

**Type:** number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ShadowOptions-offsetX?: number | Resource--><!--Device-ShadowOptions-offsetX?: number | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offsetY

```TypeScript
offsetY?: number | Resource
```

Y-axis offset of the shadow.

Default value: 0

Unit: px

**NOTE:** 

To use a value in vp, call [vp2px](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#vp2px) to convert it.

If offsetY is of the Resource type, the value passed in must be of the number type.

**Type:** number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ShadowOptions-offsetY?: number | Resource--><!--Device-ShadowOptions-offsetY?: number | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius: number | Resource
```

Shadow blur radius.

Value range: [0, +∞). Starting from API version 26.0.0, the value range changes to (-∞, +∞).

Unit: px

**NOTE:** 

Before API version 26.0.0, when a value less than 0 is set, it is processed as 0, in which case no shadow is drawn. Starting from API version 26.0.0, the set value is the final value. When the value is 0, the shadow is still drawn; when a negative value is set, no shadow is drawn.

To use a value in vp, call [vp2px](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#vp2px) to convert it.

If radius is of the Resource type, the value passed in must be of the number type.

**Type:** number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ShadowOptions-radius: number | Resource--><!--Device-ShadowOptions-radius: number | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type?: ShadowType
```

Shadow type.

Default value: COLOR

**Type:** [ShadowType](arkts-arkui-common-comp-shadowtype-e.md)

**Default:** ShadowType.COLOR

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ShadowOptions-type?: ShadowType--><!--Device-ShadowOptions-type?: ShadowType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
