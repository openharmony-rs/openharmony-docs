# Shape properties/events

```TypeScript
declare class ShapeAttribute extends CommonMethod<ShapeAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp-commonmethod-c.md) and [universal drawing attributes](arkts-arkui-common-comp-commonmethod-c.md), the following attributes are supported:

**Inheritance/Implementation:** ShapeAttribute extends CommonMethod<ShapeAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## antiAlias

```TypeScript
antiAlias(value: boolean)
```

Sets whether to enable anti-aliasing. This attribute can be dynamically set using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to enable anti-aliasing.<br>**true**: enable anti-aliasing; **false**: disable anti-aliasing.<br>Default value: **true**<br>Invalid values **undefined** and **null** are treated as **false**. |

## fill

```TypeScript
fill(value: ResourceColor)
```

Sets the color of the fill area. This attribute can be dynamically set using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier). Invalid values are treated as the default value. If this attribute and the universal attribute **foregroundColor** are both set, whichever is set later takes effect.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Color of the fill area.<br>Default value: Color.Black<br>The **undefined**, **null**, **NaN**, and **Infinity** values are invalid and treated as the default value. |

## fillOpacity

```TypeScript
fillOpacity(value: number | string | Resource)
```

Sets the opacity of the fill area. This attribute can be dynamically set using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Opacity of the fill area.<br>**NOTE:** <br>For the number type, the value range is [0.0, 1.0]. A value less than 0.0 is treated as **0.0**. A value greater than 1.0 is treated as **1.0**. Any other invalid value is treated as **1.0**.<br>For the string type, the value is a character string of the number type. The value range is the same as that of the number type.<br>For the Resource type, the value is a character string from the system resource or application resource. The value range is the same as that of the number type.<br>Default value: **1.0** |

## mesh

```TypeScript
mesh(value: Array<any>, column: number, row: number)
```

Sets the mesh effect. Divides the image into a grid of (row + 1) × (column + 1), with the coordinates of each grid intersection stored in an array (every two elements represent the x and y coordinates of an intersection). The coordinates in the **value** array are used to reposition the grid vertices, implementing local distortion of the image. This attribute can be dynamically set using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier). It is applicable to scenarios that require image deformation effects, such as image distortion and wave effects.

The coordinate array is stored in row-major order. After the original image is evenly divided, each grid area is transformed based on the new coordinates of its vertices, ultimately producing a distortion effect.

> **NOTE:** 
> 
> **mesh** takes effect only when a **pixelMap** object is passed to the shape, and the effect applies to the
> passed **pixelMap** object. It produces the same result as
> [drawPixelMapMesh&lt;sup&gt;12+&lt;/sup&gt;](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-drawing-canvas-c.md#drawpixelmapmesh) in the
> [drawing module](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-graphics-drawing.md). It is recommended that you use
> **drawPixelMapMesh**.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Array&lt;any&gt; | Yes | Array of length (row + 1) × (column + 1) × 2, which records the position of each vertex of the distorted bitmap. The coordinate system is based on the display area of the **Shape** component, with the origin (0,0) at the upper left corner, the x-axis extending to the right, and the y-axis extending downward.<br>Default unit: vp <br>When the abnormal values **undefined** and **null** are set, the parameter is processed as an empty array. |
| column | number | Yes | Number of columns in the mesh matrix.<br>The value range is ≥ 0. <br>Default value: **0** <br>When the abnormal values **undefined**, **null**, **NaN**, and **Infinity** are set, the column and row parameters are processed as the default value **0**, and the value parameter is processed as an empty array. |
| row | number | Yes | Number of rows in the mesh matrix.<br>The value range is ≥ 0. <br>Default value: **0** <br>When the abnormal values **undefined**, **null**, **NaN**, and **Infinity** are set, the column and row parameters are processed as the default value **0**, and the **value** parameter is processed as an empty array. |

## stroke

```TypeScript
stroke(value: ResourceColor)
```

Sets the stroke color. This attribute can be dynamically set using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier). If this attribute is not set, the default stroke opacity is **0**, meaning no stroke is displayed.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Stroke color.<br>Default value: Color.Transparent<br>Invalid values **undefined** and **null** values are treated as the default value, and invalid values **NaN** and **Infinity** are treated as Color.Black. |

## strokeDashArray

```TypeScript
strokeDashArray(value: Array<any>)
```

Sets the stroke dashes. This attribute can be dynamically set using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier). The value must be greater than or equal to 0. Invalid values are treated as the default value.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Array&lt;any&gt; | Yes | Array defining the dash pattern for the shape outline. Elements alternate between dash length and gap length.<br>Default value: **[]** (empty array)<br>Default unit: vp<br>The **undefined** and **null** values are invalid and treated as the default value.<br>**NOTE:** <br>Empty array: solid line<br>Even- numbered array: Elements cycle sequentially, for example, [a, b, c, d] represents: dash a -&gt; gap b -&gt; dash c -&gt; gap d -&gt; dash a -&gt; ...<br>Odd-numbered array: Elements are duplicated to create an even-numbered array, for example, [a, b, c] becomes [a, b, c, a, b, c], representing: dash a -&gt; gap b -&gt; dash c -&gt; gap a -&gt; dash b -&gt; gap c -&gt; dash a -&gt; ... |

## strokeDashOffset

```TypeScript
strokeDashOffset(value: Length)
```

Sets the offset of the start point for drawing the stroke. This attribute can be dynamically set using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier). Invalid values are treated as the default value.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Offset of the start point for drawing the stroke.<br>Default value: **0**<br>Default unit: vp<br>Invalid values **undefined** and **null** are treated as the default value. If set to **NaN** or **Infinity**, **strokeDashArray** has no effect.<br>**Since:** 20 |

## strokeLineCap

```TypeScript
strokeLineCap(value: LineCapStyle)
```

Sets the cap style of the stroke. This attribute can be dynamically set using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [LineCapStyle](../arkts-apis/arkts-arkui-linecapstyle-e.md) | Yes | Cap style of the stroke.<br>Default value: **LineCapStyle.Butt**<br>The **undefined**, **null**, **NaN**, and **Infinity** values are invalid and treated as the default value. |

## strokeLineJoin

```TypeScript
strokeLineJoin(value: LineJoinStyle)
```

Sets the join style of the stroke. This attribute can be dynamically set using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [LineJoinStyle](../arkts-apis/arkts-arkui-linejoinstyle-e.md) | Yes | Join style of the stroke.<br>Default value: **LineJoinStyle.Miter**<br>The **undefined**, **null**, **NaN**, and **Infinity** values are invalid and treated as the default value. |

## strokeMiterLimit

```TypeScript
strokeMiterLimit(value: Length)
```

Sets the limit on the ratio of the miter length to the value of stroke width used to draw a miter join. This attribute can be dynamically set using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier). The miter length indicates the distance from the outer tip to the inner corner of the miter. The border width is the value of **strokeWidth**. This attribute works only when **strokeLineJoin** is set to **LineJoinStyle.Miter**.

The value must be greater than or equal to 1.0. If the value is in the [0, 1) range, the value **1.0** will be used. In other cases, the default value will be used.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Limit on the ratio of the miter length to the value of **strokeWidth** used to draw a miter join.<br>Default value: **4**<br>The **undefined**, **null**, and **NaN** values are invalid and treated as the default value. If set to **Infinity**, **stroke** has no effect.<br>**Since:** 20 |

## strokeOpacity

```TypeScript
strokeOpacity(value: number | string | Resource)
```

Sets the stroke opacity. This attribute can be dynamically set using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier). The value range is [0.0, 1.0]. If the set value is less than 0.0, **0.0** will be used. If the set value is greater than 1.0, **1.0** will be used.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Stroke opacity.<br>Default value: opacity set by the [stroke](../../../reference/apis-arkui/arkui-ts/ts-drawing-components-shape.md#stroke) API<br>Invalid value **NaN** is treated as **0.0**, while invalid values **undefined**, **null**, and **Infinity** are treated as **1.0**. |

## strokeWidth

```TypeScript
strokeWidth(value: Length)
```

Sets the stroke width. This attribute can be dynamically set using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier). If this attribute is of the string type, percentage values are not supported and will be treated as 1 px.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Stroke width. The value must be greater than or equal to 0.<br>Default value: **1**<br> Default unit: vp<br>Invalid values **undefined**, **null**, and **NaN** are treated as the default value, and invalid value **Infinity** is treated as **0**.<br>**Since:** 20 |

## viewPort

```TypeScript
viewPort(value: ViewportRect)
```

Sets the viewport of the shape.

The viewport defines the coordinate system and display area of the drawing content. The start point coordinates (x, y) and the width and height (width, height) of the viewport determine the display position and range of the drawing content in the component. When the viewport range differs from the component size, the drawing content is automatically scaled to fit. The viewport is commonly used to adjust the display scale and position of the drawing content.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ViewportRect](arkts-arkui-shape-comp-viewportrect-i.md) | Yes | Viewport drawing attribute.<br>Default value: **{x: 0, y: 0, width: 0, height: 0}** <br>The abnormal values **undefined** and **null** are processed as the default value.<br>**Since:** 18 |
