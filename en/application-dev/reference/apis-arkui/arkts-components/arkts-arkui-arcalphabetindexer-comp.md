# ArcAlphabetIndexer

The **ArcAlphabetIndexer** component is an arc-shaped component designed for quick navigation through alphabetically sorted items. It can be integrated with container components to quickly locate items within the visible area.

> **NOTE**

> - This component can be used on phones, PCs, 2-in-1 devices, tablets, TVs, and wearables. In API version 22 and > earlier versions, a compilation warning will be reported when this component is used on phones, PCs, 2-in-1 > devices, tablets, and TVs, but the component can still run properly.

## Child Components

Not supported

## ArcAlphabetIndexer

```TypeScript
ArcAlphabetIndexer(info: ArcAlphabetIndexerInitInfo)
```

Creates an instance of the **ArcAlphabetIndexer** component with initialization parameters.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [ArcAlphabetIndexerInitInfo](arkts-arkui-arcalphabetindexer-comp-arcalphabetindexerinitinfo-i.md) | Yes | Initialization parameters for the **ArcAlphabetIndexer** component. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [ArcAlphabetIndexerInitInfo](arkts-arkui-arcalphabetindexer-comp-arcalphabetindexerinitinfo-i.md) | Initialization parameters for the **ArcAlphabetIndexer** component. |

### Types

| Name | Description |
| --- | --- |
| [OnSelectCallback](arkts-arkui-arcalphabetindexer-comp-onselectcallback-t.md) | Defines the callback used in [onSelect](arkts-arkui-arcalphabetindexer-comp-attribute.md#onselect). |

## Examples

### Example 1: Setting Linked Control and Positioning

This example demonstrates how to link an ArcAlphabetIndexer component with an ArcList component for synchronized control and navigation.



```TypeScript
// xxx.ets
import {
  LengthMetrics,
  ColorMetrics,
  ArcList,
  ArcListItem,
  ArcListAttribute,
  ArcListItemAttribute,
  ArcAlphabetIndexer,
  ArcAlphabetIndexerAttribute
} from '@kit.ArkUI';
// This sample code is compatible with API version 21 and earlier, so ArcListAttribute, ArcListItemAttribute, and ArcAlphabetIndexerAttribute are manually imported. Starting from API version 22, these attribute types do not need to be manually imported. For details, see the Modules to Import section of ArcList, ArcListItem, and ArcAlphabetIndexer.

@Entry
@Component
struct ArcListAndIndexer {
  private fullValue: string[] = [
    '#', 'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N',
    'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z'
  ];
  private arrName : string[] = [
    '1','2','3','4','5','6','7','8','9','10','11','12','13','14','15','16','17','18','19','20',
    '21','22','23','24','25','26','27','28','29','30','31','32','33','34','35','36','37','38',
    '39','40', '41','42',
  ];

  private scrollerForList: Scroller = new Scroller();
  @State indexerIndex: number = 0;

  private watchSize: string = '466px'; // Default watch size: 233*233
  private itemSize: number = 24;  // Default size of the index item area: 24

  build() {
    Column() {
      Row() {
        Stack() {
          ArcList({ scroller: this.scrollerForList, initialIndex: 0 }) {
            ForEach(this.arrName, (itemName: string, index: number) => {
              ArcListItem() {
                Text(itemName)
                  .width('90%')
                  .height('92px')
                  .fontSize(16)
                  .textAlign(TextAlign.Center)
                  .backgroundColor(index % 2 == 0 ? 0xAFEEEE : 0x00FFFF)
                  .borderRadius(23)
              }
            })
          }
          .scrollBar(BarState.Off)
          .onScrollIndex((firstIndex: number, lastIndex: number, centerIndex: number) => {
            this.indexerIndex = centerIndex;
          })
          .borderWidth(1)
          .width(this.watchSize)
          .height(this.watchSize)
          .borderRadius(this.watchSize)
          .space(LengthMetrics.px(4))

          ArcAlphabetIndexer({ arrayValue: this.fullValue, selected: 0 })
            .autoCollapse(true)
            .width(this.watchSize)
            .height(this.watchSize)
            .usePopup(false)
            .selected(this.indexerIndex)
            .onSelect((index: number) => {
              this.indexerIndex = index;
              this.scrollerForList.scrollToIndex(this.indexerIndex);
            })
            .borderWidth(1)
            .hitTestBehavior(HitTestMode.Transparent)
            .selectedColor(ColorMetrics.resourceColor(0xFFFFFF))
            .selectedBackgroundColor(ColorMetrics.resourceColor(0x1F71FF))
            .color(ColorMetrics.resourceColor(0xFFFFFF))
            .itemSize(LengthMetrics.px(this.itemSize))
            .selectedFont({
              size: '11.0fp',
              style: FontStyle.Normal,
              weight: 500,
              family: 'HarmonyOS Sans'
            })
            .font({
              size: '11.0fp',
              style: FontStyle.Normal,
              weight: 500,
              family: 'HarmonyOS Sans'
            })

        }.width('100%').height('100%')
        .backgroundColor(Color.Pink)
      }.width('100%').height('100%')
    }
  }
}
```

### Example 2: Setting Popup Display

This example uses the [popupColor](#popupcolor) and [popupBackground](#popupbackground) APIs to set the display background color and text color of the pop-up window.

Since API version 18, the popupColor and popupBackground APIs are supported.

```TypeScript
// xxx.ets
import {
  LengthMetrics,
  ColorMetrics,
  ArcList,
  ArcListItem,
  ArcListAttribute,
  ArcListItemAttribute,
  ArcAlphabetIndexer,
  ArcAlphabetIndexerAttribute
} from '@kit.ArkUI';
// Starting from API version 22, you no longer need to manually import ArcListAttribute, ArcListItemAttribute, or ArcAlphabetIndexerAttribute. For details, see the Modules to Import section of ArcList, ArcListItem, and ArcAlphabetIndexer.

@Entry
@Component
struct ArcListAndIndexer {
  private fullValue: string[] = [
    '#', 'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N',
    'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z'
  ];
  private arrName : string[] = [
    '1','2','3','4','5','6','7','8','9','10','11','12','13','14','15','16','17','18','19','20',
    '21','22','23','24','25','26','27','28','29','30','31','32','33','34','35','36','37','38',
    '39','40', '41','42',
  ];

  private scrollerForList: Scroller = new Scroller();
  @State indexerIndex: number = 0;

  private watchSize: string = '466px'; // Default watch width and height: 233*233
  private itemSize: number = 24;  // Default index item size: 24

  build() {
    Column() {
      Row() {
        Stack() {
          ArcList({ scroller : this.scrollerForList, initialIndex: 0 }) {
            ForEach(this.arrName, (itemName: string, index: number) => {
              ArcListItem() {
                Text(itemName)
                  .width('90%')
                  .height('92px')
                  .fontSize(16)
                  .textAlign(TextAlign.Center)
                  .backgroundColor(index % 2 == 0 ? 0xAFEEEE : 0x00FFFF)
                  .borderRadius(23)
              }
            })
          }
          .scrollBar(BarState.Off)
          .onScrollIndex((firstIndex: number, lastIndex: number, centerIndex: number) => {
            this.indexerIndex = centerIndex;
          })
          .borderWidth(1)
          .width(this.watchSize)
          .height(this.watchSize)
          .borderRadius(this.watchSize)
          .space(LengthMetrics.px(4))

          ArcAlphabetIndexer({ arrayValue: this.fullValue, selected: 0 })
            .autoCollapse(true)
            .width(this.watchSize)
            .height(this.watchSize)
            .usePopup(true)
            .selected(this.indexerIndex)
            .onSelect((index: number) => {
              this.indexerIndex = index;
              this.scrollerForList.scrollToIndex(this.indexerIndex);
            })
            .selectedColor(ColorMetrics.resourceColor(0xFFFFFF))
            .selectedBackgroundColor(ColorMetrics.resourceColor(0x1F71FF))
            .color(ColorMetrics.resourceColor(0xFFFFFF))
            .popupColor(ColorMetrics.resourceColor(0xFFFFFF))
            .popupBackground(ColorMetrics.resourceColor(0xD8404040))
            .popupFont({
              size: '11.0fp',
              style: FontStyle.Normal,
              weight: 500,
              family: 'HarmonyOS Sans'
            })

        }.width('100%').height('100%')
        .backgroundColor(Color.Pink)
      }.width('100%').height('100%')
    }
  }
}
```
