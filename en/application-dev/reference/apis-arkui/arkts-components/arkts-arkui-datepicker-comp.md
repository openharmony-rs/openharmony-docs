# DatePicker

**DatePicker** is a component for selecting a date through scrolling interaction.

> **NOTE**

> - Avoid changing component attributes during animation processes. > > - The maximum number of rows that can be displayed varies by screen orientation: In portrait mode, the default > number of rows is 5. In landscape mode, the number of rows depends on the system configuration. If no system > configuration is set, the default is 3 rows. To check the specific system configuration value for landscape mode, > use **$r('sys.float.ohos_id_picker_show_count_landscape')**.

Child Components

Not supported

## DatePicker

```TypeScript
DatePicker(options?: DatePickerOptions)
```

Creates a date picker in the given date range.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [DatePickerOptions](arkts-arkui-datepickeroptions-i.md) | No | Parameters of the date picker. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [DatePickerDialogOptions](arkts-arkui-datepickerdialogoptions-i.md) | Defines the configuration options of the date picker dialog box. |
| [DatePickerOptions](arkts-arkui-datepickeroptions-i.md) | Describes the parameters of the date picker. |
| [DatePickerResult](arkts-arkui-datepickerresult-i.md) | Defines the time format returned by the date picker. |
| [LunarSwitchStyle](arkts-arkui-lunarswitchstyle-i.md) | Defines the style of the lunar calendar switch in the **DatePickerDialog** component. |

### Enums

| Name | Description |
| --- | --- |
| [DatePickerMode](arkts-arkui-datepickermode-e.md) | Enumerates date display modes. |

## Examples

```TypeScript
### Example 1: Switching Between Gregorian and Lunar Calendars

This example implements a date picker that allows users to switch between the Gregorian (solar) calendar and the lunar calendar by clicking a button.


```

```TypeScript
### Example 2: Setting the Text Style

This example shows how to customize the text style using [disappearTextStyle](#disappeartextstyle10), [textStyle](#textstyle10), and [selectedTextStyle](#selectedtextstyle10).


```

```TypeScript
### Example 3: Displaying Year and Month, or Month and Day Columns

This example demonstrates how to display year and month, or month and day columns using mode.

The mode attribute of [DatePickerOptions](arkts-arkui-datepickeroptions-i.md) is added since API version 18.


```

```TypeScript
### Example 4: Setting Cyclic Scrolling

This example demonstrates how to set whether to enable cyclic scrolling using [canLoop](#canloop20), available since API version 20.
```
