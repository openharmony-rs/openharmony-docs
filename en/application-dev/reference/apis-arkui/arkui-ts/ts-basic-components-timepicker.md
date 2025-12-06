# TimePicker
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @luoying_ace_admin-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

**TimePicker** is a component that allows users to select a time from the given range through scrolling.

>  **NOTE**
>
> - This component is supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - Avoid changing component attributes during animation processes.
>
> - The maximum number of rows that can be displayed varies by screen orientation: In portrait mode, the default number of rows is 5. In landscape mode, the number of rows depends on the system configuration. If no system configuration is set, the default is 3 rows. To check the specific system configuration value for landscape mode, use **$r('sys.float.ohos_id_picker_show_count_landscape')**.


## Child Components

Not supported


## APIs

TimePicker(options?: TimePickerOptions)

Creates a time picker, which uses the 24-hour time format by default.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                           | Mandatory| Description                    |
| ------- | ----------------------------------------------- | ---- | ------------------------ |
| options | [TimePickerOptions](#timepickeroptions) | No  | Parameters of the time picker.|

## TimePickerOptions

Describes the parameters of the time picker.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                | Type                                           | Read-Only| Optional| Description                                                        |
| -------------------- | ----------------------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| selected             | Date                                            | No  | Yes  | Time of the selected item.<br>Default value: current system time<br>Since API version 10, this parameter supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md).<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| format<sup>11+</sup> | [TimePickerFormat](#timepickerformat11)| No  | Yes  | Time format.<br>Default value: **TimePickerFormat.HOUR_MINUTE**<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| start<sup>18+</sup>  | Date                                            | No  | Yes  | Start time of the time picker.<br>Default value: **Date(0, 0, 0, 0, 0, 0)**<br>**NOTE**<br>1. Only the hour and minute values take effect.<br>2. If **start** is set and is not the default value, **loop** does not take effect.<br>**Atomic service API**: This API can be used in atomic services since API version 18.|
| end<sup>18+</sup>    | Date                                            | No  | Yes  | End time of the time picker.<br>Default value: **Date(0, 0, 0, 23, 59, 59)**.<br>**NOTE**<br>1. Only the hour and minute values take effect.<br>2. If **end** is set and is not the default value, **loop** does not take effect.<br>**Atomic service API**: This API can be used in atomic services since API version 18.|

>  **NOTE**
>
>  - Property modifications made to **TimePickerOptions** during the **TimePicker** scrolling process may not take effect.
>
>  - The **Date** object is used to handle dates and time. It can be used in the following ways:
>
>  **Method 1**: new Date ()
>
>  Obtains the current system date and time.
>
>  **Method 2**: new Date(value: number | string)
>
>  | Name | Type | Mandatory | Description |
>  | ------- | ------ | ---- | ------ |
>  | value   | number \| string  | Yes | Date format.<br>**number**: number of milliseconds since 00:00:00 on January 1, 1970.<br>**string**: date string in formats such as 2025-02 2025-02-20 08:00:00 or 2025-02 2025-02-20T08:00:00.|
>
>  **Method 3**: new Date(year: number, monthIndex: number, date?: number, hours?: number, minutes?: number, seconds?: number, ms?: number)
>
>  | Name | Type | Mandatory | Description |
>  | --------| ------ | ---- | ------ |
>  | year        | number | Yes   | Year. Example: **2025**.|
>  | monthIndex  | number | Yes   | Month index, for example, **2** for March.|
>  | date        | number | No   | Day of the month, for example, **10**. (Required if **hours** is set.) |
>  | hours       | number | No   | Hour, for example, **15**. (Required if **minutes** is set.) |
>  | minutes     | number | No   | Minute, for example, **20**. (Required if **seconds** is set.) |
>  | seconds     | number | No   | Second, for example, **20**. (Required if **ms** is set.) |
>  | ms          | number | No   | Millisecond, for example, **10**.|

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name              | Value| Description                    |
| ------------------ | - | ------------------------ |
| HOUR_MINUTE        | - | Time format displaying hours and minutes.      |
| HOUR_MINUTE_SECOND | - | Time format displaying hours, minutes, and seconds.|

## Attributes

In addition to the [universal attributes](ts-component-general-attributes.md), the following attributes are supported.

### useMilitaryTime

useMilitaryTime(value: boolean)

Sets whether to display the time in 24-hour format. The 12-hour format is used by default.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                      |
| ------ | ------- | ---- | ------------------------------------------ |
| value  | boolean | Yes  | Whether to display the time in 24-hour format or 12-hour format.<br>- **true**: 24-hour format.<br>- **false**: 12-hour format.<br>Default value: **false**.|

### useMilitaryTime<sup>18+</sup>

useMilitaryTime(isMilitaryTime: Optional\<boolean>)

Sets whether to display the time in 24-hour format. The 12-hour format is used by default. Compared with [useMilitaryTime](#usemilitarytime), this API supports the **undefined** type for the **isMilitaryTime** parameter.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                      |
| ------ | ------- | ---- | ------------------------------------------ |
| isMilitaryTime | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<boolean> | Yes  | Whether to display the time in 24-hour format or 12-hour format.<br>- **true**: 24-hour format.<br>- **false**: 12-hour format.<br>Default value: **false**.<br>If the value of **isMilitaryTime** is **undefined**, the default value is used.|

### disappearTextStyle<sup>10+</sup>

disappearTextStyle(value: PickerTextStyle)

Sets the text color, font size, and font weight of edge items (the second item above or below the selected item).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | [PickerTextStyle](ts-picker-common.md#pickertextstyle) | Yes  | Text color, font size, and font weight for edge items.<br>Default value:<br>{<br>color: '#ff182431',<br>font: {<br>size: '14fp', <br>weight: FontWeight.Regular<br>}<br>} |

>  **NOTE**
>
> Edge items only appear when there are at least two visible items above or below the selected item. If insufficient items are available, no edge items will be styled.

### disappearTextStyle<sup>18+</sup>

disappearTextStyle(style: Optional\<PickerTextStyle>)

Sets the text color, font size, and font weight of edge items (the second item above or below the selected item). Compared with [disappearTextStyle<sup>10+</sup>](#disappeartextstyle10), this API supports the **undefined** type for the **style** parameter.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| style  | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<[PickerTextStyle](ts-picker-common.md#pickertextstyle)> | Yes  | Text color, font size, and font weight for edge items.<br>Default value:<br>{<br>color: '#ff182431',<br>font: {<br>size: '14fp', <br>weight: FontWeight.Regular<br>}<br>}<br>If the value of **style** is **undefined**, the default value is used.|

>  **NOTE**
>
> Edge items only appear when there are at least two visible items above or below the selected item. If insufficient items are available, no edge items will be styled.

### textStyle<sup>10+</sup>

textStyle(value: PickerTextStyle)

Text color, font size, and font weight of candidate items (the first item immediately above or below the selected item).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | [PickerTextStyle](ts-picker-common.md#pickertextstyle) | Yes  | Text color, font size, and font weight for candidate items.<br>Default value:<br>{<br>color: '#ff182431',<br>font: {<br>size: '16fp', <br>weight: FontWeight.Regular<br>}<br>} |

>  **NOTE**
>
> Candidate items only appear when there is at least one visible item above or below the selected item. If insufficient items are available, no candidate items will be styled.

### textStyle<sup>18+</sup>

textStyle(style: Optional\<PickerTextStyle>)

Sets the text color, font size, and font weight of candidate items (the first item immediately above or below the selected item). Compared with [textStyle<sup>10+</sup>](#textstyle10), this API supports the **undefined** type for the **style** parameter.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| style  | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<[PickerTextStyle](ts-picker-common.md#pickertextstyle)> | Yes  | Text color, font size, and font weight for candidate items.<br>Default value:<br>{<br>color: '#ff182431',<br>font: {<br>size: '16fp', <br>weight: FontWeight.Regular<br>}<br>}<br>If the value of **style** is **undefined**, the default value is used.|

>  **NOTE**
>
> Candidate items only appear when there is at least one visible item above or below the selected item. If insufficient items are available, no candidate items will be styled.

### selectedTextStyle<sup>10+</sup>

selectedTextStyle(value: PickerTextStyle)

Sets the text color, font size, and font weight of the selected item.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior**: This API has no effect on wearables and works on other devices.

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | [PickerTextStyle](ts-picker-common.md#pickertextstyle) | Yes  | Font color, font size, and font weight of the selected item.<br>Default value:<br>{<br>color: '#ff007dff',<br>font: {<br>size: '20fp', <br>weight: FontWeight.Medium<br>}<br>} |

### selectedTextStyle<sup>18+</sup>

selectedTextStyle(style: Optional\<PickerTextStyle>)

Sets the text color, font size, and font weight of the selected item. Compared with [selectedTextStyle<sup>10+</sup>](#selectedtextstyle10), this API supports the **undefined** type for the **style** parameter.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior**: This API has no effect on wearables and works on other devices.

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| style  | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<[PickerTextStyle](ts-picker-common.md#pickertextstyle)> | Yes  | Font color, font size, and font weight of the selected item.<br>Default value:<br>{<br>color: '#ff007dff',<br>font: {<br>size: '20fp', <br>weight: FontWeight.Medium<br>}<br>}<br>If the value of **style** is **undefined**, the default value is used.|

### loop<sup>11+</sup>

loop(value: boolean)

Sets whether to enable loop scrolling.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                                        |
| ------ | ------- | ---- | ------------------------------------------------------------ |
| value  | boolean | Yes  | Whether to enable loop scrolling.<br>- **true**: Enable loop scrolling.<br>- **false**: Disable loop scrolling.<br>Default value: **true**.|

### loop<sup>18+</sup>

loop(isLoop: Optional\<boolean>)

Sets whether to enable loop scrolling. Compared with [loop<sup>11+</sup>](#loop11), this API supports the **undefined** type for the **isLoop** parameter.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                                        |
| ------ | ------- | ---- | ------------------------------------------------------------ |
| isLoop  | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<boolean> | Yes  | Whether to enable loop scrolling.<br>- **true**: Enable loop scrolling.<br>- **false**: Disable loop scrolling.<br>Default value: **true**.<br>If the value of **isLoop** is **undefined**, the default value is used.|

### dateTimeOptions<sup>12+</sup>

dateTimeOptions(value: DateTimeOptions)

Sets whether to display a leading zero for the hours, minutes, and seconds.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                     | Mandatory| Description                                                        |
| ------ | ----------------------------------------- | ---- | ------------------------------------------------------------ |
| value  | [DateTimeOptions](#datetimeoptions12) | Yes  | Whether to display a leading zero for the hours, minutes, and seconds.<br>Default value:<br>**hour**: For the 24-hour format, the default value is **"2-digit"**, meaning the hour is displayed as a two-digit number. If the actual value is less than 10, a leading zero is added, displayed as "0X". For the 12-hour format, the default value is **"numeric"**, meaning no leading zero.<br>**minute**: The default value is **"2-digit"**, meaning the minute is displayed as a two-digit number. If the actual value is less than 10, a leading zero is added, displayed as "0X".<br>**second**: The default value is **"2-digit"**, meaning the minute is displayed as a two-digit number. If the actual value is less than 10, a leading zero is added, displayed as "0X".<br> If **hour**, **minute**, or **second** is set to **undefined**, the display follows the default rules.|

### dateTimeOptions<sup>18+</sup>

dateTimeOptions(timeFormat: Optional\<DateTimeOptions>)

Sets whether to display a leading zero for the hours, minutes, and seconds. Compared with [dateTimeOptions<sup>12+</sup>](#datetimeoptions12), this API supports the **undefined** type for the **timeFormat** parameter.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| timeFormat  | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<[DateTimeOptions](#datetimeoptions12)> | Yes  | Whether to display a leading zero for the hours, minutes, and seconds. Currently only the configuration of the **hour**, **minute**, and **second** parameters is supported.<br>Default value:<br>**hour**: For the 24-hour format, the default value is **"2-digit"**, meaning the hour is displayed as a two-digit number. If the actual value is less than 10, a leading zero is added, displayed as "0X". For the 12-hour format, the default value is **"numeric"**, meaning no leading zero.<br>**minute**: The default value is **"2-digit"**, meaning the minute is displayed as a two-digit number. If the actual value is less than 10, a leading zero is added, displayed as "0X".<br>**second**: The default value is **"2-digit"**, meaning the minute is displayed as a two-digit number. If the actual value is less than 10, a leading zero is added, displayed as "0X".<br> If **hour**, **minute**, or **second** is set to **undefined**, the display follows the default rules.|

### enableHapticFeedback<sup>12+</sup>

enableHapticFeedback(enable: boolean)

Sets whether to enable haptic feedback.

>**NOTE**
>
> This API can be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier) since API version 18.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                         | Mandatory | Description                                                                                 |
| ------ | --------------------------------------------- | ----- |-------------------------------------------------------------------------------------|
| enable  | boolean | Yes  | Whether to enable haptic feedback.<br>- **true**: Enable haptic feedback.<br>- **false**: Disable haptic feedback.<br>Default value: **true**.<br>Whether this parameter takes effect after being set to **true** depends on hardware support.|

>  **NOTE**
>
>  To enable haptic feedback, you must declare the following permission under **requestPermissions** in **module** in **src/main/module.json5** of the project.
>  ```json
>  "requestPermissions": [
>  {
>   "name": "ohos.permission.VIBRATE",
>  }
>  ]
>  ```

### enableHapticFeedback<sup>18+</sup>

enableHapticFeedback(enable: Optional\<boolean>)

Sets whether to enable haptic feedback. Compared with [enableHapticFeedback<sup>12+</sup>](#enablehapticfeedback12), this API supports the **undefined** type for the **enable** parameter.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                         | Mandatory | Description                                                                                 |
| ------ | --------------------------------------------- |-----|-------------------------------------------------------------------------------------|
| enable  | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<boolean> | Yes  | Whether to enable haptic feedback.<br>- **true**: Enable haptic feedback.<br>- **false**: Disable haptic feedback.<br>Default value: **true**.<br>If the value of **enable** is **undefined**, the default value is used.<br>Whether this parameter takes effect after being set to **true** depends on hardware support.|

>  **NOTE**
>
>  To enable haptic feedback, you must declare the following permission under **requestPermissions** in **module** in **src/main/module.json5** of the project.
>  ```json
>  "requestPermissions": [
>  {
>   "name": "ohos.permission.VIBRATE",
>  }
>  ]
>  ```

### enableCascade<sup>18+</sup>

enableCascade(enabled: boolean)

Sets whether the AM/PM indicator automatically switches based on the hour value. This setting only takes effect when **useMilitaryTime** is set to **false**.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                         | Mandatory | Description                                                                                 |
| ------ | --------------------------------------------- |-----|-------------------------------------------------------------------------------------|
| enabled | boolean | Yes  | Whether the AM/PM indicator automatically switches based on the hour value. This setting only takes effect when **useMilitaryTime** is set to **false**.<br>- **true**: The AM/PM indicator automatically switches based on the hour value.<br>- **false**: The AM/PM indicator remains static regardless of hour changes.<br>Default value: **false**.<br>When **enabled** is set to **true**, it only takes effect if the **loop** parameter is also **true**.|

### digitalCrownSensitivity<sup>18+</sup>
digitalCrownSensitivity(sensitivity: Optional\<CrownSensitivity>)

Sets the sensitivity to the digital crown rotation.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                    | Mandatory  | Description                     |
| ----- | ---------------------------------------- | ---- | ------------------------- |
| sensitivity | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<[CrownSensitivity](ts-appendix-enums.md#crownsensitivity18)> | Yes   | Sensitivity to the digital crown rotation.<br>Default value: **CrownSensitivity.MEDIUM**                   |

>  **NOTE**
>
>  This API is used for circular screens on wearables. The component needs to obtain focus before responding to the [crown event](ts-universal-events-crown.md).

## Events

In addition to the [universal events](ts-component-general-events.md), the following events are supported.

### onChange

onChange(callback: (value: TimePickerResult ) =&gt; void)

Triggered when the time picker snaps to the selected item. This event cannot be triggered by two-way bound state variables.

This callback is triggered only after the scroll animation completes. To obtain real-time index changes, use [onEnterSelectedArea](#onenterselectedarea18) instead.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                         | Mandatory| Description          |
| ------ | --------------------------------------------- | ---- | -------------- |
| value  | [TimePickerResult](#timepickerresult)| Yes  | Time in 24-hour format.|

### onChange<sup>18+</sup>

onChange(callback: Optional\<OnTimePickerChangeCallback>)

Triggered when the time options in the TimePicker rest on the selected position after scrolling. This event cannot be triggered by two-way bound state variables. Compared with [onChange](#onchange), the **callback** parameter supports the **undefined** type.

This callback is triggered only after the scroll animation completes. To obtain real-time index changes, use [onEnterSelectedArea](#onenterselectedarea18) instead.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<[OnTimePickerChangeCallback](#ontimepickerchangecallback18)> | Yes  | Callback invoked when a time option is selected.<br>If **callback** is set to **undefined**, the callback function is not used.|

### onEnterSelectedArea<sup>18+</sup>

onEnterSelectedArea(callback: Callback\<TimePickerResult>)

Triggered during the scrolling of the time picker when an item enters the divider area.

Compared with the [onChange](#onchange) event, this event is triggered earlier, specifically when the scroll distance of the current column exceeds half the height of the selected item, which indicates that the item has entered the divider area. When [enableCascade](#enablecascade18) is set to **true**, using this callback is not recommended due to the interdependent relationship between the AM/PM and hour columns. This callback indicates the moment an option enters the divider area during scrolling, and only the value of the currently scrolled column will change. The values of other non-scrolled columns will remain unchanged.

> **NOTE**
>
> This API cannot be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier).

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                      | Mandatory| Description                                      |
| -------- | -------------------------- | ---- | ------------------------------------------ |
| callback | Callback\<[TimePickerResult](#timepickerresult)> | Yes  | Callback triggered during the scrolling of the time picker when an item enters the divider area.|

## DateTimeOptions<sup>12+</sup>

type DateTimeOptions = DateTimeOptions

Defines the options for a **DateTimeOptions** object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type                                                        | Description                                      |
| ------------------------------------------------------------ | ------------------------------------------ |
| [DateTimeOptions](../../apis-localization-kit/js-apis-intl.md#datetimeoptionsdeprecated) | Options for creating the **DateTimeOptions** object.|

## OnTimePickerChangeCallback<sup>18+</sup>

type OnTimePickerChangeCallback = (result: TimePickerResult) => void

Triggered when a time is selected.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                         | Mandatory| Description          |
| ------ | --------------------------------------------- | ---- | -------------- |
| result | [TimePickerResult](#timepickerresult)| Yes  | Time in 24-hour format.|

## TimePickerResult

Describes a time in 24-hour format.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                | Type  | Read-Only| Optional| Description                               |
| -------------------- | ------ | ---- | ---- | ----------------------------------- |
| hour                 | number | No  | No  | Hour portion of the selected time.<br>Value range: [0-23]|
| minute               | number | No  | No  | Minute portion of the selected time.<br>Value range: [0-59]|
| second<sup>11+</sup> | number | No  | No  | Second portion of the selected time.<br>Value range: [0-59]|

## Example

### Example 1: Setting the Text Style

This example demonstrates how to configure [disappearTextStyle](#disappeartextstyle10), [textStyle](#textstyle10), and [selectedTextStyle](#selectedtextstyle10) to customize the text style in a time picker.

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
          console.info('select current date is: ' + JSON.stringify(value));
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
            this.selectedTime.setHours(value.hour, value.minute);
            console.info('select current date is: ' + JSON.stringify(value));
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
            console.info('select current date is: ' + JSON.stringify(value));
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
            console.info('select current date is: ' + JSON.stringify(value));
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
            this.selectedTime.setHours(value.hour, value.minute);
            console.info('select current date is: ' + JSON.stringify(value));
          }
        })
    }.width('100%')
  }
}
```

![timePicker](figures/TimePickerDemo6.png)

### Example 7: Enabling the AM/PM Indicator to Automatically Switch Based on the Hour Value in 12-hour Format

This example demonstrates how to enable the AM/PM indicator to automatically switch based on the hour value in 12-hour format using [enableCascade](#enablecascade18) and [loop](#loop11).

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
        .enableCascade(true)
        .loop(true)
        .onChange((value: TimePickerResult) => {
          if (value.hour >= 0) {
            this.selectedTime.setHours(value.hour, value.minute);
            console.info('select current date is: ' + JSON.stringify(value));
          }
        })
    }.width('100%')
  }
}
```

![timePicker](figures/TimePickerDemo7.gif)
