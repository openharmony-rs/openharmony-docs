# DatePicker

DatePicker是滑动选择日期的组件，支持公历和农历切换，可配置日期范围、选择模式和文本样式。用于需要用户选择日期的应用场景， 提供统一的日期选择交互体验，能够提升用户体验，减少开发工作量。
> **说明：** > > - 该组件从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。 > > - 该组件不建议开发者在动效过程中修改属性数据。 > > - 最大显示行数在横、竖屏模式下存在差异。竖屏时默认为5行，横屏时依赖系统配置，未配置时默认显示为3行。 > 可通过$r('sys.float.ohos_id_picker_show_count_landscape')查看横屏时的具体配置值。
>

## 子组件 > > 该组件为基础组件，不建议包含子组件。

## DatePicker

```TypeScript
DatePicker(options?: DatePickerOptions)
```

根据指定日期范围创建日期选择器。使用场景包括：生日选择、会议预订、行程安排等需要用户选择日期的应用功能。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DatePickerOptions](arkts-arkui-datepickeroptions-i.md) | 否 | 配置日期选择器组件的参数。不传该参数时使用默认配置（start默认为Date('1970-01-01')， end默认为Date('2100-12-31')，selected默认为当前系统日期）。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [DatePickerDialogOptions](arkts-arkui-datepickerdialogoptions-i.md) | 日期选择器弹窗选项。继承自[DatePickerOptions](arkts-arkui-datepickeroptions-i.md)。 |
| [DatePickerOptions](arkts-arkui-datepickeroptions-i.md) | 日期选择器组件的参数说明。 |
| [DatePickerResult](arkts-arkui-datepickerresult-i.md) | 日期选择器返回的时间格式。 |
| [LunarSwitchStyle](arkts-arkui-lunarswitchstyle-i.md) | 定义了DatePickerDialog组件中农历切换开关的样式。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DatePickerMode](arkts-arkui-datepickermode-e.md) | 设置日期展示模式。 |

## 示例

该示例实现了日期选择器组件，点击按钮可以切换公历农历。

```TypeScript
// xxx.ets
@Entry
@Component
struct DatePickerExample {
  @State isLunar: boolean = false;
  private selectedDate: Date = new Date('2021-08-08');

  build() {
    Column() {
      Button('切换公历农历')
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

该示例通过配置disappearTextStyle、textStyle、selectedTextStyle设置文本样式。

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

从API version 18开始，新增了DatePickerOptions的mode属性。

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
      Button('切换公历农历')
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

从API version 20开始，可以通过配置canLoop参数设置DatePicker是否循环滚动。

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
        Text('循环滚动').fontSize(20)
        Toggle({ type: ToggleType.Switch, isOn: this.isLoop })
          .onChange((isOn: boolean) => {
            this.isLoop = isOn;
          })
      }.position({ x: '60%', y: '40%' })
    }.width('100%')
  }
}
```
