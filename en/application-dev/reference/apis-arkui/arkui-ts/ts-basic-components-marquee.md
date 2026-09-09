# Marquee
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hddgzw-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=8aa8522c1582655206875d9c89c21656113a2dda translatedAt=2026-09-03T04:12:04.148Z -->

The **Marquee** component is used to scroll and display a single line of text. It supports custom scrolling speed, direction, and loop count. Text scrolling is activated only when the content width is greater than or equal to the component's width; otherwise, no scrolling occurs. It is suitable for scenarios where long text needs to be displayed in limited space, such as scrolling news headlines, notifications and announcements, and advertisement carousels. It effectively saves interface space and attracts user attention.


>  **NOTE**
>
>  This component is supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
>  To ensure that scrolling frame rates are not affected, it is recommended that the number of **Marquee** components in a scrolling component does not exceed 4, or use [TextOverflow.MARQUEE](ts-appendix-enums.md#textoverflow) of the [Text](ts-basic-components-text.md) component instead.
>
>  For scenarios where the **Marquee** component requires dynamic frame rates, use the [MarqueeDynamicSyncScene](../arkts-apis-uicontext-marqueedynamicsyncscene.md) API.
>
>  When the text width is smaller than the **Marquee** component's width, use the [property animation](ts-animatorproperty.md) to implement scrolling.

## Child Components

Not supported


## APIs

Marquee(options: MarqueeOptions)

Creates a marquee.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options | [MarqueeOptions](#marqueeoptions18)<sup>18+</sup> | Yes| Parameters of the marquee.|

## MarqueeOptions<sup>18+</sup>

Describes the initialization options of the **Marquee** component.

> **NOTE**
>
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18. While historical version information is preserved for anonymous objects, there may be cases where the outer element's @since version number is higher than inner elements'. This does not affect interface usability.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| start<sup>8+</sup> | boolean | No | No | Controls whether the marquee enters the playing state.<br>true: play; false: do not play.<br>**Note:**<br>When the loop parameter is set to a finite number greater than 0 and playback is complete, you cannot reset the scroll count and restart playback by changing the start parameter.<br>**Widget capability:** Since API version 9, this API is supported in ArkTS widgets.<br>**Atomic service API:** Since API version 11, this API is supported in atomic services.|
| step<sup>8+</sup> | number | No | Yes | Text step of the scrolling animation.<br>Value Range: [0, text width]. When step is greater than the text width of the Marquee, the default value is used.<br>Default Value: 6 <br>Unit: [vp](ts-pixel-units.md#basic-pixel-units) <br>**Widget capability:** Since API version 9, this API is supported in ArkTS widgets.<br>**Atomic service API:** Since API version 11, this API is supported in atomic services.|
| loop<sup>8+</sup> | number | No | Yes | Sets the loop count of repeated scrolling. When the value is less than or equal to 0, the scrolling loops infinitely.<br>Default Value: -1<br>**Note:**<br>On ArkTS widgets, this parameter scrolls only once when visible regardless of the value set. When it is set to a finite number greater than 0 and playback is complete, you cannot reset the scroll count and restart playback by changing the start parameter.<br>**Widget capability:** Since API version 9, this API is supported in ArkTS widgets. <br>**Atomic service API:** Since API version 11, this API is supported in atomic services.|
| fromStart<sup>8+</sup> | boolean | No | Yes | Sets the scrolling direction of the text.<br>true: the text scrolls forward from the beginning; false: the text scrolls in reverse.<br>Default Value: true<br>**Widget capability:** Since API version 9, this API is supported in ArkTS widgets.<br>**Atomic service API:** Since API version 11, this API is supported in atomic services. |
| src<sup>8+</sup> | string | No | No | Text to be scrolled.<br>**Widget capability:** Since API version 9, this API is supported in ArkTS widgets.<br>**Atomic service API:** Since API version 11, this API is supported in atomic services. |
| spacing<sup>23+</sup> | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | No | Yes | Spacing between two rounds of marquee scrolling. When the unit attribute of the LengthMetrics object is LengthUnit.PERCENT, this setting does not take effect and the default value is used.<br> Default Value: width of the Marquee component. <br>**Widget capability:** Since API version 23, this API is supported in ArkTS widgets.<br>**Atomic service API:** Since API version 23, this API is supported in atomic services.<br>**Model restriction:** This API can be used only in the stage model. |
| delay<sup>23+</sup> | number | No | Yes | Sets the delay between two rounds of scrolling.<br>Default Value: 0 <br>Value Range: [0, +∞). A value less than 0 is equivalent to 0.<br>Unit: millisecond<br>**Widget capability:** Since API version 23, this API is supported in ArkTS widgets.<br>**Atomic service API:** Since API version 23, this API is supported in atomic services.<br>**Model restriction:** This API can be used only in the stage model. |

## Attributes

In addition to the [universal attributes](ts-component-general-attributes.md), the following attributes are supported.

### fontColor

fontColor(value: ResourceColor)

Sets the font color. If this API is not called, the default font color is '#e6182431', which indicates dark gray (with an opacity of about 90%). On Wearable devices, the default font color is '#c5ffffff', which indicates white (with an opacity of about 77%).

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                      | Mandatory| Description      |
| ------ | ------------------------------------------ | ---- | ---------- |
| value | [ResourceColor](ts-types.md#resourcecolor) | Yes | Font color. |

### fontSize

fontSize(value: Length)

Sets the text size.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                        | Mandatory| Description                                                        |
| ------ | ---------------------------- | ---- | ------------------------------------------------------------ |
| value  | [Length](ts-types.md#length) | Yes   | Font size. When fontSize is of the number type, the fp unit is used. The default font size is 16fp. Percentage strings are not supported.<br>Default value on Wearable devices: 15fp<br>**Note:**<br>When used with the [allowScale](#allowscale) attribute, the value must be set in fp units. |

### fontWeight

fontWeight(value: number | FontWeight | string)

Sets the font weight of the text. If the value is set too large, the text may be truncated under different fonts. If this API is not called, the default font weight is FontWeight.Normal (normal weight, corresponding to the value 400).

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | number&nbsp;\|&nbsp;[FontWeight](ts-appendix-enums.md#fontweight)&nbsp;\|&nbsp;string | Yes   | Font weight of the text.<br>For the number type, the value ranges from 100 to 900, at an interval of 100. The default value is 400. A larger value indicates a bolder font. For the string type, only the string form of the number type value is supported, for example, "400", as well as "bold", "bolder", "lighter", "regular", and "medium", which correspond to the respective enum values in FontWeight. If the value is set too large, the font may be truncated in different fonts.<br>If a value beyond the value range is passed, the default value is used. If a value that does not meet the interval requirement is passed, the passed value is used when enableVariableFontWeight of fontWeightConfigs is set to true; otherwise, the default value is used. |

### fontFamily

fontFamily(value: string | Resource)

Sets the font family.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                | Mandatory| Description                                                        |
| ------ | ---------------------------------------------------- | ---- | ------------------------------------------------------------ |
| value  | string&nbsp;\|&nbsp;[Resource](ts-types.md#resource) | Yes  | Font family. Default font: **'HarmonyOS Sans'**<br>Supported fonts include **'HarmonyOS Sans'** and custom fonts registered using [loadFontSync](../../apis-arkgraphics2d/js-apis-graphics-text.md#loadfontsync).<br>Only the 'HarmonyOS Sans' font is supported for widgets.|

### allowScale

allowScale(value: boolean)

Sets whether to allow text scaling. If this API is not called, text scaling is not allowed by default.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                |
| ------ | ------- | ---- | ------------------------------------ |
| value  | boolean | Yes   | Whether to allow text scaling.<br>true: text scaling is allowed; false: text scaling is not allowed.<br>**Note:**<br>This takes effect only when [fontSize](#fontsize) is in fp units. |

### marqueeUpdateStrategy<sup>12+</sup>

marqueeUpdateStrategy(value: MarqueeUpdateStrategy)

Scrolling strategy of the **Marquee** component after its attributes are updated. (This attribute takes effect when the **Marquee** component is in the playing state and the text content width is greater than or equal to the component's width.) If this API is not called, MarqueeUpdateStrategy.DEFAULT is used by default.

Usage scenarios:
- MarqueeUpdateStrategy.DEFAULT: suitable for scenarios where you want to restart scrolling with the default strategy after the content is updated.
- MarqueeUpdateStrategy.PRESERVE_POSITION: suitable for scenarios where you want to keep the current scrolling position and continue scrolling when the content is dynamically updated, such as real-time clocks, stock prices, and other dynamic content display.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                |
| ------ | ------- | ---- | ------------------------------------ |
| value |[MarqueeUpdateStrategy](ts-appendix-enums.md#marqueeupdatestrategy12) | Yes | Scrolling strategy of the marquee after the marquee component properties are updated. |

## Events

### onStart

onStart(event:&nbsp;()&nbsp;=&gt;&nbsp;void)

Triggered when the marquee text changes or starts scrolling.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                 | Mandatory| Description          |
| ------ | ------------------------------------- | ---- | -------------- |
| event  | &nbsp;()&nbsp;=&gt;&nbsp;void | Yes  | Callback invoked when the marquee text changes or starts scrolling.|

### onBounce

onBounce(event:&nbsp;()&nbsp;=&gt;&nbsp;void)

Triggered when a complete scrolling cycle is completed. If the loop count is not 1, this event is triggered multiple times.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                 | Mandatory| Description          |
| ------ | ------------------------------------- | ---- | -------------- |
| event  | &nbsp;()&nbsp;=&gt;&nbsp;void | Yes   | Callback invoked when a complete scrolling is finished. |

### onFinish

onFinish(event:&nbsp;()&nbsp;=&gt;&nbsp;void)

Triggered when the marquee has finished the number of scrolling times set by the **loop** attribute.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                 | Mandatory| Description          |
| ------ | ------------------------------------- | ---- | -------------- |
| event  | &nbsp;()&nbsp;=&gt;&nbsp;void | Yes  | Callback invoked when the marquee has finished the number of scrolling times set by the **loop** attribute.|

### onStop

onStop(event:&nbsp;Callback&lt;void&gt;\| undefined)

Triggered when the marquee finishes scrolling or stops.

When the marquee stops, it restarts the loop from the beginning. This does not include the pause scenario, and pausing does not trigger this callback.

**Since**: 26.0.0

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type                                  | Mandatory | Description           |
| ------ | ------------------------------------- | ---- | -------------- |
| event  | [&nbsp;Callback](ts-types.md#callback12)&lt;void&gt;\| undefined| Yes   | Triggered when the marquee finishes scrolling or stops.<br>When set to undefined, the callback is not executed. |

## Example

### Example 1 (Dynamic Update of Marquee Content)

This example demonstrates the running effect when the marquee content is dynamically updated, mainly involving the settings of the start, step, loop, fromStart, and src attributes, as well as the [marqueeUpdateStrategy](#marqueeupdatestrategy12) attribute.

Since API version 23, the [MarqueeOptions](#marqueeoptions18) adds the spacing and delay attributes.

```ts
import { LengthMetrics } from '@kit.ArkUI';

// xxx.ets
@Entry
@Component
struct MarqueeExample {
  @State start: boolean = false;
  @State src: string = '';
  @State marqueeText: string = 'Running Marquee';
  private fromStart: boolean = true;
  private step: number = 10;
  private loop: number = Number.POSITIVE_INFINITY;
  controller: TextClockController = new TextClockController();

  convertToTime(value: number): string {
    let date = new Date(Number(value + '000'));
    let hours = date.getHours().toString().padStart(2, '0');
    let minutes = date.getMinutes().toString().padStart(2, '0');
    let seconds = date.getSeconds().toString().padStart(2, '0');
    return hours + ':' + minutes + ':' + seconds;
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Marquee({
        start: this.start,
        step: this.step,
        loop: this.loop,
        fromStart: this.fromStart,
        src: this.marqueeText + this.src,
        spacing: LengthMetrics.vp(300), // Since API version 23, add the spacing attribute.
        delay: 0, // Since API version 23, add the delay attribute.
      })
        .marqueeUpdateStrategy(MarqueeUpdateStrategy.PRESERVE_POSITION)
        .width('300vp')
        .height('80vp')
        .fontColor('#FFFFFF')
        .fontSize('48fp')
        .allowScale(true) // Set this to true if you want the marquee text to scale with the system font size when using the fp unit for fontSize.
        .fontWeight(700)
        .fontFamily('HarmonyOS Sans') // Use 'HarmonyOS Sans' to avoid following the theme font.
        .backgroundColor('#182431')
        .margin({ bottom: '40vp' })
        .onStart(() => {
          console.info('Succeeded in completing the onStart callback of marquee animation');
        })
        .onBounce(() => {
          console.info('Succeeded in completing the onBounce callback of marquee animation');
        })
        .onFinish(() => {
          console.info('Succeeded in completing the onFinish callback of marquee animation');
        })
      Button('Start')
        .onClick(() => {
          this.start = true;
          // Start the text clock.
          this.controller.start();
        })
        .width('120vp')
        .height('40vp')
        .fontSize('16fp')
        .fontWeight(500)
        .backgroundColor('#007DFF')
      TextClock({ timeZoneOffset: -8, controller: this.controller })
        .format('hms')
        .onDateChange((value: number) => {
          this.src = this.convertToTime(value);
        })
        .margin('20vp')
        .fontSize('30fp')
    }
    .width('100%')
    .height('100%')
  }
}
```

![marquee](figures/marquee.gif)

### Example 2 (Setting the Marquee Stop Callback)

This example changes the marquee state to trigger the onStop callback. After the callback is triggered, the value of the stop counter numberStop increases by 1.


Since API version 26.0.0, the [onStop](#onstop) API is added.

```ts
// xxx.ets
@Entry
@Component
struct MarqueeStop4 {
  @State change: boolean = true;
  @State scrollDirection: string = 'Forward scrolling';
  @State marqueeText: string =
    'This is the text with the text overflow set marquee This is the text with the text overflow set marquee This is the text with the text overflow set marquee';
  @State numberStart: number = 0;
  @State numberBounce: number = 0;
  @State numberStop: number = 0;

  build() {
    Scroll() {
      Column() {
        Row() {
          Column() {
            Text('Start')
            Text(this.numberStart.toString())
          }.margin(10)

          Column() {
            Text('Bounce')
            Text(this.numberBounce.toString())
          }.margin(10)

          Column() {
            Text('Stop')
            Text(this.numberStop.toString())
          }.margin(10)
        }.margin(20)

        Marquee({
          start: true,
          step: 6,
          loop: 1,
          fromStart: this.change,
          src: this.marqueeText
        })
          .marqueeUpdateStrategy(MarqueeUpdateStrategy.DEFAULT)
          .margin(20)
          .onStart(() => {
            // 'Status received: START';
            this.numberStart++;
          })
          .onBounce(() => {
            // 'Status received: BOUNCE';
            this.numberBounce++;
          })
          .onStop(() => {
            // 'Status received: STOP';
            this.numberStop++;
          })
        Button(this.scrollDirection.toString()).onClick(() => {
          if (this.change) {
            this.change = false;
            this.scrollDirection = 'Backward scrolling';
          } else {
            this.change = true;
            this.scrollDirection = 'Forward scrolling';
          }
        }).margin(20)
      }.height(600).width('100%').padding({ left: 35, right: 35, top: 35 })
    }
  }
}
```

![marqueeOnStop](figures/marqueeOnStop.gif)

<!--no_check-->