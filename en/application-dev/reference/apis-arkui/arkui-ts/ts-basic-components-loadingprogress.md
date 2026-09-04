# LoadingProgress
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Zhang-Dong-hui-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=8aa8522c1582655206875d9c89c21656113a2dda translatedAt=2026-09-03T04:10:22.466Z -->

The **LoadingProgress** component is used to display a loading progress bar, providing visual feedback to users during data loading to improve user experience. This component supports features such as setting the foreground color and controlling the animation display state, and is suitable for scenarios where loading progress needs to be displayed in an application.

The loading progress animation stops when the component is invisible. The component's visibility is determined by the value of **ratios** in the [onVisibleAreaChange](./ts-universal-component-visible-area-change-event.md#onvisibleareachange) handler. The component is considered visible when the visibility threshold **ratios** is greater than 0.

>  **NOTE**
>
> - This component is supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
> 
> - This component supports [WithTheme](./ts-container-with-theme.md) since API version 26.0.0.
>

## Child Components

Not supported


## APIs

LoadingProgress()

Creates a loading progress component.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## Attributes

In addition to the [universal attributes](ts-component-general-attributes.md), the following attributes are supported.

>  **NOTE**
>
> The component should be set to a reasonable width and height. When the width and height of the component are set too large, the loading progress animation may not meet the expected effect.

### color

color(value: ResourceColor)

Sets the foreground color for the **LoadingProgress** component.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                      | Mandatory| Description                                                        |
| ------ | ------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | [ResourceColor](ts-types.md#resourcecolor) | Yes   | Foreground color of the loading progress bar.<br>Default value:<br>API version 10 and earlier: '#99666666'<br>API version 11 and later: '#ff666666' |

### enableLoading<sup>10+</sup>

enableLoading(value: boolean)

Sets whether to display the LoadingProgress animation. The component still takes up space in the layout when the loading animation is not shown. The universal attribute [Visibility](ts-appendix-enums.md#visibility).Hidden hides the entire component area, including the regions specified by [border](ts-universal-attributes-border.md#border) and [padding](ts-universal-attributes-size.md#padding). In contrast, when the value of **enableLoading** is set to **false**, only the loading animation itself is hidden without affecting the borders or other elements.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                          |
| ------ | ------- | ---- | ---------------------------------------------- |
| value  | boolean | Yes   | Whether to display the LoadingProgress animation.<br>Default value: true, where true means to display the LoadingProgress animation and false means not to display it. |

### contentModifier<sup>12+</sup>

contentModifier(modifier: ContentModifier\<LoadingProgressConfiguration>)

Creates a content modifier.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                         | Mandatory| Description                                            |
| ------ | --------------------------------------------- | ---- | ------------------------------------------------ |
| modifier  | ContentModifier\<[LoadingProgressConfiguration](#loadingprogressconfiguration12)> | Yes   | Method for customizing the content area on the LoadingProgress component.<br>modifier: content modifier. Developers need to customize a class to implement the ContentModifier interface. |

## Events

The [universal events](ts-component-general-events.md) are supported.

## LoadingProgressConfiguration<sup>12+</sup>

You need a custom class to implement the **ContentModifier** API. Inherits from [CommonConfiguration](ts-universal-attributes-content-modifier.md#commonconfigurationt).

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name | Type   |    Read Only   |    Optional   |  Description             |
| ------ | ------ | ------ |-------------------------------- |-------------------------------- |
| enableLoading | boolean | No | No | Whether to display the LoadingProgress animation.<br>Default value: true, where true means to display the LoadingProgress animation and false means not to display the LoadingProgress animation. |

## LoadingProgressStyle

Enumerates style types of **LoadingProgress**. This API is not recommended for use.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                    | Value| Description                                    |
| ---------------------- | - | ---------------------------------------- |
| Default       | 1 | Default loading style. Setting this value is not supported since API version 8.           |
| Circular      | 2 | Circular loading style. Setting this value is not supported since API version 8.           |
| Orbital       | 3 | Comet-shaped loading style. This is the default style since API version 8.        |

## Example

### Example 1: Setting the Color of the Loading Progress Animation

This example uses the [color](#color) API to set the color of the loading progress bar.

```ts
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

![LoadingProgress](figures/LoadingProgress.gif)

### Example 2: Setting the Custom Content Area

This example uses the [contentModifier](#contentmodifier12) API to customize the content area, and demonstrates how to toggle the display of the custom content based on the [enableLoading](#enableloading10) property of [LoadingProgressConfiguration](#loadingprogressconfiguration12).

```ts
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

      Button('Click to toggle config.enableLoading').onClick(() => {
        this.loadingProgressIndex = (this.loadingProgressIndex + 1) % this.loadingProgressList.length;
        console.info('enableLoading:' + this.loadingProgressList[this.loadingProgressIndex]);
      }).margin(20)
    }

  }
}
```
![LoadingProgress_builder](figures/LoadingProgress_builder.gif)
