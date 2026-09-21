# Circle properties/events

```TypeScript
declare class CircleAttribute extends CommonShapeMethod<CircleAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp-commonmethod-c.md) and [universal drawing attributes](arkts-arkui-common-comp-commonmethod-c.md), the following attributes are supported:

**Inheritance/Implementation:** CircleAttribute extends CommonShapeMethod<CircleAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fill

```TypeScript
fill(value: ResourceColor | ColorMetrics)
```

Sets the color of the fill area. [ColorMetrics](../arkts-apis/arkts-arkui-graphics-colormetrics-c.md) can be used to describe the color for HDR brightening. This attribute can be dynamically set using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier). If this attribute is not set, the default fill color is Color.Black. Abnormal values **undefined**, **null**, **NaN**, and **Infinity** are treated as the default value. When this attribute is set together with the universal attribute **foregroundColor**, the one set later takes effect.

**Since:** 26.0.0

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) &#124; ColorMetrics | Yes | Color of the area to fill.<br>Default value: Color.Black <br>Abnormal values **undefined**, **null**, **NaN**, and **Infinity** are handled as the default value. |

## stroke

```TypeScript
stroke(value: ResourceColor | ColorMetrics)
```

Sets the stroke color. [ColorMetrics](../arkts-apis/arkts-arkui-graphics-colormetrics-c.md) can be used to describe the color for HDR brightening. This attribute can be dynamically set using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier). If this attribute is not set, the default stroke color is Color.Transparent, that is, no stroke is drawn. Abnormal values undefined and null are treated as the default value, and NaN and Infinity are treated as Color.Black.

**Since:** 26.0.0

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) &#124; ColorMetrics | Yes | Stroke color.<br>Default value: Color.Transparent <br>The abnormal values **undefined** and **null** are handled as the default value, and **NaN** and **Infinity** are handled as Color.Black. |
