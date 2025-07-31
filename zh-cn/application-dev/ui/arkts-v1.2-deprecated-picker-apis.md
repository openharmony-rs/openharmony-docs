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
  private selectedDate: Date = new Date('2021-08-08');

  build() {
    Column() {
      DatePicker({
        start: new Date('1970-1-1'),
        end: new Date('2100-1-1'),
        selected: this.selectedDate
      })
        .onChange((value: DatePickerResult) => {
          console.info('select current date is: ' + value.toString());
        })
    }
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
