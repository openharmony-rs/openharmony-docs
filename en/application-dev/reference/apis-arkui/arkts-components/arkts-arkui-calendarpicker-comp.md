# CalendarPicker

The **CalendarPicker** component provides a drop-down calendar for users to select a date.

> **NOTE**

Child Components

Not supported

## CalendarPicker

```TypeScript
CalendarPicker(options?: CalendarOptions)
```

Creates a calendar picker.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [CalendarOptions](arkts-arkui-calendaroptions-i.md) | No | Parameters of the calendar picker. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [CalendarDialogOptions](arkts-arkui-calendardialogoptions-i.md) | Defines the configuration options of the calendar picker dialog box. |
| [CalendarOptions](arkts-arkui-calendaroptions-i.md) | Describes the parameters of the calendar picker. |

### Enums

| Name | Description |
| --- | --- |
| [CalendarAlign](arkts-arkui-calendaralign-e.md) | Enumerates alignment types. |

## Examples

```TypeScript
### Example 1: Implementing a Calendar Picker

This example uses calendarPicker to implement the CalendarPicker component and provides a drop-down calendar.


```

```TypeScript
### Example 2: Setting Start and End Dates

This example demonstrates how to set the start and end dates for the calendar picker using start and end.

Since API version 18, the start and end attributes are added to [CalendarOptions](arkts-arkui-calendaroptions-i.md).


```

```TypeScript
### Example 3: Highlighting the Current System Date and Disabling a Specific Date Range

This example shows how to highlight the current system date using markToday and disable a specific date range using disabledDateRange.

Since API version 19, the [markToday](#marktoday19) API is added, and the disabledDateRange attribute is added to [CalendarOptions](arkts-arkui-calendaroptions-i.md).
```
