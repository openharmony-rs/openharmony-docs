# Line properties/events

In addition to the [universal attributes](arkts-arkui-commonmethod-c.md), the following attributes are supported.

**Inheritance/Implementation:** LineAttribute extends CommonShapeMethod<LineAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## endPoint

```TypeScript
endPoint(value: Array<any>)
```

Sets the coordinates (relative coordinates) of the end point of the line. This attribute can be dynamically set using attributeModifier. Invalid values are treated as the default value.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Array&lt;any&gt; | Yes | Coordinates (relative coordinates) of the end point of the line, in vp.<br>Default value: **[0, 0]**<br>The **undefined** and **null** values are treated as the default value. |

## startPoint

```TypeScript
startPoint(value: Array<any>)
```

Sets the coordinates (relative coordinates) of the start point of the line. This attribute can be dynamically set using attributeModifier. Invalid values are treated as the default value.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Array&lt;any&gt; | Yes | Coordinates (relative coordinates) of the start point of the line, in vp.<br>Default value: **[0, 0]**<br>The **undefined** and **null** values are treated as the default value. |
