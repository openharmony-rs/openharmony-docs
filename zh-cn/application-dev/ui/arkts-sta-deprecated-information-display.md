# UI组件适配（信息展示）

以下接口在ArkTS-Dyn中已废弃，在ArkTS-Sta中需使用替代接口来实现能力。

## Picker类组件

### onChange

ArkTS-Dyn接口声明：[onChange(callback: (value: DatePickerResult) => void)](../reference/apis-arkui/arkui-ts/ts-basic-components-datepicker.md#onchangedeprecated)

替代的ArkTS-Sta接口声明：[onDateChange(callback: Optional<Callback<Date>>)](../reference/apis-arkui/arkui-ts/ts-basic-components-datepicker.md#ondatechange18)


ArkTS-Dyn示例：

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

ArkTS-Sta示例：

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

### show

ArkTS-Dyn接口声明：[static show(options?: DatePickerDialogOptions)](../reference/apis-arkui/arkui-ts/ts-methods-datepicker-dialog.md#showdeprecated)

替代的ArkTS-Sta接口声明：[showDatePickerDialog(options: DatePickerDialogOptions): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#showdatepickerdialog) 


ArkTS-Dyn示例：

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

ArkTS-Sta示例：

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

ArkTS-Dyn接口声明：[onAccept: (value: DatePickerResult) => void](../reference/apis-arkui/arkui-ts/ts-methods-datepicker-dialog.md#datepickerdialogoptions对象说明)

替代的ArkTS-Sta接口声明：[onDateAccept: Callback<Date>](../reference/apis-arkui/arkui-ts/ts-methods-datepicker-dialog.md#datepickerdialogoptions对象说明)


ArkTS-Dyn示例：

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

ArkTS-Sta示例：

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

ArkTS-Dyn接口声明：[onChange: (value: DatePickerResult) => void](../reference/apis-arkui/arkui-ts/ts-methods-datepicker-dialog.md#datepickerdialogoptions对象说明)

替代的ArkTS-Sta接口声明：[onDateChange: Callback<Date>](../reference/apis-arkui/arkui-ts/ts-methods-datepicker-dialog.md#datepickerdialogoptions对象说明)


ArkTS-Dyn示例：

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

ArkTS-Sta示例：

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

### show

ArkTS-Dyn接口声明：[static show(options?: TimePickerDialogOptions)](../reference/apis-arkui/arkui-ts/ts-methods-timepicker-dialog.md#showdeprecated)

替代的ArkTS-Sta接口声明：[showTimePickerDialog(options: TimePickerDialogOptions): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#showtimepickerdialog)


ArkTS-Dyn示例：

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

ArkTS-Sta示例：

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

### show

ArkTS-Dyn接口声明：[static show(options?: TextPickerDialogOptions)](../reference/apis-arkui/arkui-ts/ts-methods-textpicker-dialog.md#showdeprecated)

替代的ArkTS-Sta接口声明：[showTextPickerDialog(options: TextPickerDialogOptions): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#showtextpickerdialog)


ArkTS-Dyn示例：

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

ArkTS-Sta示例：

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

## Panel

ArkTS-Dyn组件声明：[Panel](../reference/apis-arkui/arkui-ts/ts-container-panel.md)

替代的ArkTS-Sta接口声明：[bindSheet(isShow: Optional<boolean>, builder: CustomBuilder, options?: SheetOptions): T](../reference/apis-arkui/arkui-ts/ts-universal-attributes-sheet-transition.md#bindsheet)



ArkTS-Dyn示例：

```ts
@Entry
@Component
struct Index {
  @State panel_show: boolean = false;

  build(){
    Column(){
      Button("panel_show")
        .onClick(()=>{
          this.panel_show = !this.panel_show;
        })
      Panel(this.panel_show) {
        Text("Panel")
      }
      .show(this.panel_show)
      .type(PanelType.Foldable)
      .mode(PanelMode.Half)
      .dragBar(true)
      .halfHeight(500)
      .showCloseIcon(true)
      .onChange((width: number, height: number, mode: PanelMode) => {
        console.info(`width:${width},height:${height},mode:${mode}`);
      })
      .onHeightChange((height: number) => {
        console.info(`height:${height}`);
      })
    }
  }
}
```

ArkTS-Sta示例：

```ts
@Entry
@Component
struct Index {
  @State sheet_show: boolean = false;

  @Builder
  SheetBuilder() {
    Text("bindsheet")
  }

  build(){
    Button("sheet_show")
      .onClick(()=>{
        this.sheet_show = !this.sheet_show;
      })
      .bindSheet(this.sheet_show, this.SheetBuilder,
        {
          dragBar: true,
          detents: [500, 650],
          showClose: true,
          onHeightDidChange: (value: number) => {
            console.info(`onHeightDidChange value:${value}`);
          },
          onWidthDidChange: (value: number) => {
            console.info(`onWidthDidChange value:${value}`);
          },
          onDetentsDidChange: (value: number) => {
            console.info(`onDetentsDidChange value:${value}`);
          },
          onTypeDidChange: (sheetType: SheetType) => {
            console.info(`onTypeDidChange sheetType:${sheetType}`);
          }
        } as SheetOptions)
  }
}
```

## AlphabetIndexer

ArkTS-Dyn接口声明：[onSelected(callback: (index: number) => void)](../reference/apis-arkui/arkui-ts/ts-container-alphabet-indexer.md#onselecteddeprecated)

替代的ArkTS-Sta接口声明：[onSelect(callback: (index: number) => void)](../reference/apis-arkui/arkui-ts/ts-container-alphabet-indexer.md#onselect8)



ArkTS-Dyn示例：

```ts
AlphabetIndexer({ arrayValue: ['A', 'B'], selected: 0 })
    .onSelected((index: number) => {
        console.info(index + 'Selected!');
    })
```

ArkTS-Sta示例：

```ts
AlphabetIndexer({ arrayValue: ['A', 'B'], selected: 0 })
    .onSelect((index: number) => {
        console.info(index + 'Selected!');
    })
```

## ProgressOptions\<Type>.style

ArkTS-Dyn接口声明：[ProgressOptions\<Type>.style](../reference/apis-arkui/arkui-ts/ts-basic-components-progress.md#progressoptionstype对象说明)

替代的ArkTS-Sta接口声明：[ProgressOptions\<Type>.type](../reference/apis-arkui/arkui-ts/ts-basic-components-progress.md#progressoptionstype对象说明)

ArkTS-Dyn示例：

``` ts
@Entry
@Component
struct Index {
  build() {
    Column() {
      Progress({value: 50, style: ProgressStyle.Linear})
    }
    .height('100%')
    .width('100%')
  }
}
```

ArkTS-Sta示例：

``` ts
@Entry
@Component
struct Index {
  build() {
    Column(undefined) {
      Progress({value: 50, type: ProgressType.Linear})
    }
    .height('100%')
    .width('100%')
  }
}
```

## ChipGroup

### ChipGroupItemOptions.suffixIcon

ArkTS-Dyn接口声明：[ChipGroupItemOptions.suffixIcon](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-ChipGroup.md#chipgroupitemoptions)

替代的ArkTS-Sta接口声明：[ChipGroupItemOptions.suffixImageIcon](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-ChipGroup.md#chipgroupitemoptions)

ArkTS-Dyn示例：

```ts
import { ChipGroup } from '@kit.ArkUI';

@Entry
@Component
struct MyComponent {
  build() {
    Column() {
      ChipGroup({
        items: [{
          label: { text: '选项1' },
          suffixIcon: { src: $r('sys.media.ohos_ic_public_cut') }
        }]
      })
    }
  }
}
```

ArkTS-Sta示例：

```ts
import { Entry, Component, Column, ChipGroup, $r, SuffixImageIconOptions } from '@kit.ArkUI';

@Entry
@Component
struct MyComponent {
  build() {
    Column() {
      ChipGroup({
        items: [{
          label: { text: '选项1' },
          suffixImageIcon: { src: $r('sys.media.ohos_ic_public_cut') } as SuffixImageIconOptions
        }]
      })
    }
  }
}
```