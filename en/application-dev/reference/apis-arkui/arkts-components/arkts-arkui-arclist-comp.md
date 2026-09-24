# ArcList

The **ArcList** component is a circular layout container that displays a series of list items in an arc shape. It is suitable for presenting homogeneous data, such as images and text, in a continuous, multi-row format.

> **NOTE**

> - This component is supported since API version 18. Updates will be marked with a > superscript to indicate their earliest API version. > > - This component can be used on phones, PCs, 2-in-1 devices, tablets, TVs, and wearables. > In API version 22 and earlier versions, a compilation warning will be reported when this > component is used on phones, PCs, 2-in-1 devices, tablets, and TVs, but the component can > still run properly.

## Child Components

Only the [ArcListItem](#ohosarkuiarclist) component is supported.

## ArcList

```TypeScript
ArcList(options?: ArkListOptions)
```

Creates an **ArcList** component instance with specified configuration options.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ArkListOptions](arkts-arkui-arclist-comp-arklistoptions-i.md) | No |  |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [ArcListItemInterface](arkts-arkui-arclist-comp-arclistiteminterface-i.md) | The **ArcListItem** component is used to display individual child components in an [ArcList](#ohosarkuiarclist) component and must be used in conjunction with **ArcList**. |
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
