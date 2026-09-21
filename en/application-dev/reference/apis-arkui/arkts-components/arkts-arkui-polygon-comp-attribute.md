# Polygon properties/events

```TypeScript
declare class PolygonAttribute extends CommonShapeMethod<PolygonAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp-commonmethod-c.md) and [common attributes of drawing components](arkts-arkui-common-comp-commonmethod-c.md), the following attributes are supported:

**Inheritance/Implementation:** PolygonAttribute extends CommonShapeMethod<PolygonAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## points

```TypeScript
points(value: Array<any>)
```

Sets the vertex coordinates of the polygon. This attribute can be dynamically set using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier). Invalid values are treated as the default value.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Array&lt;any&gt; | Yes | List of vertex coordinates of the polygon. A two-dimensional array is passed in, where each sub-array represents the [x, y] coordinates of a vertex.<br>Default value: [] (empty array) <br>Default unit: vp <br>The abnormal values **undefined** and **null** are handled as the default value. |
