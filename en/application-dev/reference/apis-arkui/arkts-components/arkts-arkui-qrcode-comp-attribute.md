# QRCode properties/events

In addition to the [universal attributes](../../../reference/apis-arkui/arkui-ts/ts-component-general-attributes.md), the following attributes are supported.

The [universal events][universal events](../../../reference/apis-arkui/arkui-ts/ts-component-general-events.md) are supported.

**Inheritance/Implementation:** QRCodeAttribute extends CommonMethod<QRCodeAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor(value: ResourceColor)
```

Sets the background color of the QR code.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Background color of the QR code.<br>Default value: **Color.White**<br>Since API version 11, the default value is **'#ffffffff'** and does not change with the system color mode. |

## color

```TypeScript
color(value: ResourceColor)
```

Sets the color of the QR code.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | QR code color. The default value is **'#ff000000'** and does not change with the system color mode.<br> |

## contentOpacity

```TypeScript
contentOpacity(value: number | Resource)
```

Sets the opacity of the QR code content. The minimum value is 0, and the maximum value is 1.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Opacity of the QR code content.<br>Default value: **1**<br>Value range: [0, 1]. If the value is out of the range, the default value is used. |
