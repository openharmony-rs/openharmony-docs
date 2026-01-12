# ArcScrollBar

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @shengu_lancer; @yylong-->
<!--Designer: @yylong-->
<!--Tester: @liuzhenshuo-->
<!--Adviser: @Brilliantry_Rui-->

The **ArcScrollBar** component is designed to be used together with scrollable components such as [ArcList](ts-container-arclist.md), [List](ts-container-list.md), [Grid](ts-container-grid.md), [Scroll](ts-container-scroll.md), and [WaterFlow](ts-container-waterflow.md).

>  **NOTE**
>
>  - This component is supported since API version 18. Updates will be marked with a superscript to indicate their earliest API version.
>  - When the width and height of the **ArcScrollBar** component are not set, the **maxSize** value in the [layout constraint](../js-apis-arkui-frameNode.md#layoutconstraint12) of its parent component is used as the width and height. If the parent component of the **ArcScrollBar** component contains scrollable components, such as [ArcList](ts-container-arclist.md), [List](ts-container-list.md), [Grid](ts-container-grid.md), [Scroll](ts-container-scroll.md), or [WaterFlow](ts-container-waterflow.md), you are advised to set the width and height of the **ArcScrollBar** component. Otherwise, the width and height of the component may be infinite.


## Child Components

Not supported

## APIs

ArcScrollBar(options: ArcScrollBarOptions)

A constructor used to create an **ArcScrollBar** instance.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options |  [ArcScrollBarOptions](#arcscrollbaroptions)| Yes| Parameters of the **ArcScrollBar** component.|

## ArcScrollBarOptions

Represents the parameters used to construct an **ArcScrollBar** component.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -- | -------- | -------- |
| scroller | [Scroller](ts-container-scroll.md#scroller) | No| No| Scroller, which can be bound to scrollable components for scrolling control.|
| state | [BarState](ts-appendix-enums.md#barstate) | No| Yes| State of the scrollbar.<br>Default value: **BarState.Auto**|

>  **NOTE**
> 
> **ArcScrollBar** must be bound to a scrollable component through **scroller** to achieve synchronization. Only a one-to-one binding is allowed between **ArcScrollBar** and a scrollable component.

## Example

This example demonstrates how to use **ArcScrollBar** with a **Scroll** component to create an external circular scrollbar.

```ts
import { ArcScrollBar } from '@kit.ArkUI';

@Entry
@Component
struct ArcScrollBarExample {
  private scroller: Scroller = new Scroller();
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];

  build() {
    Stack({ alignContent: Alignment.Center }) {
      Scroll(this.scroller) {
        Flex({ direction: FlexDirection.Column }) {
          ForEach(this.arr, (item: number) => {
            Row() {
              Text(item.toString())
                .width('80%')
                .height(60)
                .backgroundColor('#3366CC')
                .borderRadius(15)
                .fontSize(16)
                .textAlign(TextAlign.Center)
                .margin({ top: 5 })
            }
          }, (item: number) => item.toString())
        }.margin({ right: 15 })
      }
      .width('90%')
      .scrollBar(BarState.Off)

      ArcScrollBar({ scroller: this.scroller, state: BarState.Auto })
    }
    .width('100%')
    .height('100%')
  }
}
```

![en-us_image_0000001232775585](figures/ArcScrollBar.PNG)
