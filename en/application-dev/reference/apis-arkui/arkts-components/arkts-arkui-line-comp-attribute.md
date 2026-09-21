# Line properties/events

```TypeScript
declare class LineAttribute extends CommonShapeMethod<LineAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp-commonmethod-c.md) and [common attributes for drawing components](arkts-arkui-common-comp-commonmethod-c.md), the following attributes are supported:

**Inheritance/Implementation:** LineAttribute extends CommonShapeMethod<LineAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## endPoint

```TypeScript
endPoint(value: Array<any>)
```

Sets the coordinates of the line end point (relative to the origin at the upper left corner of the **Line** component drawing area). This attribute supports [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) for dynamic setting of the attribute method. Abnormal values are processed as the default value.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Array&lt;any&gt; | Yes | End point coordinate of the line (relative to the upper left corner of the **Line** component drawing area), in vp. The array format is [x coordinate, y coordinate]. The array length must be 2, and the elements must be of the Length type.<br>Default value: **[0, 0]** <br>Abnormal values **undefined** and **null** are processed as the default value. |

## startPoint

```TypeScript
startPoint(value: Array<any>)
```

Sets the coordinates of the line start point (relative to the origin at the upper left corner of the **Line** component drawing area). This attribute supports [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) for dynamic setting of the attribute method. Abnormal values are processed as the default value.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Array&lt;any&gt; | Yes | Coordinates of the start point of the line (relative to the upper left corner of the Line component's drawing area), in vp. The array format is [x-coordinate, y-coordinate]. The array length must be 2, and the elements must be of the Length type.<br>Default value: **[0, 0]** <br>The abnormal values **undefined** and **null** are processed as the default value. |
