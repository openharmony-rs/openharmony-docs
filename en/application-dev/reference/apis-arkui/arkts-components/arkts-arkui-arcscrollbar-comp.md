# ArcScrollBar

The **ArcScrollBar** component is designed to be used together with scrollable components such as [ArcList](arkts-arkui-arclist-comp.md#ohosarkuiarclist), List, Grid, Scroll, and WaterFlow.

> **NOTE** > > - This component is supported since API version 18. Updates will be marked with a superscript to indicate their > earliest API version. > > - When the width and height of the **ArcScrollBar** component are not set, the **maxSize** value specified in its > parent component [LayoutConstraint](../arkts-apis/arkts-arkui-framenode-layoutconstraint-i.md) is used as the width and height. If > the parent component of the **ArcScrollBar** component contains scrollable components, such as > [ArcList](arkts-arkui-arclist-comp.md#ohosarkuiarclist), List, > Grid, Scroll, or > WaterFlow, you are advised to set the width and height of the > **ArcScrollBar** component. Otherwise, the width and height of the component may be infinite. > > - This component can be used on phones, PCs, 2-in-1 devices, tablets, TVs, and wearables. In API version 22 and > earlier versions, a compilation warning will be reported when this component is used on phones, PCs, 2-in-1 devices > , tablets, and TVs, but the component can still run properly.

## Child Components

Not supported

## ArcScrollBar

```TypeScript
ArcScrollBar(options: ArcScrollBarOptions)
```

A constructor used to create an **ArcScrollBar** instance.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ArcScrollBarOptions](arkts-arkui-arcscrollbar-comp-arcscrollbaroptions-i.md) | Yes | Parameters of the **ArcScrollBar** component. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [ArcScrollBarOptions](arkts-arkui-arcscrollbar-comp-arcscrollbaroptions-i.md) | Represents the parameters used to construct an **ArcScrollBar** component. |

## Examples

This example demonstrates how to synchronize ArcScrollBar with the [Scroll](ts-container-scroll.md) component to implement an arc scrollbar.

```TypeScript
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
