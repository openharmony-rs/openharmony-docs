# Divider properties/events

```TypeScript
declare class DividerAttribute extends CommonMethod<DividerAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp-commonmethod-c.md), the following attributes are supported.

The [universal events](arkts-arkui-common-comp-commonmethod-c.md) are supported.

**Inheritance/Implementation:** DividerAttribute extends CommonMethod<DividerAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color(value: ResourceColor)
```

Sets the color of the divider. This attribute can be dynamically set using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Color of the divider.<br>Default value: **'#33182431'** <br>Invalid values are treated as the default value. <br>You can set a common divider color using WithTheme. |

## lineCap

```TypeScript
lineCap(value: LineCapStyle)
```

Sets the line cap style of the divider. This attribute can be dynamically set using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [LineCapStyle](../arkts-apis/arkts-arkui-linecapstyle-e.md) | Yes | Line cap style of the divider.<br>Default value: **LineCapStyle.Butt** <br>Invalid values are treated as the default value. |

## strokeWidth

```TypeScript
strokeWidth(value: number | string)
```

Sets the stroke width of the divider. This attribute can be dynamically set using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

> **NOTE:** 
> 
> - The width of the divider cannot be in percentage.
> 
> - When a horizontal divider is used, **strokeWidth** controls the height, and its priority is lower than that of the universal attribute [height](arkts-arkui-common-comp-commonmethod-c.md#height). When a vertical divider is used,
> **strokeWidth** controls the width, and its priority is lower than that of the universal attribute
> [width](arkts-arkui-common-comp-commonmethod-c.md#width).
> 
> - If the size exceeds the value set by the universal attribute, the divider is clipped based on the universal attribute.
> 
> - If the divider is not displayed due to 1-pixel rounding on the device hardware, 2 pixels are recommended.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string | Yes | Stroke width of the divider.<br>Default value: **1px** <br>Invalid values are treated as the default value. <br>Unit: vp |

## vertical

```TypeScript
vertical(value: boolean)
```

Sets the direction of the divider. This attribute can be dynamically set using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the divider is vertical or horizontal.<br>**false**: A horizontal divider is used. <br>**true**: A vertical divider is used. <br>Default value: **false** <br>Invalid values are treated as the default value. |
