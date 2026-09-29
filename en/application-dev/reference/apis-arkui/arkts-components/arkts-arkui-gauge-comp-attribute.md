# Gauge properties/events

```TypeScript
declare class GaugeAttribute extends CommonMethod<GaugeAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md), the following attributes are supported.

**Inheritance/Implementation:** GaugeAttribute extends CommonMethod<GaugeAttribute>

**Since:** 8

<!--Device-unnamed-declare class GaugeAttribute extends CommonMethod<GaugeAttribute>--><!--Device-unnamed-declare class GaugeAttribute extends CommonMethod<GaugeAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## colors

```TypeScript
colors(colors: ResourceColor | LinearGradient | Array<[ResourceColor | LinearGradient, number]>)
```

Sets the colors of the gauge.

Since API version 11, this API follows the following rules:

If the data type is [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md), the ring is of the monochrome type.

If the data type is LinearGradient, the ring is of the gradient type.

If the parameter type is Array, the ring is a segmented gradient ring. The first parameter indicates the color value or gradient object (LinearGradient). If it is set to a non-color type, the color value is set to "0xFFE84026". The second parameter indicates the proportion of the color. If it is set to a negative number or a non-numeric type, the proportion is set to 0.

A ring of the gradient type contains a maximum of nine color segments. If there are more than nine segments, the excess is not displayed.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-GaugeAttribute-colors(colors: ResourceColor | LinearGradient | Array<[ResourceColor | LinearGradient, number]>): GaugeAttribute--><!--Device-GaugeAttribute-colors(colors: ResourceColor | LinearGradient | Array<[ResourceColor | LinearGradient, number]>): GaugeAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| colors | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) &#124; LinearGradient &#124; Array&lt;[ResourceColor &#124; LinearGradient, number]&gt; | Yes | Colors of the gauge, which support segmented color settings.<br>Default value since API version 9: Color.Black <br>Default value since API version 11: <br>If no color is passed or the array is empty, the ring type and colors cannot be determined, and the ring is a gradient ring with the colors "0xFF64BB5C", "0xFFF7CE00", and "0xFFE84026". <br>If a color is passed but the color value is invalid, the color is "0xFFE84026". <br>If the proportion of a color is 0, the color is not displayed in the ring. If the proportions of all colors are 0, the ring is not displayed. <br>Since API version 10, the Array&lt;ResourceColor, number&gt; type is supported. <br>Since API version 11, the LinearGradient and Array&lt;LinearGradient, number&gt; types are supported.<br>**Since:** 11 |

## contentModifier

```TypeScript
contentModifier(modifier: ContentModifier<GaugeConfiguration>)
```

Creates a content modifier.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GaugeAttribute-contentModifier(modifier: ContentModifier<GaugeConfiguration>): GaugeAttribute--><!--Device-GaugeAttribute-contentModifier(modifier: ContentModifier<GaugeConfiguration>): GaugeAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| modifier | [ContentModifier](arkts-arkui-common-comp-contentmodifier-i.md)&lt;[GaugeConfiguration](arkts-arkui-gauge-comp-gaugeconfiguration-i.md)&gt; | Yes | Method for customizing the content area on the Gauge component.<br>modifier: content modifier. Developers need to customize a class to implement the ContentModifier interface. |

## description

```TypeScript
description(value: CustomBuilder)
```

Sets the description of the gauge.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

<!--Device-GaugeAttribute-description(value: CustomBuilder): GaugeAttribute--><!--Device-GaugeAttribute-description(value: CustomBuilder): GaugeAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) | Yes | Content description.<br>**Note:** <br>The content in @Builder is customized by the developer. Text or images are recommended. <br>If the width and height of the custom part are in percentage, the reference range is a rectangle of 44.4%*25.4% of the ring diameter (28.6%*28.6% for images), 0 vp from the bottom of the ring, centered horizontally. <br>If set to null, no content is displayed. <br>If not set, whether content is displayed depends on whether the maximum and minimum data values are set. <br>If both or only one of the maximum and minimum values are set, the maximum and minimum values are displayed. <br>If neither the maximum nor the minimum value is set, no content is displayed. <br>The maximum and minimum values are displayed at the bottom of the ring and cannot be moved. If the ring opening angle is set improperly, the text may be obscured by the ring. |

## endAngle

```TypeScript
endAngle(angle: number)
```

Sets the end angle of the gauge. Ensure an appropriate difference between the start angle and end angle. If this difference is too small, the drawn chart may be abnormal. You are advised to use a monochrome ring to set the **value** attribute of the **Gauge**. You can also use **setTimeout** to delay value loading.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-GaugeAttribute-endAngle(angle: number): GaugeAttribute--><!--Device-GaugeAttribute-endAngle(angle: number): GaugeAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| angle | number | Yes | End angle position. 0 degrees is at the 12 o'clock position, with positive angles in the clockwise direction and negative angles in the counterclockwise direction. An angle exceeding 360 degrees is equivalent to the remainder after modulo 360.<br>Default value: 360 <br>Unit: deg (degree) <br>Drawing from the start position to the end position is only in the clockwise direction. <br>If the difference between the start angle and end angle is too small, an abnormal image may be drawn. Use reasonable start and end angles. |

## indicator

```TypeScript
indicator(value: GaugeIndicatorOptions)
```

Sets the indicator style of the gauge.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

<!--Device-GaugeAttribute-indicator(value: GaugeIndicatorOptions): GaugeAttribute--><!--Device-GaugeAttribute-indicator(value: GaugeIndicatorOptions): GaugeAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [GaugeIndicatorOptions](arkts-arkui-gauge-comp-gaugeindicatoroptions-i.md) | Yes | Pointer style.<br>**NOTE:** <br>If null is set, the pointer is not displayed. |

## privacySensitive

```TypeScript
privacySensitive(isPrivacySensitiveMode: Optional<boolean>)
```

Sets whether to enable privacy mode.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 20.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-GaugeAttribute-privacySensitive(isPrivacySensitiveMode: Optional<boolean>): GaugeAttribute--><!--Device-GaugeAttribute-privacySensitive(isPrivacySensitiveMode: Optional<boolean>): GaugeAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isPrivacySensitiveMode | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Sets privacy sensitivity. In privacy mode, the Gauge pointer points to the 0 position, the maximum and minimum value texts are masked, and the range is displayed in gray or the background color. The value **true** enables privacy sensitivity, and **false** disables it. <br>**Note:** <br>If this parameter is set to null, the content is not sensitive.<!--Del--> <br>To use Gauge in a card, set the [privacy mask](arkts-arkui-common-comp.md) attribute through the [FormComponent](arkts-arkui-formcomponent-comp-sys.md) component. The privacy mask takes effect only when the card is displayed.<!--DelEnd--> |

## startAngle

```TypeScript
startAngle(angle: number)
```

Sets the start angle position. If the difference between the start angle and the end angle is too small, an abnormal image will be drawn. Use reasonable start and end angles. It is recommended to use a single-color ring to adjust the data value by changing the `value` parameter of Gauge. You can use the timer `setTimeout` to delay the loading of the value.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-GaugeAttribute-startAngle(angle: number): GaugeAttribute--><!--Device-GaugeAttribute-startAngle(angle: number): GaugeAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| angle | number | Yes | Start angle position. The 0 o'clock position is 0 degrees. Clockwise is a positive angle, and counterclockwise is a negative angle. An angle greater than 360 degrees is equivalent to the remainder after dividing by 360 degrees.<br>Default value: 0 <br>Unit: deg <br>The drawing from the start position to the end position is clockwise only. <br>If the difference between the start angle and the end angle is too small, an abnormal image may be drawn. Use reasonable start and end angles. |

## strokeWidth

```TypeScript
strokeWidth(length: Length)
```

Sets the stroke width of the gauge.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-GaugeAttribute-strokeWidth(length: Length): GaugeAttribute--><!--Device-GaugeAttribute-strokeWidth(length: Length): GaugeAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| length | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Thickness of the ring gauge.<br>Default value: 4 <br>Unit: vp <br>**Note:** <br>If the value is less than or equal to 0, the default value is used. <br>The maximum thickness is the radius of the ring. If the value exceeds the maximum, the maximum value is used. <br>Percentage is not supported. |

## trackShadow

```TypeScript
trackShadow(value: GaugeShadowOptions)
```

Sets the shadow style of the gauge.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

<!--Device-GaugeAttribute-trackShadow(value: GaugeShadowOptions): GaugeAttribute--><!--Device-GaugeAttribute-trackShadow(value: GaugeShadowOptions): GaugeAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [GaugeShadowOptions](arkts-arkui-gauge-comp-gaugeshadowoptions-i.md) | Yes | Adds a shadow effect. You can specify the blur radius and the offsets along the X-axis and Y-axis.<br>**Note:** <br>The shadow color is the same as the ring color. <br>Set this parameter to null to disable the shadow. |

## value

```TypeScript
value(value: number)
```

Sets the value of the gauge.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-GaugeAttribute-value(value: number): GaugeAttribute--><!--Device-GaugeAttribute-value(value: number): GaugeAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Data value of the gauge, which can be used to dynamically modify the data value of the gauge.<br>**Note:** <br>If value is not within the range of min and max, min is used as the actual value. <br>Default value: 0 |
