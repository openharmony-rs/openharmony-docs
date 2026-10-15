# TimePicker

**TimePicker** is a component for selecting a time by sliding. It supports 12/24-hour formats, multiple time formats (hour/minute/second), loop scrolling, style customization, and time range restrictions. It is suitable for scenarios where users need to select a time, such as schedule arrangement, time reservation, and task management. It improves user experience, reduces input errors, and can be quickly integrated into applications.

> **NOTE:** 
> 
> - This component is supported since API version 8. New APIs added in later versions are marked with a superscript to indicate their
> 
> - It is not recommended to modify attribute data of this component during animation.
> 
> - The maximum number of displayed rows differs between landscape and portrait modes. In portrait mode, the default is 5 rows. In landscape mode, it depends on the system configuration, and the default is 3 rows when not configured. You can use the following parameter to view the specific configuration value: $r('sys.float.ohos_id_picker_show_count_landscape').

## Child Components

This is a basic component, and it is not recommended to include child components.

## TimePicker

```TypeScript
TimePicker(options?: TimePickerOptions)
```

Creates a sliding picker, which uses a 24-hour time range by default. It is suitable for scenarios where a time needs to be selected, such as schedule arrangement, alarm setting, and time recording.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TimePickerInterface-(options?: TimePickerOptions): TimePickerAttribute--><!--Device-TimePickerInterface-(options?: TimePickerOptions): TimePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [TimePickerOptions](arkts-arkui-timepicker-comp-timepickeroptions-i.md) | No | Parameters for configuring the TimePicker component. Pass this parameter when you need to customize the initial selected time, time format, time range, and other configurations. If this parameter is not passed, the default configuration is used (the initial selected time is the current system time, the time format is hour and minute by default, and the time range is 00:00-23:59 by default, with the default end time being 23:59:59). |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [TimePickerDialogOptions](arkts-arkui-timepicker-comp-timepickerdialogoptions-i.md) | Defines the configuration options of the time picker dialog box. |
| [TimePickerOptions](arkts-arkui-timepicker-comp-timepickeroptions-i.md) | Describes the parameters of the time picker. |
| [TimePickerResult](arkts-arkui-timepicker-comp-timepickerresult-i.md) | Returns the selected time result, where hour ranges from 0 to 23, regardless of the display format. |

### Types

| Name | Description |
| --- | --- |
| [DateTimeOptions](arkts-arkui-timepicker-comp-datetimeoptions-t.md) | Defines the options for a **DateTimeOptions** object. |
| [OnTimePickerChangeCallback](arkts-arkui-timepicker-comp-ontimepickerchangecallback-t.md) | Triggered when a time is selected. |

### Enums

| Name | Description |
| --- | --- |
| [TimePickerFormat](arkts-arkui-timepicker-comp-timepickerformat-e.md) | Enumerates time display formats of the time picker. |

## Examples

### Example 1: Setting the Text Style

This example demonstrates how to customize the text style in a time picker using [disappearTextStyle](#disappeartextstyle10), [textStyle](#textstyle10), and [selectedTextStyle](#selectedtextstyle10).



```TypeScript
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

### Example 2: Switching Between 12-Hour and 24-Hour Formats

This example demonstrates how to switch between 12-hour and 24-hour formats using useMilitaryTime.



```TypeScript
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

### Example 3: Setting the Time Format

This example shows how to set the time format using format and dateTimeOptions.



```TypeScript
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

### Example 4: Setting Loop Scrolling

This example demonstrates how to set whether to enable loop scrolling using [loop](#loop11).



```TypeScript
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

### Example 5: Setting the Start Time

This example demonstrates how to set the start time for the time picker.



```TypeScript
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

### Example 6: Setting the End Time

This example demonstrates how to set the end time for the time picker.



```TypeScript
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

### Example 7: Enabling the AM/PM Indicator to Automatically Switch Based on the Hour Value in 12-hour Format

This example demonstrates how to enable the AM/PM indicator to automatically switch based on the hour value in 12-hour format using [enableCascade](#enablecascade18) and [loop](#loop11).

The enableCascade API is added since API version 18.

```TypeScript
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
