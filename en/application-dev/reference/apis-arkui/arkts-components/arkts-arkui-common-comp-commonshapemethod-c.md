# CommonShapeMethod

```TypeScript
declare class CommonShapeMethod<T> extends CommonMethod<T>
```

CommonShapeMethod

**Inheritance/Implementation:** CommonShapeMethod extends CommonMethod<T>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## antiAlias

```TypeScript
antiAlias(value: boolean): T
```

Sets whether to enable anti-aliasing. This attribute supports the attributeModifier attribute method for dynamic setting.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to enable anti-aliasing.<br> true: enables anti-aliasing; false: disables anti-aliasing. <br> Default value: true <br> The abnormal values undefined and null are processed as false. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## fill

```TypeScript
fill(value: ResourceColor): T
```

Sets the fill color. This attribute supports the attributeModifier attribute method for dynamic setting. Invalid values are treated as the default value. If this attribute is set together with the universal attribute foregroundColor, the one set later takes effect.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Fill color.<br> Default value: Color.Black. <br> Abnormal values undefined, null, NaN, and Infinity are treated as the default value. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## fillOpacity

```TypeScript
fillOpacity(value: number | string | Resource): T
```

Sets the opacity of the fill area. This attribute supports dynamic setting through attributeModifier.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Opacity of the fill area.<br> **NOTE:**   The value range of the number format is [0.0, 1.0]. If the given value is less than 0.0, the value is 0.0; if the given value is greater than 1.0, the value is 1.0. Other abnormal values are processed as 1.0. The string format supports the string form of the number format value, and the value range is the same as that of the number format.  The Resource format supports strings in system resources or app resources, and the value range is the same as that of the number format.  The abnormal value NaN is processed as 0.0, and undefined, null, and Infinity are processed as 1.0. Default value: 1.0 |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## stroke

```TypeScript
stroke(value: ResourceColor): T
```

Sets the stroke color. This attribute supports the attributeModifier attribute method for dynamic setting. If it is not set, the default stroke opacity is 0, that is, no stroke is displayed.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Stroke color.<br> Default value: Color.Transparent. <br> Abnormal values undefined and null are processed as the default value, and NaN and Infinity are processed as Color.Black. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## strokeDashArray

```TypeScript
strokeDashArray(value: Array<any>): T
```

Sets the dashed line segment length and gap length of the stroke. This attribute supports the attributeModifier dynamic setting attribute method. The value range is ≥ 0. Abnormal values are processed as the default value.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Array&lt;any&gt; | Yes | Array that defines the dashed pattern of the Rect stroke. The array elements alternately represent the segment length and gap length.<br> Default value: [] (empty array) <br> Default unit: vp <br> The abnormal values undefined and null are processed as the default value. <br> **NOTE:** Empty array: solid line <br> Even-numbered multi-element array: the array elements are cycled in order. For example, [a, b, c, d] represents segment length a -&gt; gap length b -&gt; segment length c -&gt; gap length d -&gt; segment length a -&gt; ... Odd-numbered multi-element array: the array elements are repeated once and then cycled following the rule of an even-numbered multi-element array. For example, [a, b, c] is equivalent to [a, b, c, a, b, c], which represents segment length a -&gt; gap length b -&gt; segment length c -&gt; gap length a -&gt; segment length b -&gt; gap length c -&gt; segment length a -&gt; ... |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## strokeDashOffset

```TypeScript
strokeDashOffset(value: number | string): T
```

Sets the offset of the stroke drawing start point. This attribute supports the attributeModifier attribute method for dynamic setting. Abnormal values are processed as the default value.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string | Yes | Offset of the stroke drawing start point.<br> Default value: 0 <br> Default unit: vp <br> The abnormal values undefined and null are processed as the default value. NaN and Infinity cause strokeDashArray to become invalid. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## strokeLineCap

```TypeScript
strokeLineCap(value: LineCapStyle): T
```

Sets the line cap style of the stroke. This attribute supports the attributeModifier attribute method for dynamic setting.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [LineCapStyle](../arkts-apis/arkts-arkui-linecapstyle-e.md) | Yes | Line cap style of the stroke.<br> Default value: LineCapStyle.Butt <br> The abnormal values undefined, null, NaN, and Infinity are processed as the default value. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## strokeLineJoin

```TypeScript
strokeLineJoin(value: LineJoinStyle): T
```

Sets the style for drawing the corners of the stroke. This attribute method supports the attributeModifier for dynamic setting.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [LineJoinStyle](../arkts-apis/arkts-arkui-linejoinstyle-e.md) | Yes | Style for drawing the corners of the stroke.<br> Default value: LineJoinStyle.Miter <br> Abnormal values undefined, null, NaN, and Infinity are processed as the default value. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## strokeMiterLimit

```TypeScript
strokeMiterLimit(value: number | string): T
```

Sets the limit value of the ratio of the miter length to the stroke width. This attribute supports the attributeModifier attribute method for dynamic setting. The miter length is the distance from the intersection of the outer edges to the intersection of the inner edges, and the stroke width is the value of the strokeWidth attribute. This attribute takes effect only when the strokeLineJoin attribute is set to LineJoinStyle.Miter. The valid value range of this attribute must be greater than or equal to 1.0. When the value is in the range [0, 1), it is processed as 1.0, and other abnormal values are processed as the default value.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string | Yes | Limit value of the ratio of the miter length to the stroke width.<br> Default value: 4 <br> The abnormal values undefined, null, and NaN are processed as the default value, and Infinity causes stroke to become invalid. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## strokeOpacity

```TypeScript
strokeOpacity(value: number | string | Resource): T
```

Sets the stroke opacity. This attribute supports the attributeModifier attribute method for dynamic setting. The value range of this attribute is [0.0, 1.0]. If the given value is less than 0.0, the value is 0.0; if the given value is greater than 1.0, the value is 1.0.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Stroke opacity.<br> Default value: the opacity set by stroke. <br> The abnormal value NaN is processed as 0.0, and undefined, null, and Infinity are processed as 1.0. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## strokeWidth

```TypeScript
strokeWidth(value: Length): T
```

Sets the stroke width. This attribute supports the attributeModifier dynamic setting attribute method. If this attribute is of the string type, percentages are not supported, and a percentage is processed as 1px.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Stroke width.<br> Value range: ≥0. <br> Default value: 1 <br> Default unit: vp <br> The abnormal values undefined, null, and NaN are processed as the default value, and Infinity is processed as 0. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |
