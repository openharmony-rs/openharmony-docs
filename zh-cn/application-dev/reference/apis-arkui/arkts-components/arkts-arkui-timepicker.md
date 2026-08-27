# TimePicker

TimePicker是用于滑动选择时间的组件，支持12/24小时制、多种时间格式（小时/分钟/秒）、循环滚动、样式定制和时间范围限制等功能。 适用于日程安排、时间预约、任务管理等需要用户选择时间的场景，能够提升用户体验，减少输入错误，并可快速集成到应用中。
> **说明：** > > - 该组件从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。 > > - 该组件不建议开发者在动效过程中修改属性数据。 > > - 最大显示行数在横、竖屏模式下存在差异。竖屏时默认为5行，横屏时依赖系统配置，未配置时默认显示为3行。 > 可通过如下参数查看具体配置值$r('sys.float.ohos_id_picker_show_count_landscape')。
>

## 子组件 > > 该组件为基础组件，不建议包含子组件。

## TimePicker

```TypeScript
TimePicker(options?: TimePickerOptions)
```

创建滑动选择器，默认使用24小时的时间区间。适用于日程安排、闹钟设置、时间记录等需要选择时间的场景。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TimePickerOptions](arkts-arkui-timepickeroptions-i.md) | 否 | 配置时间选择组件的参数。当需要自定义初始选中时间、时间格式、时间范围等配置时传入此参数， 不传入时使用默认配置（初始选中时间为当前系统时间，时间格式默认为小时和分钟，时间范围默认为00:00-23:59（默认结束时间为23:59:59））。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [TimePickerDialogOptions](arkts-arkui-timepickerdialogoptions-i.md) | 时间选择器弹窗选项。继承自[TimePickerOptions](arkts-arkui-timepickeroptions-i.md)。 |
| [TimePickerOptions](arkts-arkui-timepickeroptions-i.md) | 时间选择器组件的参数说明。在TimePicker组件滑动过程中修改TimePickerOptions中的属性，会导致这些属性无法生效。 |
| [TimePickerResult](arkts-arkui-timepickerresult-i.md) | 返回选中的时间结果，hour取值0-23，与展示制式无关。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [DateTimeOptions](arkts-arkui-datetimeoptions-t.md) | 时间、日期格式化时可设置的配置项。 |
| [OnTimePickerChangeCallback](arkts-arkui-ontimepickerchangecallback-t.md) | 选择时间时触发该事件。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [TimePickerFormat](arkts-arkui-timepickerformat-e.md) | 时间选择器的数据格式。 |

## 示例

该示例通过配置[disappearTextStyle](#disappeartextstyle10)、[textStyle](#textstyle10)和[selectedTextStyle](#selectedtextstyle10)实现文本选择器中的文本样式。

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

该示例通过配置useMilitaryTime实现12小时制、24小时制的切换。

```TypeScript
// xxx.ets
@Entry
@Component
struct TimePickerExample {
  @State isMilitaryTime: boolean = false;
  private selectedTime: Date = new Date('2022-07-22T08:00:00');

  build() {
    Column() {
      Button('切换12小时制/24小时制')
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

该示例使用format和dateTimeOptions设置TimePicker时间格式。

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

该示例通过配置[loop](#loop11)设置TimePicker是否循环滚动。

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
        Text('循环滚动').fontSize(20)

        Toggle({ type: ToggleType.Switch, isOn: true })
          .onChange((isOn: boolean) => {
            this.isLoop = isOn;
          })
      }.position({ x: '60%', y: '40%' })

    }.width('100%')
  }
}
```

该示例设置TimePicker的起始时间。

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

该示例设置TimePicker的结束时间。

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

从API version 18开始，新增enableCascade接口。

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
