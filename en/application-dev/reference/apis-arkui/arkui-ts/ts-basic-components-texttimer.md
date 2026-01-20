# TextTimer
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Zhang-Dong-hui-->
<!--Designer: @xiangyuan6-->
<!--Tester:@jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

The **TextTimer** component displays timing information and is controlled in text format.

The time updates stop when the component is invisible. The component's visibility is determined by the value of **ratios** in the [onVisibleAreaChange](./ts-universal-component-visible-area-change-event.md#onvisibleareachange) event callback: If the value is greater than 0, the component is visible.

>  **NOTE**
>
> This component is supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.

## Child Components

Not supported

## APIs

TextTimer(options?: TextTimerOptions)

**Widget capability**: Since API version 10, this API is supported in ArkTS widgets.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options |  [TextTimerOptions](#texttimeroptions)| No| Parameters of the **TextTimer** component.|

## TextTimerOptions

Options used to build the TextTimer component.

**Widget capability**: Since API version 10, this API is supported in ArkTS widgets.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type    | Read-Only| Optional| Description                  |
| ----------- | -------- | -------- | -------- | -------- |
| isCountDown | boolean  | No | Yes | Countdown switch. The value **true** means that the timer counts down (for example, from 30 seconds to 0 seconds), and **false** means that the timer counts up (for example, from 0 seconds to 30 seconds).<br>Default value: **false**|
| count       | number   | No | Yes | Timer duration, in milliseconds. It is effective only when **isCountDown** is **true**. The maximum value is 86400000 ms (24 hours). If 0 < **count** < 86400000, **count** is the initial value of the timer. Otherwise, the default value is used as the initial value.<br>Default value: **60000**|
| controller  | [TextTimerController](#texttimercontroller) | No| Yes| **TextTimer** controller.|

## Attributes

In addition to the [universal attributes](ts-component-general-attributes.md), the following attributes are supported.

### format

format(value: string)

Sets the custom format. The value must contain at least one of the following keywords: **HH**, mm, **ss**, and **SS**. If the date format is yy, MM, or dd, the default value is used.

The timer update frequency is in the minimum unit of format. For example, if format is set to HH:mm, the update frequency is one minute.

**Widget capability**: Since API version 10, this API is supported in ArkTS widgets.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                  |
| ------ | ------ | ---- | -------------------------------------- |
| value  | string | Yes  | Custom date display format.<br>Default value: **'HH:mm:ss.SS'**|


### fontColor

fontColor(value: ResourceColor)

Sets the font color.

**Widget capability**: Since API version 10, this API is supported in ArkTS widgets.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                      | Mandatory| Description      |
| ------ | ------------------------------------------ | ---- | ---------- |
| value  | [ResourceColor](ts-types.md#resourcecolor) | Yes  | Font color.<br>The default value on wearable devices is '#c5ffffff', indicating that the text is displayed in white.<br>Default value on other devices: '#e6182431', which is displayed in black.|

### fontSize

fontSize(value: Length)

Sets the font size.

**Widget capability**: Since API version 10, this API is supported in ArkTS widgets.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                        | Mandatory| Description                                                        |
| ------ | ---------------------------- | ---- | ------------------------------------------------------------ |
| value  | [Length](ts-types.md#length) | Yes  | Font size. If **fontSize** is of the number type, the unit fp is used. The default font size is 16 fp. The value cannot be a percentage.|

### fontStyle

fontStyle(value: FontStyle)

Sets the font style.

**Widget capability**: Since API version 10, this API is supported in ArkTS widgets.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                       | Mandatory| Description                                   |
| ------ | ------------------------------------------- | ---- | --------------------------------------- |
| value  | [FontStyle](ts-appendix-enums.md#fontstyle) | Yes  | Font style, for example, italic.<br>Default value: **FontStyle.Normal**|

### fontWeight

fontWeight(value: number | FontWeight | ResourceStr)

Font weight of the text. If the value is too large, the text in different fonts may be truncated.

**Widget capability**: Since API version 10, this API is supported in ArkTS widgets.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type | Mandatory| Description     |
| ------ | ---------- | ------ | ----------------- |
| value  | number&nbsp;\|&nbsp;[FontWeight](ts-appendix-enums.md#fontweight)&nbsp;\|&nbsp;[ResourceStr](ts-types.md#resourcestr) | Yes  | Font width of the text. The value range of the number type is [100,&nbsp;900]. The value interval is 100. A larger value indicates a wider font. If the value of the number type is not within the value range, the default value is 400. The [ResourceStr] (ts-types.md#resourcestr) type supports only the string of the number type, for example, 400, bold, bolder, lighter, regular, and medium, corresponds to the corresponding enumerated values in FontWeight.<br>Default value: **FontWeight.Normal**<br>The Resource type is supported since API version 20.|

### fontFamily

fontFamily(value: ResourceStr)

Sets the font family.

**Widget capability**: Since API version 10, this API is supported in ArkTS widgets.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                  | Mandatory| Description                                                        |
| ------ | -------------------------------------- | ---- | ------------------------------------------------------------ |
| value  | [ResourceStr](ts-types.md#resourcestr) | Yes  | Font family. The default font is **'HarmonyOS Sans'**.<br>The 'HarmonyOS Sans' font and [registered custom fonts](../js-apis-font.md) are supported for applications.<br>Only the 'HarmonyOS Sans' font is supported for widgets.|

### textShadow<sup>11+</sup>

textShadow(value: ShadowOptions | Array&lt;ShadowOptions&gt;)

Sets the text shadow. It supports input parameters in an array to implement multiple text shadows. This API does not work with the **fill** attribute or coloring strategy.

>**NOTE**
>
> This API can be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier) since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description          |
| ------ | ------------------------------------------------------------ | ---- | -------------- |
| value  | [ShadowOptions](ts-universal-attributes-image-effect.md#shadowoptions)&nbsp;\|&nbsp;Array&lt;[ShadowOptions](ts-universal-attributes-image-effect.md#shadowoptions)> | Yes  | Parameters of the text shadow effect, including the color, blur radius, and offset.|

### contentModifier<sup>12+</sup>

contentModifier(modifier: ContentModifier\<TextTimerConfiguration>)

Creates a content modifier.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                         | Mandatory| Description                                            |
| ------ | --------------------------------------------- | ---- | ------------------------------------------------ |
| modifier  | [ContentModifier](./ts-universal-attributes-content-modifier.md#contentmodifiert)[\<TextTimerConfiguration>](#texttimerconfiguration12) | Yes  | Content modifier to apply to the **TextTimer** component.<br>**modifier**: content modifier. You need a custom class to implement the **ContentModifier** API.|

## Events

### onTimer

onTimer(event:&nbsp;(utc:&nbsp;number,&nbsp;elapsedTime:&nbsp;number)&nbsp;=&gt;&nbsp;void)

This event is triggered when the time text changes. This event is not triggered when the screen is locked or the application is running in the background.
When the high-precision [format](#format) (SSS or SS) is set, the callback interval may fluctuate.

**Widget capability**: Since API version 10, this API is supported in ArkTS widgets.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type  | Mandatory| Description                                                        |
| ----------- | ------ | ---- | ------------------------------------------------------------ |
| utc         | number | Yes  | Linux timestamp, which is the amount of time that has elapsed since January 1, 1970, in the minimum unit of the format.|
| elapsedTime | number | Yes  | Elapsed time of the timer, in the minimum unit of the format.                |

## TextTimerController

Implements a controller for controlling the **TextTimer** component. A **TextTimer** component can only be bound to one controller, and the relevant commands can only be called after the component has been created.

**Widget capability**: Since API version 10, this API is supported in ArkTS widgets.

**Atomic service API**: This API can be used in atomic services since API version 11.

### Objects to Import

``` ts
textTimerController: TextTimerController = new TextTimerController();
```

### constructor

constructor()

A constructor used to create a **TextTimerController** object.

**Widget capability**: Since API version 10, this API is supported in ArkTS widgets.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### start

start()

Starts the timer.

**Widget capability**: Since API version 10, this API is supported in ArkTS widgets.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### pause

pause()

Pauses the timer.

**Widget capability**: Since API version 10, this API is supported in ArkTS widgets.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### reset

reset()

Resets the timer.

**Widget capability**: Since API version 10, this API is supported in ArkTS widgets.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## TextTimerConfiguration<sup>12+</sup>

Defines the configuration of the TextTimer used by the ContentModifier API.

You need a custom class to implement the **ContentModifier** API.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type   |  Read-Only |  Optional  |  Description             |
| ------ | ------ | ------ | ------ |-------------------------------- |
| count | number | No| No| Timer duration, in milliseconds. It is effective only when **isCountDown** is **true**. The maximum value is 86400000 ms (24 hours). If the value is between 0 and 86,400,000, it is used as the initial countdown time. Otherwise, the default value is used as the initial countdown time.<br> Default value: **60000**|
| isCountDown | boolean| No| No| Whether the timer is a countdown.<br>true: The timer starts to count down, for example, from 30s to 0s. false: The timer starts to count up, for example, from 0s to 30s.<br> Default value: **false**|
| started | boolean | No| No| Whether the timer has already started.<br>true: The timer has started. false: The timer has not started.<br>Default value: **false**|
| elapsedTime | number | No| No|Elapsed time of the timer, in the minimum unit of the format.|

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
          console.info('textTimer notCountDown utc is: ' + utc + ', elapsedTime: ' + elapsedTime)
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


![en-us_image_0000001251007721](figures/en-us_image_0000001251007721.gif)

### Example 2: Setting the Text Shadow Style

In this example, the [textShadow](#textshadow11) property is used to set the text shadow style of the timer.

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
        Text (config.isCountDown ? ' Countdown' : 'Counting up') .fontColor(Color.White)
        Text(
          (config.isCountDown ? ' Remaining' : 'Has passed') + (config.isCountDown ?
            (Math.max(config.count / 1000 - config.elapsedTime / 100, 0)).toFixed(1) + '/' +
            (config.count / 1000).toFixed(0)
            : ((config.elapsedTime / 100).toFixed(0))
          ) + '')
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
      Scroll()
        .height('20%')
      TextTimer({ isCountDown: true, count: 30000, controller: this.textTimerController })
        .format(this.format)
        .fontColor(Color.Black)
        .fontSize(50)
        .onTimer((utc: number, elapsedTime: number) => {
          console.info('textTimer notCountDown utc is: ' + utc + ', elapsedTime: ' + elapsedTime)
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

This example uses the [fontColor](#fontcolor), [fontSize](#fontsize), [fontStyle](#fontstyle), [fontWeight](#fontweight) and [fontFamily](#fontfamily) attributes to display text in different styles.

``` ts
// xxx.ets
@Entry
@Component
struct demo {
  textTimerController: TextTimerController = new TextTimerController();
  @State format: string = 'HH:mm:ss.SS';
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

