# @ohos.arkui.advanced.DatePickerComponent

## Modules to Import

```TypeScript
import { DatePickerComponent, DatePickerComponentOptions, DisplayMode, DateMode, TimeFormat, DatePickerComponentResult } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [CommonOptions](arkts-arkui-arkui-advanced-datepickercomponent-commonoptions-c.md) | CommonOptions defines common options for the date time picker. |
| [DateOptions](arkts-arkui-arkui-advanced-datepickercomponent-dateoptions-c.md) | DateOptions defines options for the date picker. |
| [DatePickerComponentOptions](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentoptions-c.md) | DatePickerComponentOptions defines options for the date time picker component. |
| [DatePickerComponentResult](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentresult-c.md) | DatePickerComponentResult defines the selection result of the date time picker. |
| [TimeOptions](arkts-arkui-arkui-advanced-datepickercomponent-timeoptions-c.md) | TimeOptions defines options for the time picker. |

### Structs

| Name | Description |
| --- | --- |
| [DatePickerComponent](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponent-s.md) | DatePickerComponent component is used to select date (year, month, day) and time (hour, minute, second). |

### Enums

| Name | Description |
| --- | --- |
| [DateMode](arkts-arkui-arkui-advanced-datepickercomponent-datemode-e.md) | DateMode enum defines the mode of the date picker. |
| [DisplayMode](arkts-arkui-arkui-advanced-datepickercomponent-displaymode-e.md) | DisplayMode enum defines the display mode of the picker. |
| [TimeFormat](arkts-arkui-arkui-advanced-datepickercomponent-timeformat-e.md) | TimeFormat enum defines the format of the time picker. |

## Examples

```TypeScript
### Example 1: Date Picker

This example implements a date picker by setting displayMode in [DatePickerComponentOptions](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentoptions-c.md) to DisplayMode.DATE.

Since API version 26.0.0, the [DatePickerComponentOptions](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentoptions-c.md) parameter is added.
```

```TypeScript
### Example 2: Time Picker

This example implements a time picker by setting displayMode in [DatePickerComponentOptions](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentoptions-c.md) to DisplayMode.TIME.

Since API version 26.0.0, the [DatePickerComponentOptions](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentoptions-c.md) parameter is added.


```

```TypeScript
### Example 3: Date and Time Picker

This example sets displayMode in [DatePickerComponentOptions](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentoptions-c.md) to DisplayMode.DATE_TIME to select both date and time.

Since API version 26.0.0, the [DatePickerComponentOptions](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentoptions-c.md) parameter is added.
```

```TypeScript
### Example 4: Disabling Loop Mode

This example disables the loop scrolling mode of the picker by setting loop in DateOptions to false.

Since API version 26.0.0, the DateOptions parameter is added.
```
