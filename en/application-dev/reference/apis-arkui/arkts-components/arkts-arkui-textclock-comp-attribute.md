# TextClock properties/events

```TypeScript
declare class TextClockAttribute extends CommonMethod<TextClockAttribute>
```

In addition to the [universal attributes](../../../reference/apis-arkui/arkui-ts/ts-component-general-attributes.md), the following attributes are supported.

In addition to the [universal events](../../../reference/apis-arkui/arkui-ts/ts-component-general-events.md), the following events are supported.

**Inheritance/Implementation:** TextClockAttribute extends CommonMethod<TextClockAttribute>

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## contentModifier

```TypeScript
contentModifier(modifier: ContentModifier<TextClockConfiguration>)
```

Creates a content modifier.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| modifier | [ContentModifier](arkts-arkui-common-comp-contentmodifier-i.md)&lt;[TextClockConfiguration](arkts-arkui-textclock-comp-textclockconfiguration-i.md)&gt; | Yes | Content modifier to apply to the text clock.<br> **modifier**: content modifier. You need to customize a class to implement the **ContentModifier** API. |

## dateTimeOptions

```TypeScript
dateTimeOptions(dateTimeOptions: Optional<DateTimeOptions>)
```

Sets whether to display a leading zero for the hour.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dateTimeOptions | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[DateTimeOptions](arkts-arkui-timepicker-comp-datetimeoptions-t.md)&gt; | Yes | Whether to display leading zeros in the hour. It only supports setting the **hour** parameter. When the parameter value is **{hour: "2-digit"}**, a leading zero is displayed. When the parameter value is **{hour: "numeric"}**, no leading zero is displayed.<br>Default value: **undefined**. By default, leading zeros are displayed in 24-hour format, but not displayed in 12-hour format. |

## fontColor

```TypeScript
fontColor(value: ResourceColor)
```

Sets the font color.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Font color.<br>Default value for wearables: '#c5ffffff'; default value for other devices: '#e6182431' |

## fontFamily

```TypeScript
fontFamily(value: ResourceStr)
```

Sets the font family.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Font family. Default font: **'HarmonyOS Sans'**<br>The 'HarmonyOS Sans' font and [registered custom fonts](../arkts-apis/arkts-arkui-font.md) are supported for applications.<br>Only the 'HarmonyOS Sans'font is supported for widgets. |

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | Font feature. |

## fontSize

```TypeScript
fontSize(value: Length)
```

Sets the font size.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Font size. If **fontSize** is of the number type, the unit fp is used. The default font size is 16 fp. The value cannot be a percentage. |

## fontStyle

```TypeScript
fontStyle(value: FontStyle)
```

Sets the font style.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [FontStyle](../arkts-apis/arkts-arkui-fontstyle-e.md) | Yes | Font style.<br>Default value: **FontStyle.Normal**, indicating the standard font style (non-italic) |

## fontWeight

```TypeScript
fontWeight(value: number | FontWeight | string)
```

Sets the font weight of the text. If the value is too large, the text in different fonts may be truncated.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [FontWeight](../arkts-apis/arkts-arkui-fontweight-e.md) &#124; string | Yes | Font width of the text. The value range of the number type is [100, 900]. The value interval is 100. A larger value indicates a wider font. If the value of the number type is not within the value range, the default value is **400**. For the string type, only strings that represent a number, for example, **"400"**, and the following enumerated values of **FontWeight** are supported: **"bold"**, **"bolder"**, **"lighter"**, **"regular"**, and **"medium"**.<br>Default value: **FontWeight.Normal** |

## format

```TypeScript
format(value: ResourceStr)
```

Sets the time format, for example, **yyyy/MM/dd** or **yyyy-MM-dd**.

**y**: year (**yyyy** indicates the complete year, and **yy** indicates the last two digits of the year.)

**M**: month (To display 01 for January, use **MM** instead.)

**d**: day (To display 01 for the first day, use **dd** instead.)

**E**: day of week (To display the full name, use **EEEE**; to display the abbreviation, use **E**, **EE**, or **EEE**.)

**H**: hour (24-hour format); **h**: hour (12-hour format)

**m**: minute

**s**: second

**SS**: centisecond (If the number of S characters in the format is less than 3, all are treated as centiseconds.)

**SSS**: millisecond (If the number of S characters in the format is greater than or equal to 3, all are treated as milliseconds.)

**a**: morning/afternoon (This parameter does not take effect when the hour part is set to **H**.)

Date separators: year, month, day, slash (/), hyphen (-), and period (.) (Custom separator styles are allowed. Letters cannot be used as separators, while Chinese characters can be treated as separators.)

The parts of the date can be used alone or combined with each other as needed. The time can be updated as frequent as once per second. As such, whenever possible, avoid setting the centisecond and millisecond parts separately.

When an invalid letter is set, the letter is ignored. If all letters in **format** are invalid, the display format follows the system's language and hour format settings.

If **format** is an empty string ("") or **undefined**, the default value is used.

Default value outside of widgets: 12-hour format: aa hh:mm:ss; 24-hour format: HH:mm:ss.

Default value in widgets: 12-hour format: hh:mm, 24-hour format: HH:mm.

When used in widgets, the minimum time unit is minute. In this case, if the format contains seconds or centiseconds, the default value will be used.

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
| [d](../../apis-arkts/arkts-apis/arkts-arkts-math-decimal-decimal-c.md) | 4 |
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
| [mm:ss.SS](../../apis-performance-analysis-kit/arkts-apis/arkts-performanceanalysis-hitracechain-hitracetracepointtype-e.md) | 00:04.91 |
| mm:ss.SSS | 00:04.536 |
| hh:mm:ss aa | 5:00:04 AM |
| HH | 17 |

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Time format to set.<br>**Since:** 20 |

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (value: number) =&gt; void | Yes | Unix time stamp, which is the number of seconds that have elapsed since the Unix epoch. |

## textShadow

```TypeScript
textShadow(value: ShadowOptions | Array<ShadowOptions>)
```

Sets the text shadow. It supports input parameters in an array to implement multiple text shadows. This API does not work with the **fill** attribute or coloring strategy.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ShadowOptions](arkts-arkui-common-comp-shadowoptions-i.md) &#124; Array&lt;[ShadowOptions](arkts-arkui-common-comp-shadowoptions-i.md)&gt; | Yes | Font shadow of the text. |
