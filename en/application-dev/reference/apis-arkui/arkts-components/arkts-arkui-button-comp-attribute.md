# Button properties/events

```TypeScript
declare class ButtonAttribute extends CommonMethod<ButtonAttribute>
```

In addition to the universal attributes, the following attributes are supported.

The universal events are supported.

**Inheritance/Implementation:** ButtonAttribute extends CommonMethod<ButtonAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## buttonStyle

```TypeScript
buttonStyle(value: ButtonStyleMode)
```

Sets the style and primacy for the button. The system automatically adjusts the button background color and text color based on the enumerated value. You can also use the [backgroundColor](arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor), [fontColor](#fontcolor), and [role](#role) APIs to set the background color and text color. The actual displayed effect will be determined by the last setting.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 12.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ButtonStyleMode](arkts-arkui-button-comp-buttonstylemode-e.md) | Yes | Style and primacy of the button<br>Default value: **ButtonStyleMode.EMPHASIZED** |

## contentModifier

```TypeScript
contentModifier(modifier: ContentModifier<ButtonConfiguration>)
```

Creates a content modifier.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| modifier | [ContentModifier](arkts-arkui-common-comp-contentmodifier-i.md)&lt;[ButtonConfiguration](arkts-arkui-button-comp-buttonconfiguration-i.md)&gt; | Yes | Content modifier to apply to the button.<br> **modifier**: content modifier. You need a custom class to implement the **ContentModifier** API. |

## controlSize

```TypeScript
controlSize(value: ControlSize)
```

Sets the size for the button.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 12.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ControlSize](arkts-arkui-button-comp-controlsize-e.md) | Yes | Size of the button.<br>Default value: **ControlSize.NORMAL** |

## fontColor

```TypeScript
fontColor(value: ResourceColor)
```

Sets the font color for the button.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Font color of the button.<br>Default value: **$r('sys.color.font_on_primary')**, which means white |

## fontFamily

```TypeScript
fontFamily(value: string | Resource)
```

Sets the font family.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Font family. The 'HarmonyOS Sans' font and [registered custom fonts](../arkts-apis/arkts-arkui-font.md) are supported. |

## fontSize

```TypeScript
fontSize(value: Length)
```

Sets the font size for the button.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Font size of the button.<br>Default value:<br>**$r('sys.float.Body_L')** when **controlSize** is set to **ControlSize.NORMAL**<br>**$r('sys.float.Body_S')** when **controlSize** is set to **ControlSize.SMALL**<br>Note: For the string type, percentage values are not supported. |

## fontStyle

```TypeScript
fontStyle(value: FontStyle)
```

Sets the font style for the button.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [FontStyle](../arkts-apis/arkts-arkui-fontstyle-e.md) | Yes | Font style of the button.<br>Default value: **FontStyle.Normal** |

## fontWeight

```TypeScript
fontWeight(value: number | FontWeight | string)
```

Sets the font weight for the button.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [FontWeight](../arkts-apis/arkts-arkui-fontweight-e.md) &#124; string | Yes | Font weight of the button. For the number type, the value ranges from 100 to 900, at an interval of 100. A larger value indicates a thicker font.<br>Default value: **500**<br> For the string type, only strings that represent a number, for example, **'400'**, and the following enumerated values of **FontWeight** are supported: **'bold'**, **'bolder'**, **'lighter'**, **'regular'**, and **'medium'**.<br>If the value is abnormal or invalid, the font weight defaults to 400. |

## labelStyle

```TypeScript
labelStyle(value: LabelStyle)
```

Sets the label style for the button.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [LabelStyle](arkts-arkui-button-comp-labelstyle-i.md) | Yes | Label style of the button. |

## maxFontScale

```TypeScript
maxFontScale(scale: number | Resource)
```

Sets the maximum font scale factor for text.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scale | number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Maximum font scale factor for text.<br>Value range: [1, +∞)<br>**NOTE:** <br>A value less than 1 is handled as **1**. Abnormal values are ineffective by default.<br>If this parameter is not configured, the maximum scale for a circular button is 1x, while the maximum scale for capsule-type buttons, standard buttons, and rounded rectangle buttons defaults to the system-defined value. |

## minFontScale

```TypeScript
minFontScale(scale: number | Resource)
```

Sets the minimum font scale factor for text.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scale | number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Minimum font scale factor for text.<br>Value range: [0, 1]<br>**NOTE:** <br>A value less than 0 is handled as **0**. A value greater than 1 is handled as **1**. Abnormal values are ineffective by default. |

## role

```TypeScript
role(value: ButtonRole)
```

Sets the role of the button. The system automatically adjusts the button background color and text color based on the enumerated value. You can also use the [backgroundColor](arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor), [fontColor](#fontcolor), and [buttonStyle](#buttonstyle) APIs to set the background color and text color. The actual displayed effect will be determined by the last setting.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ButtonRole](arkts-arkui-button-comp-buttonrole-e.md) | Yes | Role of the button.<br>Default value: **ButtonRole.NORMAL** |

## stateEffect

```TypeScript
stateEffect(value: boolean)
```

Specifies whether to enable the pressed state effect when the button is clicked.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to enable the pressed state effect when the button is clicked.<br>**true**: The pressed state effect is enabled. **false**: The pressed state effect is disabled.<br>Default value: **true** |

## type

```TypeScript
type(value: ButtonType)
```

Sets the button type.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ButtonType](arkts-arkui-button-comp-buttontype-e.md) | Yes | Button type.<br>API version 18 and later: The default value is **ButtonType.ROUNDED_RECTANGLE**. |
