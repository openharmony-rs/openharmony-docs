# Scroll

Defines Scroll Component.

## Scroll

```TypeScript
Scroll(scroller?: Scroller)
```

Called when a scrollable container is set.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scroller | [Scroller](arkts-arkui-scroll-comp-scroller-c.md) | No |  |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [OffsetOptions](arkts-arkui-scroll-comp-offsetoptions-i.md) | Provides parameters for setting the initial scrolling offset. |
| [OffsetResult](arkts-arkui-scroll-comp-offsetresult-i.md) | Represents the offset values resulting from a scroll operation. |
| [OnScrollFrameBeginHandlerResult](arkts-arkui-scroll-comp-onscrollframebeginhandlerresult-i.md) | The data returned by the event handler when onScrollFrameBegin. |
| [ScrollAnimationOptions](arkts-arkui-scroll-comp-scrollanimationoptions-i.md) | Provides parameters for customizing scroll animations. |
| [ScrollEdgeOptions](arkts-arkui-scroll-comp-scrolledgeoptions-i.md) | Provides parameters for scrolling to the edge of a scrollable container. |
| [ScrollOptions](arkts-arkui-scroll-comp-scrolloptions-i.md) | Provides parameters for scrolling to a specific position in a scrollable container. |
| [ScrollPageOptions](arkts-arkui-scroll-comp-scrollpageoptions-i.md) | Provides parameters for page scrolling behavior. |
| [ScrollSnapOptions](arkts-arkui-scroll-comp-scrollsnapoptions-i.md) | Defines a scroll snapping mode object. |
| [ScrollToIndexOptions](arkts-arkui-scroll-comp-scrolltoindexoptions-i.md) | Provides parameters for scrolling to a specific index. |
| [UIScrollEvent](arkts-arkui-scroll-comp-uiscrollevent-i.md) | Defines a UIScrollableCommonEvent which is used to set different common event to target component. |

### Types

| Name | Description |
| --- | --- |
| [OnScrollEdgeCallback](arkts-arkui-scroll-comp-onscrolledgecallback-t.md) | Represents the callback triggered when scrolling reaches an edge. |
| [OnScrollFrameBeginCallback](arkts-arkui-scroll-comp-onscrollframebegincallback-t.md) | Represents the callback triggered before each frame scrolling starts. |
| [ScrollOnDidZoomCallback](arkts-arkui-scroll-comp-scrollondidzoomcallback-t.md) | callback of Scroll, using in onDidZoom. |
| [ScrollOnScrollCallback](arkts-arkui-scroll-comp-scrollonscrollcallback-t.md) | Represents the callback triggered when the &lt;em&gt;Scroll&lt;/em&gt; component scrolls. |
| [ScrollOnWillScrollCallback](arkts-arkui-scroll-comp-scrollonwillscrollcallback-t.md) | Called before scroll to allow developer to control real offset the Scroll can scroll. |

### Enums

| Name | Description |
| --- | --- |
| [ScrollAlign](arkts-arkui-scroll-comp-scrollalign-e.md) | Enumerates alignment modes. |
| [ScrollDirection](arkts-arkui-scroll-comp-scrolldirection-e.md) | Enumerates the scrolling directions. |

## Examples

### Example 1: Setting the Scroller

This example demonstrates the use of some attributes of the Scroll component and the Scroller.



```TypeScript
// xxx.ets
import { curves } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct ScrollExample {
  scroller: Scroller = new Scroller();
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];

  build() {
    Stack({ alignContent: Alignment.TopStart }) {
      Scroll(this.scroller) {
        Column() {
          ForEach(this.arr, (item: number) => {
            Text(item.toString())
              .width('90%')
              .height(150)
              .backgroundColor(0xFFFFFF)
              .borderRadius(15)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .margin({ top: 10 })
          }, (item: number) => item.toString())
        }.width('100%')
      }
      .scrollable(ScrollDirection.Vertical) // The scrollbar scrolls in the vertical direction.
      .scrollBar(BarState.On) // The scrollbar is always displayed.
      .scrollBarColor(Color.Gray) // The scrollbar color is gray.
      .scrollBarWidth(10) // The scrollbar width is 10.
      .friction(0.6)
      .edgeEffect(EdgeEffect.None)
      .onWillScroll((xOffset: number, yOffset: number, scrollState: ScrollState) => {
        console.info(`onWillScroll xOffset = ${xOffset}, yOffset = ${yOffset}, scrollState = ${scrollState}`);
      })
      .onScrollEdge((side: Edge) => {
        console.info('To the edge');
      })
      .onScrollStop(() => {
        console.info('Scroll Stop');
      })

      Button('scroll 150')
        .height('5%')
        .onClick(() => { // Scroll down 150.0vp.
          this.scroller.scrollBy(0, 150);
        })
        .margin({ top: 10, left: 20 })
      Button('scroll 100')
        .height('5%')
        .onClick(() => { // Click to scroll down by 100.0 vp.
          const yOffset: number = this.scroller.currentOffset().yOffset;
          this.scroller.scrollTo({ xOffset: 0, yOffset: yOffset + 100 });
        })
        .margin({ top: 60, left: 20 })
      Button('scroll 100')
        .height('5%')
        .onClick(() => {// Click to scroll down by 100.0 vp. An animation is applied to the scrolling.
          let curve = curves.interpolatingSpring(10, 1, 228, 30); // Create a spring curve.
          const yOffset: number = this.scroller.currentOffset().yOffset;
          this.scroller.scrollTo({ xOffset: 0, yOffset: yOffset + 100, animation: { duration: 1000, curve: curve } });
        })
        .margin({ top: 110, left: 20 })
      Button('back top')
        .height('5%')
        .onClick(() => { // Click to go back to the top.
          this.scroller.scrollEdge(Edge.Top);
        })
        .margin({ top: 160, left: 20 })
      Button('next page')
        .height('5%')
        .onClick(() => { // Click to go to the next page.
          this.scroller.scrollPage({ next: true ,animation: true });
        })
        .margin({ top: 210, left: 20 })
      Button('fling -3000')
        .height('5%')
        .onClick(() => { // Trigger a fling with an initial velocity of -3000 vp/s.
          try {
            this.scroller.fling(-3000);
          } catch (error) {
            let err: BusinessError = error as BusinessError;
            console.error(`Failed to execute fling scroll. Code: ${err.code}, message: ${err.message}`);
          }
        })
        .margin({ top: 260, left: 20 })
      Button('scroll to bottom 700')
        .height('5%')
        .onClick(() => {// After the button is clicked, the component scrolls to the bottom edge at a velocity of 700 vp/s.
          this.scroller.scrollEdge(Edge.Bottom, { velocity: 700 });
        })
        .margin({ top: 310, left: 20 })
    }.width('100%').height('100%').backgroundColor(0xDCDCDC)
  }
}
```

### Example 2: Implementing Nested Scrolling (Method 1)

This example uses the onScrollFrameBegin event to achieve nested scrolling between an inner List component and an outer Scroll component.



```TypeScript
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct NestedScroll {
  @State listPosition: number = 0; // 0 indicates scrolling to the top of the list, 1 indicates scrolling to the middle of the list, and 2 indicates scrolling to the bottom of the list.
  private arr: number[] = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
  private scrollerForScroll: Scroller = new Scroller();
  private scrollerForList: Scroller = new Scroller();

  build() {
    Flex() {
      Scroll(this.scrollerForScroll) {
        Column() {
          Text('Scroll Area')
            .width('100%')
            .height('40%')
            .backgroundColor(0X330000FF)
            .fontSize(16)
            .textAlign(TextAlign.Center)
            .onClick(() => {
              this.scrollerForList.scrollToIndex(5, false, ScrollAlign.START, { extraOffset: LengthMetrics.vp(5) });
            })

          List({ space: 20, scroller: this.scrollerForList }) {
            ForEach(this.arr, (item: number) => {
              ListItem() {
                Text('ListItem' + item)
                  .width('100%')
                  .height('100%')
                  .borderRadius(15)
                  .fontSize(16)
                  .textAlign(TextAlign.Center)
                  .backgroundColor(Color.White)
              }.width('100%').height(100)
            }, (item: number) => item.toString())
          }
          .width('100%')
          .height('50%')
          .edgeEffect(EdgeEffect.None)
          .friction(0.6)
          .onReachStart(() => {
            this.listPosition = 0;
          })
          .onReachEnd(() => {
            this.listPosition = 2;
          })
          .onScrollFrameBegin((offset: number) => {
            if ((this.listPosition == 0 && offset <= 0) || (this.listPosition == 2 && offset >= 0)) {
              this.scrollerForScroll.scrollBy(0, offset);
              return { offsetRemain: 0 };
            }
            this.listPosition = 1;
            return { offsetRemain: offset };
          })

          Text('Scroll Area')
            .width('100%')
            .height('40%')
            .backgroundColor(0X330000FF)
            .fontSize(16)
            .textAlign(TextAlign.Center)
        }
      }
      .width('100%').height('100%')
    }.width('100%').height('100%').backgroundColor(0xDCDCDC).padding(20)
  }
}
```

### Example 3: Implementing Nested Scrolling (Method 2)

This example uses the [nestedScroll](#nestedscroll10) attribute to achieve nested scrolling between an inner List component and an outer Scroll component.



```TypeScript
@Entry
@Component
struct StickyNestedScroll {
  @State arr: number[] = [];

  @Styles
  listCard() {
    .backgroundColor(Color.White)
    .height(72)
    .width('100%')
    .borderRadius(12)
  }

  build() {
    Scroll() {
      Column() {
        Text('Scroll Area')
          .width('100%')
          .height('40%')
          .backgroundColor('#0080DC')
          .textAlign(TextAlign.Center)
        Tabs({ barPosition: BarPosition.Start }) {
          TabContent() {
            List({ space: 10 }) {
              ForEach(this.arr, (item: number) => {
                ListItem() {
                  Text('item' + item)
                    .fontSize(16)
                }.listCard()
              }, (item: number) => item.toString())
            }.width('100%')
            .edgeEffect(EdgeEffect.Spring)
            .nestedScroll({
              scrollForward: NestedScrollMode.PARENT_FIRST,
              scrollBackward: NestedScrollMode.SELF_FIRST
            })
          }.tabBar('Tab1')

          TabContent() {
          }.tabBar('Tab2')
        }
        .vertical(false)
        .height('100%')
      }.width('100%')
    }
    .edgeEffect(EdgeEffect.Spring)
    .friction(0.6)
    .backgroundColor('#DCDCDC')
    .scrollBar(BarState.Off)
    .width('100%')
    .height('100%')
  }

  aboutToAppear() {
    for (let i = 0; i < 30; i++) {
      this.arr.push(i);
    }
  }
}
```

### Example 4: Implementing Nested Scrolling with Parent-to-Child Scrolling Propagation

This example demonstrates how to propagate scrolling from a parent component to a child component using the [enableScrollInteraction](#enablescrollinteraction10) attribute and the [onScrollFrameBegin](#onscrollframebegin9) event.



```TypeScript
@Entry
@Component
struct NestedScroll {
  private headerHeight: number = 0;
  private arr: number[] = [];
  private scrollerForParent: Scroller = new Scroller();
  private scrollerForChild: Scroller = new Scroller();

  aboutToAppear(): void {
    for (let i = 0; i < 10; i++) {
      this.arr.push(i);
    }
  }

  build() {
    Scroll(this.scrollerForParent) {
      Column() {
        Text('Scroll Area')
          .width('100%')
          .height('40%')
          .backgroundColor(0X330000FF)
          .fontSize(16)
          .textAlign(TextAlign.Center)
          .onClick(() => {
            this.scrollerForChild.scrollToIndex(5);
          })
          .onSizeChange((oldValue: SizeOptions, newValue: SizeOptions) => {
            this.headerHeight = newValue.height! as number;
          })
        List({ space: 20, scroller: this.scrollerForChild }) {
          ForEach(this.arr, (item: number) => {
            ListItem() {
              Text('ListItem' + item)
                .width('100%')
                .height('100%')
                .borderRadius(15)
                .fontSize(16)
                .textAlign(TextAlign.Center)
                .backgroundColor(Color.White)
            }.width('100%').height(100)
          }, (item: number) => item.toString())
        }
        .width('100%')
        .height('100%')
        .edgeEffect(EdgeEffect.None)
        .scrollBar(BarState.Off)
        .enableScrollInteraction(false)

        Text('Scroll Area')
          .width('100%')
          .height('40%')
          .backgroundColor(0X330000FF)
          .fontSize(16)
          .textAlign(TextAlign.Center)
      }
    }
    .scrollBar(BarState.Off)
    .edgeEffect(EdgeEffect.Spring)
    .onScrollFrameBegin((offset: number, state: ScrollState) => {
      let retOffset = offset;
      let currOffset = this.scrollerForParent.currentOffset().yOffset;
      let newOffset = currOffset + offset;
      if (offset > 0) {
        if (this.scrollerForChild.isAtEnd()) {
          return { offsetRemain: offset };
        }
        if (newOffset > this.headerHeight) {
          retOffset = this.headerHeight - currOffset;
        }
        this.scrollerForChild.scrollBy(0, offset - retOffset);
      } else {
        if (this.scrollerForChild.currentOffset().yOffset <= 0) {
          return { offsetRemain: offset };
        }
        if (newOffset < this.headerHeight) {
          retOffset = this.headerHeight - currOffset;
        }
        this.scrollerForChild.scrollBy(0, offset - retOffset);
      }
      return { offsetRemain: retOffset };
    })
    .width('100%')
    .height('100%')
    .backgroundColor(0xDCDCDC)
  }
}
```

### Example 5: Setting Scroll Snapping

This example shows how to set scroll snapping for a Scroll component.



```TypeScript
@Entry
@Component
struct Index {
  scroller: Scroller = new Scroller();
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15];
  build() {
    Scroll(this.scroller) {
      Column() {
        ForEach(this.arr, (item: number) => {
          Text(item.toString())
            .width('90%')
            .height(200)
            .backgroundColor(0xFFFFFF)
            .borderWidth(1)
            .borderColor(Color.Black)
            .borderRadius(15)
            .fontSize(16)
            .textAlign(TextAlign.Center)
        }, (item: number) => item.toString())
      }.width('100%').backgroundColor(0xDCDCDC)
    }
    .backgroundColor(Color.Yellow)
    .height('100%')
    .edgeEffect(EdgeEffect.Spring)
    .scrollSnap({snapAlign:ScrollSnapAlign.START, snapPagination:400, enableSnapToStart:true, enableSnapToEnd:true})
  }
}
```

### Example 6: Obtaining the Index of a Child Component

This example demonstrates how to obtain the index of a child component in a List component.



```TypeScript
// xxx.ets
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct ListExample {
  private arr: number[] = [];
  private scroller: ListScroller = new ListScroller();
  @State listSpace: number = 10;
  @State listChildrenSize: ChildrenMainSize = new ChildrenMainSize(120);
  @State listIndex: number = -1;
  @State itemBackgroundColorArr: boolean[] = [];
  aboutToAppear(){
    // Initialize the data source.
    for (let i = 0; i < 10; i++) {
      this.arr.push(i);
      this.itemBackgroundColorArr.push(false);
    }
    try {
      this.listChildrenSize.splice(0, 5, [100, 100, 100, 100, 100]);
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`Failed to splice childrenMainSize for first 5 items. Code: ${err.code}, message: ${err.message}`);
    }
  }
  build() {
    Column() {
      List({ space: this.listSpace, initialIndex: 4, scroller: this.scroller }) {
        ForEach(this.arr, (item: number) => {
          ListItem() {
            Text('item-' + item)
              .height( item < 5 ? 100 : this.listChildrenSize.childDefaultSize)
              .width('90%')
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .borderRadius(10)
              .backgroundColor( this.itemBackgroundColorArr[item] ? 0x68B4FF: 0xFFFFFF)
          }
        }, (item: number) => item.toString())
      }
      .backgroundColor(Color.Gray)
      .layoutWeight(1)
      .scrollBar(BarState.On)
      .childrenMainSize(this.listChildrenSize)
      .alignListItem(ListItemAlign.Center)
      .gesture(
        PanGesture()
          .onActionUpdate((event: GestureEvent) => {
            if (event.fingerList[0] != undefined && event.fingerList[0].localX != undefined && event.fingerList[0].localY != undefined) {
              try {
                this.listIndex = this.scroller.getItemIndex(event.fingerList[0].localX, event.fingerList[0].localY);
              } catch (error) {
                let err: BusinessError = error as BusinessError;
                console.error(`Failed to get item index from scroller. Code: ${err.code}, message: ${err.message}`);
              }
              if (this.listIndex >= 0 && this.listIndex < this.itemBackgroundColorArr.length) {
                this.itemBackgroundColorArr[this.listIndex] = true;
              }
            }
          })
      )
      .gesture(
        TapGesture({ count: 1 })
          .onAction((event: GestureEvent) => {
            if (event) {
              this.itemBackgroundColorArr = this.arr.map(() => false);
            }
          })
      )

      Text('You are currently at index '+ this.listIndex)
        .fontColor(Color.Red)
        .height(50)
    }
  }
}
```

### Example 7: Setting Edge Fading

This example demonstrates how to implement a Scroll component with an edge fading effect and set the length of the fading edge.



```TypeScript
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI';
@Entry
@Component
struct ScrollExample {
  scroller: Scroller = new Scroller();
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12];

  build() {
    Stack({ alignContent: Alignment.TopStart }) {
      Scroll(this.scroller) {
        Column() {
          ForEach(this.arr, (item: number) => {
            Text(item.toString())
              .width('90%')
              .height(150)
              .backgroundColor(0xFFFFFF)
              .borderRadius(15)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .margin({ top: 10 })
          }, (item: number) => item.toString())
        }.width('100%')
      }
      .fadingEdge(true,{fadingEdgeLength:LengthMetrics.vp(80)})



    }.width('100%').height('100%').backgroundColor(0xDCDCDC)
  }
}
```

### Example 8: Setting the Single-Side Edge Effect

This example demonstrates how to set a single-side edge effect for the Scroll component using the [edgeEffect](#edgeeffect) API.



```TypeScript
// xxx.ets
@Entry
@Component
struct ScrollExample {
  scroller: Scroller = new Scroller();
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12];

  build() {
    Stack({ alignContent: Alignment.TopStart }) {
      Scroll(this.scroller) {
        Column() {
          ForEach(this.arr, (item: number) => {
            Text(item.toString())
              .width('90%')
              .height(150)
              .backgroundColor(0xFFFFFF)
              .borderRadius(15)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .margin({ top: 10 })
          }, (item: number) => item.toString())
        }.width('100%')
      }
      .edgeEffect(EdgeEffect.Spring,{alwaysEnabled:true,effectEdge:EffectEdge.START})
    }.width('100%').height('100%').backgroundColor(0xDCDCDC)
  }
}
```

### Example 9: Implementing the Swipe-to-Turn-Pages Effect

This example demonstrates how to implement the swipe-to-turn-pages feature for a Scroll component using the [enablePaging](arkts-arkui-scroll-comp-attribute.md#enablepaging) API.



```TypeScript
// xxx.ets
@Entry
@Component
struct EnablePagingExample {
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

  build() {
    Stack({ alignContent: Alignment.Center }) {
      Scroll() {
        Column() {
          ForEach(this.arr, (item: number) => {
            Text(item.toString())
              .width('100%')
              .height('100%')
              .borderRadius(15)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .backgroundColor(0xFFFFFF)
          }, (item: number) => item.toString())
        }
      }.width('90%').height('90%')
      .enablePaging(true)
    }.width('100%').height('100%').backgroundColor(0xDCDCDC)
  }
}
```

### Example 10: Implementing the Overscroll Stay Effect

This example demonstrates how to implement the overscroll stay effect for a Scroll component using the [scrollTo](#scrollto) API.



```TypeScript
// xxx.ets
import { curves } from '@kit.ArkUI';

@Entry
@Component
struct StickyNestedScroll {
  scroller: Scroller = new Scroller();

  build() {
    Column() {
      Row() {
        Button('scrollTo: Animation').onClick(() => {
          let curve = curves.interpolatingSpring(0.5, 5, 10, 15) // Create a spring curve.
          const yOffset: number = this.scroller.currentOffset().yOffset;
          this.scroller.scrollTo({
            xOffset: 0,
            yOffset: yOffset - 100,
            animation: { duration: 1000, curve: curve, canOverScroll: true },
            canOverScroll: true
          })
        }).margin({ top: 10 })
        Button('scrollTo: No Animation').onClick(() => {
          const yOffset: number = this.scroller.currentOffset().yOffset;
          this.scroller.scrollTo({
            xOffset: 0,
            yOffset: yOffset - 100,
            animation: false,
            canOverScroll: true
          })
        }).margin({ top: 10, left: 20 })
      }.margin({ bottom: 20 })

      Scroll(this.scroller) {
        Column() {
          Text('Scroll Area')
            .width('100%')
            .height('100%')
            .backgroundColor('#0080DC')
            .textAlign(TextAlign.Center)
        }
        .width('100%')
        .height('100%')
      }
      .scrollable(ScrollDirection.Vertical)
      .edgeEffect(EdgeEffect.Spring) // Set the edge effect.
      .fadingEdge(false) // Disable the edge fading effect.
      .scrollBar(BarState.Auto)
      .friction(undefined)
      .backgroundColor('#DCDCDC')
      .width('100%')
      .height('50%')
    }
  }
}
```

### Example 11: Implementing Free Scrolling and Scaling

This example demonstrates how to implement free scrolling and scaling of the Scroll component. This functionality is supported since API version 20.



```TypeScript
@Entry
@Component
struct ScrollZoomExample {
  @State currScale:number = 1;
  build() {
    Column() {
      Scroll() {
        Image($r('app.media.image1')) // 'app.media.image1' is only as an example. Replace it with the actual image.
      }
      .height(400)
      .scrollable(ScrollDirection.FREE)
      .minZoomScale(1)
      .maxZoomScale(2)
      .zoomScale(this.currScale!!)
      .enableBouncesZoom(true)
      .onDidZoom((scale: number) => {
        console.info(`onDidZoom:${scale}`);
      })
      .onZoomStart(() => {
        console.info('onZoomStart');
      })
      .onZoomStop(() => {
        console.info('onZoomStop');
      })
    }.width('100%').height('100%')
  }
}
```

### Example 12: Obtaining the Total Content Size

This example demonstrates how to obtain the total content size. This functionality is supported since API version 22.



```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct ScrollExample1 {
  scroller: Scroller = new Scroller();
  private arr: number[] = []

  aboutToAppear() {
    for (let j = 0; j < 10; j++) {
      this.arr.push(j);
    }
  }

  @State contentWidth: number = -1;
  @State contentHeight: number = -1;

  build() {
    Column() {
      Text('Set Scroller Controller and ForEach')
      Row() {
        // Button to obtain the content size.
        Button('GetContentSize')
          .onClick(() => {
            // Scroller throws an exception when not bound to a component; wrap with try-catch for safety.
            try {
              // Obtain the content width using contentSize.
              this.contentWidth = this.scroller.contentSize().width;
              // Obtain the content height using contentSize.
              this.contentHeight = this.scroller.contentSize().height;
            } catch (error) {
              let err: BusinessError = error as BusinessError;
              console.error(`Failed to get contentSize. Code: ${err.code}, message: ${err.message}`);
            }
          })
        // Display the obtained content size.
        Text('Width: ' + this.contentWidth + ', Height: ' + this.contentHeight)
          .fontColor(Color.Red)
          .height(50)
      }

      Stack({ alignContent: Alignment.TopStart }) {
        Scroll(this.scroller) {
          Column() {
            ForEach(this.arr, (item: number) => {
              Text(item.toString())
                .width('90%')
                .height(150)
                .backgroundColor(0xFFFFFF)
                .borderRadius(15)
                .fontSize(16)
                .textAlign(TextAlign.Center)
                .margin({ top: 10 })
            }, (item: number) => item.toString())
          }.width('100%')
        }
        .scrollable(ScrollDirection.Vertical) // The scrollbar scrolls in the vertical direction.
        .scrollBar(BarState.On) // The scrollbar is always displayed.
        .scrollBarColor(Color.Gray) // The scrollbar color is gray.
        .scrollBarWidth(10) // The scrollbar width is 10.
        .friction(0.6)
        .edgeEffect(EdgeEffect.None)
      }.width('100%').height('100%').backgroundColor(0xDCDCDC)
    }
  }
}
```

### Example 13: Setting Scrolling Events

This example obtains a [UIScrollEvent](arkts-arkui-scroll-comp-uiscrollevent-i.md) instance via getEvent('Scroll') on a FrameNode and sets scroll event callbacks for a Scroll component. This approach is intended for scenarios where the page code cannot be directly modified to use declarative callbacks.

The UIScrollEvent API is supported since API version 19.

```TypeScript
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

class MyNodeController extends NodeController {
  public rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);
    this.rootNode.commonAttribute.width(100);
    return this.rootNode;
  }

  addCommonEvent(frameNode: FrameNode) {
    // Obtain the Scroll event object.
    let scrollEvent: UIScrollEvent | undefined = typeNode.getEvent(frameNode, 'Scroll');

    // Set the OnWillScroll callback.
    scrollEvent?.setOnWillScroll((xOffset: number, yOffset: number, scrollState: ScrollState,
      scrollSource: ScrollSource) => {
      console.info(`onWillScroll xOffset = ${xOffset}, yOffset = ${yOffset}, scrollState = ${scrollState}, scrollSource = ${scrollSource}`);
    });

    // Set the OnDidScroll callback.
    scrollEvent?.setOnDidScroll((xOffset: number, yOffset: number, scrollState: ScrollState) => {
      console.info(`onDidScroll xOffset = ${xOffset}, yOffset = ${yOffset}, scrollState = ${scrollState}`);
    });

    // Set the OnReachStart callback.
    scrollEvent?.setOnReachStart(() => {
      console.info('onReachStart');
    });

    // Set the OnReachEnd callback.
    scrollEvent?.setOnReachEnd(() => {
      console.info('onReachEnd');
    });

    // Set the OnScrollStart callback.
    scrollEvent?.setOnScrollStart(() => {
      console.info('onScrollStart');
    });

    // Set the OnScrollStop callback.
    scrollEvent?.setOnScrollStop(() => {
      console.info('onScrollStop');
    });

    // Set the OnScrollFrameBegin callback.
    scrollEvent?.setOnScrollFrameBegin((offset: number, state: ScrollState) => {
      console.info(`onScrollFrameBegin offset = ${offset}, state = ${state}`);
      return undefined;
    });
  }
}

@Entry
@Component
struct Index {
  @State index: number = 0;
  private myNodeController: MyNodeController = new MyNodeController();
  @State numbers: string[] = [];

  aboutToAppear() {
    for (let i = 0; i < 30; i++) {
      this.numbers.push(`${i + 1}`);
    }
  }

  build() {
    Column() {
      Button('add CommonEvent to Scroll')
        .onClick(() => {
          this.myNodeController!.addCommonEvent(this.myNodeController!.rootNode!.getParent()!.getPreviousSibling()!)
        })
      Scroll() {
        Column() {
          ForEach(this.numbers, (day: string, index: number) => {
            Column() {
              Text(day)
                .fontSize(16)
                .backgroundColor(0xF9CF93)
                .width('90%')
                .height(80)
                .textAlign(TextAlign.Center)
                .margin({ top: 10 })
            }
            .width('100%')
            .justifyContent(FlexAlign.Center)
            .alignItems(HorizontalAlign.Center)
          }, (day: string, index: number) => index.toString() + day)
        }
      }
      .scrollable(ScrollDirection.Vertical)
      .edgeEffect(EdgeEffect.Spring)
      .width('90%')
      .backgroundColor(0xFAEEE0)
      .height(300)
      NodeContainer(this.myNodeController)
    }
  }
}
```
