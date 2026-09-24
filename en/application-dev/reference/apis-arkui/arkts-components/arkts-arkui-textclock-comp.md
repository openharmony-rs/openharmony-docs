# TextClock

The **TextClock** component displays the current system time in text format for different time zones. The time is accurate to seconds.

When the component is invisible, the time change stops. The visible status of a component is processed based on [onVisibleAreaChange](arkts-arkui-common-comp-commonmethod-c.md#onvisibleareachange). If the visible threshold **ratios** is greater than 0, the component is visible.

## Child Components

Not supported

## TextClock

```TypeScript
TextClock(options?: TextClockOptions)
```

Create TextClock component.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [TextClockOptions](arkts-arkui-textclock-comp-textclockoptions-i.md) | No | Options of the text clock. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [TextClockConfiguration](arkts-arkui-textclock-comp-textclockconfiguration-i.md) | You need a custom class to implement the **ContentModifier** API. |
| [TextClockOptions](arkts-arkui-textclock-comp-textclockoptions-i.md) | Options used to build the **TextClock** component. |

## Examples

### Example 1: Implementing a Text Clock with Start/Stop Control

This example demonstrates the basic usage of the TextClock component, setting the clock display format using the [format](#format) attribute.

Clicking "start TextClock" triggers the callback to invoke TextClockController and initiate the clock. Clicking "stop TextClock" to invoke TextClockController and stop the clock.

This example uses the [onDateChange](#ondatechange) callback to update accumulateTime whenever the text clock refreshes.



```TypeScript
@Entry
@Component
struct Second {
  @State accumulateTime: number = 0;
  // Create the controller object.
  controller: TextClockController = new TextClockController();

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Text('Current milliseconds is ' + this.accumulateTime)
        .fontSize(20)
      // Display the system time in 12-hour format for the UTC+8 time zone, accurate to seconds.
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
          // Start the text clock.
          this.controller.start();
        })
      Button('stop TextClock')
        .onClick(() => {
          // Stop the text clock.
          this.controller.stop();
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

### Example 2: Setting the Text Shadow Style

This example sets the shadow style of the clock text through [textShadow](#textshadow11).



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

### Example 3: Configuring the Custom Content Area

This example implements the functionality of customizing the style of a text clock, creating a time picker component with a custom style: The time picker dynamically adjusts its selected value based on the text clock's timezone offset and the timezone offset in seconds from UTC to deliver a clock effect. Depending on whether the text clock is started, the time picker toggles between a 12-hour and a 24-hour format display.



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
        // Calculate the local time based on the UTC seconds and time zone offset: config.timeValue is the UTC seconds, which needs to be multiplied by 1000 to convert to milliseconds;
        // currentTimeZoneOffset is the current system time zone offset, and timeZoneOffset is the target time zone offset,
        // The difference between the two, multiplied by 3600000, gives the time zone adjustment in milliseconds.
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
          // Start the text clock.
          this.controller1.start();
          this.controller2.start();
        })
      Button('stop TextClock')
        .margin({ bottom: 30 })
        .onClick(() => {
          // Stop the text clock.
          this.controller1.stop();
          this.controller2.stop();
        })

    }
    .width('100%')
    .height('100%')
  }
}
```

### Example 4: Setting Leading Zero

This example demonstrates how to use the [dateTimeOptions](#datetimeoptions12) attribute to add or remove the leading zero for the hour field. By default, the hour field includes a leading zero in the 24-hour format, but typically does not include a leading zero in the 12-hour format.



```TypeScript
@Entry
@Component
struct TextClockExample {
  build() {
    Column({ space: 8 }) {
      Row() {
        Text('Remove the leading zero in 24-hour format: ')
          .fontSize(20)
        TextClock()
          .fontSize(20)
          .format('HH:mm:ss')
          .dateTimeOptions({ hour: 'numeric' })
      }

      Row() {
        Text('Add the leading zero in 12-hour format: ')
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

### Example 5: Setting the Text Display Style

This example demonstrates how to use the [fontFeature](#fontfeature11), [fontColor](#fontcolor), [fontStyle](#fontstyle), [fontWeight](#fontweight) and [fontFamily](#fontfamily) attributes to set the text display style of the clock.

```TypeScript
@Entry
@Component
struct Index {
  build() {
    Column() {
      Text('fontFeature').fontColor(0xCCCCCC)
      // Set text features.
      TextClock()
        .fontFeature('\"sinf\" off')
      TextClock()
        .fontFeature('\"sinf\" on')
        .margin('10%')

      // Set the font color.
      Text('fontColor').fontColor(0xCCCCCC)
      TextClock()
        .fontColor(Color.Black)
      TextClock()
        .fontColor(Color.Blue)
        .margin('10%')

      Text('fontStyle').fontColor(0xCCCCCC)
      // Set the font style.
      TextClock()
        .fontStyle(FontStyle.Normal)
      TextClock()
        .fontStyle(FontStyle.Italic)
        .margin('10%')

      Text('fontWeight').fontColor(0xCCCCCC)
      // Set the font weight.
      TextClock()
        .fontWeight(FontWeight.Normal)
      TextClock()
        .fontWeight(FontWeight.Bold)
        .margin('10%')

      Text('fontFamily').fontColor(0xCCCCCC)
      // Set the font.
      TextClock()
        .fontFamily('HarmonyOS Sans')
    }
    .width('100%')
    .height('100%')
  }
}
```
