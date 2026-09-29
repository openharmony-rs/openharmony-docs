# ArcList

An arc list consists of a series of list items arranged along an arc, suitable for circular screen devices. It is ideal for continuously presenting multiple rows of similar data, such as images and text.

> **NOTE:** 
> 
> - This component can be used on phones, PCs, 2-in-1 devices, tablets, TVs, and wearables. In API version 22 and earlier versions, a compilation warning will be reported when this component is used on phones, PCs, 2-in-1devices, tablets, and TVs, but the component can still run properly.

## Child Components

Only the [ArcListItem](arkts-arkui-arclist-comp-con.md#arclistitem) component is supported.

> **NOTE:** 
> 
> Rules for calculating the index value of child components in **ArcList**:
> 
> - The index value increments sequentially based on the order of child components.
> 
> - In an [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md) statement, only the child components in the branch where the condition is true participate in index value calculation. Child components in branches where the condition is false are not counted.
> 
> - In a [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)/[LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md) statement, the index values of all expanded child components are calculated.
> 
> - When [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md),[ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), and [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md) change, the child component index values are updated.
> 
> - Child components of **ArcList** with the [visibility](arkts-arkui-common-comp-commonmethod-c.md#visibility) attribute set to **Hidden** or **None** still have their index values calculated.

## ArcList

```TypeScript
ArcList(options?: ArkListOptions)
```

Creates an **ArcList** component instance with specified configuration options.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcListInterface-(options?: ArkListOptions): ArcListAttribute--><!--Device-ArcListInterface-(options?: ArkListOptions): ArcListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ArkListOptions](arkts-arkui-arclist-comp-arklistoptions-i.md) | No | Configuration options for the arc list, used to set the initial loading position, scroll controller, and header component. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [ArcListItemInterface](arkts-arkui-arclist-comp-arclistiteminterface-i.md) | A child component used to display items in an arc list. It must be used in conjunction with [ArcList](arkts-arkui-arclist-comp.md). |
| [ArkListOptions](arkts-arkui-arclist-comp-arklistoptions-i.md) | Provides basic parameters for creating an **ArcList** component. |

### Types

| Name | Description |
| --- | --- |
| [ArcScrollIndexHandler](arkts-arkui-arclist-comp-arcscrollindexhandler-t.md) | Represents the callback triggered when a child component enters or leaves the visible area of the **ArcList** component. |

## Examples

This example demonstrates an ArcList component with a header component and auto-scaling child items.

```TypeScript
// xxx.ets
import { ComponentContent, LengthMetrics, UIContext, CircleShape } from '@kit.ArkUI';
// Starting from API version 22, you do not need to manually import ArcListAttribute and ArcListItemAttribute. For details, refer to the Modules to Import section of the ArcList and ArcListItem reference documents.
import { ArcList, ArcListItem, ArcListAttribute, ArcListItemAttribute } from '@kit.ArkUI';

@Builder
function buildText() {
  Column() {
    Text('header')
      .fontSize('60px')
      .fontWeight(FontWeight.Bold)
      .fontColor(Color.Black)
  }.margin(0)
}

@Entry
@Component
struct Index {
  @State private numItems: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];

  private watchSize: string = '466px'; // Default size on wearables: 466*466
  private listSize: string = '414px'; // Item width

  context: UIContext = this.getUIContext();
  headerContent: ComponentContent<Object> = new ComponentContent(this.context, wrapBuilder(buildText));

  @Builder
  buildList() {
    Stack() {
      Column() {
      }
      .justifyContent(FlexAlign.Center)
      .width(this.watchSize)
      .height(this.watchSize)
      .clipShape(new CircleShape({ width: '100%', height: '100%' }))
      .backgroundColor(Color.White)

      ArcList({ initialIndex: 0, header: this.headerContent }) {
        ForEach(this.numItems, (item: number, index: number) => {
          ArcListItem() {
            Button('' + item, { type: ButtonType.Capsule })
              .width(this.listSize)
              .height('100px')
              .fontSize('40px')
              .focusable(true)
              .focusOnTouch(true)
              .backgroundColor(0x17A98D)
          }.align(Alignment.Center)
        }, (item: number, index: number) => (item + index).toString())
      }
      .space(LengthMetrics.px(10))
      .borderRadius(this.watchSize)
      .focusable(true)
      .focusOnTouch(true)
      .defaultFocus(true)
    }
    .align(Alignment.Center)
    .width(this.watchSize)
    .height(this.watchSize)
    .border({color: Color.Black, width: 1})
    .borderRadius(this.watchSize)
  }

  build() {
    Column() {
      this.buildList()
    }
    .width('100%')
    .height('100%')
    .alignItems(HorizontalAlign.Center)
    .justifyContent(FlexAlign.Center)
  }
}
```
