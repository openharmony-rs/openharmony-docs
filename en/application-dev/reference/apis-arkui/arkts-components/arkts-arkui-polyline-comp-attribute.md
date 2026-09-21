# Polyline properties/events

```TypeScript
declare class PolylineAttribute extends CommonShapeMethod<PolylineAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp-commonmethod-c.md) and [universal drawing attributes](arkts-arkui-common-comp-commonmethod-c.md), the following attributes are supported:

**Inheritance/Implementation:** PolylineAttribute extends CommonShapeMethod<PolylineAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## points

```TypeScript
points(value: Array<any>)
```

Sets the list of coordinate points that the polyline passes through. This attribute supports [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) for dynamic setting of the attribute.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Array&lt;any&gt; | Yes | List of coordinate points that the polyline passes through. Pass in a two-dimensional array, where each sub-array represents the [x, y] coordinates of a vertex.<br>Default value: [] (empty array) <br>Default unit: vp <br>Abnormal values undefined and null are processed as the default value. |
