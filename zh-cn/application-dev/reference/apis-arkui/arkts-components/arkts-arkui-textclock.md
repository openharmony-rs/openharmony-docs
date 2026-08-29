# TextClock

TextClock组件通过文本将当前系统时间显示在设备上，支持不同时区的时间显示和时间格式自定义，最高精度到秒级。适用于需要在应用界面上实时展示系统时间、支持多时区显示的场景，可帮助开发者快速实现时间文本展示功能，无需手动计算和更新时 间。
组件不可见时，时间变动将停止。组件的可见状态基于 [onVisibleAreaChange](arkts-arkui-commonmethod-c.md#onvisibleareachange) 处理，可见阈值ratios大于0即视为可见状态。

## 子组件

无

## TextClock

```TypeScript
TextClock(options?: TextClockOptions)
```

创建文本时钟组件。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TextClockOptions](arkts-arkui-textclockoptions-i.md) | 否 | 通过文本显示当前系统时间的组件参数。不传入时使用默认配置，各属性默认值详见TextClockOptions。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [TextClockConfiguration](arkts-arkui-textclockconfiguration-i.md) | 开发者需要自定义class实现ContentModifier接口。 |
| [TextClockOptions](arkts-arkui-textclockoptions-i.md) | 用于构建TextClock组件的选项。 |

## 示例

示例中的组件通过设置onDateChange回调函数，在文本时钟更新时，持续修改accumulateTime的内容。

```TypeScript
@Entry
@Component
struct Second {
  @State accumulateTime: number = 0;
  // 导入对象
  controller: TextClockController = new TextClockController();

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Text('Current milliseconds is ' + this.accumulateTime)
        .fontSize(20)
      // 以12小时制显示东八区的系统时间，精确到秒。
      TextClock({ timeZoneOffset: -8, controller: this.controller })
        .format('aa hh:mm:ss')
        .onDateChange((value: number) => {
          this.accumulateTime = value;
        })
        .margin(20)
        .fontSize(30)
      Button('start TextClock')
        .margin({ bottom: 10 })
        .onClick(() => {
          // 启动文本时钟
          this.controller.start();
        })
      Button('stop TextClock')
        .onClick(() => {
          // 停止文本时钟
          this.controller.stop();
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

该示例通过textShadow属性设置时钟文本的阴影样式。

```TypeScript
@Entry
@Component
struct TextClockExample {
  @State textShadows: ShadowOptions | Array<ShadowOptions> = [{
    radius: 10,
    color: Color.Red,
    offsetX: 10,
    offsetY: 0
  }, {
    radius: 10,
    color: Color.Black,
    offsetX: 20,
    offsetY: 0
  }, {
    radius: 10,
    color: Color.Brown,
    offsetX: 30,
    offsetY: 0
  }, {
    radius: 10,
    color: Color.Green,
    offsetX: 40,
    offsetY: 0
  }, {
    radius: 10,
    color: Color.Yellow,
    offsetX: 100,
    offsetY: 0
  }];

  build() {
    Column({ space: 8 }) {
      TextClock().fontSize(50).textShadow(this.textShadows)
    }
  }
}
```

该示例实现了自定义文本时钟样式的功能，自定义样式实现了一个时间选择器组件：通过文本时钟的时区偏移量与UTC秒数，来动态改变时间选择器的选中值，实现时钟效果。同时，根据文本时钟的启动状态，实现时间选择器的12小时制与24小时制的切换。

```TypeScript
class MyTextClockStyle implements ContentModifier<TextClockConfiguration> {
  currentTimeZoneOffset: number = new Date().getTimezoneOffset() / 60;
  title: string = '';

  constructor(title: string) {
    this.title = title;
  }

  applyContent(): WrappedBuilder<[TextClockConfiguration]> {
    return wrapBuilder(buildTextClock);
  }
}

@Builder
function buildTextClock(config: TextClockConfiguration) {
  Row() {
    Column() {
      Text((config.contentModifier as MyTextClockStyle).title)
        .fontSize(20)
        .margin(20)
      TimePicker({
        // 根据UTC秒数和时区偏移量计算本地时间：config.timeValue为UTC秒数，需乘1000转为毫秒；
        // currentTimeZoneOffset为当前系统时区偏移量，timeZoneOffset为目标时区偏移量，
        // 二者之差乘以3600000得到时区调整的毫秒数
        selected: (new Date(config.timeValue * 1000 +
          ((config.contentModifier as MyTextClockStyle).currentTimeZoneOffset - config.timeZoneOffset) * 60 * 60 *
            1000)),
        format: TimePickerFormat.HOUR_MINUTE_SECOND
      })
        .useMilitaryTime(!config.started)
    }
  }
}

@Entry
@Component
struct TextClockExample {
  @State accumulateTime1: number = 0;
  @State timeZoneOffset: number = -8;
  controller1: TextClockController = new TextClockController();
  controller2: TextClockController = new TextClockController();

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Text('Current milliseconds is ' + this.accumulateTime1)
        .fontSize(20)
        .margin({ top: 20 })
      TextClock({ timeZoneOffset: this.timeZoneOffset, controller: this.controller1 })
        .format('aa hh:mm:ss')
        .onDateChange((value: number) => {
          this.accumulateTime1 = value;
        })
        .margin(20)
        .fontSize(30)
      TextClock({ timeZoneOffset: this.timeZoneOffset, controller: this.controller2 })
        .format('aa hh:mm:ss')
        .fontSize(30)
        .contentModifier(new MyTextClockStyle('ContentModifier:'))
      Button('start TextClock')
        .margin({ top: 20, bottom: 10 })
        .onClick(() => {
          // 启动文本时钟
          this.controller1.start();
          this.controller2.start();
        })
      Button('stop TextClock')
        .margin({ bottom: 30 })
        .onClick(() => {
          // 停止文本时钟
          this.controller1.stop();
          this.controller2.stop();
        })

    }
    .width('100%')
    .height('100%')
  }
}
```

该示例演示了dateTimeOptions属性为小时字段增加或去除前导0的功能。24小时制的小时字段默认带有前导0，可通过dateTimeOptions属性去除前导0，12小时制的小时字段默认不带有前导0，可通过dateTimeOptions属性增加前导0。

```TypeScript
@Entry
@Component
struct TextClockExample {
  build() {
    Column({ space: 8 }) {
      Row() {
        Text('24小时制去除前导0：')
          .fontSize(20)
        TextClock()
          .fontSize(20)
          .format('HH:mm:ss')
          .dateTimeOptions({ hour: 'numeric' })
      }

      Row() {
        Text('12小时制增加前导0：')
          .fontSize(20)
        TextClock()
          .fontSize(20)
          .format('aa hh:mm:ss')
          .dateTimeOptions({ hour: '2-digit' })
      }
    }
    .alignItems(HorizontalAlign.Start)
  }
}
```

该示例演示了使用fontFeature、fontColor、fontStyle、fontWeight、fontFamily属性设置时钟文字显示样式的功能。

```TypeScript
@Entry
@Component
struct Index {
  build() {
    Column() {
      Text('fontFeature').fontColor(0xCCCCCC)
      // 设置文本特性
      TextClock()
        .fontFeature('\"sinf\" off')
      TextClock()
        .fontFeature('\"sinf\" on')
        .margin('10%')

      // 设置字体颜色
      Text('fontColor').fontColor(0xCCCCCC)
      TextClock()
        .fontColor(Color.Black)
      TextClock()
        .fontColor(Color.Blue)
        .margin('10%')

      Text('fontStyle').fontColor(0xCCCCCC)
      // 设置字体样式
      TextClock()
        .fontStyle(FontStyle.Normal)
      TextClock()
        .fontStyle(FontStyle.Italic)
        .margin('10%')

      Text('fontWeight').fontColor(0xCCCCCC)
      // 设置字体粗细
      TextClock()
        .fontWeight(FontWeight.Normal)
      TextClock()
        .fontWeight(FontWeight.Bold)
        .margin('10%')

      Text('fontFamily').fontColor(0xCCCCCC)
      // 设置字体
      TextClock()
        .fontFamily('HarmonyOS Sans')
    }
    .width('100%')
    .height('100%')
  }
}
```
