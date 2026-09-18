# Circle properties/events

In addition to the [universal attributes](arkts-arkui-commonmethod-c.md), the following attributes are supported.

**Inheritance/Implementation:** CircleAttribute extends CommonShapeMethod<CircleAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fill

```TypeScript
fill(value: ResourceColor | ColorMetrics)
```

Sets the color of the fill area. An invalid value is handled as the default value. If this attribute and the universal attribute foregroundColor are both set, whichever is set later takes effect.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) &#124; ColorMetrics | Yes | Color of the fill area<br>Default value : Color.Black. |

## stroke

```TypeScript
stroke(value: ResourceColor | ColorMetrics)
```

Sets the stroke color. This attribute can be dynamically set using attributeModifier. If this attribute is not set, the default stroke opacity is 0, meaning no stroke is displayed.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) &#124; ColorMetrics | Yes | Stroke color.<br>Default value: Color.Transparent.<br>Invalid values **undefined** and **null** values are treated as the default value, and invalid values **NaN** and **Infinity** are treated as Color.Black. |
