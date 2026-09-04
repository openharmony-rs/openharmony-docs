# TimePicker
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @luoying_ace_admin-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=c0ac8fcc98a238d8876502f1ec9d63a5c16c2a67 translatedAt=2026-09-03T12:49:54.145Z -->

**TimePicker** is a component for selecting a time by sliding. It supports 12/24-hour formats, multiple time formats (hour/minute/second), loop scrolling, style customization, and time range restrictions. It is suitable for scenarios where users need to select a time, such as schedule arrangement, time reservation, and task management. It improves user experience, reduces input errors, and can be quickly integrated into applications.

>  **NOTE**
>
> - This component is supported since API version 8. New APIs added in later versions are marked with a superscript to indicate their earliest API version.
>
> - It is not recommended to modify attribute data of this component during animation.
>
> - The maximum number of displayed rows differs between landscape and portrait modes. In portrait mode, the default is 5 rows. In landscape mode, it depends on the system configuration, and the default is 3 rows when not configured. You can use the following parameter to view the specific configuration value: $r('sys.float.ohos_id_picker_show_count_landscape').


## Child Components

This is a basic component, and it is not recommended to include child components.


## APIs

TimePicker(options?: TimePickerOptions)

Creates a sliding picker, which uses a 24-hour time range by default. It is suitable for scenarios where a time needs to be selected, such as schedule arrangement, alarm setting, and time recording.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                           | Mandatory| Description                    |
| ------- | ----------------------------------------------- | ---- | ------------------------ |
| options | [TimePickerOptions](#timepickeroptions) | No   | Parameters for configuring the TimePicker component. Pass this parameter when you need to customize the initial selected time, time format, time range, and other configurations. If this parameter is not passed, the default configuration is used (the initial selected time is the current system time, the time format is hour and minute by default, and the time range is 00:00-23:59 by default, with the default end time being 23:59:59). |

## TimePickerOptions

Describes the parameters of the time picker.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                | Type                                           | Read Only| Optional| Description                                                        |
| -------------------- | ----------------------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| selected             | Date                                            | No   | Yes   | Sets the time of the selected item.<br>Default value: current system time<br>Since API version 10, this parameter supports [$$](../../../ui/state-management/arkts-two-way-sync.md) two-way binding variables.<br>**Atomic service API:** Since API version 11, this API is supported in atomic services. |
| format<sup>11+</sup> | [TimePickerFormat](#timepickerformat11) | No   | Yes   | Specifies the format of the TimePicker to be displayed.<br>Default value: TimePickerFormat.HOUR_MINUTE <br>**Atomic service API:** Since API version 12, this API is supported in atomic services.<br>**Model restriction:** This API can be used only in the stage model. |
| start<sup>18+</sup>  | Date                                            | No   | Yes   | Specifies the start time of the TimePicker component.<br>Default value: the start time is 00:00:00 (hour = 0, minute = 0)<br>**Note:**<br>1. Only the set hour and minute take effect.<br>2. When start or end is set to a non-default value, loop does not take effect. <br>**Atomic service API:** Since API version 18, this API is supported in atomic services.<br>**Model restriction:** This API can be used only in the stage model. |
| end<sup>18+</sup>    | Date                                            | No   | Yes   | Specifies the end time of the TimePicker component.<br>Default value: the end time is 23:59:59 (hour = 23, minute = 59)<br>**Note:**<br>1. Only the set hour and minute take effect.<br>2. When start or end is set to a non-default value, loop does not take effect. <br>**Atomic service API:** Since API version 18, this API is supported in atomic services.<br>**Model restriction:** This API can be used only in the stage model. |

Property modifications made to **TimePickerOptions** during the **TimePicker** scrolling process may not take effect.

The **Date** object is used to handle dates and time. It can be used in the following ways:

**Method 1**: new Date()

Obtains the current system date and time.

**Method 2**: new Date(value: number | string)

| Name  | Type  | Mandatory| Description  |
| ------- | ------ | ---- | ------ |
| value   | number&nbsp;\|&nbsp;string  | Yes | Sets the date format.<br>number: milliseconds, the number of milliseconds elapsed since 00:00:00 on January 1, 1970. Value range: [0, +∞).<br>string: a string in time format, for example, '2025-02-20 08:00:00' or '2025-02-20T08:00:00'. |

**Method 3**: new Date(year: number, monthIndex: number, date?: number, hours?: number, minutes?: number, seconds?: number, ms?: number)

| Name  | Type  | Mandatory| Description  |
| --------| ------ | ---- | ------ |
| year        | number | Yes  | Year, for example, **2025**.|
| monthIndex  | number | Yes   | Month index (value range: 0 to 11), where 0 indicates January and 11 indicates December. For example, 0 indicates January and 2 indicates March. A value out of range causes a date calculation error.|
| date        | number | No  | Date, for example, **10** (if **hours** is set, **date** cannot be omitted).|
| hours       | number | No   | Hour (value range: [0, 23]). A value out of range causes a date calculation error. For example, 15 (if minutes is set, hours cannot be omitted). Unit: hour.|
| minutes     | number | No   | Minute (value range: [0, 59]). A value out of range causes a date calculation error. For example, 20 (if seconds is set, minutes cannot be omitted). Unit: minute.|
| seconds     | number | No   | Second (value range: [0, 59]). A value out of range causes a date calculation error. For example, 20 (if ms is set, seconds cannot be omitted). Unit: second.|
| ms          | number | No   | Millisecond (value range: [0, 999]). A value out of range causes a date calculation error. For example, 10. Unit: ms (millisecond).|

**Handling in the case of date configuration exceptions**

| Exception  | Result |
| -------- |  ------------------------------------------------------------ |
| The start time is later than the end time.   | Both start time and end time are set to their default values. |
| The selected time is earlier than the start time.  | The selected time is set to the start time. |
| The selected time is later than the end time.   | The selected time is set to the end time. |
| The start time is later than the current system time, and the selected time is not set.   | The selected time is set to the start time.|
| The end time is earlier than the current system time, and the selected time is not set.   | The selected time is set to the end time. |
| The time format is invalid, such as **'01:61:61'**.  | The default value is used. |

## TimePickerFormat<sup>11+</sup>

Enumerates time display formats of the time picker.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name              | Value| Description                    |
| ------------------ | - | ------------------------ |
| HOUR_MINUTE        | 0 | Time format displaying hours and minutes.      |
| HOUR_MINUTE_SECOND | 1 | Time format displaying hours, minutes, and seconds.|

## Attributes

In addition to the [universal attributes](ts-component-general-attributes.md), the following attributes are supported.

### useMilitaryTime

useMilitaryTime(value: boolean)

Sets whether the time is displayed in 24-hour format. If this API is not used, the system time format is used by default. The 24-hour format is suitable for precise time recording and scheduling scenarios, while the 12-hour format is suitable for more intuitive time display requirements such as daily alarm setting.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                      |
| ------ | ------- | ---- | ------------------------------------------ |
| value | boolean | Yes | Whether the time is displayed in 24-hour format.<br>- true: The time is displayed in 24-hour format.<br>- false: The time is displayed in 12-hour format. |

### useMilitaryTime<sup>18+</sup>

useMilitaryTime(isMilitaryTime: Optional\<boolean>)

Sets whether the time is displayed in 24-hour format. If this attribute is not specified, the system time format is used by default. Compared with [useMilitaryTime](#usemilitarytime), this API supports the **undefined** type for the **isMilitaryTime** parameter.

**Atomic service API**: This API can be used in atomic services since API version 18.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                      |
| ------ | ------- | ---- | ------------------------------------------ |
| isMilitaryTime | [Optional](ts-universal-attributes-custom-property.md#optionalt)\<boolean> | Yes | Whether the displayed time is in 24-hour format.<br>- true: The displayed time is in 24-hour format.<br>- false: The displayed time is in 12-hour format.<br>When the value of isMilitaryTime is undefined, the system setting is followed.|

### disappearTextStyle<sup>10+</sup>

disappearTextStyle(value: PickerTextStyle)

Sets the text color, font size, and font weight of edge items (the second item above or below the selected item).

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | [PickerTextStyle](ts-picker-common.md#pickertextstyle) | Yes   | Text color, font size, and font weight of the edge items (the second item above or below the selected item).<br>Default value:<br>{<br>color: '#ff182431',<br>font: {<br>size: '14fp', <br>weight: FontWeight.Regular<br>}<br>} |

>  **NOTE**
>
> Edge items only appear when there are at least two visible items above or below the selected item. If insufficient items are available, no edge items will be styled.

### disappearTextStyle<sup>18+</sup>

disappearTextStyle(style: Optional\<PickerTextStyle>)

Sets the text color, font size, and font weight of edge items (the second item above or below the selected item). Compared with [disappearTextStyle<sup>10+</sup>](#disappeartextstyle10), this API supports the **undefined** type for the **style** parameter.

**Atomic service API**: This API can be used in atomic services since API version 18.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| style  | [Optional](ts-universal-attributes-custom-property.md#optionalt)\<[PickerTextStyle](ts-picker-common.md#pickertextstyle)> | Yes   | Text color, font size, and font weight of the edge items.<br>Default value:<br>{<br>color: '#ff182431',<br>font: {<br>size: '14fp', <br>weight: FontWeight.Regular<br>}<br>}<br>When the value of style is undefined, the default value is used. |

>  **NOTE**
>
> Edge items only appear when there are at least two visible items above or below the selected item. If insufficient items are available, no edge items will be styled.

### textStyle<sup>10+</sup>

textStyle(value: PickerTextStyle)

Sets the text color, font size, and font weight of candidate items (the item immediately adjacent to the selected item, above or below).

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | [PickerTextStyle](ts-picker-common.md#pickertextstyle) | Yes   | Text color, font size, and font weight of the options.<br>Default value:<br>{<br>color: '#ff182431',<br>font: {<br>size: '16fp', <br>weight: FontWeight.Regular<br>}<br>} |

>  **NOTE**
>
> Candidate items only appear when there is at least one visible item above or below the selected item. If insufficient items are available, no candidate items will be styled.

### textStyle<sup>18+</sup>

textStyle(style: Optional\<PickerTextStyle>)

Sets the text color, font size, and font weight of candidate items (the item immediately adjacent to the selected item, above or below). Compared with [textStyle<sup>10+</sup>](#textstyle10), this API supports the **undefined** type for the **style** parameter.

**Atomic service API**: This API can be used in atomic services since API version 18.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| style  | [Optional](ts-universal-attributes-custom-property.md#optionalt)\<[PickerTextStyle](ts-picker-common.md#pickertextstyle)> | Yes   | Text color, font size, and font weight of the options.<br>Default value:<br>{<br>color: '#ff182431',<br>font: {<br>size: '16fp', <br>weight: FontWeight.Regular<br>}<br>}<br>When the value of style is undefined, the default value is used. |

>  **NOTE**
>
> Candidate items only appear when there is at least one visible item above or below the selected item. If insufficient items are available, no candidate items will be styled.

### selectedTextStyle<sup>10+</sup>

selectedTextStyle(value: PickerTextStyle)

Sets the text color, font size, and font weight of the selected item.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | [PickerTextStyle](ts-picker-common.md#pickertextstyle) | Yes   | Text color, font size, and font weight of the selected item.<br>Default value:<br>{<br>color: '#ff007dff',<br>font: {<br>size: '20fp', <br>weight: FontWeight.Medium<br>}<br>} |

### selectedTextStyle<sup>18+</sup>

selectedTextStyle(style: Optional\<PickerTextStyle>)

Sets the text color, font size, and font weight of the selected item. Compared with [selectedTextStyle<sup>10+</sup>](#selectedtextstyle10), the **style** parameter additionally supports the **undefined** type.

**Atomic service API**: This API can be used in atomic services since API version 18.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| style  | [Optional](ts-universal-attributes-custom-property.md#optionalt)\<[PickerTextStyle](ts-picker-common.md#pickertextstyle)> | Yes   | Text color, font size, and font weight of the selected item.<br>Default value:<br>{<br>color: '#ff007dff',<br>font: {<br>size: '20fp', <br>weight: FontWeight.Medium<br>}<br>}<br>When the value of style is undefined, the default value is used. |

### loop<sup>11+</sup>

loop(value: boolean)

Sets whether to enable loop mode. Loop mode is suitable for scenarios where the time needs to be selected through continuous scrolling, while non-loop mode is suitable for scenarios with a fixed time range restriction.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                                        |
| ------ | ------- | ---- | ------------------------------------------------------------ |
| value  | boolean | Yes  | Whether to enable loop mode.<br>- true: loop mode is enabled.<br>- false: loop mode is disabled.<br>Default value: true<br>**Note:** When start or end is set to a non-default value, loop does not take effect. |

### loop<sup>18+</sup>

loop(isLoop: Optional\<boolean>)

Sets whether to enable loop scrolling. Compared with [loop<sup>11+</sup>](#loop11), this API supports the **undefined** type for the **isLoop** parameter.

>  **NOTE**
>
> When **start** or **end** is set to a non-default value, **loop** does not take effect.

**Atomic service API**: This API can be used in atomic services since API version 18.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                                        |
| ------ | ------- | ---- | ------------------------------------------------------------ |
| isLoop  | [Optional](ts-universal-attributes-custom-property.md#optionalt)\<boolean> | Yes   | Whether to enable loop mode.<br>- true: enable loop mode.<br>- false: disable loop mode.<br>Default value: true<br>When the value of isLoop is undefined, the default value is used. |

### dateTimeOptions<sup>12+</sup>

dateTimeOptions(value: DateTimeOptions)

Sets whether to display a leading zero for the hour, minute, and second. '2-digit' is suitable for scenarios where a unified format is required (such as tables and reports), while 'numeric' is suitable for more concise display requirements.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                     | Mandatory| Description                                                        |
| ------ | ----------------------------------------- | ---- | ------------------------------------------------------------ |
| value  | [DateTimeOptions](#datetimeoptions12) | Yes   | Sets whether to display leading zeros for the hour, minute, and second.<br>Default value:<br>hour: The default value is "2-digit" in the 24-hour format, which sets whether the hour is displayed as a 2-digit number. If the actual value is less than 10, a leading zero is added and displayed, that is, "0X". The default value is "numeric" in the 12-hour format, that is, no leading zero.<br>minute: The default value is "2-digit", which sets whether the minute is displayed as a 2-digit number. If the actual value is less than 10, a leading zero is added and displayed, that is, "0X".<br>second: The default value is "2-digit", which sets whether the second is displayed as a 2-digit number. If the actual value is less than 10, a leading zero is added and displayed, that is, "0X".<br> When the values of hour, minute, and second are set to undefined, the display effect follows the same rules as their default values.|

### dateTimeOptions<sup>18+</sup>

dateTimeOptions(timeFormat: Optional\<DateTimeOptions>)

Sets whether to display a leading zero for the hours, minutes, and seconds. Compared with [dateTimeOptions<sup>12+</sup>](#datetimeoptions12), this API supports the **undefined** type for the **timeFormat** parameter.

**Atomic service API**: This API can be used in atomic services since API version 18.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| timeFormat  | [Optional](ts-universal-attributes-custom-property.md#optionalt)\<[DateTimeOptions](#datetimeoptions12)> | Yes   | Sets whether the hour, minute, and second are displayed with a leading zero. Currently, only the hour, minute, and second parameters are supported.<br>Default value:<br>hour: The default value is "2-digit" in the 24-hour format. Sets whether the hour is displayed as a 2-digit number. If the actual value is less than 10, a leading zero is added and displayed, that is, "0X". The default value is "numeric" in the 12-hour format, that is, no leading zero.<br>minute: The default value is "2-digit". Sets whether the minute is displayed as a 2-digit number. If the actual value is less than 10, a leading zero is added and displayed, that is, "0X".<br>second: The default value is "2-digit". Sets whether the second is displayed as a 2-digit number. If the actual value is less than 10, a leading zero is added and displayed, that is, "0X".<br> When the values of hour, minute, and second are set to undefined, the display effect follows the same rules as their default values.|

### enableHapticFeedback<sup>12+</sup>

enableHapticFeedback(enable: boolean)

Sets whether to enable haptic feedback.

To enable haptic feedback, you must declare the following permission under **requestPermissions** in **module** in **src/main/module.json5** of the project.

``` json
"requestPermissions": [
   {
      "name": "ohos.permission.VIBRATE"
   }
]
```

>**NOTE**
>
> This API can be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier) since API version 18.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                         | Mandatory | Description                                                                                 |
| ------ | --------------------------------------------- | ----- |-------------------------------------------------------------------------------------|
| enable  | boolean | Yes   | Whether to enable haptic feedback.<br>- true: Enable haptic feedback.<br>- false: Disable haptic feedback.<br>Default value: true<br>If this parameter is set to true but the system hardware does not support the vibration function, no vibration feedback is generated. |

### enableHapticFeedback<sup>18+</sup>

enableHapticFeedback(enable: Optional\<boolean>)

Sets whether to enable haptic feedback. Compared with [enableHapticFeedback<sup>12+</sup>](#enablehapticfeedback12), the enable parameter additionally supports the undefined type.

To enable haptic feedback, you must declare the following permission under **requestPermissions** in **module** in **src/main/module.json5** of the project.

``` json
"requestPermissions": [
  {
    "name": "ohos.permission.VIBRATE"
  }
]
```

**Atomic service API**: This API can be used in atomic services since API version 18.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                         | Mandatory | Description                                                                                 |
| ------ | --------------------------------------------- |-----|-------------------------------------------------------------------------------------|
| enable  | [Optional](ts-universal-attributes-custom-property.md#optionalt)\<boolean> | Yes   | Whether to enable haptic feedback.<br>- true: haptic feedback is enabled.<br>- false: haptic feedback is disabled.<br>Default value: true<br>When the value of enable is undefined, the default value is used.<br>If the value is set to true but the system hardware does not support vibration, no vibration feedback is generated. |

### enableCascade<sup>18+</sup>

enableCascade(enabled: boolean)

Sets whether the AM/PM indicator automatically switches based on the hour value. This takes effect only when [useMilitaryTime](#usemilitarytime) is set to false. Automatic switching applies to daily consumer scenarios such as alarms and schedules that emphasize operation efficiency and a smooth experience, while manual switching applies to scenarios such as healthcare and legal affairs that demand strict time precision and tolerate no ambiguity.

**Atomic service API**: This API can be used in atomic services since API version 18.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                         | Mandatory | Description                                                                                 |
| ------ | --------------------------------------------- |-----|-------------------------------------------------------------------------------------|
| enabled | boolean | Yes | Whether the AM/PM indicator automatically switches based on the hour. This parameter takes effect only when useMilitaryTime is set to false.<br>- true: automatically switches. When enabled is set to true, it takes effect only when the loop parameter is also set to true.<br>- false: does not automatically switch. The AM/PM indicator must be selected manually and is not automatically adjusted based on the hour.<br>Default value: false |

> **NOTE**
>
> **Constraints:**
>
> - If the loop parameter is false or is not set to true, enableCascade(true) does not take effect, and the AM/PM indicator does not switch automatically.
> - loop(true) must be set to enable the automatic switching feature.
> - When a non-default start/end is set, the automatic switching of enableCascade also does not take effect.
> - There is a dependency on useMilitaryTime: enableCascade takes effect only when useMilitaryTime is false (12-hour format).

### digitalCrownSensitivity<sup>18+</sup>
digitalCrownSensitivity(sensitivity: Optional\<CrownSensitivity>)

Sets the crown sensitivity. High sensitivity applies to scenarios where the time needs to be adjusted quickly, and low sensitivity applies to scenarios where the time needs to be adjusted precisely.

**Atomic service API**: This API can be used in atomic services since API version 18.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                    | Mandatory  | Description                     |
| ----- | ---------------------------------------- | ---- | ------------------------- |
| sensitivity | [Optional](ts-universal-attributes-custom-property.md#optionalt)\<[CrownSensitivity](ts-appendix-enums.md#crownsensitivity18)> | Yes    | Crown response sensitivity.<br>Default value: CrownSensitivity.MEDIUM, indicating a moderate response speed.                    |

>  **NOTE**
>
>  This API is used for circular screens on wearables. The component needs to obtain focus before responding to the [crown event](ts-universal-events-crown.md).

## Events

In addition to the [universal events](ts-component-general-events.md), the following events are supported.

### onChange

onChange(callback:&nbsp;(value:&nbsp;TimePickerResult )&nbsp;=&gt;&nbsp;void)

Triggered when the time option returns to the selected item position after the TimePicker is scrolled. It cannot be triggered by the state variable of two-way binding. It applies to scenarios where operations such as saving and updating the UI need to be performed after the user confirms the time selection.

The callback is triggered after the scroll animation ends. If you need to obtain index changes quickly, use the [onEnterSelectedArea](#onenterselectedarea18) API instead. Note that when [enableCascade](#enablecascade18) is set to true, because the AM/PM column and the hour column are linked, the behavior of this callback may not meet expectations, and it is not recommended to use it in this scenario.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                         | Mandatory| Description          |
| ------ | --------------------------------------------- | ---- | -------------- |
| value  | [TimePickerResult](#timepickerresult) | Yes   | Selected time result. The value of hour ranges from 0 to 23, regardless of the display format. |

### onChange<sup>18+</sup>

onChange(callback: Optional\<OnTimePickerChangeCallback>)

Triggered when the time picker snaps to the selected item. This event cannot be triggered by two-way bound state variables. Compared with [onChange](#onchange), this API supports the **undefined** type for the **callback** parameter.

The callback is triggered after the scroll animation ends. If you need to obtain index changes quickly, use the [onEnterSelectedArea](#onenterselectedarea18) API instead. Note that when [enableCascade](#enablecascade18) is set to true, because the AM/PM column and the hour column are linked, the behavior of this callback may not meet expectations, and it is not recommended to use it in this scenario.

**Atomic service API**: This API can be used in atomic services since API version 18.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | [Optional](ts-universal-attributes-custom-property.md#optionalt)\<[OnTimePickerChangeCallback](#ontimepickerchangecallback18)> | Yes | Callback invoked when the time is selected.<br>When the value of callback is undefined, the callback is not used. |

### onEnterSelectedArea<sup>18+</sup>

onEnterSelectedArea(callback: Callback\<TimePickerResult>)

Triggered when an option enters the divider area during the scrolling of the TimePicker. It applies to scenarios that require a quick response, such as updating the UI in real time and validating the time range in real time during scrolling. Compared with onChange, this callback is triggered earlier and is suitable for scenarios that require immediate feedback.

The difference from the [onChange](#onchange) event is that this event is triggered earlier than the [onChange](#onchange) event. When the scroll distance of the scrolled column exceeds half the height of the selected item, the option has already entered the divider area, and this event is triggered. When [enableCascade](#enablecascade18) is set to true, because the AM/PM column and the hour column are linked (that is, the AM/PM indicator is automatically adjusted based on the hour value), it is not recommended to use this callback. This callback marks the point at which the option enters the divider area during scrolling, while the options changed by the linkage do not involve scrolling. Therefore, in the return value of the callback, only the value of the currently scrolled column changes normally, and the values of the other unscrolled columns remain unchanged.

> **NOTE**
>
> This API cannot be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier).

**Atomic service API**: This API can be used in atomic services since API version 18.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                      | Mandatory| Description                                      |
| -------- | -------------------------- | ---- | ------------------------------------------ |
| callback | Callback\<[TimePickerResult](#timepickerresult)> | Yes  | Callback triggered during the scrolling of the time picker when an item enters the divider area.|

## DateTimeOptions<sup>12+</sup>

type DateTimeOptions = import('../api/@ohos.intl').default.DateTimeOptions

Defines the options for a **DateTimeOptions** object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type                                                        | Description                                      |
| ------------------------------------------------------------ | ------------------------------------------ |
| import('../api/@ohos.intl').default.[DateTimeOptions](../../apis-localization-kit/js-apis-intl.md#datetimeoptionsdeprecated) | Configuration options that can be set when creating a time and date formatting object. |

## OnTimePickerChangeCallback<sup>18+</sup>

type OnTimePickerChangeCallback = (result: TimePickerResult) => void

Triggered when a time is selected.

**Atomic service API**: This API can be used in atomic services since API version 18.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                         | Mandatory| Description          |
| ------ | --------------------------------------------- | ---- | -------------- |
| result | [TimePickerResult](#timepickerresult) | Yes | Selected time result. The value of hour ranges from 0 to 23, regardless of the display format. |

## TimePickerResult

Returns the selected time result, where hour ranges from 0 to 23, regardless of the display format.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                | Type  | Read Only| Optional| Description                               |
| -------------------- | ------ | ---- | ---- | ----------------------------------- |
| hour                 | number | No   | No   | Hour of the selected time.<br>Value range: [0-23], independent of the display format. |
| minute               | number | No   | No   | Minute of the selected time.<br>Value range: [0-59] |
| second<sup>11+</sup> | number | No   | No   | Second of the selected time.<br>Value range: [0-59]<br>**Model restriction:** This API can be used only in the stage model. |

## Example

### Example 1: Setting the Text Style

This example demonstrates how to customize the text style in a time picker using [disappearTextStyle](#disappeartextstyle10), [textStyle](#textstyle10), and [selectedTextStyle](#selectedtextstyle10).

```ts
// xxx.ets
@Entry
@Component
struct TimePickerExample {
  private selectedTime: Date = new Date('2022-07-22T08:00:00');

  build() {
    TimePicker({
      selected: this.selectedTime
    })
      .disappearTextStyle({ color: '#004aaf', font: { size: 24, weight: FontWeight.Lighter } })
      .textStyle({ color: Color.Black, font: { size: 26, weight: FontWeight.Normal } })
      .selectedTextStyle({ color: Color.Blue, font: { size: 30, weight: FontWeight.Bolder } })
      .onChange((value: TimePickerResult) => {
        if (value.hour >= 0) {
          this.selectedTime.setHours(value.hour, value.minute);
          console.info('select current time is: ' + JSON.stringify(value));
        }
      })
  }
}
```

![timePicker](figures/TimePickerDemo1.png)

### Example 2: Switching Between 12-Hour and 24-Hour Formats

This example demonstrates how to switch between 12-hour and 24-hour formats using **useMilitaryTime**.

```ts
// xxx.ets
@Entry
@Component
struct TimePickerExample {
  @State isMilitaryTime: boolean = false;
  private selectedTime: Date = new Date('2022-07-22T08:00:00');

  build() {
    Column() {
      Button('Switch Time Format')
        .margin(30)
        .onClick(() => {
          this.isMilitaryTime = !this.isMilitaryTime;
        })

      TimePicker({
        selected: this.selectedTime
      })
        .useMilitaryTime(this.isMilitaryTime)
        .onChange((value: TimePickerResult) => {
          if (value.hour >= 0) {
            this.selectedTime.setHours(value.hour, value.minute);
            console.info('select current time is: ' + JSON.stringify(value));
          }
        })
        .onEnterSelectedArea((value: TimePickerResult) => {
            console.info('item enter selected area, time is: ' + JSON.stringify(value));
        })
    }.width('100%')
  }
}
```

![timePicker](figures/TimePickerDemo2.gif)

### Example 3: Setting the Time Format

This example shows how to set the time format using **format** and **dateTimeOptions**.

```ts
// xxx.ets
@Entry
@Component
struct TimePickerExample {
  private selectedTime: Date = new Date('2022-07-22T08:00:00');

  build() {
    Column() {
      TimePicker({
        selected: this.selectedTime,
        format: TimePickerFormat.HOUR_MINUTE_SECOND
      })
        .dateTimeOptions({ hour: "numeric", minute: "2-digit", second: "2-digit" })
        .onChange((value: TimePickerResult) => {
          if (value.hour >= 0) {
            this.selectedTime.setHours(value.hour, value.minute, value.second);
            console.info('select current time is: ' + JSON.stringify(value));
          }
        })
    }.width('100%')
  }
}
```

![timePicker](figures/TimePickerDemo3.gif)

### Example 4: Setting Loop Scrolling

This example demonstrates how to set whether to enable loop scrolling using [loop](#loop11).

```ts
// xxx.ets
@Entry
@Component
struct TimePickerExample {
  @State isLoop: boolean = true;
  @State selectedTime: Date = new Date('2022-07-22T12:00:00');

  build() {
    Column() {
      TimePicker({
        selected: this.selectedTime
      })
        .loop(this.isLoop)
        .onChange((value: TimePickerResult) => {
          if (value.hour >= 0) {
            this.selectedTime.setHours(value.hour, value.minute);
            console.info('select current time is: ' + JSON.stringify(value));
          }
        })

      Row() {
        Text('Loopable scrolling').fontSize(20)

        Toggle({ type: ToggleType.Switch, isOn: true })
          .onChange((isOn: boolean) => {
            this.isLoop = isOn;
          })
      }.position({ x: '60%', y: '40%' })

    }.width('100%')
  }
}
```

![timePicker](figures/TimePickerDemo4.gif)

### Example 5: Setting the Start Time

This example demonstrates how to set the start time for the time picker.

```ts
// xxx.ets
@Entry
@Component
struct TimePickerExample {
  private selectedTime: Date = new Date('2022-07-22T08:50:00');

  build() {
    Column() {
      TimePicker({
        selected: this.selectedTime,
        format: TimePickerFormat.HOUR_MINUTE_SECOND,
        start: new Date('2022-07-22T08:30:00')
      })
        .dateTimeOptions({ hour: "numeric", minute: "2-digit", second: "2-digit" })
        .onChange((value: TimePickerResult) => {
          if (value.hour >= 0) {
            this.selectedTime.setHours(value.hour, value.minute);
            console.info('select current time is: ' + JSON.stringify(value));
          }
        })
    }.width('100%')
  }
}
```
![timePicker](figures/TimePickerDemo5.png)

### Example 6: Setting the End Time

This example demonstrates how to set the end time for the time picker.

```ts
// xxx.ets
@Entry
@Component
struct TimePickerExample {
  private selectedTime: Date = new Date('2022-07-22T08:50:00');

  build() {
    Column() {
      TimePicker({
        selected: this.selectedTime,
        format: TimePickerFormat.HOUR_MINUTE_SECOND,
        end: new Date('2022-07-22T15:20:00'),
      })
        .dateTimeOptions({ hour: "numeric", minute: "2-digit", second: "2-digit" })
        .onChange((value: TimePickerResult) => {
          if (value.hour >= 0) {
            this.selectedTime.setHours(value.hour, value.minute, value.second);
            console.info('select current time is: ' + JSON.stringify(value));
          }
        })
    }.width('100%')
  }
}
```

![timePicker](figures/TimePickerDemo6.png)

### Example 7: Setting AM/PM to Follow the Time Linkage

This example uses [enableCascade](#enablecascade18) and [loop](#loop11) to implement the linkage of AM/PM following the time in the 12-hour format.

The **enableCascade** API is added since API version 18.

```ts
// xxx.ets
@Entry
@Component
struct TimePickerExample {
  private selectedTime: Date = new Date('2022-07-22T08:00:00');

  build() {
    Column() {
      TimePicker({
        selected: this.selectedTime,
      })
        .useMilitaryTime(false)
        .enableCascade(true)
        .loop(true)
        .onChange((value: TimePickerResult) => {
          if (value.hour >= 0) {
            this.selectedTime.setHours(value.hour, value.minute);
          console.info('select current time is: ' + JSON.stringify(value));
          }
        })
    }.width('100%')
  }
}
```

![timePicker](figures/TimePickerDemo7.gif)
