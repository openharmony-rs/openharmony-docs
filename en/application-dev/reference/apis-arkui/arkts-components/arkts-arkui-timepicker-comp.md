# TimePicker

**TimePicker** is a component that allows users to select a time from the given range through scrolling.

**NOTE**

- Avoid changing component attributes during animation processes.

- The maximum number of rows that can be displayed varies by screen orientation: In portrait mode, the default
number of rows is 5. In landscape mode, the number of rows depends on the system configuration. If no system configuration is set, the default is 3 rows. To check the specific system configuration value for landscape mode, use **$r('sys.float.ohos_id_picker_show_count_landscape')**.

Child Components

Not supported

## TimePicker

```TypeScript
TimePicker(options?: TimePickerOptions)
```

Creates a time picker, which uses the 24-hour time format by default.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [TimePickerOptions](arkts-arkui-timepickeroptions-i.md) | No | Parameters of the time picker. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [TimePickerDialogOptions](arkts-arkui-timepickerdialogoptions-i.md) | Defines the configuration options of the time picker dialog box. |
| [TimePickerOptions](arkts-arkui-timepickeroptions-i.md) | Describes the parameters of the time picker. |
| [TimePickerResult](arkts-arkui-timepickerresult-i.md) | Describes a time in 24-hour format. |

### Types

| Name | Description |
| --- | --- |
| [DateTimeOptions](arkts-arkui-datetimeoptions-t.md) | Defines the options for a **DateTimeOptions** object. |
| [OnTimePickerChangeCallback](arkts-arkui-ontimepickerchangecallback-t.md) | Triggered when a time is selected. |

### Enums

| Name | Description |
| --- | --- |
| [TimePickerFormat](arkts-arkui-timepickerformat-e.md) | Enumerates time display formats of the time picker. |

## Examples

```TypeScript
### Example 1: Setting the Text Style

This example demonstrates how to customize the text style in a time picker using [disappearTextStyle](#disappeartextstyle10), [textStyle](#textstyle10), and [selectedTextStyle](#selectedtextstyle10).


```

```TypeScript
### Example 2: Switching Between 12-Hour and 24-Hour Formats

This example demonstrates how to switch between 12-hour and 24-hour formats using useMilitaryTime.


```

```TypeScript
### Example 3: Setting the Time Format

This example shows how to set the time format using format and dateTimeOptions.


```

```TypeScript
### Example 4: Setting Loop Scrolling

This example demonstrates how to set whether to enable loop scrolling using [loop](#loop11).


```

```TypeScript
### Example 5: Setting the Start Time

This example demonstrates how to set the start time for the time picker.


```

```TypeScript
### Example 6: Setting the End Time

This example demonstrates how to set the end time for the time picker.


```

```TypeScript
### Example 7: Setting AM/PM to Follow the Time Linkage

This example uses [enableCascade](#enablecascade18) and [loop](#loop11) to implement the linkage of AM/PM following the time in the 12-hour format.

The enableCascade API is added since API version 18.
```
