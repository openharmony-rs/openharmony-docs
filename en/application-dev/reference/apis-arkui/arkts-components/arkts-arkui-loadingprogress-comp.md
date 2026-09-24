# LoadingProgress

The **LoadingProgress** component is used to create a loading progress animation.

The loading progress animation stops when the component is invisible. The component's visibility is determined by the value of **ratios** in the [onVisibleAreaChange](arkts-arkui-common-comp-commonmethod-c.md#onvisibleareachange) event callback: If the value is greater than 0, the component is visible.

> **NOTE** > > - This component supports [WithTheme](arkts-arkui-withtheme-comp.md#with_themedefines-withtheme-component) since API version 26.0.0.

## Child Components

Not supported

## LoadingProgress

```TypeScript
LoadingProgress()
```

Creates a loading progress component.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [LoadingProgressConfiguration](arkts-arkui-loadingprogress-comp-loadingprogressconfiguration-i.md) | You need a custom class to implement the **ContentModifier** API. Inherits from [CommonConfiguration](arkts-arkui-common-comp-commonconfiguration-i.md). |

### Enums

| Name | Description |
| --- | --- |
| [LoadingProgressStyle](arkts-arkui-loadingprogress-comp-loadingprogressstyle-e.md) | Enumerates style types of **LoadingProgress**. This API is not recommended for use. |

## Examples

### Example 1: Setting the Color of the Loading Progress Animation

This example demonstrates how to set the color of the loading progress bar using the [color](#color) API.



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

### Example 2: Setting the Custom Content Area

This example demonstrates how to customize the content area using the [contentModifier](#contentmodifier12) API, and how to toggle the display of the custom content based on the [enableLoading](#enableloading10) attribute of [LoadingProgressConfiguration](arkts-arkui-loadingprogress-comp-loadingprogressconfiguration-i.md).

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

      Button('Switch config.enableLoading').onClick(() => {
        this.loadingProgressIndex = (this.loadingProgressIndex + 1) % this.loadingProgressList.length;
        console.info('enableLoading:' + this.loadingProgressList[this.loadingProgressIndex]);
      }).margin(20)
    }

  }
}
```
