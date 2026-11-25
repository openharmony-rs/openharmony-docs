# TextTimer
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Zhang-Dong-hui-->
<!--Designer: @xiangyuan6-->
<!--Tester:@jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

The **TextTimer** component displays timing information in text and controls the timer status. It supports both forward timing and countdown modes and allows you to customize the display format. It is suitable for scenarios where the elapsed time needs to be displayed, such as stopwatch and activity countdown. It is commonly used in countdown scenarios, such as exam countdown, time-limited activities, and workout timing.

When the component is invisible (in the screen-unlocked state or when the application is running in the background), the UI time change stops (that is, the component is not drawn at this time), but [onTimer](#ontimer) is still triggered.

>  **NOTE**
>
> This component is supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Child Components

Not supported

## APIs

TextTimer(options?: TextTimerOptions)

**Widget capability**: This API can be used in ArkTS widgets since API version 10.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options | [TextTimerOptions](#texttimeroptions)| No| Parameters of the **TextTimer** component. This parameter is passed when you need to customize the timer configuration (such as the countdown switch, timing duration, initial time, and controller). If this parameter is not passed, the default configuration of **TextTimerOptions** is used.<br>The default value is inherited from [TextTimerOptions](#texttimeroptions).|

## TextTimerOptions

Sets the options used to build the **TextTimer** component.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type    | Read-Only| Optional| Description                  |
| ----------- | -------- | -------- | -------- | -------- |
| isCountDown | boolean  | No | Yes | Countdown switch.<br>**true**: The timer counts down (for example, from 30 seconds to 0 seconds).<br>**false**: The timer counts up (for example, from 0 seconds to 30 seconds).<br>Default value: **false**<br>**Widget capability**: This API can be used in ArkTS widgets since API version 10.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| count       | number   | No | Yes | Initial time of the timer, in milliseconds. This parameter is valid only when **isCountDown** is set to **true**.<br>Default value: **60000**<br>The value range is (0, 86400000), that is, the value cannot exceed 24 hours. If the value is out of the range, the default value is used.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 10.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| controller | [TextTimerController](#texttimercontroller) | No| Yes| **TextTimer** controller, which is used to programmatically control the start, pause, and reset of a timer. If this parameter is not passed, the timer can still be displayed properly, but its status cannot be controlled through code.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 10.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| startTime | number | No| Yes| Initial time of the timer in forward timing mode. This parameter takes effect only when **isCountDown** is set to **false**.<br>Value range: [−2147483648, 2147483647]<br>Default value: **0**<br>Unit: ms<br>If the value is negative, the timer starts from the negative value and continues to count up after passing 0.<br>**Since**: 26.0.0<br>**Model restriction**: This API can be used only in the stage model.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 26.0.0.<br>**Atomic service API**: This API can be used in atomic services since API version 26.0.0.|

## Attributes

In addition to the [universal attributes](ts-component-general-attributes.md), the following attributes are supported.

### format

format(value: string)

Sets the custom time format. The value must contain at least one of the following keywords: **HH**, **mm**, **ss**, and **SS**. If the date format is **yy**, **MM**, or **dd**, this format is not supported and the default format **'HH:mm:ss.SS'** is used.

The timer update frequency is in the minimum unit of **format**. For example, if **format** is set to **'HH:mm'**, the update frequency is one minute. If a high-precision format (for example, containing **SS**) is set, the **onTimer** callback interval may be uneven.

**Widget capability**: This API can be used in ArkTS widgets since API version 10.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                  |
| ------ | ------ | ---- | -------------------------------------- |
| value  | string | Yes  | Custom time format displayed by the timer. The value must contain at least one of the following keywords: **HH**, **mm**, **ss**, and **SS**.<br>Default value: **'HH:mm:ss.SS'**|


### fontColor

fontColor(value: ResourceColor)

Sets the font color.

**Widget capability**: This API can be used in ArkTS widgets since API version 10.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                      | Mandatory| Description      |
| ------ | ------------------------------------------ | ---- | ---------- |
| value  | [ResourceColor](ts-types.md#resourcecolor) | Yes  | Font color.<br>Default value on wearable devices: **'#c5ffffff'**, indicating that the text is displayed in white.<br>Default value on other devices: **'#e6182431'**, indicating that the text is displayed in black.|

### fontSize

fontSize(value: Length)

Sets the font size.

**Widget capability**: This API can be used in ArkTS widgets since API version 10.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                        | Mandatory| Description                                                        |
| ------ | ---------------------------- | ---- | ------------------------------------------------------------ |
| value  | [Length](ts-types.md#length) | Yes  | Font size.<br>Default value: **16fp**<br>When the value is of the number type in Length, the unit is fp. For the string type in **Length**: If the string does not start with a digit, it is treated as 0 fp. If the string starts with a digit and contains characters other than [pixel units](ts-pixel-units.md) (such as letters or special characters) following the digit, the leading numeric part is extracted as the value and the unit is fp.<br>For example, the value **"abc"** is treated as **0fp**, **"10vp"** is treated as **10vp**, and **"10vp11abc"** is treated as **10fp**. The value cannot be a percentage.|

### fontStyle

fontStyle(value: FontStyle)

Sets the font style.

**Widget capability**: This API can be used in ArkTS widgets since API version 10.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                       | Mandatory| Description                                   |
| ------ | ------------------------------------------- | ---- | --------------------------------------- |
| value  | [FontStyle](ts-appendix-enums.md#fontstyle) | Yes  | Font style, for example, italic.<br>Default value: **FontStyle.Normal**|

### fontWeight

fontWeight(value: number | FontWeight | ResourceStr)

Sets the font weight of the text. If the value is too large, the text in different fonts may be truncated.

**Widget capability**: This API can be used in ArkTS widgets since API version 10.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type | Mandatory| Description     |
| ------ | ---------- | ------ | ----------------- |
| value  | number&nbsp;\|&nbsp;[FontWeight](ts-appendix-enums.md#fontweight)&nbsp;\|&nbsp;[ResourceStr](ts-types.md#resourcestr) | Yes  | Font width of the text. The value range of the number type is [100, 900]. The value interval is 100. A larger value indicates a wider font. If the value of the number type is not within the value range, the default value is **400**. The [ResourceStr](ts-types.md#resourcestr) type supports only strings of the number type, such as **"400"**, **"bold"**, **"bolder"**, **"lighter"**, **"regular"**, and **"medium"**, corresponding to the enums in **FontWeight**.<br>Default value: **FontWeight.Normal**<br>The Resource type is supported since API version 20.|

### fontFamily

fontFamily(value: ResourceStr)

Sets the font family.

**Widget capability**: This API can be used in ArkTS widgets since API version 10.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                  | Mandatory| Description                                                        |
| ------ | -------------------------------------- | ---- | ------------------------------------------------------------ |
| value  | [ResourceStr](ts-types.md#resourcestr) | Yes  | Font family. The default font is **'HarmonyOS Sans'**.<br>The 'HarmonyOS Sans' font and [registered custom fonts](../js-apis-font.md) are supported for applications.<br>Only the 'HarmonyOS Sans' font is supported for widgets.|

### textShadow<sup>11+</sup>

textShadow(value: ShadowOptions | Array&lt;ShadowOptions&gt;)

Sets the text shadow. It supports input parameters in an array to implement multiple text shadows. The **fill** field and coloring strategy are not supported.

>**NOTE**
>
> This API can be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier) since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description          |
| ------ | ------------------------------------------------------------ | ---- | -------------- |
| value  | [ShadowOptions](ts-universal-attributes-image-effect.md#shadowoptions)&nbsp;\|&nbsp;Array&lt;[ShadowOptions](ts-universal-attributes-image-effect.md#shadowoptions)> | Yes  | Parameters of the text shadow effect, including the color, blur radius, and offset.|

### contentModifier<sup>12+</sup>

contentModifier(modifier: ContentModifier\<TextTimerConfiguration>)

Creates a content modifier. If the default text display style cannot meet your requirements, you can use this API to customize the timer UI effect.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                         | Mandatory| Description                                            |
| ------ | --------------------------------------------- | ---- | ------------------------------------------------ |
| modifier  | [ContentModifier](./ts-universal-attributes-content-modifier.md#contentmodifiert)\<[TextTimerConfiguration](#texttimerconfiguration12)> | Yes  | Content modifier to apply to the **TextTimer** component.<br>**modifier**: content modifier. You need a custom class to implement the **ContentModifier** API.|

## Events

### onTimer

onTimer(event:&nbsp;(utc:&nbsp;number,&nbsp;elapsedTime:&nbsp;number)&nbsp;=&gt;&nbsp;void)

Event triggered when the time text changes. This event is not triggered when the screen is locked or the application is running in the background. When the component is invisible (in the screen-unlocked state or when the application is running in the background), the UI time change stops, but this event is still triggered. When the high-precision [format](#format) (**SS**) is set, the callback interval may be uneven, and the interval between two consecutive callbacks may vary.

**Widget capability**: This API can be used in ArkTS widgets since API version 10.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type  | Mandatory| Description                                                        |
| ----------- | ------ | ---- | ------------------------------------------------------------ |
| utc         | number | Yes  | Linux timestamp, which is the amount of time that has elapsed since January 1, 1970, in the minimum unit of the format specified by the [format](#format) attribute.|
| elapsedTime | number | Yes  | Elapsed time of the timer, in the minimum unit of the format.                |

## TextTimerController

Defines the controller for controlling the **TextTimer** component. A **TextTimer** component can only be bound to one controller, and the relevant commands can only be called after the component has been created. A **TextTimerController** can control only the last **TextTimer** component bound to it.

**Widget capability**: This API can be used in ArkTS widgets since API version 10.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### Objects to Import

``` ts
textTimerController: TextTimerController = new TextTimerController();
```

### constructor

constructor()

A constructor used to create a **TextTimerController** object.

**Widget capability**: This API can be used in ArkTS widgets since API version 10.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### start

start()

Starts the timer. This API needs to be called after the **TextTimer** component is created and bound to the controller.

**Widget capability**: This API can be used in ArkTS widgets since API version 10.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### pause

pause()

Pauses the timer. This API must be called after the component is created.

**Widget capability**: This API can be used in ArkTS widgets since API version 10.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### reset

reset()

Resets the timer. This API must be called after the component is created.

**Widget capability**: This API can be used in ArkTS widgets since API version 10.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## TextTimerConfiguration<sup>12+</sup>

Defines the **TextTimer** configuration used by the **ContentModifier** API.

You need a custom class to implement the **ContentModifier** API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type   |  Read-Only |  Optional  |  Description             |
| ------ | ------ | ------ | ------ |-------------------------------- |
| count | number | No| No| Initial time of the timer, in milliseconds. This parameter is valid only when **isCountDown** is set to **true**.<br>Default value: **60000**<br>The value range is (0, 86400000), that is, the value cannot exceed 24 hours. If the value is out of the range, the default value is used.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| isCountDown | boolean| No| No| Whether the timer is a countdown.<br>**true**: The timer counts down, e.g., from 30s to 0s. **false**: The timer counts up, e.g., from 0s to 30s.<br> Default value: **false**<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| started | boolean | No| No| Whether the timer has already started.<br>**true**: The timer has started. **false**: The timer has not started.<br>Default value: **false**<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| elapsedTime | number | No| No|Elapsed time of the timer, in the minimum unit of the format.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| startTime | number | No| Yes| Initial time of the timer in forward timing mode. This parameter takes effect only when **isCountDown** is set to **false**.<br>Value range: [-2147483648, 2147483647]. Negative values are supported.<br>Default value: **0**<br>Unit: ms<br>If the value is negative, the timer starts from the negative value and continues to count up after passing 0.<br>**Since**: 26.0.0<br>**Atomic service API**: This API can be used in atomic services since API version 26.0.0.|

## Example
### Example 1: Implementing a Text Timer with Start, Pause, and Reset Buttons

This example demonstrates the basic usage of the **TextTimer** component, setting the timer display format using the [format](#format) attribute.

Users can start, pause, and reset the timer by clicking the **start**, **pause**, and **reset** buttons.

```ts
// xxx.ets
@Entry
@Component
struct TextTimerExample {
  textTimerController: TextTimerController = new TextTimerController();
  @State format: string = 'mm:ss.SS';

  build() {
    Column() {
      TextTimer({ isCountDown: true, count: 30000, controller: this.textTimerController })
        .format(this.format)
        .fontColor(Color.Black)
        .fontSize(50)
        .onTimer((utc: number, elapsedTime: number) => {
          console.info('textTimer countDown utc is: ' + utc + ', elapsedTime: ' + elapsedTime);
        })
      Row() {
        Button('start').onClick(() => {
          this.textTimerController.start();
        })
        Button('pause').onClick(() => {
          this.textTimerController.pause();
        })
        Button('reset').onClick(() => {
          this.textTimerController.reset();
        })
      }
    }
  }
}
```


![textTimer](figures/textTimer.gif)

### Example 2: Setting the Text Shadow Style

This example shows how to set the text shadow style for the timer using the [textShadow](#textshadow11) attribute.

``` ts
// xxx.ets
@Entry
@Component
struct TextTimerExample {
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
      TextTimer().fontSize(50).textShadow(this.textShadows)
    }
  }
}
```
![TextshadowExample](figures/text_timer_textshadow.png)

### Example 3: Configuring the Custom Content Area

This example showcases two simple **TextTimer** components set against a light gray background. Once the timers are activated, they display the time progression in real-time. When the countdown timer starts, the background turns black; when the count-up timer starts, the background turns gray.

``` ts
// xxx.ets
class MyTextTimerModifier implements ContentModifier<TextTimerConfiguration> {
  constructor() {
  }

  applyContent(): WrappedBuilder<[TextTimerConfiguration]> {
    return wrapBuilder(buildTextTimer);
  }
}

@Builder
function buildTextTimer(config: TextTimerConfiguration) {
  Column() {
    Stack({ alignContent: Alignment.Center }) {
      Circle({ width: 150, height: 150 })
        .fill(config.started ? (config.isCountDown ? 0xFF232323 : 0xFF717171) : 0xFF929292)
      Column() {
        Text(config.isCountDown ? 'Countdown' : 'Count-up').fontColor(Color.White)
        Text(
          (config.isCountDown ? 'Remaining ' : 'Elapsed ') + (config.isCountDown ?
            (Math.max(config.count / 1000 - config.elapsedTime / 100, 0)).toFixed(1) + '/' +
            (config.count / 1000).toFixed(0)
            : ((config.elapsedTime / 100).toFixed(0))
          ) + 's'
        ).fontColor(Color.White)
      }
    }
  }
}

@Entry
@Component
struct Index {
  @State count: number = 10000;
  @State myTimerModifier: MyTextTimerModifier = new MyTextTimerModifier();
  countDownTextTimerController: TextTimerController = new TextTimerController();
  countUpTextTimerController: TextTimerController = new TextTimerController();

  build() {
    Row() {
      Column() {
        TextTimer({ isCountDown: true, count: this.count, controller: this.countDownTextTimerController })
          .contentModifier(this.myTimerModifier)
          .onTimer((utc: number, elapsedTime: number) => {
            console.info('textTimer onTimer utc is: ' + utc + ', elapsedTime: ' + elapsedTime);
          })
          .margin(10)
        TextTimer({ isCountDown: false, controller: this.countUpTextTimerController })
          .contentModifier(this.myTimerModifier)
          .onTimer((utc: number, elapsedTime: number) => {
            console.info('textTimer onTimer utc is: ' + utc + ', elapsedTime: ' + elapsedTime);
          })
        Row() {
          Button('start').onClick(() => {
            this.countDownTextTimerController.start();
            this.countUpTextTimerController.start();
          }).margin(10)
          Button('pause').onClick(() => {
            this.countDownTextTimerController.pause();
            this.countUpTextTimerController.pause();
          }).margin(10)
          Button('reset').onClick(() => {
            this.countDownTextTimerController.reset();
            this.countUpTextTimerController.reset();
          }).margin(10)
        }.margin(20)
      }.width('100%')
    }.height('100%')
  }
}
```
![text_timer_content_modifier](figures/text_timer_content_modifier.gif)

### Example 4: Enabling the Timer to Start Immediately After Creation

This example demonstrates how to start the **TextTimer** immediately after it is created.

``` ts
// xxx.ets
@Entry
@Component
struct TextTimerStart {
  textTimerController: TextTimerController = new TextTimerController();
  @State format: string = 'mm:ss.SS';

  build() {
    Column() {
      TextTimer({ isCountDown: true, count: 30000, controller: this.textTimerController })
        .format(this.format)
        .fontColor(Color.Black)
        .fontSize(50)
        .onTimer((utc: number, elapsedTime: number) => {
          console.info('textTimer countDown utc is: ' + utc + ', elapsedTime: ' + elapsedTime);
        })
        .onAppear(() => {
          this.textTimerController.start();
        })
    }
    .height('100%')
    .width('100%')
    .justifyContent(FlexAlign.Center)
  }
}
```
![text_timer_auto_start](figures/text_timer_auto_start.gif)

### Example 5: Setting the Text Style

This example shows text effects in different styles using the [fontColor](#fontcolor), [fontSize](#fontsize), [fontStyle](#fontstyle), [fontWeight](#fontweight) and [fontFamily](#fontfamily) attributes.

``` ts
// xxx.ets
@Entry
@Component
struct TextTimerDemo {
  // textTimerController is used to control the start and stop of the timer. This example mainly demonstrates style configuration.
  textTimerController: TextTimerController = new TextTimerController();
  @State countValue: number = 5025678;

  build() {
    Column({ space: 10 }) {
      Text ('Set the font color').fontColor(0xCCCCCC)
      TextTimer({ isCountDown: true, count: this.countValue, controller: this.textTimerController })
        .fontColor(Color.Blue)
      TextTimer({ isCountDown: true, count: this.countValue, controller: this.textTimerController })
        .fontColor(Color.Gray)

      Text ('Set the font size').fontColor(0xCCCCCC)
      TextTimer({ isCountDown: true, count: this.countValue, controller: this.textTimerController })
        .fontSize(10)
      TextTimer({ isCountDown: true, count: this.countValue, controller: this.textTimerController })
        .fontSize(30)

      Text ('Set the font style').fontColor(0xCCCCCC)
      TextTimer({ isCountDown: true, count: this.countValue, controller: this.textTimerController })
        .fontStyle(FontStyle.Normal)
      TextTimer({ isCountDown: true, count: this.countValue, controller: this.textTimerController })
        .fontStyle(FontStyle.Italic)

      Text ('Set the font weight').fontColor(0xCCCCCC)
      TextTimer({ isCountDown: true, count: this.countValue, controller: this.textTimerController })
        .fontWeight(FontWeight.Lighter)
      TextTimer({ isCountDown: true, count: this.countValue, controller: this.textTimerController })
        .fontWeight(FontWeight.Bolder)

      Text ('Set the font family').fontColor(0xCCCCCC)
      TextTimer({ isCountDown: true, count: this.countValue, controller: this.textTimerController })
        .fontFamily('HMOS Color Emoji')
      TextTimer({ isCountDown: true, count: this.countValue, controller: this.textTimerController })
        .fontFamily('HarmonyOS Sans')
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }
}
```

![](figures/text_timer_example_font_setting.png)

### Example 6: Setting the Initial Time

This example shows how to set the initial time for the timer using the **startTime** attribute of [TextTimerOptions](#texttimeroptions).

The **startTime** attribute is added to [TextTimerOptions](#texttimeroptions) since API version 26.0.0.

``` ts
// xxx.ets
@Entry
@Component
struct TextTimerExample {
  textTimerController: TextTimerController = new TextTimerController();
  @State format: string = 'mm:ss.SS';

  build() {
    Column() {
      TextTimer({ isCountDown: false, controller: this.textTimerController, startTime: 30000 })
        .format(this.format)
        .fontColor(Color.Black)
        .fontSize(50)
        .onTimer((utc: number, elapsedTime: number) => {
          console.info('textTimer notCountDown utc is: ' + utc + ', elapsedTime: ' + elapsedTime);
        })
      Row({ space: 10 }) {
        Button('start').onClick(() => {
          this.textTimerController.start();
        })
        Button('pause').onClick(() => {
          this.textTimerController.pause();
        })
        Button('reset').onClick(() => {
          this.textTimerController.reset();
        })
      }
    }
  }
}
```
![text_timer_auto_start](figures/text_timer_starttime.gif)
