# Marquee

跑马灯组件，用于滚动展示一段单行文本，支持自定义滚动速度、方向、循环次数等。仅当文本内容宽度大于等于跑马灯组件宽度时滚动，否则不滚动。适用于需要在有限空间内展示较长文本的场景，如新闻标题滚动、通知公告、广告轮播等，可以有效节省界面空间 并吸引用户注意。
> **说明：** > > 为了不影响滚动帧率，建议在滚动类组件中Marquee的个数不超过4个，或者使用 > > 对于Marquee组件动态帧率的场景，可以使用[MarqueeDynamicSyncScene](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md)接口实现。 > > 在文本宽度小于跑马灯组件宽度时，使用属性动画实现滚动。

## 子组件

无

## Marquee

```TypeScript
Marquee(options: MarqueeOptions)
```

创建跑马灯组件。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [MarqueeOptions](arkts-arkui-marqueeoptions-i.md) | 是 | 配置跑马灯组件的参数。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [MarqueeOptions](arkts-arkui-marqueeoptions-i.md) | Marquee初始化参数。 |

## 示例

从API version 23开始，MarqueeOptions新增spacing、delay属性。

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
        spacing: LengthMetrics.vp(300), // 从API version 23开始，新增spacing属性
        delay: 0, // 从API version 23开始，新增delay属性
      })
        .marqueeUpdateStrategy(MarqueeUpdateStrategy.PRESERVE_POSITION)
        .width('300vp')
        .height('80vp')
        .fontColor('#FFFFFF')
        .fontSize('48fp')
        .allowScale(true) // 当fontSize为‘fp’单位且想要Marquee组件文本跟随系统字体大小缩放，可以设置该属性为true
        .fontWeight(700)
        .fontFamily('HarmonyOS Sans') // 不想跟随主题字体可设置该属性为默认字体'HarmonyOS Sans'
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
          // 启动文本时钟
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

从API版本26.0.0开始，新增onStop接口。

```TypeScript
// xxx.ets
@Entry
@Component
struct MarqueeStop4 {
  @State change: boolean = true;
  @State scrollDirection: String = '正向滚动';
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
            // '收到状态: START';
            this.numberStart++;
          })
          .onBounce(() => {
            // '收到状态: BOUNCE';
            this.numberBounce++;
          })
          .onStop(() => {
            // '收到状态: STOP';
            this.numberStop++;
          })
        Button(this.scrollDirection.toString()).onClick(() => {
          if (this.change) {
            this.change = false;
            this.scrollDirection = '反向滚动';
          } else {
            this.change = true;
            this.scrollDirection = '正向滚动';
          }
        }).margin(20)
      }.height(600).width('100%').padding({ left: 35, right: 35, top: 35 })
    }
  }
}
```
