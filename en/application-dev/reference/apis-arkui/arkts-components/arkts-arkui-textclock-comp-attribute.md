# TextClock properties/events

```TypeScript
declare class TextClockAttribute extends CommonMethod<TextClockAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md), the following attributes are supported:

**Inheritance/Implementation:** TextClockAttribute extends CommonMethod<TextClockAttribute>

**Since:** 8

<!--Device-unnamed-declare class TextClockAttribute extends CommonMethod<TextClockAttribute>--><!--Device-unnamed-declare class TextClockAttribute extends CommonMethod<TextClockAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## contentModifier

```TypeScript
contentModifier(modifier: ContentModifier<TextClockConfiguration>)
```

Creates a content modifier.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextClockAttribute-contentModifier(modifier: ContentModifier<TextClockConfiguration>): TextClockAttribute--><!--Device-TextClockAttribute-contentModifier(modifier: ContentModifier<TextClockConfiguration>): TextClockAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| modifier | [ContentModifier](arkts-arkui-common-comp-contentmodifier-i.md)&lt;[TextClockConfiguration](arkts-arkui-textclock-comp-textclockconfiguration-i.md)&gt; | Yes | Method for customizing the content area on the TextClock component.<br>modifier: content modifier. Developers need to customize a class to implement the ContentModifier API. |

## dateTimeOptions

```TypeScript
dateTimeOptions(dateTimeOptions: Optional<DateTimeOptions>)
```

Sets whether to display a leading zero for the hour.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-TextClockAttribute-dateTimeOptions(dateTimeOptions: Optional<DateTimeOptions>): TextClockAttribute--><!--Device-TextClockAttribute-dateTimeOptions(dateTimeOptions: Optional<DateTimeOptions>): TextClockAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dateTimeOptions | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[DateTimeOptions](arkts-arkui-timepicker-comp-datetimeoptions-t.md)&gt; | Yes | Sets whether to display a leading zero for the hour. Only the hour parameter is supported. The value {hour: "2-digit"} indicates that a leading zero is displayed, and the value {hour: "numeric"} indicates that no leading zero is displayed.<br>Default value: undefined. By default, a leading zero is displayed in the 24-hour format and not displayed in the 12-hour format. |

## fontColor

```TypeScript
fontColor(value: ResourceColor)
```

Sets the font color.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

<!--Device-TextClockAttribute-fontColor(value: ResourceColor): TextClockAttribute--><!--Device-TextClockAttribute-fontColor(value: ResourceColor): TextClockAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Font Color.<br>Default value on Wearable devices: '#c5ffffff'; default value on other devices: '#e6182431' |

## fontFamily

```TypeScript
fontFamily(value: ResourceStr)
```

Sets the font family.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

<!--Device-TextClockAttribute-fontFamily(value: ResourceStr): TextClockAttribute--><!--Device-TextClockAttribute-fontFamily(value: ResourceStr): TextClockAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Font list. The default font is 'HarmonyOS Sans'. <br>The application currently supports the 'HarmonyOS Sans' font and [registered custom fonts](../arkts-apis/arkts-arkui-font.md). <br>The card currently supports only the 'HarmonyOS Sans' font. |

## fontFeature

```TypeScript
fontFeature(value: string)
```

Sets the font feature, for example, monospaced digits.

Format: normal \| \&lt;feature-tag-value\&gt;

Format of **\&lt;feature-tag-value\&gt;**: \&lt;string\&gt; \[ \&lt;integer\&gt; \| on \| off ]

There can be multiple **\&lt;feature-tag-value\&gt;** values, which are separated by commas (,).

For example, the input format for monospaced clock fonts is "ss01" on.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

<!--Device-TextClockAttribute-fontFeature(value: string): TextClockAttribute--><!--Device-TextClockAttribute-fontFeature(value: string): TextClockAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | Text feature effect, used to set the OpenType features of the text. Format: normal &#124; &lt;feature-tag-value&gt;, where the &lt;feature-tag-value&gt; format is: &lt;string&gt; [ &lt;integer&gt; &#124; on &#124; off ]. Multiple features can be set, separated by ','. For example, the format for using monospaced clock digits is:'"ss01" on'. |

## fontSize

```TypeScript
fontSize(value: Length)
```

Sets the font size.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

<!--Device-TextClockAttribute-fontSize(value: Length): TextClockAttribute--><!--Device-TextClockAttribute-fontSize(value: Length): TextClockAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Font size. When fontSize is of the number type, the unit fp is used.<br>The default font size is 16fp. Percentage strings are not supported. If a percentage string is passed in, the default value is used. |

## fontStyle

```TypeScript
fontStyle(value: FontStyle)
```

Sets the font style.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

<!--Device-TextClockAttribute-fontStyle(value: FontStyle): TextClockAttribute--><!--Device-TextClockAttribute-fontStyle(value: FontStyle): TextClockAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [FontStyle](../arkts-apis/arkts-arkui-fontstyle-e.md) | Yes | Font style.<br>Default value: FontStyle.Normal, which indicates the standard font style (not italic). |

## fontWeight

```TypeScript
fontWeight(value: number | FontWeight | string)
```

Sets the font weight of the text. If the value is too large, the text in different fonts may be truncated.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

<!--Device-TextClockAttribute-fontWeight(value: number | FontWeight | string): TextClockAttribute--><!--Device-TextClockAttribute-fontWeight(value: number | FontWeight | string): TextClockAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [FontWeight](../arkts-apis/arkts-arkui-fontweight-e.md) &#124; string | Yes | Font weight of the text. For the number type, the value ranges from 100 to 900, at an interval of 100. A larger value indicates a heavier font. The default value is 400 for values outside the range of the number type. For the string type, the following values are supported: the string form of a number type value (for example, 400), and the enum values 'lighter' (corresponding to 300), 'regular' (corresponding to 400), 'medium' (corresponding to 500), 'bold' (corresponding to 700), and 'bolder' (corresponding to 900), which correspond to the respective enum values in FontWeight.<br>Default value: FontWeight.Normal |

## format

```TypeScript
format(value: ResourceStr)
```

Sets the time format, for example, **yyyy/MM/dd** or **yyyy-MM-dd**.

y: year (yyyy indicates the full year, and yy indicates the last two digits of the year)

M: month (use MM to display the month as 01)

d: day (use dd to display the day as 01)

E: day of the week (use EEEE to display Saturday, and use E, EE, or EEE to display Sat)

H: hour (24-hour format)

h: hour (12-hour format)

m: minute

s: second

SS: centisecond (if the number of S in the format is less than 3, all are processed as centiseconds)

SSS: millisecond (if the number of S in the format is greater than or equal to 3, all are processed as milliseconds)

a: AM/PM (this parameter does not take effect when the hour format is set to H)

Date separators: year, month, day, slash (/), hyphen (-), and period (.) (Custom separator styles are allowed. Letters cannot be used as separators, while Chinese characters can be treated as separators.)

The parts of the date can be used alone or combined with each other as needed. The time can be updated as frequent as once per second. As such, whenever possible, avoid setting the centisecond and millisecond parts separately.

When an invalid letter is set, the letter is ignored. If all letters in **format** are invalid, the display format follows the system's language and hour format settings.

If **format** is an empty string ("") or **undefined**, the default value is used.

Default value in non-widget scenarios: 12-hour format: aa hh:mm:ss; 24-hour format: HH:mm:ss.

Default value in widgets: 12-hour format: hh:mm; 24-hour format: HH:mm.

When used in a widget, the minimum time unit is minute. If the set format contains seconds or centiseconds, the default value is used.

The following table shows how different settings of **format** work out.

| Input Format | Display Effect |  
| ------------------------- | ---------------------- |  
| EEEE, M, d, yyyy | Saturday, Feb, 4, 2023 |
| M d, yyyy | Feb 4, 2023 |
| EEEE, M, d | Saturday, Feb, 4 |
| M d | Feb 4 |
| MM/dd/yyyy | Feb/04/2023 |
| EEEE MM dd | Saturday Feb 04 |
| yyyy | 2023 |
| yy | 23 |
| MM | Feb |
| M | Feb |
| dd (complete date) | 04 |
| d | 4 |
| EEEE (full name) | Saturday |
| E, EE, EEE (abbreviation) | [Sat](../arkts-apis/arkts-arkui-week-e.md) |
| M d, yyyy | Feb 4, 2023 |
| yyyy/M/d | 2023/Feb/4 |
| yyyy-M-d | 2023-Feb-4 |
| yyyy.M.d | 2023.Feb.4 |
| HH:mm:ss | 17:00:04 |
| aa hh:mm:ss | AM 5:00:04 |
| hh:mm:ss | 5:00:04 |
| HH:mm | 17:00 |
| aa hh:mm | AM 5:00 |
| hh:mm | 5:00 |
| mm:ss | 00:04 |
| mm:ss.SS | 00:04.91 |
| mm:ss.SSS | 00:04.536 |
| hh:mm:ss aa | 5:00:04 AM |
| HH | 17 |

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

<!--Device-TextClockAttribute-format(value: ResourceStr): TextClockAttribute--><!--Device-TextClockAttribute-format(value: ResourceStr): TextClockAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Time format to display.<br>Since API version 20, the Resource type is supported.<br>**Since:** 20 |

## onDateChange

```TypeScript
onDateChange(event: (value: number) => void)
```

Triggered when the time changes.

This event does not take effect when the component is invisible.

If the event is not used in a widget, it is triggered when the change occurs in seconds.

If the event is used in a widget, it is triggered when the change occurs in minutes.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

<!--Device-TextClockAttribute-onDateChange(event: (value: number) => void): TextClockAttribute--><!--Device-TextClockAttribute-onDateChange(event: (value: number) => void): TextClockAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (value: number) =&gt; void | Yes | Unix time stamp, which is the number of seconds that have elapsed since the Unix epoch. |

## textShadow

```TypeScript
textShadow(value: ShadowOptions | Array<ShadowOptions>)
```

Sets the text shadow effect. This API supports passing an array as the input parameter to implement multiple text shadows. The fill field and the smart color mode are not supported.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

<!--Device-TextClockAttribute-textShadow(value: ShadowOptions | Array<ShadowOptions>): TextClockAttribute--><!--Device-TextClockAttribute-textShadow(value: ShadowOptions | Array<ShadowOptions>): TextClockAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ShadowOptions](arkts-arkui-common-comp-shadowoptions-i.md) &#124; Array&lt;[ShadowOptions](arkts-arkui-common-comp-shadowoptions-i.md)&gt; | Yes | Text shadow effect. Supports a single shadow object or an array of shadow objects to achieve multiple shadow effects. The ShadowOptions object contains attributes such as radius (blur radius), color (shadow color), offsetX (X-axis offset), and offsetY (Y-axis offset). <br>The fill field and the smart color picking mode are not supported. For details about the attributes, see [ShadowOptions](arkts-arkui-common-comp-shadowoptions-i.md). |
