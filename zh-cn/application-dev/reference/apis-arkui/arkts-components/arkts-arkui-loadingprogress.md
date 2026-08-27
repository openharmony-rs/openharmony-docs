# LoadingProgress

LoadingProgress是用于显示加载进度条的组件，在数据加载过程中为用户提供视觉反馈，提升用户体验。该组件支持设置前景色、控制动画显示状态等特性，适用于需要在应用内展示加载进度的场景。
加载进度条的动效在组件不可见时停止，组件的可见状态基于 [onVisibleAreaChange](arkts-arkui-commonmethod-c.md#onvisibleareachange) 处理，可见阈值ratios大于0即视为可见状态。
> **说明：** > > - 该组件从API版本26.0.0开始支持WithTheme。

## 子组件

无

## LoadingProgress

```TypeScript
LoadingProgress()
```

创建加载进度组件。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [LoadingProgressConfiguration](arkts-arkui-loadingprogressconfiguration-i.md) | 开发者需要自定义class实现ContentModifier接口。继承自[CommonConfiguration](arkts-arkui-commonconfiguration-i.md)。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [LoadingProgressStyle](arkts-arkui-loadingprogressstyle-e.md) | 表示LoadingProgress的样式类型，不推荐使用。 |

## 示例

该示例通过[color](#color)接口，实现了设置加载进度条颜色的功能。

```TypeScript
// xxx.ets
@Entry
@Component
struct LoadingProgressExample {
  build() {
    Column({ space: 5 }) {
      Text('Orbital LoadingProgress ').fontSize(9).fontColor(0xCCCCCC).width('90%')
      LoadingProgress()
        .color(Color.Blue)
        .layoutWeight(1)
    }.width('100%').margin({ top: 5 })
  }
}
```

该示例通过[contentModifier](#contentmodifier12)接口，实现了定制内容区的功能，并通过[enableLoading](#enableloading10)接口实现了通过按钮切换是否显示LoadingProgress的效果。

```TypeScript
// xxx.ets
import { UIContext } from '@kit.ArkUI';

class MyLoadingProgressStyle implements ContentModifier<LoadingProgressConfiguration> {
  enableLoading: boolean = false;
  ctx: UIContext | undefined = undefined;

  constructor(enableLoading: boolean, ctx: UIContext) {
    this.enableLoading = enableLoading;
    this.ctx = ctx;
  }

  applyContent(): WrappedBuilder<[LoadingProgressConfiguration]> {
    return wrapBuilder(buildLoadingProgress);
  }
}

let arr: string[] = ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9'];

@Builder
function buildLoadingProgress(config: LoadingProgressConfiguration) {
  Column({ space: 8 }) {
    Row() {
      Column() {
        Circle({
          width: ((config.contentModifier as MyLoadingProgressStyle).enableLoading) ? 100 : 80,
          height: ((config.contentModifier as MyLoadingProgressStyle).enableLoading) ? 100 : 80
        })
          .fill(((config.contentModifier as MyLoadingProgressStyle).enableLoading) ? Color.Grey : 0x2577e3)
      }.width('50%')

      Column() {
        Button('' + ((config.contentModifier as MyLoadingProgressStyle).enableLoading))
          .onClick((event: ClickEvent) => {
            let uiContext = (config.contentModifier as MyLoadingProgressStyle).ctx;
            if (uiContext) {
              uiContext.getPromptAction().showToast({
                message: ((config.contentModifier as MyLoadingProgressStyle).enableLoading) + ''
              });
            }
          })
          .fontColor(Color.White)
          .backgroundColor(((config.contentModifier as MyLoadingProgressStyle).enableLoading) ? Color.Grey : 0x2577e3)
      }.width('50%')

    }

    Row() {
      Column() {
        Gauge({
          value: (config.contentModifier as MyLoadingProgressStyle).enableLoading ? 50 : 30, min: 11, max: 100
        }) {
          Column() {
            Text('60')
              .maxFontSize('180sp')
              .minFontSize('160.0vp')
              .fontWeight(FontWeight.Medium)
              .fontColor('#ff182431')
              .width('40%')
              .height('30%')
              .textAlign(TextAlign.Center)
              .margin({ top: '22.2%' })
              .textOverflow({ overflow: TextOverflow.Ellipsis })
              .maxLines(1)
          }.width('100%').height('100%')
        }
        .colors(((config.contentModifier as MyLoadingProgressStyle).enableLoading) ? Color.Grey : 0x2577e3)
        .width(200)
        .strokeWidth(18)
        .padding(5)
        .trackShadow({ radius: 7, offsetX: 7, offsetY: 7 })
        .height(200)
      }.width('100%')

    }

    Column() {
      List({ space: 20, initialIndex: 0 }) {
        ForEach(arr, (item: string) => {
          ListItem() {
            Text((config.contentModifier as MyLoadingProgressStyle).enableLoading ? '' + item : Number(item) * 2 + '')
              .width('100%')
              .height('100%')
              .fontColor((config.contentModifier as MyLoadingProgressStyle).enableLoading ? Color.White : Color.Orange)
              .fontSize((config.contentModifier as MyLoadingProgressStyle).enableLoading ? 16 : 20)
              .textAlign(TextAlign.Center)
              .backgroundColor((config.contentModifier as MyLoadingProgressStyle).enableLoading ? Color.Grey : 0x2577e3)
          }
          .height(110)
          .border({
            width: 2,
            color: Color.White
          })
        }, (item: string) => item)
      }
      .height(200)
      .width('100%')
      .friction(0.6)

      .lanes({
        minLength: (config.contentModifier as MyLoadingProgressStyle).enableLoading ? 40 : 80,
        maxLength: (config.contentModifier as MyLoadingProgressStyle).enableLoading ? 40 : 80
      })
      .scrollBar(BarState.Off)
    }

  }.width('100%').padding(10)
}


@Entry
@Component
struct LoadingProgressDemoExample {
  @State loadingProgressList: (boolean | undefined | null)[] = [undefined, true, null, false];
  @State loadingProgressIndex: number = 0;
  @State clickFlag: number = 0;
  scroller: Scroller = new Scroller();

  build() {
    Column() {
      Scroll(this.scroller) {
        Column({ space: 5 }) {
          Column() {
            LoadingProgress()
              .color('#106836')
              .size({ width: '100%' })
              .contentModifier(new MyLoadingProgressStyle(this.loadingProgressList[this.loadingProgressIndex], this.getUIContext()))
          }.width('100%').backgroundColor(0xdcdcdc)
        }.width('100%').margin({ top: 5 })
      }.height('85%')

      Button('点击切换config.enableLoading').onClick(() => {
        this.clickFlag++;
        this.loadingProgressIndex = (this.loadingProgressIndex + 1) % this.loadingProgressList.length;
        console.info('enableLoading:' + this.loadingProgressList[this.loadingProgressIndex]);
      }).margin(20)
    }

  }
}
```
