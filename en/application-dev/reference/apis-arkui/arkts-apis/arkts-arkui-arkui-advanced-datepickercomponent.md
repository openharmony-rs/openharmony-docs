# @ohos.arkui.advanced.DatePickerComponent

## Modules to Import

```TypeScript
import { DatePickerComponent, DatePickerComponentOptions, DisplayMode, DateMode, TimeFormat, DatePickerComponentResult } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [CommonOptions](arkts-arkui-arkui-advanced-datepickercomponent-commonoptions-c.md) | Defines the common options of the date and time picker. |
| [DateOptions](arkts-arkui-arkui-advanced-datepickercomponent-dateoptions-c.md) | Defines the options of the date picker. |
| [DatePickerComponentOptions](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentoptions-c.md) | Defines the options of the date and time picker component. |
| [DatePickerComponentResult](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentresult-c.md) | Defines the selection result of the date and time picker, including the year, month, day, hour, minute, and second selected by the user. It is used to pass the specific date and time values in the **onChange** and **onScrollStop** callbacks. |
| [TimeOptions](arkts-arkui-arkui-advanced-datepickercomponent-timeoptions-c.md) | Defines the options of the time picker. |

### Structs

| Name | Description |
| --- | --- |
| [DatePickerComponent](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponent-s.md) | The **DatePickerComponent** is used to select dates (year, month, and day) and times (hour, minute, and second). |

### Enums

| Name | Description |
| --- | --- |
| [DateMode](arkts-arkui-arkui-advanced-datepickercomponent-datemode-e.md) | Enumerates the modes of the date picker. |
| [DisplayMode](arkts-arkui-arkui-advanced-datepickercomponent-displaymode-e.md) | Enumerates the display modes of the picker. |
| [TimeFormat](arkts-arkui-arkui-advanced-datepickercomponent-timeformat-e.md) | Enumerates the formats of the time picker. |

## Examples

### Example 1: Date Picker

This example implements a date picker by setting displayMode in [DatePickerComponentOptions](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentoptions-c.md) to DisplayMode.DATE.

Since API version 26.0.0, the [DatePickerComponentOptions](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentoptions-c.md) parameter is added.

```TypeScript
import { DatePickerComponent, DisplayMode, DateMode } from '@kit.ArkUI';

@Entry
@Component
struct DatePickerExample {
  @State selectedYear: number = 2026
  @State selectedMonth: number = 0
  @State selectedDay: number = 1

  build() {
    Column() {
      DatePickerComponent({
        options: {
          displayMode: DisplayMode.DATE,
          dateOptions: {
            mode: DateMode.DATE,
            selected: new Date(this.selectedYear, this.selectedMonth, this.selectedDay),
            start: new Date('2020-03-01'),
            end: new Date('2030-10-31'),
            enableHapticFeedback: true,
            onChange: (result) => {
              console.info('Selected date: ' + (result.year ?? 0) + '-' + ((result.month ?? 0) + 1) + '-' + (result.day ?? 0));
              if (result.year !== undefined) {
                this.selectedYear = result.year
              }
              if (result.month !== undefined) {
                this.selectedMonth = result.month
              }
              if (result.day !== undefined) {
                this.selectedDay = result.day
              }
            },
            onScrollStop: (result) => {
              console.info('Scroll stop: ' + (result.year ?? 0) + '-' + ((result.month ?? 0) + 1) + '-' + (result.day ?? 0));
            }
          }
        }
      })
    }
  }
}
```

### Example 2: Time Picker

This example implements a time picker by setting displayMode in [DatePickerComponentOptions](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentoptions-c.md) to DisplayMode.TIME.

Since API version 26.0.0, the [DatePickerComponentOptions](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentoptions-c.md) parameter is added.



```TypeScript
import { DatePickerComponent, DisplayMode, TimeFormat } from '@kit.ArkUI';

@Entry
@Component
struct TimePickerExample {
  build() {
    Column() {
      DatePickerComponent({
        options: {
          displayMode: DisplayMode.TIME,
          timeOptions: {
            format: TimeFormat.HOUR_MINUTE,
            useMilitaryTime: true,
            enableHapticFeedback: true,
            onChange: (result) => {
              console.info('Selected time: ' + (result.hour ?? 0) + ':' + (result.minute ?? 0));
            },
            onScrollStop: (result) => {
              console.info('Scroll stop: ' + (result.hour ?? 0) + ':' + (result.minute ?? 0));
            }
          }
        }
      })
    }
  }
}
```

### Example 3: Date and Time Picker

This example sets displayMode in [DatePickerComponentOptions](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentoptions-c.md) to DisplayMode.DATE_TIME to select both date and time.

Since API version 26.0.0, the [DatePickerComponentOptions](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentoptions-c.md) parameter is added.

```TypeScript
import { DatePickerComponent, DisplayMode, DateMode, TimeFormat } from '@kit.ArkUI';

@Entry
@Component
struct DateTimePickerExample {
  build() {
    Column() {
      DatePickerComponent({
        options: {
          displayMode: DisplayMode.DATE_TIME,
          dateOptions: {
            mode: DateMode.DATE,
            lunar: false,
            enableHapticFeedback: true,
            onChange: (result) => {
              console.info('Selected: ' + JSON.stringify(result));
            },
            onScrollStop: (result) => {
              console.info('Scroll stop: ' + JSON.stringify(result));
            }
          },
          timeOptions: {
            format: TimeFormat.HOUR_MINUTE_SECOND,
            useMilitaryTime: false,
            onChange: (result) => {
              console.info('Selected: ' + JSON.stringify(result));
            },
            onScrollStop: (result) => {
              console.info('Scroll stop: ' + JSON.stringify(result));
            }
          }
        }
      })
    }
  }
}
```

### Example 4: Disabling Loop Mode

This example disables the loop scrolling mode of the picker by setting loop in DateOptions to false.

Since API version 26.0.0, the DateOptions parameter is added.

```TypeScript
import { DatePickerComponent, DisplayMode, DateMode } from '@kit.ArkUI';

@Entry
@Component
struct NoLoopPickerExample {
  build() {
    Column() {
      DatePickerComponent({
        options: {
          displayMode: DisplayMode.DATE,
          dateOptions: {
            mode: DateMode.DATE,
            selected: new Date(),
            start: new Date('2020-01-01'),
            end: new Date('2030-12-31'),
            loop: false,
            onChange: (result) => {
              console.info('Selected date: ' + (result.year ?? 0) + '-' + ((result.month ?? 0) + 1) + '-' + (result.day ?? 0));
            }
          }
        }
      })
    }
  }
}
```
