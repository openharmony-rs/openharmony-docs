# TextTimer properties/events

```TypeScript
declare class TextTimerAttribute extends CommonMethod<TextTimerAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md), the following attributes are supported.

**Inheritance/Implementation:** TextTimerAttribute extends CommonMethod&lt;TextTimerAttribute&gt;

**Since:** 8

<!--Device-unnamed-declare class TextTimerAttribute extends CommonMethod<TextTimerAttribute>--><!--Device-unnamed-declare class TextTimerAttribute extends CommonMethod<TextTimerAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## contentModifier

```TypeScript
contentModifier(modifier: ContentModifier<TextTimerConfiguration>)
```

Customizes the content area of **TextTimer**. When the default text display style cannot meet the requirements, this API can be used to implement a custom timer UI effect.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextTimerAttribute-contentModifier(modifier: ContentModifier<TextTimerConfiguration>): TextTimerAttribute--><!--Device-TextTimerAttribute-contentModifier(modifier: ContentModifier<TextTimerConfiguration>): TextTimerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| modifier | [ContentModifier](arkts-arkui-common-comp-contentmodifier-i.md)&lt;[TextTimerConfiguration](arkts-arkui-texttimer-comp-texttimerconfiguration-i.md)&gt; | Yes | Method for customizing the content area on the TextTimer component.<br>modifier: content modifier. The developer needs to define a custom class to implement the ContentModifier interface. |

## fontColor

```TypeScript
fontColor(value: ResourceColor)
```

Sets the font color.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-TextTimerAttribute-fontColor(value: ResourceColor): TextTimerAttribute--><!--Device-TextTimerAttribute-fontColor(value: ResourceColor): TextTimerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Font color.<br>Default value on Wearable devices: '#c5ffffff', displayed in white. <br>Default value on other devices: '#e6182431', displayed in black. |

## fontFamily

```TypeScript
fontFamily(value: ResourceStr)
```

Sets the font family.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-TextTimerAttribute-fontFamily(value: ResourceStr): TextTimerAttribute--><!--Device-TextTimerAttribute-fontFamily(value: ResourceStr): TextTimerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Font family. The default font is **'HarmonyOS Sans'**. <br>The 'HarmonyOS Sans' font and [registered custom fonts](../arkts-apis/arkts-arkui-font.md) are supported for applications. <br>Only the 'HarmonyOS Sans' font is supported for widgets. |

## fontSize

```TypeScript
fontSize(value: Length)
```

Sets the font size.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-TextTimerAttribute-fontSize(value: Length): TextTimerAttribute--><!--Device-TextTimerAttribute-fontSize(value: Length): TextTimerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Font size. <br>Default value: 16fp <br>When value is of the number type in Length, the unit is fp. When value is of the string type in Length, if the set value does not start with a digit, it is processed as 0fp; if the set value starts with a digit, and the content after the digit contains characters other than [pixel units](arkts-arkui-common-comp.md) (such as letters and special symbols), the numeric part at the beginning of the string is used, with the unit being fp. <br>For example, when the set value is "abc", the value is 0fp; when the set value is "10vp", the value is 10 vp; when the set value is "10vp11abc", the value is 10fp. Percentage strings are not supported. |

## fontStyle

```TypeScript
fontStyle(value: FontStyle)
```

Sets the font style.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-TextTimerAttribute-fontStyle(value: FontStyle): TextTimerAttribute--><!--Device-TextTimerAttribute-fontStyle(value: FontStyle): TextTimerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [FontStyle](../arkts-apis/arkts-arkui-fontstyle-e.md) | Yes | Font style, for example, the italic font style.<br>Default value: FontStyle.Normal |

## fontWeight

```TypeScript
fontWeight(value: number | FontWeight | ResourceStr)
```

Sets the font weight of the text. If the value is too large, the text in different fonts may be truncated.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-TextTimerAttribute-fontWeight(value: number | FontWeight | ResourceStr): TextTimerAttribute--><!--Device-TextTimerAttribute-fontWeight(value: number | FontWeight | ResourceStr): TextTimerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [FontWeight](../arkts-apis/arkts-arkui-fontweight-e.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Font weight of the text. For the number type, the value range is [100, 900], with an interval of 100. A larger value indicates a heavier font weight. The default value for a number outside the value range is 400. For the [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) type, only the string form of the number value is supported, for example, "400", as well as "bold", "bolder", "lighter", "regular", and "medium", which correspond to the respective enum values in FontWeight.<br>Default value: FontWeight.Normal <br>Since API version 20, the Resource type is supported.<br>**Since:** 20 |

## format

```TypeScript
format(value: string)
```

Sets the custom time format, which must contain at least one of the following keywords: **HH**, **mm**, **ss**, and **SS**. When date formats such as **yy**, **MM**, and **dd** are used, they are not supported, and the default format **'HH:mm:ss.SS'** is used instead.

The timer update frequency is processed based on the minimum unit of **format**. For example, when **format** is set to **'HH:mm'**, the update frequency is one minute. When a high-precision **format** (for example, one containing **SS**) is set, the intervals of the **onTimer** callback may be uneven.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-TextTimerAttribute-format(value: string): TextTimerAttribute--><!--Device-TextTimerAttribute-format(value: string): TextTimerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | Custom time format displayed by the timer. It must contain at least one of the keywords HH, mm, ss, or SS.<br>Default value: 'HH:mm:ss.SS' |

## onTimer

```TypeScript
onTimer(event: (utc: number, elapsedTime: number) => void)
```

Triggered when the time text changes. This event is not triggered in the locked-screen state or the application background state. When the component is invisible (not in the locked-screen state or the application background state), the UI time change stops, but this event is still triggered normally. When a high-precision [format](#format) (**SS**) is set, the callback intervals may be uneven, and the time intervals between two adjacent callbacks may differ.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-TextTimerAttribute-onTimer(event: (utc: number, elapsedTime: number) => void): TextTimerAttribute--><!--Device-TextTimerAttribute-onTimer(event: (utc: number, elapsedTime: number) => void): TextTimerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (utc: number, elapsedTime: number) =&gt; void | Yes | utc: Linux timestamp, which is the amount of time that has elapsed since January 1, 1970, in the minimum unit of the format.<br>elapsedTime: Elapsed time of the timer, in the minimum unit of the format. |

## textShadow

```TypeScript
textShadow(value: ShadowOptions | Array<ShadowOptions>)
```

Sets the text shadow effect. This API supports input parameters in an array to implement multiple text shadows. The **fill** field and the smart color picking mode are not supported.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 12.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextTimerAttribute-textShadow(value: ShadowOptions | Array<ShadowOptions>): TextTimerAttribute--><!--Device-TextTimerAttribute-textShadow(value: ShadowOptions | Array<ShadowOptions>): TextTimerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ShadowOptions](arkts-arkui-common-comp-shadowoptions-i.md) &#124; Array&lt;[ShadowOptions](arkts-arkui-common-comp-shadowoptions-i.md)&gt; | Yes | Parameters of the text shadow effect, including the color, blur radius, and offset. |
