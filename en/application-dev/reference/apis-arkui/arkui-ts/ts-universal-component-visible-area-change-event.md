# Visible Area Change Event
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

The visible area change event of a component refers to the change in the visual portion of the component on the screen. It can be used to determine whether the component is completely or partially displayed on the screen. It is usually applicable to scenarios such as advertisement exposure tracing.

> **NOTE**
>
>  The APIs of this module are supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.

## onVisibleAreaChange

onVisibleAreaChange(ratios: Array&lt;number&gt;, event: VisibleAreaChangeCallback): T

Called when the visible area of the component changes. For details about the development guidelines and FAQs, see [Detecting Component Visibility](./../../../ui/arkts-manage-components-visibility.md).

> **NOTE**
>
>- This API can be called in [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier) since API version 20.
>
>- This API only takes into account the relative clipped area ratio of the component with respect to all ancestor nodes (up to the window boundary) and its own area.
> 
>- The following calculation scenarios are not supported: clipping by sibling nodes, clipping by siblings of any ancestor node, window-level occlusion, and component rotation. Examples include layouts using [Stack](ts-container-stack.md), [z-order control](ts-universal-attributes-z-order.md), and [rotate](ts-universal-attributes-transformation.md#rotate) transformations.
>
>- It does not support visibility change calculations for nodes that are not in the component tree. For example, preloaded nodes or custom nodes mounted using the [overlay](ts-universal-attributes-overlay.md#overlay) capability.
>
>- This API does not support the [scale](ts-universal-attributes-transformation.md#scale) attribute. To enable support for the [scale](ts-universal-attributes-transformation.md#scale) attribute, use [onVisibleAreaChange<sup>22+</sup>](#onvisibleareachange22) and set **measureFromViewport** to **true**.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                               | Mandatory| Description                                                        |
| ------ | --------------------------------------------------- | ---- | ------------------------------------------------------------ |
| ratios | Array&lt;number&gt;                                 | Yes  | Threshold array. Each threshold represents a ratio of the component's visible area (that is, the area of the component that is visible on screen; only the area within the parent component is counted) to the component's total area. This callback is invoked when the ratio of the component's visible area to its total area is greater than or less than the threshold. The value of each threshold ranges from 0.0 to 1.0. If a threshold value is less than 0.0, it is clamped to 0.0; if it is greater than 1.0, it is clamped to 1.0.<br>**NOTE**<br>When the value is close to the boundary 0 or 1, it is rounded off with a round-off error not greater than 0.001. For example, 0.9997 is rounded off to 1.|
| event  | [VisibleAreaChangeCallback](./ts-universal-component-visible-area-change-event.md#visibleareachangecallback12) | Yes  | Callback for visible area changes of the component.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

## onVisibleAreaChange<sup>22+</sup>

onVisibleAreaChange(ratios: Array&lt;number&gt;, event: VisibleAreaChangeCallback, measureFromViewport: boolean): T

Called when the visible area of the component changes. You can use **measureFromViewport** to set the visible area calculation mode. For details about the development guidelines and FAQs, see [Detecting Component Visibility](./../../../ui/arkts-manage-components-visibility.md).

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                               | Mandatory| Description                                                        |
| ------ | --------------------------------------------------- | ---- | ------------------------------------------------------------ |
| ratios | Array&lt;number&gt;                                 | Yes  | Threshold array. Each threshold represents a ratio of a visible area of the component to an area of the component. This callback is invoked when the ratio of the component's visible area to its total area is greater than or less than the threshold. The value of each threshold ranges from 0.0 to 1.0. If a threshold value is less than 0.0, it is clamped to 0.0; if it is greater than 1.0, it is clamped to 1.0.<br>**NOTE**<br>When the value is close to the boundary 0 or 1, it is rounded off with a round-off error not greater than 0.001. For example, 0.9997 is rounded off to 1.|
| event  | [VisibleAreaChangeCallback](./ts-universal-component-visible-area-change-event.md#visibleareachangecallback12) | Yes  | Callback for visible area changes of the component.|
| measureFromViewport  | boolean | Yes | Visible area calculation mode.<br>**true**: considers the parent's [clip](./ts-universal-attributes-sharp-clipping.md#clip12) attribute. If [clip](./ts-universal-attributes-sharp-clipping.md#clip12) is **false**, areas of the child component beyond the parent's bounds are counted as visible; if [clip](./ts-universal-attributes-sharp-clipping.md#clip12) is **true**, such areas are counted as invisible. **false**: ignores the parent's [clip](./ts-universal-attributes-sharp-clipping.md#clip12) attribute, treating areas beyond the parent's bounds as invisible.<br>When **measureFromViewport** is set to **true**, and an ancestor node has the [scale](ts-universal-attributes-transformation.md#scale) attribute set, the visible area of the component will be correctly calculated.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

> **NOTE**
>
>
>- This API only takes into account the relative clipped area ratio of the component with respect to all ancestor nodes (up to the window boundary) and its own area.
> 
>- The following calculation scenarios are not supported: clipping by sibling nodes, clipping by siblings of any ancestor node, window-level occlusion, and component rotation. Examples include layouts using [Stack](ts-container-stack.md), [z-order control](ts-universal-attributes-z-order.md), and [rotate](ts-universal-attributes-transformation.md#rotate) transformations.
>
>- It does not support visibility change calculations for nodes that are not in the component tree. For example, preloaded nodes or custom nodes mounted using the [overlay](ts-universal-attributes-overlay.md#overlay) capability.

## onVisibleAreaApproximateChange<sup>17+</sup>

onVisibleAreaApproximateChange(options: VisibleAreaEventOptions, event: VisibleAreaChangeCallback | undefined): T

Configures a callback for the **onVisibleAreaApproximateChange** event, with options to limit the callback execution interval.

> **NOTE**
>
> This API cannot be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier).

**Atomic service API**: This API can be used in atomic services since API version 17.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| options  | [VisibleAreaEventOptions](#visibleareaeventoptions12) | Yes  | Visible area change configuration options.|
| event  | [VisibleAreaChangeCallback](#visibleareachangecallback12)   \| undefined | Yes  | Callback for the **onVisibleAreaChange** event. This callback is triggered when the ratio of the component's visible area to its total area approaches the threshold set in **options**.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

>**NOTE**
>
>- Compared with [onVisibleAreaChange](./ts-universal-component-visible-area-change-event.md#onvisibleareachange), this API reduces calculation frequency to optimize performance when many nodes are registered. The calculation interval is controlled by the **expectedUpdateInterval** parameter in [VisibleAreaEventOptions](#visibleareaeventoptions12).
>
>- By default, the interval threshold of the visible area change callback includes 0. This means that, if the provided threshold is [0.5], the effective threshold will be [0.0, 0.5].
>
>- This API can be called in custom components since API version 18.
>
>- This API does not support the [scale](ts-universal-attributes-transformation.md#scale) attribute. To enable support for the [scale](ts-universal-attributes-transformation.md#scale) attribute, set **measureFromViewport** in [VisibleAreaEventOptions](#visibleareaeventoptions12) to **true**.
>
>- Since API version 21, the return value type is changed from **void** to **T**.

## VisibleAreaEventOptions<sup>12+</sup>

Describes visible area change configuration options.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type                                               | Read-Only| Optional| Description                                                        |
| ------ | --------------------------------------------------- | ---- | -------- | ------------------------------------------------------------ |
| ratios | Array&lt;number&gt;                                 | No| No  | Threshold array. Each threshold represents a ratio of the component's visible area (that is, the area of the component that is visible on screen; only the area within the parent component is counted) to the component's total area. The value of each threshold ranges from 0.0 to 1.0. If a threshold value is less than 0.0, it is clamped to 0.0; if it is greater than 1.0, it is clamped to 1.0.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| expectedUpdateInterval | number | No| Yes| Expected calculation interval, in ms.<br>Default value: **1000**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| measureFromViewport<sup>22+</sup> | boolean | No| Yes| Visible area calculation mode.<br>**true**: considers the parent's [clip](./ts-universal-attributes-sharp-clipping.md#clip12) attribute. If [clip](./ts-universal-attributes-sharp-clipping.md#clip12) is **false**, areas of the child component beyond the parent's bounds are counted as visible; if [clip](./ts-universal-attributes-sharp-clipping.md#clip12) is **true**, such areas are counted as invisible. **false**: ignores the parent's [clip](./ts-universal-attributes-sharp-clipping.md#clip12) attribute, treating areas beyond the parent's bounds as invisible.<br>Default value: **false**.<br>If **measureFromViewport** is set to **true**, and an ancestor node has the [scale](ts-universal-attributes-transformation.md#scale) attribute set, the visible area of the component will be correctly calculated.<br>**Atomic service API**: This API can be used in atomic services since API version 22.|

## VisibleAreaChangeCallback<sup>12+</sup>

type VisibleAreaChangeCallback = (isExpanding: boolean, currentRatio: number) => void

Represents a callback for visible area changes of the component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name           | Type              | Mandatory     | Description                                      |
| ------------- | ------------------   | ------------- | ---------------------- |
| isExpanding | boolean | Yes| Whether the component's visible area has increased or decreased relative to its total area since the last callback. The value **true** indicates that the visible area has increased, and **false** indicates that the visible area has decreased.|
| currentRatio | number | Yes| Ratio of the visible area of a component to its own area when a callback is triggered.|

## Example

### Example 1: Using onVisibleAreaChange to Listen for Visible Area Changes

This example demonstrates how to set an [onVisibleAreaChange](#onvisibleareachange) event for a component, which triggers the callback when the component is fully displayed or completely hidden.

```ts
// xxx.ets
@Entry
@Component
struct ScrollExample {
  scroller: Scroller = new Scroller()
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
  @State testTextStr: string = 'test'
  @State testRowStr: string = 'test'

  build() {
    Column() {
      Column() {
        Text(this.testTextStr)
          .fontSize(20)

        Text(this.testRowStr)
          .fontSize(20)
      }
      .height(100)
      .backgroundColor(Color.Gray)
      .opacity(0.3)

      Scroll(this.scroller) {
        Column() {
          Text("Test Text Visible Change")
            .fontSize(20)
            .height(200)
            .margin({ top: 50, bottom: 20 })
            .backgroundColor(Color.Green)
            // Set ratios to [0.0, 1.0] to invoke the callback when the component is fully visible or invisible on screen.
            .onVisibleAreaChange([0.0, 1.0], (isExpanding: boolean, currentRatio: number) => {
              console.info(`Test Text isExpanding: ${isExpanding}, currentRatio: ${currentRatio}`)
              if (isExpanding && currentRatio >= 1.0) {
                console.info(`Test Text is fully visible. currentRatio: ${currentRatio}`)
                this.testTextStr = 'Test Text is fully visible'
              }

              if (!isExpanding && currentRatio <= 0.0) {
                console.info('Test Text is completely invisible.')
                this.testTextStr = 'Test Text is completely invisible'
              }
            })

          Row() {
            Text('Test Row Visible Change')
              .fontSize(20)
              .margin({ bottom: 20 })

          }
          .height(200)
          .backgroundColor(Color.Yellow)
          .onVisibleAreaChange([0.0, 1.0], (isExpanding: boolean, currentRatio: number) => {
            console.info(`Test Text isExpanding: ${isExpanding}, currentRatio: ${currentRatio}`)
            if (isExpanding && currentRatio >= 1.0) {
              console.info('Test Row is fully visible.')
              this.testRowStr = 'Test Row is fully visible'
            }

            if (!isExpanding && currentRatio <= 0.0) {
              console.info('Test Row is completely invisible.')
              this.testRowStr = 'Test Row is completely invisible'
            }
          })

          ForEach(this.arr, (item: number) => {
            Text(item.toString())
              .width('90%')
              .height(150)
              .backgroundColor(0xFFFFFF)
              .borderRadius(15)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .margin({ top: 10 })
          }, (item: number) => (item.toString()))

        }.width('100%')
      }
      .backgroundColor(0x317aff)
      .scrollable(ScrollDirection.Vertical)
      .scrollBar(BarState.On)
      .scrollBarColor(Color.Gray)
      .scrollBarWidth(10)
      .onWillScroll((xOffset: number, yOffset: number, scrollState: ScrollState) => {
        console.info(`${xOffset} ${yOffset}`)
      })
      .onScrollEdge((side: Edge) => {
        console.info('To the edge')
      })
      .onScrollStop(() => {
        console.info('Scroll Stop')
      })

    }.width('100%').height('100%').backgroundColor(0xDCDCDC)
  }
}
```

### Example 2: Using onVisibleAreaApproximateChange to Listen for Visible Area Changes

This example demonstrates how to set an [onVisibleAreaApproximateChange](#onvisibleareaapproximatechange17) event for a component, which triggers the callback when the component is fully displayed or completely hidden. This feature is supported from API version 17.

```ts
// xxx.ets
@Entry
@Component
struct ScrollExample {
  scroller: Scroller = new Scroller()
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
  @State testTextStr: string = 'test'
  @State testRowStr: string = 'test'

  build() {
    Column() {
      Column() {
        Text(this.testTextStr)
          .fontSize(20)

        Text(this.testRowStr)
          .fontSize(20)
      }
      .height(100)
      .backgroundColor(Color.Gray)
      .opacity(0.3)

      Scroll(this.scroller) {
        Column() {
          Text("Test Text Visible Change")
            .fontSize(20)
            .height(200)
            .margin({ top: 50, bottom: 20 })
            .backgroundColor(Color.Green)
            // Set ratios to [0.0, 1.0] to invoke the callback when the component is fully visible or invisible on screen.
            .onVisibleAreaApproximateChange({ ratios: [0.0, 1.0], expectedUpdateInterval: 1000 },
              (isExpanding: boolean, currentRatio: number) => {
                console.info(`Test Text isExpanding: ${isExpanding}, currentRatio: ${currentRatio}`)
                if (isExpanding && currentRatio >= 1.0) {
                  console.info(`Test Text is fully visible. currentRatio: ${currentRatio}`)
                  this.testTextStr = 'Test Text is fully visible'
                }

                if (!isExpanding && currentRatio <= 0.0) {
                  console.info('Test Text is completely invisible.')
                  this.testTextStr = 'Test Text is completely invisible'
                }
              })

          Row() {
            Text('Test Row Visible Change')
              .fontSize(20)
              .margin({ bottom: 20 })

          }
          .height(200)
          .backgroundColor(Color.Yellow)
          .onVisibleAreaChange([0.0, 1.0], (isExpanding: boolean, currentRatio: number) => {
            console.info(`Test Text isExpanding: ${isExpanding}, currentRatio: ${currentRatio}`)
            if (isExpanding && currentRatio >= 1.0) {
              console.info('Test Row is fully visible.')
              this.testRowStr = 'Test Row is fully visible'
            }

            if (!isExpanding && currentRatio <= 0.0) {
              console.info('Test Row is completely invisible.')
              this.testRowStr = 'Test Row is completely invisible'
            }
          })

          ForEach(this.arr, (item: number) => {
            Text(item.toString())
              .width('90%')
              .height(150)
              .backgroundColor(0xFFFFFF)
              .borderRadius(15)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .margin({ top: 10 })
          }, (item: number) => (item.toString()))

        }.width('100%')
      }
      .backgroundColor(0x317aff)
      .scrollable(ScrollDirection.Vertical)
      .scrollBar(BarState.On)
      .scrollBarColor(Color.Gray)
      .scrollBarWidth(10)
      .onWillScroll((xOffset: number, yOffset: number, scrollState: ScrollState) => {
        console.info(`${xOffset} ${yOffset}`)
      })
      .onScrollEdge((side: Edge) => {
        console.info('To the edge')
      })
      .onScrollStop(() => {
        console.info('Scroll Stop')
      })

    }.width('100%').height('100%').backgroundColor(0xDCDCDC)
  }
}
```
![en-us_visible_area_change.gif](figures/en-us_visible_area_change.gif)

### Example 3: Allowing the Child Component to Display Beyond the Parent Component When measureFromViewport Is Set to true

Starting from API version 22, this example demonstrates the effect comparison of setting **measureFromViewport** in the **onVisibleAreaChange** event. The core difference lies in the returned component visibility ratio (**currentRatio**): When **measureFromViewport** is set to **true**, the returned **currentRatio** value is more consistent with the actual display effect. The **currentRatio** value varies slightly on different devices.

```ts
@Entry
@Component
struct OnVisibleAreaChangeSample {
  @State ratio1: number = 0.0;
  @State ratio2: number = 0.0;
  @State ratio3: number = 0.0;

  build() {
    Column() {
      Text(`onVisibleChange1 with measureFromViewport \nratio: ${this.ratio1}`)
      Column() {
        Row() {
          Row() {

          }
          .backgroundColor(Color.Blue)
          .height(120)
          .width(120)
          .offset({ x: 0, y: 60 })
          // If measureFromViewport is set to true and clip (true) is not set for the parent component, any area of the child component that extends beyond its parent component is regarded as a visible area.
          .onVisibleAreaApproximateChange({
            ratios: [0.0, 1.0],
            expectedUpdateInterval: 500,
            measureFromViewport: true
          }, (isExpanding: boolean, currentRatio: number) => {
            console.log(`onVisibleAreaApproximateChange1 isExpanding: ${isExpanding} currentRatio: ${currentRatio}`)
          })
          .onVisibleAreaChange([0.0, 1.0], (isExpanding: boolean, currentRatio: number) => {
            this.ratio1 = currentRatio
          }, true)
        }
        .backgroundColor(Color.Pink)
        .height(120)
        .width(120)
      }
      .padding(5)
      .borderWidth(1)
      .height(200)
      .width(200)

      Text(`onVisibleChange2 without measureFromViewport \nratio: ${this.ratio2}`)
      Column() {
        Row() {
          Row() {

          }
          .backgroundColor(Color.Blue)
          .height(120)
          .width(120)
          .offset({ x: 0, y: 60 })
          // If measureFromViewport is not set, the default value false is used. If clip (true) is not set for the parent component, any area of a component that extends beyond its parent component regarded as an invisible area.
          .onVisibleAreaApproximateChange({ ratios: [0.0, 1.0], expectedUpdateInterval: 500 },
            (isExpanding: boolean, currentRatio: number) => {
              console.log(`onVisibleAreaApproximateChange2 isExpanding: ${isExpanding} currentRatio: ${currentRatio}`)
            })
          .onVisibleAreaChange([0.0, 1.0], (isExpanding: boolean, currentRatio: number) => {
            this.ratio2 = currentRatio
          })
        }
        .backgroundColor(Color.Pink)
        .height(120)
        .width(120)
      }
      .padding(5)
      .borderWidth(1)
      .height(200)
      .width(200)

      Text(`parent set clip(true) onVisibleChange3 with measureFromViewport \nratio: ${this.ratio3}`)
      Column() {
        Row() {
          Row() {

          }
          .backgroundColor(Color.Blue)
          .height(120)
          .width(120)
          .offset({ x: 0, y: 60 })
          // If measureFromViewport is set to true and clip is set to true for the parent component, any area of the child component that extends beyond its parent component regarded as an invisible area.
          .onVisibleAreaApproximateChange({
            ratios: [0.0, 1.0],
            expectedUpdateInterval: 500,
            measureFromViewport: true
          }, (isExpanding: boolean, currentRatio: number) => {
            console.log(`onVisibleAreaApproximateChange3 isExpanding: ${isExpanding} currentRatio: ${currentRatio}`)
          })
          .onVisibleAreaChange([0.0, 1.0], (isExpanding: boolean, currentRatio: number) => {
            this.ratio3 = currentRatio
          }, true)
        }
        .clip(true)
        .backgroundColor(Color.Pink)
        .height(120)
        .width(120)
      }
      .padding(5)
      .borderWidth(1)
      .height(200)
      .width(200)
    }
    .height('100%')
    .width('100%')
  }
}
```
![en-us_visible_area_change.gif](figures/en-us_visible_area_change3.jpg)
