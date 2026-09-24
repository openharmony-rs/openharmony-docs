# AlphabetIndexer

The **AlphabetIndexer** component can create a logically indexed array of items in a container for instant location.

> **NOTE**

## Child Components

Not supported

## AlphabetIndexer

```TypeScript
AlphabetIndexer(options: AlphabetIndexerOptions)
```

Creates an **AlphabetIndexer** component.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [AlphabetIndexerOptions](arkts-arkui-alphabetindexer-comp-alphabetindexeroptions-i.md) | Yes | Options of the **AlphabetIndexer** component. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [AlphabetIndexerOptions](arkts-arkui-alphabetindexer-comp-alphabetindexeroptions-i.md) | Defines the options of the **AlphabetIndexer** component. |

### Types

| Name | Description |
| --- | --- |
| [OnAlphabetIndexerPopupSelectCallback](arkts-arkui-alphabetindexer-comp-onalphabetindexerpopupselectcallback-t.md) | Represents the callback invoked when a secondary index item in the pop-up window is selected. |
| [OnAlphabetIndexerRequestPopupDataCallback](arkts-arkui-alphabetindexer-comp-onalphabetindexerrequestpopupdatacallback-t.md) | Represents the callback invoked when an index item is selected and [usingPopup](arkts-arkui-alphabetindexer-comp-attribute.md#usingpopup) is set to **true**. |
| [OnAlphabetIndexerSelectCallback](arkts-arkui-alphabetindexer-comp-onalphabetindexerselectcallback-t.md) | Represents the callback invoked when an index item is selected. |

### Enums

| Name | Description |
| --- | --- |
| [IndexerAlign](arkts-arkui-alphabetindexer-comp-indexeralign-e.md) | Enumerates the alignment styles of the indexer pop-up window. |

## Examples

### Example 1: Setting the Display Text for the Index Pop-up Window

This example demonstrates how to customize the display text for the index pop-up window using the [onRequestPopupData](arkts-arkui-alphabetindexer-comp-attribute.md#onrequestpopupdata) event.



```TypeScript
// xxx.ets
@Entry
@Component
struct AlphabetIndexerSample {
  private arrayA: string[] = ['An'];
  private arrayB: string[] = ['Bu', 'Bai', 'Bao', 'Bi', 'Bing'];
  private arrayC: string[] = ['Cao', 'Cheng', 'Chen', 'Cui'];
  private arrayL: string[] = ['Liu', 'Li', 'Lou', 'Liang', 'Lei', 'Lv', 'Liu', 'Lu'];
  private value: string[] = ['#', 'A', 'B', 'C', 'D', 'E', 'F', 'G',
    'H', 'I', 'J', 'K', 'L', 'M', 'N',
    'O', 'P', 'Q', 'R', 'S', 'T', 'U',
    'V', 'W', 'X', 'Y', 'Z'];

  build() {
    Stack({ alignContent: Alignment.Start }) {
      Row() {
        List({ space: 20, initialIndex: 0 }) {
          ForEach(this.arrayA, (item: string) => {
            ListItem() {
              Text(item)
                .width('80%')
                .height('5%')
                .fontSize(30)
                .textAlign(TextAlign.Center)
            }
          }, (item: string) => item)

          ForEach(this.arrayB, (item: string) => {
            ListItem() {
              Text(item)
                .width('80%')
                .height('5%')
                .fontSize(30)
                .textAlign(TextAlign.Center)
            }
          }, (item: string) => item)

          ForEach(this.arrayC, (item: string) => {
            ListItem() {
              Text(item)
                .width('80%')
                .height('5%')
                .fontSize(30)
                .textAlign(TextAlign.Center)
            }
          }, (item: string) => item)

          ForEach(this.arrayL, (item: string) => {
            ListItem() {
              Text(item)
                .width('80%')
                .height('5%')
                .fontSize(30)
                .textAlign(TextAlign.Center)
            }
          }, (item: string) => item)
        }
        .width('50%')
        .height('100%')

        AlphabetIndexer({ arrayValue: this.value, selected: 0 })
          .autoCollapse (false) // Disable the auto-collapse mode.
          .enableHapticFeedback(false) // Disable haptic feedback.
          .selectedColor(0xFFFFFF) // Text color of the selected item.
          .popupColor(0xFFFAF0) // Text color of the primary index item in the pop-up window.
          .selectedBackgroundColor(0xCCCCCC) // Background color of the selected item.
          .popupBackground (0xD2B48C) // Background color of the pop-up window.
          .usingPopup(true) // Display a pop-up window when an index item is selected.
          .selectedFont({ size: 16, weight: FontWeight.Bolder }) // Text style of the selected item.
          .popupFont({ size: 30, weight: FontWeight.Bolder }) // Text style of the primary index item in the pop-up window.
          .itemSize(28) // Size of each index item.
          .alignStyle (IndexerAlign.Left) // The pop-up window is displayed on the right of the indexer.
          .popupItemBorderRadius(24) // Set the radius of the index background rounded corners in the pop-up window.
          .itemBorderRadius(14) // Set the radius of the index background rounded corners.
          .popupBackgroundBlurStyle(BlurStyle.NONE) // Set the background blur style of the pop-up window.
          .popupTitleBackground(0xCCCCCC) // Background color of the primary index item in the pop-up window.
          .popupSelectedColor(0x00FF00) // Text color of the selected secondary index items in the pop-up window.
          .popupUnselectedColor(0x0000FF) // Text color of the unselected secondary index item in the pop-up window.
          .popupItemFont({ size: 30, style: FontStyle.Normal }) // Text style of the secondary index item in the pop-up window.
          .popupItemBackgroundColor(0xCCCCCC) // Background color of the secondary index item in the pop-up window.
          .onSelect((index: number) => {
            console.info(this.value[index] + ' Selected!');
          })
          .onRequestPopupData((index: number) => {
            // When A is selected, the secondary index item list in the pop-up window displays arrayA. Similarly, selecting B, C, or L will display their respective arrays.
            // For other index items, the pop-up window will only show the primary index item.
            if (this.value[index] == 'A') {
              return this.arrayA;
            } else if (this.value[index] == 'B') {
              return this.arrayB;
            } else if (this.value[index] == 'C') {
              return this.arrayC;
            } else if (this.value[index] == 'L') {
              return this.arrayL;
            } else {
              return [];
            }
          })
          .onPopupSelect((index: number) => {
            console.info('onPopupSelected:' + index);
          })
      }
      .width('100%')
      .height('100%')
    }
  }
}
```

### Example 2: Enabling Adaptive Collapse Mode

This example demonstrates how to enable adaptive collapse mode using the [autoCollapse](#autocollapse11) attribute.



```TypeScript
// xxx.ets
@Entry
@Component
struct AlphabetIndexerSample {
  private arrayA: string[] = ['An'];
  private arrayB: string[] = ['Bu', 'Bai', 'Bao', 'Bi', 'Bing'];
  private arrayC: string[] = ['Cao', 'Cheng', 'Chen', 'Cui'];
  private arrayJ: string[] = ['Jia', 'Jia'];
  private value: string[] = ['#', 'A', 'B', 'C', 'D', 'E', 'F', 'G',
    'H', 'I', 'J', 'K', 'L', 'M', 'N',
    'O', 'P', 'Q', 'R', 'S', 'T', 'U',
    'V', 'W', 'X', 'Y', 'Z'];
  @State isNeedAutoCollapse: boolean = false;
  @State indexerHeight: string = '75%';

  build() {
    Stack({ alignContent: Alignment.Start }) {
      Row() {
        List({ space: 20, initialIndex: 0 }) {
          ForEach(this.arrayA, (item: string) => {
            ListItem() {
              Text(item)
                .width('80%')
                .height('5%')
                .fontSize(30)
                .textAlign(TextAlign.Center)
            }
          }, (item: string) => item)

          ForEach(this.arrayB, (item: string) => {
            ListItem() {
              Text(item)
                .width('80%')
                .height('5%')
                .fontSize(30)
                .textAlign(TextAlign.Center)
            }
          }, (item: string) => item)

          ForEach(this.arrayC, (item: string) => {
            ListItem() {
              Text(item)
                .width('80%')
                .height('5%')
                .fontSize(30)
                .textAlign(TextAlign.Center)
            }
          }, (item: string) => item)

          ForEach(this.arrayJ, (item: string) => {
            ListItem() {
              Text(item)
                .width('80%')
                .height('5%')
                .fontSize(30)
                .textAlign(TextAlign.Center)
            }
          }, (item: string) => item)
        }
        .width('50%')
        .height('100%')

        Column() {
          Column() {
            AlphabetIndexer({ arrayValue: this.value, selected: 0 })
              .autoCollapse (this.isNeedAutoCollapse) // Enable or disable adaptive collapse mode.
              .height (this.indexerHeight) // Indexer height.
              .enableHapticFeedback(false) // Disable haptic feedback.
              .selectedColor(0xFFFFFF) // Text color of the selected item.
              .popupColor(0xFFFAF0) // Text color of the primary index item in the pop-up window.
              .selectedBackgroundColor(0xCCCCCC) // Background color of the selected item.
              .popupBackground (0xD2B48C) // Background color of the pop-up window.
              .usingPopup(true) // Display a pop-up window when an index item is selected.
              .selectedFont({ size: 16, weight: FontWeight.Bolder }) // Text style of the selected item.
              .popupFont({ size: 30, weight: FontWeight.Bolder }) // Text style of the primary index item in the pop-up window.
              .itemSize(28) // Size of an item in the alphabetic index bar.
              .alignStyle(IndexerAlign.Right) // The pop-up window is displayed on the left of the indexer.
              .popupTitleBackground(0xD2B48C) // Background color of the primary index item in the pop-up window.
              .popupSelectedColor(0x00FF00) // Text color of the selected secondary index items in the pop-up window.
              .popupUnselectedColor(0x0000FF) // Text color of the unselected secondary index item in the pop-up window.
              .popupItemFont({ size: 30, style: FontStyle.Normal }) // Text style of the secondary index item in the pop-up window.
              .popupItemBackgroundColor(0xCCCCCC) // Background color of the secondary index item in the pop-up window.
              .onSelect((index: number) => {
                console.info(this.value[index] + ' Selected!');
              })
              .onRequestPopupData((index: number) => {
                // When A is selected, the secondary index item list in the pop-up window displays arrayA. Similarly, selecting B, C, or J will display their respective arrays.
                // For other index items, the pop-up window will only show the primary index item.
                if (this.value[index] == 'A') {
                  return this.arrayA;
                } else if (this.value[index] == 'B') {
                  return this.arrayB;
                } else if (this.value[index] == 'C') {
                  return this.arrayC;
                } else if (this.value[index] == 'J') {
                  return this.arrayJ;
                } else {
                  return [];
                }
              })
              .onPopupSelect((index: number) => {
                console.info('onPopupSelected:' + index);
              })
          }
          .height('80%')
          .justifyContent(FlexAlign.Center)

          Column() {
            Button('Collapse')
              .margin('5vp')
              .onClick(() => {
                this.isNeedAutoCollapse = true;
              })
            Button('30% of Index Bar Height')
              .margin('5vp')
              .onClick(() => {
                this.indexerHeight = '30%';
              })
            Button('70% of Index Bar Height')
              .margin('5vp')
              .onClick(() => {
                this.indexerHeight = '70%';
              })
          }.height('20%')
        }
        .width('50%')
        .justifyContent(FlexAlign.Center)
      }
      .width('100%')
      .height(720)
    }
  }
}
```

### Example 3: Setting the Background Blur Style of the Pop-up Window

This example demonstrates how to apply a background blur effect to the pop-up window using the [popupBackgroundBlurStyle](#popupbackgroundblurstyle12) attribute.

```TypeScript
// xxx.ets
@Entry
@Component
struct AlphabetIndexerSample {
  private arrayA: string[] = ['An'];
  private arrayB: string[] = ['Bu', 'Bai', 'Bao', 'Bi', 'Bing'];
  private arrayC: string[] = ['Cao', 'Cheng', 'Chen', 'Cui'];
  private arrayL: string[] = ['Liu', 'Li', 'Lou', 'Liang', 'Lei', 'Lv', 'Liu', 'Lu'];
  private value: string[] = ['#', 'A', 'B', 'C', 'D', 'E', 'F', 'G',
    'H', 'I', 'J', 'K', 'L', 'M', 'N',
    'O', 'P', 'Q', 'R', 'S', 'T', 'U',
    'V', 'W', 'X', 'Y', 'Z'];
  @State customBlurStyle: BlurStyle = BlurStyle.NONE;

  build() {
    Stack({ alignContent: Alignment.Start }) {
      Row() {
        List({ space: 20, initialIndex: 0 }) {
          ForEach(this.arrayA, (item: string) => {
            ListItem() {
              Text(item)
                .width('80%')
                .height('5%')
                .fontSize(30)
                .textAlign(TextAlign.Center)
            }
          }, (item: string) => item)

          ForEach(this.arrayB, (item: string) => {
            ListItem() {
              Text(item)
                .width('80%')
                .height('5%')
                .fontSize(30)
                .textAlign(TextAlign.Center)
            }
          }, (item: string) => item)

          ForEach(this.arrayC, (item: string) => {
            ListItem() {
              Text(item)
                .width('80%')
                .height('5%')
                .fontSize(30)
                .textAlign(TextAlign.Center)
            }
          }, (item: string) => item)

          ForEach(this.arrayL, (item: string) => {
            ListItem() {
              Text(item)
                .width('80%')
                .height('5%')
                .fontSize(30)
                .textAlign(TextAlign.Center)
            }
          }, (item: string) => item)
        }
        .width('30%')
        .height('100%')

        Column() {
          Column() {
            Text('Switch Blur Style: ')
              .fontSize(24)
              .fontColor(0xcccccc)
              .width('100%')
            Button('COMPONENT_REGULAR')
              .margin('5vp')
              .width(200)
              .onClick(() => {
                this.customBlurStyle = BlurStyle.COMPONENT_REGULAR;
              })
            Button('BACKGROUND_THIN')
              .margin('5vp')
              .width(200)
              .onClick(() => {
                this.customBlurStyle = BlurStyle.BACKGROUND_THIN;
              })
          }.height('20%')

          Column() {
            AlphabetIndexer({ arrayValue: this.value, selected: 0 })
              .usingPopup(true) // Display a pop-up window when an index item is selected.
              .alignStyle (IndexerAlign.Left) // The pop-up window is displayed on the right of the indexer.
              .popupItemBorderRadius(24) // Set the radius of the index background rounded corners in the pop-up window.
              .itemBorderRadius(14) // Set the radius of the index background rounded corners.
              .popupBackgroundBlurStyle(this.customBlurStyle) // Set the background blur style of the pop-up window.
              .popupTitleBackground(0xCCCCCC) // Background color of the primary index item in the pop-up window.
              .onSelect((index: number) => {
                console.info(this.value[index] + ' Selected!');
              })
              .onRequestPopupData((index: number) => {
                // When A is selected, the secondary index item list in the pop-up window displays arrayA. Similarly, selecting B, C, or L will display their respective arrays.
                // For other index items, the pop-up window will only show the primary index item.
                if (this.value[index] == 'A') {
                  return this.arrayA;
                } else if (this.value[index] == 'B') {
                  return this.arrayB;
                } else if (this.value[index] == 'C') {
                  return this.arrayC;
                } else if (this.value[index] == 'L') {
                  return this.arrayL;
                } else {
                  return [];
                }
              })
              .onPopupSelect((index: number) => {
                console.info('onPopupSelected:' + index);
              })
          }
          .height('80%')
        }
        .width('70%')
      }
      .width('100%')
      .height('100%')
      // Replace $r('app.media.image') with the image resource file you use.
      .backgroundImage($r("app.media.image"))
    }
  }
}
```
