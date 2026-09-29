# TimePicker properties/events

```TypeScript
declare class TimePickerAttribute extends CommonMethod<TimePickerAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md), the following attributes are supported.

In addition to the [universal events](arkts-arkui-common-comp.md), the following events are supported.

**Inheritance/Implementation:** TimePickerAttribute extends CommonMethod<TimePickerAttribute>

**Since:** 8

<!--Device-unnamed-declare class TimePickerAttribute extends CommonMethod<TimePickerAttribute>--><!--Device-unnamed-declare class TimePickerAttribute extends CommonMethod<TimePickerAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dateTimeOptions

```TypeScript
dateTimeOptions(value: DateTimeOptions)
```

Sets whether to display a leading zero for the hour, minute, and second. '2-digit' is suitable for scenarios where a unified format is required (such as tables and reports), while 'numeric' is suitable for more concise display requirements.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TimePickerAttribute-dateTimeOptions(value: DateTimeOptions): TimePickerAttribute--><!--Device-TimePickerAttribute-dateTimeOptions(value: DateTimeOptions): TimePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [DateTimeOptions](arkts-arkui-timepicker-comp-datetimeoptions-t.md) | Yes | Sets whether to display leading zeros for the hour, minute, and second.<br>Default value: <br>hour: The default value is "2-digit" in the 24-hour format, which sets whether the hour is displayed as a 2 -digit number. If the actual value is less than 10, a leading zero is added and displayed, that is, "0X". The default value is "numeric" in the 12-hour format, that is, no leading zero. <br>minute: The default value is "2-digit", which sets whether the minute is displayed as a 2-digit number. If the actual value is less than 10, a leading zero is added and displayed, that is, "0X". <br>second: The default value is "2-digit", which sets whether the second is displayed as a 2-digit number. If the actual value is less than 10, a leading zero is added and displayed, that is, "0X". <br> When the values of hour, minute, and second are set to undefined, the display effect follows the same rules as their default values. |

<a id="datetimeoptions-1"></a>

## dateTimeOptions

```TypeScript
dateTimeOptions(timeFormat: Optional<DateTimeOptions>)
```

Sets whether to display a leading zero for the hours, minutes, and seconds. Compared with [dateTimeOptions&lt;sup&gt;12+&lt;/sup&gt;](#datetimeoptions), this API supports the **undefined** type for the **timeFormat** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TimePickerAttribute-dateTimeOptions(timeFormat: Optional<DateTimeOptions>): TimePickerAttribute--><!--Device-TimePickerAttribute-dateTimeOptions(timeFormat: Optional<DateTimeOptions>): TimePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| timeFormat | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[DateTimeOptions](arkts-arkui-timepicker-comp-datetimeoptions-t.md)&gt; | Yes | Sets whether the hour, minute, and second are displayed with a leading zero. Currently, only the hour, minute, and second parameters are supported.<br>Default value: <br>hour: The default value is "2-digit" in the 24-hour format. Sets whether the hour is displayed as a 2-digit number. If the actual value is less than 10, a leading zero is added and displayed, that is, "0X". The default value is "numeric" in the 12-hour format, that is, no leading zero. <br>minute: The default value is "2-digit". Sets whether the minute is displayed as a 2-digit number. If the actual value is less than 10, a leading zero is added and displayed, that is, "0X". <br>second: The default value is "2-digit". Sets whether the second is displayed as a 2-digit number. If the actual value is less than 10, a leading zero is added and displayed, that is, "0X". <br> When the values of hour, minute, and second are set to undefined, the display effect follows the same rules as their default values. |

## digitalCrownSensitivity

```TypeScript
digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>)
```

Sets the crown sensitivity. High sensitivity applies to scenarios where the time needs to be adjusted quickly, and low sensitivity applies to scenarios where the time needs to be adjusted precisely.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TimePickerAttribute-digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>): TimePickerAttribute--><!--Device-TimePickerAttribute-digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>): TimePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sensitivity | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[CrownSensitivity](../arkts-apis/arkts-arkui-crownsensitivity-e.md)&gt; | Yes | Crown response sensitivity.<br>Default value: CrownSensitivity.MEDIUM, indicating a moderate response speed. |

## disappearTextStyle

```TypeScript
disappearTextStyle(value: PickerTextStyle)
```

Sets the text color, font size, and font weight of edge items (the second item above or below the selected item).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TimePickerAttribute-disappearTextStyle(value: PickerTextStyle): TimePickerAttribute--><!--Device-TimePickerAttribute-disappearTextStyle(value: PickerTextStyle): TimePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md) | Yes | Text color, font size, and font weight of the edge items (the second item above or below the selected item).<br>Default value: <br>{<br>color: '#ff182431', <br>font: {<br>size: '14fp', <br>weight: FontWeight.Regular <br>} <br>} |

<a id="disappeartextstyle-1"></a>

## disappearTextStyle

```TypeScript
disappearTextStyle(style: Optional<PickerTextStyle>)
```

Sets the text color, font size, and font weight of edge items (the second item above or below the selected item). Compared with [disappearTextStyle&lt;sup&gt;10+&lt;/sup&gt;](#disappeartextstyle), this API supports the **undefined** type for the **style** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TimePickerAttribute-disappearTextStyle(style: Optional<PickerTextStyle>): TimePickerAttribute--><!--Device-TimePickerAttribute-disappearTextStyle(style: Optional<PickerTextStyle>): TimePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md)&gt; | Yes | Text color, font size, and font weight of the edge items.<br>Default value: <br>{<br>color: '#ff182431', <br>font: {<br>size: '14fp', <br>weight: FontWeight.Regular <br>} <br>} <br>When the value of style is undefined, the default value is used. |

## enableCascade

```TypeScript
enableCascade(enabled: boolean)
```

Sets whether the AM/PM indicator automatically switches based on the hour value. This takes effect only when [useMilitaryTime](#usemilitarytime) is set to false. Automatic switching applies to daily consumer scenarios such as alarms and schedules that emphasize operation efficiency and a smooth experience, while manual switching applies to scenarios such as healthcare and legal affairs that demand strict time precision and tolerate no ambiguity.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TimePickerAttribute-enableCascade(enabled: boolean): TimePickerAttribute--><!--Device-TimePickerAttribute-enableCascade(enabled: boolean): TimePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether the AM/PM indicator automatically switches based on the hour. This parameter takes effect only when useMilitaryTime is set to false.<br>- true: automatically switches. When enabled is set to true, it takes effect only when the loop parameter is also set to true. <br>- false: does not automatically switch. The AM/PM indicator must be selected manually and is not automatically adjusted based on the hour. <br>Default value: false |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(enable: boolean)
```

Sets whether to enable haptic feedback.

To enable haptic feedback, you must declare the following permission under **requestPermissions** in **module** in **src/main/module.json5** of the project.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 18.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TimePickerAttribute-enableHapticFeedback(enable: boolean): TimePickerAttribute--><!--Device-TimePickerAttribute-enableHapticFeedback(enable: boolean): TimePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to enable haptic feedback.<br>- true: Enable haptic feedback. <br>- false: Disable haptic feedback. <br>Default value: true <br>If this parameter is set to true but the system hardware does not support the vibration function, no vibration feedback is generated. |

<a id="enablehapticfeedback-1"></a>

## enableHapticFeedback

```TypeScript
enableHapticFeedback(enable: Optional<boolean>)
```

Sets whether to enable haptic feedback. Compared with [enableHapticFeedback&lt;sup&gt;12+&lt;/sup&gt;](#enablehapticfeedback), the enable parameter additionally supports the undefined type.

To enable haptic feedback, you must declare the following permission under **requestPermissions** in **module** in **src/main/module.json5** of the project.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TimePickerAttribute-enableHapticFeedback(enable: Optional<boolean>): TimePickerAttribute--><!--Device-TimePickerAttribute-enableHapticFeedback(enable: Optional<boolean>): TimePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable haptic feedback.<br>- true: haptic feedback is enabled. <br>- false: haptic feedback is disabled. <br>Default value: true <br>When the value of enable is undefined, the default value is used. <br>If the value is set to true but the system hardware does not support vibration, no vibration feedback is generated. |

## loop

```TypeScript
loop(value: boolean)
```

Sets whether to enable loop mode. Loop mode is suitable for scenarios where the time needs to be selected through continuous scrolling, while non-loop mode is suitable for scenarios with a fixed time range restriction.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TimePickerAttribute-loop(value: boolean): TimePickerAttribute--><!--Device-TimePickerAttribute-loop(value: boolean): TimePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to enable loop mode.<br>- true: loop mode is enabled. <br>- false: loop mode is disabled. <br>Default value: true <br>**Note:** When start or end is set to a non-default value, loop does not take effect. |

<a id="loop-1"></a>

## loop

```TypeScript
loop(isLoop: Optional<boolean>)
```

Sets whether to enable loop scrolling. Compared with [loop&lt;sup&gt;11+&lt;/sup&gt;](#loop), this API supports the **undefined** type for the **isLoop** parameter.

> **NOTE:** 
> 
> When **start** or **end** is set to a non-default value, **loop** does not take effect.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TimePickerAttribute-loop(isLoop: Optional<boolean>): TimePickerAttribute--><!--Device-TimePickerAttribute-loop(isLoop: Optional<boolean>): TimePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isLoop | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable loop mode.<br>- true: enable loop mode. <br>- false: disable loop mode. <br>Default value: true <br>When the value of isLoop is undefined, the default value is used. |

## onChange

```TypeScript
onChange(callback: (value: TimePickerResult) => void)
```

Triggered when the time option returns to the selected item position after the TimePicker is scrolled. It cannot be triggered by the state variable of two-way binding. It applies to scenarios where operations such as saving and updating the UI need to be performed after the user confirms the time selection.

The callback is triggered after the scroll animation ends. If you need to obtain index changes quickly, use the [onEnterSelectedArea](#onenterselectedarea) API instead. Note that when [enableCascade](#enablecascade) is set to true, because the AM/PM column and the hour column are linked, the behavior of this callback may not meet expectations, and it is not recommended to use it in this scenario.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TimePickerAttribute-onChange(callback: (value: TimePickerResult) => void): TimePickerAttribute--><!--Device-TimePickerAttribute-onChange(callback: (value: TimePickerResult) => void): TimePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (value: TimePickerResult) =&gt; void | Yes | Time in 24-hour format. |

<a id="onchange-1"></a>

## onChange

```TypeScript
onChange(callback: Optional<OnTimePickerChangeCallback>)
```

Triggered when the time picker snaps to the selected item. This event cannot be triggered by two-way bound state variables. Compared with [onChange](#onchange), this API supports the **undefined** type for the **callback** parameter.

The callback is triggered after the scroll animation ends. If you need to obtain index changes quickly, use the [onEnterSelectedArea](#onenterselectedarea) API instead. Note that when [enableCascade](#enablecascade) is set to true, because the AM/PM column and the hour column are linked, the behavior of this callback may not meet expectations, and it is not recommended to use it in this scenario.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TimePickerAttribute-onChange(callback: Optional<OnTimePickerChangeCallback>): TimePickerAttribute--><!--Device-TimePickerAttribute-onChange(callback: Optional<OnTimePickerChangeCallback>): TimePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[OnTimePickerChangeCallback](arkts-arkui-timepicker-comp-ontimepickerchangecallback-t.md)&gt; | Yes | Callback invoked when the time is selected.<br>When the value of callback is undefined, the callback is not used. |

## onEnterSelectedArea

```TypeScript
onEnterSelectedArea(callback: Callback<TimePickerResult>)
```

Triggered when an option enters the divider area during the scrolling of the TimePicker. It applies to scenarios that require a quick response, such as updating the UI in real time and validating the time range in real time during scrolling. Compared with onChange, this callback is triggered earlier and is suitable for scenarios that require immediate feedback.

The difference from the [onChange](#onchange) event is that this event is triggered earlier than the [onChange](#onchange) event. When the scroll distance of the scrolled column exceeds half the height of the selected item, the option has already entered the divider area, and this event is triggered. When [enableCascade](#enablecascade) is set to true, because the AM/PM column and the hour column are linked (that is, the AM/PM indicator is automatically adjusted based on the hour value), it is not recommended to use this callback. This callback marks the point at which the option enters the divider area during scrolling, while the options changed by the linkage do not involve scrolling. Therefore, in the return value of the callback, only the value of the currently scrolled column changes normally, and the values of the other unscrolled columns remain unchanged.

> **NOTE:** 
> 
> This API cannot be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TimePickerAttribute-onEnterSelectedArea(callback: Callback<TimePickerResult>): TimePickerAttribute--><!--Device-TimePickerAttribute-onEnterSelectedArea(callback: Callback<TimePickerResult>): TimePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[TimePickerResult](arkts-arkui-timepicker-comp-timepickerresult-i.md)&gt; | Yes | Callback triggered during the scrolling of the time picker when an item enters the divider area. |

## selectedTextStyle

```TypeScript
selectedTextStyle(value: PickerTextStyle)
```

Sets the text color, font size, and font weight of the selected item.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TimePickerAttribute-selectedTextStyle(value: PickerTextStyle): TimePickerAttribute--><!--Device-TimePickerAttribute-selectedTextStyle(value: PickerTextStyle): TimePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md) | Yes | Text color, font size, and font weight of the selected item.<br>Default value: <br>{<br>color: '#ff007dff', <br>font: {<br>size: '20fp', <br>weight: FontWeight.Medium <br>} <br>} |

<a id="selectedtextstyle-1"></a>

## selectedTextStyle

```TypeScript
selectedTextStyle(style: Optional<PickerTextStyle>)
```

Sets the text color, font size, and font weight of the selected item. Compared with [selectedTextStyle&lt;sup&gt;10+&lt;/sup&gt;](#selectedtextstyle), the **style** parameter additionally supports the **undefined** type.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TimePickerAttribute-selectedTextStyle(style: Optional<PickerTextStyle>): TimePickerAttribute--><!--Device-TimePickerAttribute-selectedTextStyle(style: Optional<PickerTextStyle>): TimePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md)&gt; | Yes | Text color, font size, and font weight of the selected item.<br>Default value: <br>{<br>color: '#ff007dff', <br>font: {<br>size: '20fp', <br>weight: FontWeight.Medium <br>} <br>} <br>When the value of style is undefined, the default value is used. |

## textStyle

```TypeScript
textStyle(value: PickerTextStyle)
```

Sets the text color, font size, and font weight of candidate items (the item immediately adjacent to the selected item, above or below).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TimePickerAttribute-textStyle(value: PickerTextStyle): TimePickerAttribute--><!--Device-TimePickerAttribute-textStyle(value: PickerTextStyle): TimePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md) | Yes | Text color, font size, and font weight of the options.<br>Default value: <br>{<br>color: '#ff182431', <br>font: {<br>size: '16fp', <br>weight: FontWeight.Regular <br>} <br>} |

<a id="textstyle-1"></a>

## textStyle

```TypeScript
textStyle(style: Optional<PickerTextStyle>)
```

Sets the text color, font size, and font weight of candidate items (the item immediately adjacent to the selected item, above or below). Compared with [textStyle&lt;sup&gt;10+&lt;/sup&gt;](#textstyle), this API supports the **undefined** type for the **style** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TimePickerAttribute-textStyle(style: Optional<PickerTextStyle>): TimePickerAttribute--><!--Device-TimePickerAttribute-textStyle(style: Optional<PickerTextStyle>): TimePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md)&gt; | Yes | Text color, font size, and font weight of the options.<br>Default value: <br>{<br>color: '#ff182431', <br>font: {<br>size: '16fp', <br>weight: FontWeight.Regular <br>} <br>} <br>When the value of style is undefined, the default value is used. |

## useMilitaryTime

```TypeScript
useMilitaryTime(value: boolean)
```

Sets whether the time is displayed in 24-hour format. If this API is not used, the system time format is used by default. The 24-hour format is suitable for precise time recording and scheduling scenarios, while the 12-hour format is suitable for more intuitive time display requirements such as daily alarm setting.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TimePickerAttribute-useMilitaryTime(value: boolean): TimePickerAttribute--><!--Device-TimePickerAttribute-useMilitaryTime(value: boolean): TimePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the time is displayed in 24-hour format.<br>- true: The time is displayed in 24-hour format. <br>- false: The time is displayed in 12-hour format. |

<a id="usemilitarytime-1"></a>

## useMilitaryTime

```TypeScript
useMilitaryTime(isMilitaryTime: Optional<boolean>)
```

Sets whether the time is displayed in 24-hour format. If this attribute is not specified, the system time format is used by default. Compared with [useMilitaryTime](#usemilitarytime), this API supports the **undefined** type for the **isMilitaryTime** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TimePickerAttribute-useMilitaryTime(isMilitaryTime: Optional<boolean>): TimePickerAttribute--><!--Device-TimePickerAttribute-useMilitaryTime(isMilitaryTime: Optional<boolean>): TimePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isMilitaryTime | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether the displayed time is in 24-hour format.<br>- true: The displayed time is in 24-hour format. <br>- false: The displayed time is in 12-hour format. <br>When the value of isMilitaryTime is undefined, the system setting is followed. |
