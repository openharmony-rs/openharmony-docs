# Polygon properties/events

In addition to the [universal attributes](arkts-arkui-commonmethod-c.md), the following attributes are supported.

**Inheritance/Implementation:** PolygonAttribute extends CommonShapeMethod<PolygonAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## points

```TypeScript
points(value: Array<any>)
```

Sets the vertex coordinates of the polygon. This attribute can be dynamically set using attributeModifier. Invalid values are treated as the default value.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Array&lt;any&gt; | Yes | Vertex coordinates of the polygon. A two-dimensional array is passed, and each subarray indicates the `[x, y]` coordinates of a vertex.<br>Default value: **[]** (empty array) <br>Default unit: vp<br>The **undefined** and **null** values are invalid and treated as the default value. |
