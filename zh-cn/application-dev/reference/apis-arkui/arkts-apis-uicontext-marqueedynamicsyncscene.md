# Class (MarqueeDynamicSyncScene)

提供Marquee组件相关帧率的配置。

> **说明：**
>
> - 本模块首批接口从API version 10开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 本Class首批接口从API version 14开始支持。
>
> - MarqueeDynamicSyncScene继承自[DynamicSyncScene](arkts-apis-uicontext-dynamicsyncscene.md)，对应[Marquee](arkui-ts/ts-basic-components-marquee.md)的动态帧率场景。

## 属性

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

| 名称       | 类型                                                      | 只读 | 可选 | 说明                                |
| --------- | --------------------------------------------------------- | ---- | ---- | ---------------------------------- |
| type      | [MarqueeDynamicSyncSceneType](./arkts-apis-uicontext-e.md#marqueedynamicsyncscenetype14) | 是   | 否   | Marquee的动态帧率场景。             |

**示例：**

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
  convert2time(value: number): string {
    let date = new Date(Number(value+'000'));
    let hours = date.getHours().toString().padStart(2, '0');
    let minutes = date.getMinutes().toString().padStart(2, '0');
    let seconds = date.getSeconds().toString().padStart(2, '0');
    return hours+ ":" + minutes + ":" + seconds;
  }
  @State ANIMATION: ExpectedFrameRateRange = { min: 0, max: 120, expected: 30 };
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
          this.scenes.forEach((scenes: MarqueeDynamicSyncScene) => {
            if (scenes.type == MarqueeDynamicSyncSceneType.ANIMATION) {
              scenes.setFrameRateRange(this.ANIMATION);
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
          this.src = this.convert2time(value);
        })
        .margin(20)
        .fontSize(30)
    }
    .width('100%')
    .height('100%')
  }
}
```