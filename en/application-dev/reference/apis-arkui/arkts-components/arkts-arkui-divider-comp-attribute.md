# Divider properties/events

In addition to the [universal attributes](arkts-arkui-commonmethod-c.md), the following attributes are supported.

The [universal events](arkts-arkui-commonmethod-c.md) are supported.

**Inheritance/Implementation:** DividerAttribute extends CommonMethod<DividerAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color(value: ResourceColor)
```

Sets the color of the divider. This attribute can be dynamically set using attributeModifier.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Color of the divider.<br>Default value: **'#33182431'**<br>Invalid values are treated as the default value. <br>You can set a common divider color using WithTheme. |

## lineCap

```TypeScript
lineCap(value: LineCapStyle)
```

Sets the line cap style of the divider. This attribute can be dynamically set using attributeModifier.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [LineCapStyle](../arkts-apis/arkts-arkui-linecapstyle-e.md) | Yes | Line cap style of the divider.<br>Default value: **LineCapStyle.Butt**<br>Invalid values are treated as the default value. |

## strokeWidth

```TypeScript
strokeWidth(value: number | string)
```

Sets the stroke width of the divider. This attribute can be dynamically set using attributeModifier.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string | Yes | Stroke width of the divider.<br>Default value: **1px**<br>Invalid values are treated as the default value.<br>Unit: vp<br>**NOTE:** <br>Percentage values are not supported. This attribute has lower priority than the height attribute. If its value exceeds the **height** setting, cropping is performed based on the **height** constraint. Due to hardware limitations on some devices where 1 px dividers may not display properly after rounding, you are advised to use the **2px** value. |

## vertical

```TypeScript
vertical(value: boolean)
```

Sets the direction of the divider. This attribute can be dynamically set using attributeModifier.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the divider is vertical or horizontal.<br>**false**: A horizontal divider is used.<br>**true**: A vertical divider is used.<br>Default value: **false**<br>Invalid values are treated as the default value. |
