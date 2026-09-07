# ArcScrollBar

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @shengu_lancer; @rongShao-Z-->
<!--Designer: @yangcan18-->
<!--Tester: @leiyuqian-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=608175d8fd85ddfce5e6f9d9b165b9d12862adb2 translatedAt=2026-09-03T03:45:42.137Z -->

The **ArcScrollBar** component is an arc-shaped scroll bar suitable for scenarios that require an arc-shaped scroll bar, such as circular screens. It is designed to be used together with scrollable components such as [ArcList](ts-container-arclist.md), [List](ts-container-list.md), [Grid](ts-container-grid.md), [Scroll](ts-container-scroll.md), and [WaterFlow](ts-container-waterflow.md).

> **NOTE**
>
> - This component is supported since API version 18. Updates will be marked with a superscript to indicate their earliest API version.
> - When the width and height are not set, **ArcScrollBar** uses the maxSize in the parent component's [LayoutConstraint](../js-apis-arkui-frameNode.md#layoutconstraint12) as its size. If the parent component contains a scrollable component, such as [ArcList](ts-container-arclist.md), [List](ts-container-list.md), [Grid](ts-container-grid.md), [Scroll](ts-container-scroll.md), or [WaterFlow](ts-container-waterflow.md), you are advised to set the width and height of **ArcScrollBar**; otherwise, the size may be infinite.
> - This component can be used on phones, PCs/2-in-1s, tablets, TVs, and wearables. In API version 22 and earlier, using this component on phones, PCs/2-in-1s, tablets, and TVs generates a compilation warning, but the component can still run normally.


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
| options | [ArcScrollBarOptions](#arcscrollbaroptions) | Yes | Configuration parameters of ArcScrollBar, used to specify the bound scrollable component controller and scroll bar state. |

## ArcScrollBarOptions

Represents the parameters used to construct an **ArcScrollBar** component.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -- | -------- | -------- |
| scroller | [Scroller](ts-container-scroll.md#scroller) | No | No | Controller of a scrollable component, used to bind to the scrollable component. Before setting it, create a Scroller object and pass it to the corresponding scrollable component. |
| state | [BarState](ts-appendix-enums.md#barstate) | No | Yes | State of the scroll bar. The value can be BarState.Off (0, not displayed), BarState.Auto (1, displayed as needed, shown on touch and hidden after 2s), or BarState.On (2, always displayed).<br/>Default value: BarState.Auto |

>  **NOTE**
> 
> **ArcScrollBar** must be bound to a scrollable component through **scroller** to achieve synchronization. Only a one-to-one binding is allowed between **ArcScrollBar** and a scrollable component.

## Example

This example demonstrates how to synchronize **ArcScrollBar** with the [Scroll](ts-container-scroll.md) component to implement an arc scrollbar.

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