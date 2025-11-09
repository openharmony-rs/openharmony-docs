# Visible Area Change Event
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @HelloCrease-->

The visible area change event of a component refers to the change in the visual portion of the component on the screen. It can be used to determine whether the component is completely or partially displayed on the screen. It is usually applicable to scenarios such as advertisement exposure tracing.

> **NOTE**
>
>  The APIs of this module are supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.

## onVisibleAreaChange

onVisibleAreaChange(ratios: Array&lt;number&gt;, event: VisibleAreaChangeCallback): T

Called when the visible area of the component changes.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                               | Mandatory| Description                                                        |
| ------ | --------------------------------------------------- | ---- | ------------------------------------------------------------ |
| ratios | Array&lt;number&gt;                                 | Yes  | Threshold array. Each threshold represents a ratio of the component's visible area (that is, the area of the component that is visible on screen; only the area within the parent component is counted) to the component's total area. This callback is invoked when the ratio of the component's visible area to its total area is greater than or less than the threshold. The value range of the threshold is [0.0, 1.0]. If the threshold set exceeds this range, the value **0.0** or **1.0** will be used.<br>**NOTE**<br>When the value is close to the boundary 0 or 1, it is rounded off with a round-off error not greater than 0.001. For example, 0.9997 is rounded off to 1.|
| event  | [VisibleAreaChangeCallback](./ts-universal-component-visible-area-change-event.md#visibleareachangecallback12) | Yes  | Callback for visible area changes of the component.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

> **NOTE**
>- This API can be called in [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier) since API version 20.
>
>- This API only takes into account the relative clipped area ratio of the component with respect to all ancestor nodes (up to the window boundary) and its own area.
> 
>- Blocking calculation of sibling components on their own nodes is not supported. Blocking calculation of all ancestor sibling nodes on their own nodes is not supported. Blocking calculation of windows is not supported. Component rotation calculation is not supported. For example, [Stack](ts-container-stack.md). [Z-order control](ts-universal-attributes-z-order.md), [rotate](ts-universal-attributes-transformation.md#rotate), and so on.
>
>- It does not support visibility change calculations for nodes that are not in the component tree. For example, preloaded nodes or custom nodes mounted using the [overlay](ts-universal-attributes-overlay.md#overlay) capability.

## onVisibleAreaChange<sup>21+</sup>

onVisibleAreaChange(ratios: Array&lt;number&gt;, event: VisibleAreaChangeCallback, measureFromViewport: boolean): T

Called when the visible area of the component changes. You can use measureFromViewport to set the visible region calculation mode.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                               | Mandatory| Description                                                        |
| ------ | --------------------------------------------------- | ---- | ------------------------------------------------------------ |
| ratios | Array&lt;number&gt;                                 | Yes  | Threshold array. Each threshold represents a ratio of a visible area of the component to an area of the component. This callback is invoked when the ratio of the component's visible area to its total area is greater than or less than the threshold. The value range of the threshold is [0.0, 1.0]. If the threshold set exceeds this range, the value **0.0** or **1.0** will be used.<br>**NOTE**<br>When the value is close to the boundary 0 or 1, it is rounded off with a round-off error not greater than 0.001. For example, 0.9997 is rounded off to 1.|
| event  | [VisibleAreaChangeCallback](./ts-universal-component-visible-area-change-event.md#visibleareachangecallback12) | Yes  | Callback for visible area changes of the component.|
| measureFromViewport  | boolean | Yes | Sets the visible region calculation mode.<br>When measureFromViewport is set to true, the system considers the [clip](./ts-universal-attributes-sharp-clipping.md#clip12) attribute of the parent component when calculating the visible area of the component. If [clip](./ts-universal-attributes-sharp-clipping.md#clip12) of the parent component is false, it is considered that the child components in the parent component can be displayed beyond the area of the parent component. Therefore, the area beyond the parent component is also considered as a visible area for calculation. If [clip](./ts-universal-attributes-sharp-clipping.md#clip12) of the parent component is set to true, the area that exceeds the parent component is cropped and cannot be displayed. Therefore, the area is considered as an invisible area for calculation. When measureFromViewport is set to false, the part that exceeds the parent component is regarded as an invisible area without considering the impact of [clip](./ts-universal-attributes-sharp-clipping.md#clip12).|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

> **NOTE**
>
>
>- This API only takes into account the relative clipped area ratio of the component with respect to all ancestor nodes (up to the window boundary) and its own area.
> 
>- Blocking calculation of sibling components on their own nodes is not supported. Blocking calculation of all ancestor sibling nodes on their own nodes is not supported. Blocking calculation of windows is not supported. Component rotation calculation is not supported. For example, [Stack] (ts-container-stack.md). [Z-order control](ts-universal-attributes-z-order.md), [rotate](ts-universal-attributes-transformation.md#rotate), and so on.
>
>- It does not support visibility change calculations for nodes that are not in the component tree. For example, preloaded nodes or custom nodes mounted using the [overlay](ts-universal-attributes-overlay.md#overlay) capability.

## onVisibleAreaApproximateChange<sup>17+</sup>

onVisibleAreaApproximateChange(options: VisibleAreaEventOptions, event: VisibleAreaChangeCallback | undefined): void

Configures a callback for the **onVisibleAreaApproximateChange** event, with options to limit the callback execution interval.

**Atomic service API**: This API can be used in atomic services since API version 17.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| options  | [VisibleAreaEventOptions](#visibleareaeventoptions12) | Yes  | Visible area change configuration options.|
| event  | [VisibleAreaChangeCallback](#visibleareachangecallback12)   \| undefined | Yes  | Callback for the **onVisibleAreaChange** event. This callback is triggered when the ratio of the component's visible area to its total area approaches the threshold set in **options**.|

>**NOTE**
>
>- Compared with [onVisibleAreaChange](./ts-universal-component-visible-area-change-event.md#onvisibleareachange), this API reduces calculation frequency to optimize performance when many nodes are registered. The calculation interval is controlled by the **expectedUpdateInterval** parameter in [VisibleAreaEventOptions](#visibleareaeventoptions12).
>
>- By default, the interval threshold of the visible area change callback includes 0. This means that, if the provided threshold is [0.5], the effective threshold will be [0.0, 0.5].
>
>- This API can be called in custom components since API version 18.

## VisibleAreaEventOptions<sup>12+</sup>

Describes visible area change configuration options.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type                                               | Read-Only| Optional| Description                                                        |
| ------ | --------------------------------------------------- | ---- | -------- | ------------------------------------------------------------ |
| ratios | Array&lt;number&gt;                                 | No| No  | Threshold array. Each threshold represents a ratio of the component's visible area (that is, the area of the component that is visible on screen; only the area within the parent component is counted) to the component's total area. The value range of the threshold is [0.0, 1.0]. If the threshold set exceeds this range, the value **0.0** or **1.0** will be used.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| expectedUpdateInterval | number | No| Yes| Expected calculation interval, in ms.<br>Default value: **1000**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| measureFromViewport<sup>21+</sup> | boolean | No| Yes| Visible area calculation mode.<br>**true**: considers parent's [clip](./ts-universal-attributes-sharp-clipping.md#clip12) attribute. If [clip](./ts-universal-attributes-sharp-clipping.md#clip12) is **false**, areas of the child component beyond the parent's bounds are counted as visible; if [clip](./ts-universal-attributes-sharp-clipping.md#clip12) is **true**, such areas are counted as invisible. **false**: ignores the parent's [clip](./ts-universal-attributes-sharp-clipping.md#clip12) attribute, treating areas beyond the parent's bounds as invisible.<br>Default value: **false**.<br>**Atomic service API**: This API can be used in atomic services since API version 21.|

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

This example demonstrates how to set an **onVisibleAreaChange** event for a component, which triggers the callback when the component is fully displayed or completely hidden.

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
              console.info('Test Text isExpanding: ' + isExpanding + ', currentRatio:' + currentRatio)
              if (isExpanding && currentRatio >= 1.0) {
                console.info('Test Text is fully visible. currentRatio:' + currentRatio)
                this.testTextStr = 'Test Text is fully visible'
              }

              if (!isExpanding && currentRatio <= 0.0) {
                console.info('Test Text is completely invisible.')
                this.testTextStr = 'Test Text is completely invisible'
              }
            })

          Row() {
            Text('Test Row Visible  Change')
              .fontSize(20)
              .margin({ bottom: 20 })

          }
          .height(200)
          .backgroundColor(Color.Yellow)
          .onVisibleAreaChange([0.0, 1.0], (isExpanding: boolean, currentRatio: number) => {
            console.info('Test Row isExpanding:' + isExpanding + ', currentRatio:' + currentRatio)
            if (isExpanding && currentRatio >= 1.0) {
              console.info('Test Row is fully visible.')
              this.testRowStr = 'Test Row is fully visible'
            }

            if (!isExpanding && currentRatio <= 0.0) {
              console.info('Test Row is completely invisible.')
              this.testRowStr = 'Test Row is completely invisible'
            }
          })

          ForEach(this.arr, (item:number) => {
            Text(item.toString())
              .width('90%')
              .height(150)
              .backgroundColor(0xFFFFFF)
              .borderRadius(15)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .margin({ top: 10 })
          }, (item:number) => (item.toString()))

        }.width('100%')
      }
      .backgroundColor(0x317aff)
      .scrollable(ScrollDirection.Vertical)
      .scrollBar(BarState.On)
      .scrollBarColor(Color.Gray)
      .scrollBarWidth(10)
      .onWillScroll((xOffset: number, yOffset: number, scrollState: ScrollState) => {
        console.info(xOffset + ' ' + yOffset)
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

This example demonstrates how to set an **onVisibleAreaApproximateChange** event for a component, which triggers the callback when the component is fully displayed or completely hidden.

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
            .onVisibleAreaApproximateChange({ratios: [0.0, 1.0], expectedUpdateInterval: 1000}, (isExpanding: boolean, currentRatio: number) => {
              console.info('Test Text isExpanding: ' + isExpanding + ', currentRatio:' + currentRatio)
              if (isExpanding && currentRatio >= 1.0) {
                console.info('Test Text is fully visible. currentRatio:' + currentRatio)
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
            console.info('Test Row isExpanding:' + isExpanding + ', currentRatio:' + currentRatio)
            if (isExpanding && currentRatio >= 1.0) {
              console.info('Test Row is fully visible.')
              this.testRowStr = 'Test Row is fully visible'
            }

            if (!isExpanding && currentRatio <= 0.0) {
              console.info('Test Row is completely invisible.')
              this.testRowStr = 'Test Row is completely invisible'
            }
          })

          ForEach(this.arr, (item:number) => {
            Text(item.toString())
              .width('90%')
              .height(150)
              .backgroundColor(0xFFFFFF)
              .borderRadius(15)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .margin({ top: 10 })
          }, (item:number) => (item.toString()))

        }.width('100%')
      }
      .backgroundColor(0x317aff)
      .scrollable(ScrollDirection.Vertical)
      .scrollBar(BarState.On)
      .scrollBarColor(Color.Gray)
      .scrollBarWidth(10)
      .onWillScroll((xOffset: number, yOffset: number, scrollState: ScrollState) => {
        console.info(xOffset + ' ' + yOffset)
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
