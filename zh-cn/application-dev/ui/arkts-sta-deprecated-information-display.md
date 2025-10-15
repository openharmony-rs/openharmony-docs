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

## Swiper

### indicatorStyle
ArkTS-Dyn接口声明：[indicatorStyle(value?: IndicatorStyle): SwiperAttribute](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#indicatorstyledeprecated)

替代的ArkTS-Sta接口声明：[indicator(value: DotIndicator | DigitIndicator | boolean): SwiperAttribute](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#indicator)



ArkTS-Dyn示例：

```ts
Swiper().indicatorStyle()
```

ArkTS-Sta示例：

```ts
 Swiper().indicator(true)
```

### IndicatorStyle
ArkTS-Dyn接口声明：[declare interface IndicatorStyle](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#indicatorstyledeprecated对象说明)

替代的ArkTS-Sta接口声明：[declare class DotIndicator extends Indicator<DotIndicator>](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#dotindicator10)



ArkTS-Dyn示例：

```ts
let a: IndicatorStyle = {color: "#FFFF00FF"}
```

ArkTS-Sta示例：

```ts
let a: DotIndicator = new DotIndicator().color("#FFFF00FF")
```


### color
ArkTS-Dyn接口声明：[IndicatorStyle.color?: ResourceColor](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#indicatorstyledeprecated对象说明)

替代的ArkTS-Sta接口声明：[color(value: ResourceColor): DotIndicator](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#dotindicator10)



ArkTS-Dyn示例：

```ts
Swiper().indicatorStyle({color: "#FFFF00FF"})
```

ArkTS-Sta示例：

```ts
Swiper().indicator(new DotIndicator().color("#FFFF00FF"))
```


### right
ArkTS-Dyn接口声明：[IndicatorStyle.right?: Length](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#indicatorstyledeprecated对象说明)

替代的ArkTS-Sta接口声明：[right(value: Length): T](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#dotindicator10)



ArkTS-Dyn示例：

```ts
Swiper().indicatorStyle({right: 0})
```

ArkTS-Sta示例：

```ts
Swiper().indicator(new DotIndicator().right(0))
```


### left
ArkTS-Dyn接口声明：[IndicatorStyle.left?: Length](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#indicatorstyledeprecated对象说明)

替代的ArkTS-Sta接口声明：[left(value: Length): T](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#dotindicator10)



ArkTS-Dyn示例：

```ts
Swiper().indicatorStyle({left: 0})
```

ArkTS-Sta示例：

```ts
Swiper().indicator(new DotIndicator().left(0))
```


### top
ArkTS-Dyn接口声明：[IndicatorStyle.top?: Length](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#indicatorstyledeprecated对象说明)

替代的ArkTS-Sta接口声明：[top(value: Length): T](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#dotindicator10)



ArkTS-Dyn示例：

```ts
Swiper().indicatorStyle({top: 0})
```

ArkTS-Sta示例：

```ts
Swiper().indicator(new DotIndicator().top(0))
```


### bottom
ArkTS-Dyn接口声明：[IndicatorStyle.bottom?: Length](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#indicatorstyledeprecated对象说明)

替代的ArkTS-Sta接口声明：[bottom(value: Length): T](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#dotindicator10)



ArkTS-Dyn示例：

```ts
Swiper().indicatorStyle({bottom: 0})
```

ArkTS-Sta示例：

```ts
Swiper().indicator(new DotIndicator().bottom(0))
```


### selectedColor
ArkTS-Dyn接口声明：[IndicatorStyle.selectedColor?: ResourceColor](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#indicatorstyledeprecated对象说明)

替代的ArkTS-Sta接口声明：[selectedColor(value: ResourceColor): DotIndicator](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#dotindicator10)



ArkTS-Dyn示例：

```ts
Swiper().indicatorStyle({selectedColor: "#FFFF00FF"})
```

ArkTS-Sta示例：

```ts
Swiper().indicator(new DotIndicator().selectedColor("#FFFF00FF"))
```


### mask
ArkTS-Dyn接口声明：[IndicatorStyle.mask?: boolean](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#indicatorstyledeprecated对象说明)

替代的ArkTS-Sta接口声明：[mask(value: boolean): DotIndicator](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#dotindicator10)



ArkTS-Dyn示例：

```ts
Swiper().indicatorStyle({mask: true})
```

ArkTS-Sta示例：

```ts
Swiper().indicator(new DotIndicator().mask(true))
```


### size
ArkTS-Dyn接口声明：[IndicatorStyle.size?: Length](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#indicatorstyledeprecated对象说明)

替代的ArkTS-Sta接口声明：[itemWidth(value: Length): DotIndicator](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#dotindicator10)



ArkTS-Dyn示例：

```ts
Swiper().indicatorStyle({size: 100})
```

ArkTS-Sta示例：

```ts
Swiper().indicator(new DotIndicator().itemWidth(100).itemHeight(100).selectedItemWidth(100).selectedItemHeight(100))
```


### Stretch
ArkTS-Dyn接口声明：[SwiperDisplayMode.Stretch](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#swiperdisplaymode枚举说明)

替代的ArkTS-Sta接口声明：[SwiperDisplayMode.STRETCH](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#swiperdisplaymode枚举说明)



ArkTS-Dyn示例：

```ts
Swiper().displayMode(SwiperDisplayMode.Stretch)
```

ArkTS-Sta示例：

```ts
Swiper().displayMode(SwiperDisplayMode.STRETCH)
```


### AutoLinear
ArkTS-Dyn接口声明：[SwiperDisplayMode.AutoLinear](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#swiperdisplaymode枚举说明)

替代的ArkTS-Sta接口声明：[scrollTo(options: ScrollOptions)](../reference/apis-arkui/arkui-ts/ts-container-scroll.md#scrollto)


适配方案详见[示例](###示例)。


### AUTO_LINEAR
ArkTS-Dyn接口声明：[SwiperDisplayMode.AUTO_LINEAR](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#swiperdisplaymode枚举说明)

替代的ArkTS-Sta接口声明：[scrollTo(options: ScrollOptions)](../reference/apis-arkui/arkui-ts/ts-container-scroll.md#scrollto)

适配方案详见[示例](###示例)。


### 示例

ArkTS-Dyn示例：

```ts
@Entry
@Component
struct SwiperExample {
  private data: number[] = [1, 2, 3, 4, 5, 6, 7, 8]
  private swiperController: SwiperController = new SwiperController()

  build() {
    Column() {
      Swiper(this.swiperController) {
        ForEach(this.data, (item: number) => {
          Column() {
            Text(item.toString())
              .width('100%')
              .height('100%')
              .textAlign(TextAlign.Center)
          }
          .width(90)
          .height(160)
          .backgroundColor(0xAFEEEE)
        })
      }
      .displayMode(SwiperDisplayMode.AUTO_LINEAR)
      //.displayMode(SwiperDisplayMode.AutoLinear)
      .itemSpace(20)
      .curve(Curve.Linear)
      .duration(1000)
      .loop(false)
      .indicator(false)
      .onChange((index: number) => {
        console.info(index.toString())
      })
      Row({ space: 12 }) {
        Button('showNext')
          .onClick(() => {
            this.swiperController.showNext();
          })
        Button('showPrevious')
          .onClick(() => {
            this.swiperController.showPrevious();
          })
      }.margin(5)
    }.width('100%')
  }
}
```

ArkTS-Sta示例：

```ts
@Entry
@Component
struct ScrollExample {
  private data: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8];
  private scroller: Scroller = new Scroller();

  build() {
    Column() {
      Scroll(this.scroller) {
        Row() {
          ForEach(this.data, (item: number) => {
            Column() {
              Text(item.toString())
                .width('100%')
                .height('100%')
                .textAlign(TextAlign.Center)
            }
            .width(90)
            .height(160)
            .backgroundColor(0xAFEEEE)
            .margin({ right: item === this.data[this.data.length - 1] ? 0 : 20 })
          })
        }.height(160)
      }
      .scrollable(ScrollDirection.Horizontal)
      .scrollBar(BarState.Off)
      .edgeEffect(EdgeEffect.Spring)
      Row({ space: 12 }) {
        Button('showNext')
          .onClick(() => {
            const xOffset: number = this.scroller.currentOffset().xOffset;
            this.scroller.scrollTo({ xOffset: xOffset + 90 + 20, yOffset: 0, animation: { duration: 1000, curve: Curve.Linear } });
          })
        Button('showPrevious')
          .onClick(() => {
            const xOffset: number = this.scroller.currentOffset().xOffset;
            this.scroller.scrollTo({ xOffset: xOffset - 90 - 20, yOffset: 0, animation: { duration: 1000, curve: Curve.Linear } });
          })
      }.margin(5)
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

## ChipGroup

### ChipGroupItemOptions.suffixIcon

ArkTS-Dyn接口声明：[ChipGroupItemOptions.suffixIcon](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-ChipGroup.md#chipgroupitemoptions)

替代的ArkTS-Sta接口声明：[ChipGroupItemOptions.suffixImageIcon](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-ChipGroup.md#chipgroupitemoptions)

ArkTS-Dyn示例：

```ts
ChipGroup({
  items: [{
    label: { text: '选项1' },
    suffixIcon: { src: $r('sys.media.ohos_ic_public_cut') }
  }]
})
```

ArkTS-Sta示例：

```ts
ChipGroup({
  items: [{
    label: { text: '选项1' },
    suffixImageIcon: { src: $r('sys.media.ohos_ic_public_cut') }
  }]
})
```