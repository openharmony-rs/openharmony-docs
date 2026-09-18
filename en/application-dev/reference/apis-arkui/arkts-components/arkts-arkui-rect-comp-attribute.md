# Rect properties/events

In addition to the [universal attributes](arkts-arkui-commonmethod-c.md), the following attributes are supported.

**Inheritance/Implementation:** RectAttribute extends CommonShapeMethod<RectAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius(value: Length | Array<any>)
```

Sets the radius of the rounded corner. The value must be greater than or equal to 0. This attribute can be dynamically set using attributeModifier. Invalid values are treated as the default value.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) &#124; Array&lt;any&gt; | Yes | Radius of the rounded corner. You can set separate radii for the four rounded corners.<br>Default value: **0**<br>Default unit: vp<br>Invalid values **undefined** and **null** are treated as **[[0, 0], [0, 0], [0, 0], [0, 0]]**.<br>**Since:** 20 |

## radiusHeight

```TypeScript
radiusHeight(value: Length)
```

Sets the height of the rounded corner. The width and height are the same when only the height is set. This attribute can be dynamically set using attributeModifier. Invalid values are treated as the default value.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Height of the rounded corner. The value must be greater than or equal to 0.<br>Default value: **0**<br>Default unit: vp<br>The **undefined** value is invalid and treated as the default value.<br>**Since:** 20 |

## radiusWidth

```TypeScript
radiusWidth(value: Length)
```

Sets the width of the rounded corner. The width and height are the same when only the width is set. This attribute can be dynamically set using attributeModifier. Invalid values are treated as the default value.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Width of the rounded corner. The value must be greater than or equal to 0.<br>Default value: **0**<br>Default unit: vp<br>The **undefined** value is invalid and treated as the default value.<br>**Since:** 20 |
