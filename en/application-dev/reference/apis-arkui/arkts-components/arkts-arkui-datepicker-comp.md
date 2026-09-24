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

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [DatePickerOptions](arkts-arkui-datepicker-comp-datepickeroptions-i.md) | No | Parameters of the date picker. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [DatePickerDialogOptions](arkts-arkui-datepicker-comp-datepickerdialogoptions-i.md) | Defines the configuration options of the date picker dialog box. |
| [DatePickerOptions](arkts-arkui-datepicker-comp-datepickeroptions-i.md) | Describes the parameters of the date picker. |
| [DatePickerResult](arkts-arkui-datepicker-comp-datepickerresult-i.md) | Defines the time format returned by the date picker. |
| [LunarSwitchStyle](arkts-arkui-datepicker-comp-lunarswitchstyle-i.md) | Defines the style of the lunar calendar switch in the **DatePickerDialog** component. |

### Enums

| Name | Description |
| --- | --- |
| [DatePickerMode](arkts-arkui-datepicker-comp-datepickermode-e.md) | Enumerates date display modes. |

## Examples

### Example 1: Switching Between Gregorian and Lunar Calendars

This example implements a date picker that allows users to switch between the Gregorian (solar) calendar and the lunar calendar by clicking a button.



```TypeScript
// xxx.ets
@Entry
@Component
struct DatePickerExample {
  @State isLunar: boolean = false;
  private selectedDate: Date = new Date('2021-08-08');

  build() {
    Column() {
      Button('Switch Calendar')
        .margin({ top: 30, bottom: 30 })
        .onClick(() => {
          this.isLunar = !this.isLunar;
        })
      DatePicker({
        start: new Date('1970-1-1'),
        end: new Date('2100-1-1'),
        selected: this.selectedDate
      })
        .lunar(this.isLunar)
        .onDateChange((value: Date) => {
          this.selectedDate = value;
          console.info('select current date is: ' + value.toString());
        })

    }.width('100%')
  }
}
```

### Example 2: Setting the Text Style

This example shows how to customize the text style using [disappearTextStyle](#disappeartextstyle10), [textStyle](#textstyle10), and [selectedTextStyle](#selectedtextstyle10).



```TypeScript
// xxx.ets
@Entry
@Component
struct DatePickerExample {
  private selectedDate: Date = new Date('2021-08-08');

  build() {
    Column() {
      DatePicker({
        start: new Date('1970-1-1'),
        end: new Date('2100-1-1'),
        selected: this.selectedDate
      })
        .disappearTextStyle({ color: Color.Gray, font: { size: '16fp', weight: FontWeight.Bold } })
        .textStyle({ color: '#ff182431', font: { size: '18fp', weight: FontWeight.Normal } })
        .selectedTextStyle({ color: '#ff0000FF', font: { size: '26fp', weight: FontWeight.Regular, family: "HarmonyOS Sans", style: FontStyle.Normal } })
        .onDateChange((value: Date) => {
          this.selectedDate = value;
          console.info('select current date is: ' + value.toString());
        })

    }.width('100%')
  }
}
```

### Example 3: Displaying Year and Month, or Month and Day Columns

This example demonstrates how to display year and month, or month and day columns using mode.

The mode attribute of [DatePickerOptions](arkts-arkui-datepicker-comp-datepickeroptions-i.md) is added since API version 18.



```TypeScript
// xxx.ets
@Entry
@Component
struct DatePickerExample {
  @State isLunar: boolean = false;
  private selectedDate: Date = new Date('2025-01-15');
  @State datePickerModeList: (DatePickerMode)[] = [
    DatePickerMode.DATE,
    DatePickerMode.YEAR_AND_MONTH,
    DatePickerMode.MONTH_AND_DAY,
  ];
  @State datePickerModeIndex: number = 0;

  build() {
    Column() {
      Button('Switch Gregorian/Lunar Calendar')
        .margin({ top: 30, bottom: 30 })
        .onClick(() => {
          this.isLunar = !this.isLunar;
        })
      DatePicker({
        start: new Date('1970-1-1'),
        end: new Date('2100-1-1'),
        selected: this.selectedDate,
        mode: this.datePickerModeList[this.datePickerModeIndex]
      })
        .lunar(this.isLunar)
        .onDateChange((value: Date) => {
          this.selectedDate = value;
          console.info('select current date is: ' + value.toString());
        })

      Button('mode :' + this.datePickerModeIndex).margin({ top: 20 })
        .onClick(() => {
          this.datePickerModeIndex++;
          if (this.datePickerModeIndex >= this.datePickerModeList.length) {
            this.datePickerModeIndex = 0;
          }
        })
    }.width('100%')
  }
}
```

### Example 4: Setting Cyclic Scrolling

This example demonstrates how to set whether to enable cyclic scrolling using [canLoop](#canloop20), available since API version 20.

```TypeScript
// xxx.ets
@Entry
@Component
struct DatePickerExample {
  @State isLoop: boolean = true;
  selectedDate: Date = new Date("2010-1-1");

  build() {
    Column() {
      DatePicker({
        selected: this.selectedDate,
      })
        .canLoop(this.isLoop)
        .onDateChange((value: Date) => {
            console.info("DatePicker:onDateChange()" + value.toString());
        })

      Row() {
        Text('Cyclic scrolling').fontSize(20)
        Toggle({ type: ToggleType.Switch, isOn: this.isLoop })
          .onChange((isOn: boolean) => {
            this.isLoop = isOn;
          })
      }.position({ x: '60%', y: '40%' })
    }.width('100%')
  }
}
```
