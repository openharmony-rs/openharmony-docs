# Class (MarqueeDynamicSyncScene)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiangyuan6-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=89682c631d1be2b78acdb9477c9eda01133e0baf translatedAt=2026-08-05T03:08:38.468Z pushedAt=2026-08-05T07:48:40.035Z -->

Provides the dynamic frame rate configuration capability for the Marquee component, supporting dynamic frame rate adjustment during Marquee animation to optimize performance and power consumption. It is applicable to scenarios where animation smoothness and system resource consumption need to be balanced in marquee contexts.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 14.
>
> - **MarqueeDynamicSyncScene** inherits from [DynamicSyncScene](arkts-apis-uicontext-dynamicsyncscene.md) and represents the dynamic sync scene of the [Marquee](arkui-ts/ts-basic-components-marquee.md) component.

## Properties

**Atomic service API**: This API can be used in atomic services since API version 14.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

| Name      | Type                                                     | Read-Only| Optional| Description                               |
| --------- | --------------------------------------------------------- | ---- | ---- | ---------------------------------- |
| type      | [MarqueeDynamicSyncSceneType](./arkts-apis-uicontext-e.md#marqueedynamicsyncscenetype14) | Yes   | No   | Dynamic sync scene type of the Marquee component. It is used to specify the dynamic sync scene type mode of the Marquee component. Different scene types correspond to different frame rate adjustment strategies. For details, see MarqueeDynamicSyncSceneType.             |

**Example**

```ts
import { MarqueeDynamicSyncSceneType, MarqueeDynamicSyncScene } from '@kit.ArkUI';

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
  @State frameRateRange: ExpectedFrameRateRange = { min: 0, max: 120, expected: 30 };
  private scenes: MarqueeDynamicSyncScene[] = [];

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Marquee({
        start: this.start,
        step: this.step,
        loop: this.loop,
        fromStart: this.fromStart,
        src: this.marqueeText + this.src
      })
        .marqueeUpdateStrategy(MarqueeUpdateStrategy.PRESERVE_POSITION)
        .width(300)
        .height(80)
        .fontColor('#FFFFFF')
        .fontSize(48)
        .fontWeight(700)
        .backgroundColor('#182431')
        .margin({ bottom: 40 })
        .id('dynamicMarquee')
        .onAppear(()=>{
          this.scenes = this.getUIContext().requireDynamicSyncScene('dynamicMarquee') as MarqueeDynamicSyncScene[];
        })
      Button('Start')
        .onClick(() => {
          this.start = true;
          this.controller.start();
          this.scenes.forEach((scene: MarqueeDynamicSyncScene) => {
            if (scene.type == MarqueeDynamicSyncSceneType.ANIMATION) {
              scene.setFrameRateRange(this.frameRateRange);
            }
          });
        })
        .width(120)
        .height(40)
        .fontSize(16)
        .fontWeight(500)
        .backgroundColor('#007DFF')
      TextClock({ timeZoneOffset: -8, controller: this.controller })
        .format('hms')
        .onDateChange((value: number) => {
          this.src = this.convertToTime(value);
        })
        .margin(20)
        .fontSize(30)
    }
    .width('100%')
    .height('100%')
  }
}
```