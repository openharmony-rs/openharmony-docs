# Marquee

The **Marquee** component is used to display a scrolling piece of text. Text scrolling is activated only when the content width is greater than or equal to the component's width.

> **NOTE** > > To ensure that scrolling frame rates are not affected, it is recommended that the number of **Marquee** components > in a scroll container does not exceed four, or alternatively, use the Text component's > [TextOverflow.MARQUEE](../arkts-apis/arkts-arkui-textoverflow-e.md) as a substitute. > > For the scenario where the frame rate of the **Marquee** component is dynamic, you can use the > [MarqueeDynamicSyncScene](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md) API. > > If the text width is less than the **Marquee** component width, use the [property animation](arkts-arkui-common-comp.md#common) to > implement scrolling.

## Child Components

Not supported

## Marquee

```TypeScript
Marquee(options: MarqueeOptions)
```

Creates a marquee.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [MarqueeOptions](arkts-arkui-marquee-comp-marqueeoptions-i.md) | Yes | Parameters of the marquee. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [MarqueeOptions](arkts-arkui-marquee-comp-marqueeoptions-i.md) | Describes the initialization options of the **Marquee** component. |

## Examples

### Example 1: Dynamic Update of Marquee Content

This example demonstrates the running effect when the marquee content is dynamically updated, mainly involving the settings of the start, step, loop, fromStart, and src attributes, as well as the [marqueeUpdateStrategy](#marqueeupdatestrategy12) attribute.

Since API version 23, the spacing and delay attributes are added to [MarqueeOptions](#marqueeoptions18).



```TypeScript
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

### Example 2: Setting the Callback for Marquee Stopping

This example shows how to change the marquee state to trigger the onStop callback. After the callback is triggered, the value of numberStop increases by 1.

Since API version 26.0.0, the [onStop](#onstop) API is added.

```TypeScript
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
