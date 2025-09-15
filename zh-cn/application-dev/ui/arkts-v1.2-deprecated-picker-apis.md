# Picker类组件

## DatePicker

以下接口在ArkTS1.1中已标记为废弃，并在ArkTS1.2中不再支持。

### onChange

ArkTS1.1接口声明：[onChange(callback: (value: DatePickerResult) => void)](../reference/apis-arkui/arkui-ts/ts-basic-components-datepicker.md#onchangedeprecated)

替代的ArkTS1.2接口声明：[onDateChange(callback: Optional<Callback<Date>>)](../reference/apis-arkui/arkui-ts/ts-basic-components-datepicker.md#ondatechange18)


ArkTS1.1

```ts
@Entry
@Component
struct DatePickerExample {
  @State selectedDate: Date = new Date('2021-08-08');

  build() {
    Column() {
      DatePicker({
        start: new Date('1970-1-1'),
        end: new Date('2100-1-1'),
        selected: this.selectedDate
      })
        .onChange((value: DatePickerResult) => {
          this.selectedDate.setFullYear(value.year ? value.year : 2025, value.month ? value.month : 0,
            value.day ? value.day : 1);
          console.info('select current date is: ' + JSON.stringify(value));
        })
    }.width('100%')
  }
}
```

ArkTS1.2

```ts
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
        .onDateChange((value: Date) => {
          console.info('select current date is: ' + value.toString());
        })
    }
  }
}
```
## DatePickerDialog

以下接口在ArkTS1.1中已标记为废弃，并在ArkTS1.2中不再支持。

### show

ArkTS1.1接口声明：[static show(options?: DatePickerDialogOptions)](../reference/apis-arkui/arkui-ts/ts-methods-datepicker-dialog.md#showdeprecated)

替代的ArkTS1.2接口声明：[showDatePickerDialog(options: DatePickerDialogOptions): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#showdatepickerdialog) 


ArkTS1.1

```ts
@Entry
@Component
struct DatePickerDialogExample {
  selectedDate: Date = new Date("2010-1-1");

  build() {
    Column() {
      Button("DatePickerDialog")
        .margin(20)
        .onClick(() => {
          DatePickerDialog.show({
            start: new Date("2000-1-1"),
            end: new Date("2100-12-31"),
            selected: this.selectedDate,
            onDateAccept: (value: Date) => {
              console.info("DatePickerDialog:onDateAccept()" + value.toString());
            }
          });
        })
    }
  }
}
```

ArkTS1.2

```ts
@Entry
@Component
struct DatePickerDialogExample {
  selectedDate: Date = new Date("2010-1-1");

  build() {
    Column() {
      Button("DatePickerDialog")
        .margin(20)
        .onClick(() => {
          this.getUIContext().showDatePickerDialog({
            start: new Date("2000-1-1"),
            end: new Date("2100-12-31"),
            selected: this.selectedDate,
            onDateAccept: (value: Date) => {
              console.info("DatePickerDialog:onDateAccept()" + value.toString());
            }
          });
        })
    }
  }
}
```
### onAccept

ArkTS1.1接口声明：[onAccept: (value: DatePickerResult) => void](../reference/apis-arkui/arkui-ts/ts-methods-datepicker-dialog.md#datepickerdialogoptions对象说明)

替代的ArkTS1.2接口声明：[onDateAccept: Callback<Date>](../reference/apis-arkui/arkui-ts/ts-methods-datepicker-dialog.md#datepickerdialogoptions对象说明)


ArkTS1.1

```ts
@Entry
@Component
struct DatePickerDialogExample {
  @State selectedDate: Date = new Date('2010-1-1');

  build() {
    Column() {
      Button("DatePickerDialog")
        .margin(30)
        .onClick(() => {
          this.getUIContext().showDatePickerDialog({
            start: new Date('2000-1-1'),
            end: new Date('2100-12-31'),
            selected: this.selectedDate,
            onAccept: (value: DatePickerResult) => {
              this.selectedDate.setFullYear(value.year ? value.year : 2025, value.month ? value.month : 0,
                  value.day ? value.day : 1);
              console.info('DatePickerDialog:onDateAccept()' + JSON.stringify(value));
            }
          });
        })
    }.width('100%')
  }
}

```

ArkTS1.2

```ts
@Entry
@Component
struct DatePickerDialogExample {
  selectedDate: Date = new Date("2010-1-1");

  build() {
    Column() {
      Button("DatePickerDialog")
        .margin(20)
        .onClick(() => {
          this.getUIContext().showDatePickerDialog({
            start: new Date("2000-1-1"),
            end: new Date("2100-12-31"),
            selected: this.selectedDate,
            onDateAccept: (value: Date) => {
              console.info("DatePickerDialog:onDateAccept()" + value.toString());
            }
          });
        })
    }
  }
}
```
### onChange

ArkTS1.1接口声明：[onChange: (value: DatePickerResult) => void](../reference/apis-arkui/arkui-ts/ts-methods-datepicker-dialog.md#datepickerdialogoptions对象说明)

替代的ArkTS1.2接口声明：[onDateChange: Callback<Date>](../reference/apis-arkui/arkui-ts/ts-methods-datepicker-dialog.md#datepickerdialogoptions对象说明)


ArkTS1.1

```ts
@Entry
@Component
struct DatePickerDialogExample {
  @State selectedDate: Date = new Date('2010-1-1');

  build() {
    Column() {
      Button('DatePickerDialog')
        .margin(30)
        .onClick(() => {
          this.getUIContext().showDatePickerDialog({
            start: new Date('2000-1-1'),
            end: new Date('2100-12-31'),
            selected: this.selectedDate,
            onChange: (value: DatePickerResult) => {
              console.info('DatePickerDialog:onDateChange()' + JSON.stringify(value));
            },
          });
        })
    }.width('100%')
  }
}
```

ArkTS1.2

```ts
@Entry
@Component
struct DatePickerDialogExample {
  selectedDate: Date = new Date("2010-1-1");

  build() {
    Column() {
      Button("DatePickerDialog")
        .margin(20)
        .onClick(() => {
          this.getUIContext().showDatePickerDialog({
            start: new Date("2000-1-1"),
            end: new Date("2100-12-31"),
            selected: this.selectedDate,
            onDateChange: (value: Date) => {
              console.info("DatePickerDialog:onDateChange()" + value.toString());
            },
          });
        })
    }
  }
}
```
## TimePickerDialog

以下接口在ArkTS1.1中已标记为废弃，并在ArkTS1.2中不再支持。

### show

ArkTS1.1接口声明：[static show(options?: TimePickerDialogOptions)](../reference/apis-arkui/arkui-ts/ts-methods-timepicker-dialog.md#showdeprecated)

替代的ArkTS1.2接口声明：[showTimePickerDialog(options: TimePickerDialogOptions): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#showtimepickerdialog)


ArkTS1.1

```ts
@Entry
@Component
struct TimePickerDialogExample {
  private selectTime: Date = new Date('2022-07-22T08:00:00');

  build() {
    Column() {
      Button("TimePickerDialog")
        .onClick(() => {
          TimePickerDialog.show({
            useMilitaryTime: false,
            selected: this.selectTime,
            onAccept: (value: TimePickerResult) => {
              if (value.hour != undefined && value.minute != undefined) {
                console.info("TimePickerDialog:onAccept()" + JSON.stringify(value));
              }
            }
          });
        })
    }.width('100%')
  }
}
```

ArkTS1.2

```ts
@Entry
@Component
struct TimePickerDialogExample {
  private selectTime: Date = new Date('2022-07-22T08:00:00');

  build() {
    Column() {
      Button("TimePickerDialog")
        .onClick(() => {
          this.getUIContext().showTimePickerDialog({
            useMilitaryTime: false,
            selected: this.selectTime,
            onAccept: (value: TimePickerResult) => {
              if (value.hour != undefined && value.minute != undefined) {
                console.info("TimePickerDialog:onAccept()" + JSON.stringify(value));
              }
            }
          });
        })
    }.width('100%')
  }
}

```

## TextPickerDialog

以下接口在ArkTS1.1中已标记为废弃，并在ArkTS1.2中不再支持。

### show

ArkTS1.1接口声明：[static show(options?: TextPickerDialogOptions)](../reference/apis-arkui/arkui-ts/ts-methods-textpicker-dialog.md#showdeprecated)

替代的ArkTS1.2接口声明：[showTextPickerDialog(options: TextPickerDialogOptions): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#showtextpickerdialog)


ArkTS1.1

```ts
@Entry
@Component
struct TextPickerDialogExample {
  private select: number | number[] = 0;
  private fruits: string[] = ['apple1', 'orange2', 'peach3', 'grape4', 'banana5'];

  build() {
      Column() {
        Button("TextPickerDialog:")
          .onClick(() => {
            TextPickerDialog.show({
              range: this.fruits,
              selected: this.select,
              onAccept: (value: TextPickerResult) => {
                console.info("TextPickerDialog:onAccept()" + JSON.stringify(value));
              }
            });
          })
      }.width('100%')
    }
}
```

ArkTS1.2

```ts
@Entry
@Component
struct TextPickerDialogExample {
  private selected: number = 0;
  private fruits: string[] = ['apple1', 'orange2', 'peach3', 'grape4', 'banana5'];

  build() {
    Column() {
      Button('TextPickerDialog')
        .onClick(() => {
          this.getUIContext().showTextPickerDialog({
            range: this.fruits,
            selected: this.selected,
            onAccept: (value: TextPickerResult) => {
              console.info('TextPickerDialog:onAccept()' + JSON.stringify(value));
            }
          });
        })
    }.width('100%')
  }
}
```