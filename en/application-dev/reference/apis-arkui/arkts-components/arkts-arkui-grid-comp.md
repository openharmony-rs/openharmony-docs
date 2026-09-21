# Grid

The **Grid** component consists of cells formed by rows and columns. You can specify the cells where items are located to form various layouts.

> **NOTE** > > The component has been bound with gestures to implement functions such as follow-up scrolling. If you need to add > custom gestures, refer to Gesture Blocking Enhancement.

## Child Components

Child components are limited to GridItem and custom components. When using custom components inside **Grid**, it is recommended to wrap the custom component with a **GridItem** as the top-level container. Setting attributes or event methods directly on custom components is not recommended.

Child components can be dynamically generated using rendering control types [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md), [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), and [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md). **LazyForEach** or **Repeat** is recommended to optimize performance.

> **NOTE:** 
> 
> Below are the rules for calculating the indexes of the child components of **Grid**:
> 
> The index increases in ascending order of child components.
> 
> In the **if/else** statement, only the child components in the branch where the condition is met participate in the
> index calculation.
> 
> In the ForEach/LazyForEach and Repeat statements, index values are calculated for all expanded child components.
> 
> After changes occur in [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md),
> [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md),
> [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), and
> [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md), index values are updated
> accordingly for child components.
> 
> The child component that has the **visibility** attribute set to **Hidden** or **None** is included in the index
> calculation.
> 
> The child component that has the **visibility** attribute set to **None** is not displayed, but still takes up the
> corresponding cell.
> 
> The child component that has the **position** attribute set is displayed in the corresponding cell, offset by the
> distance specified by **position** relative to the upper left corner of the grid. This child component does not
> scroll with the corresponding cell and is not displayed after the corresponding cell extends beyond the display
> range of the grid.
> 
> When there is a gap between child components, it is filled as much as possible based on the current display area.
> Therefore, the relative position of grid items may change as the grid scrolls.
> 
> Since API version 21, the maximum width and height of a single **Grid** child component are 16777216 px. In API
> version 20 and earlier versions, the maximum width and height of a single **Grid** child component are 1000000 px.
> Exceeding these limits may result in scrolling or display abnormalities.

## Grid

```TypeScript
Grid(scroller?: Scroller, layoutOptions?: GridLayoutOptions)
```

Creates a **Grid** component.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scroller | [Scroller](arkts-arkui-scroll-comp-scroller-c.md) | No | Controller, which can be bound to scrollable components.<br>**NOTE:** <br>It cannot be bound to the same scrolling control object as other scrollable components, such as [ArcList](arkts-arkui-arclist-comp.md#ohosarkuiarclist), List, Grid, Scroll, and WaterFlow. |
| layoutOptions | [GridLayoutOptions](arkts-arkui-grid-comp-gridlayoutoptions-i.md) | No | Grid layout options. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [ComputedBarAttribute](arkts-arkui-grid-comp-computedbarattribute-i.md) | Provides information about the position and length of the scrollbar. |
| [GridLayoutOptions](arkts-arkui-grid-comp-gridlayoutoptions-i.md) | Defines the grid layout options. In this API, **irregularIndexes** and **onGetIrregularSizeByIndex** can be used for grids where either **rowsTemplate** or **columnsTemplate** is set. These properties allow you to specify an index array and set the number of rows and columns to be occupied by a grid item at the specified index. For details about the usage, see [Example 3](../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#example-3-implementing-a-scrollable-grid-with-grid-items-spanning-rows-and-columns). On the other hand, **onGetRectByIndex** can be used for grids where both **rowsTemplate** and **columnsTemplate** are set. It allows you to specify the position and size for the grid item at the specified index. For details about the usage, see [Example 1](../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#example-1-creating-a-fixed-row-and-column-grid-layout). |
| [StartLineInfo](arkts-arkui-grid-comp-startlineinfo-i-sys.md) | Define start line info used in GridLayoutOptions. |
| [UIGridEvent](arkts-arkui-grid-comp-uigridevent-i.md) | Represents the return value of the [getEvent('Grid')](../arkts-apis/arkts-arkui-typenode-getevent-f.md#getevent-3) method in **frameNode**, which can be used to set scroll events for a **Grid** node. |

### Types

| Name | Description |
| --- | --- |
| [OnGetStartIndexByIndexCallback](arkts-arkui-grid-comp-ongetstartindexbyindexcallback-t-sys.md) | Defines the callback type used in onGetStartIndexByIndex of GridLayoutOptions. |
| [OnGetStartIndexByOffsetCallback](arkts-arkui-grid-comp-ongetstartindexbyoffsetcallback-t-sys.md) | Defines the callback type used in onGetStartIndexByOffset of GridLayoutOptions. |
| [OnGridScrollIndexCallback](arkts-arkui-grid-comp-ongridscrollindexcallback-t.md) | Represents a callback for item changes in the visible area of the **Grid** component. |

### Enums

| Name | Description |
| --- | --- |
| [GridDirection](arkts-arkui-grid-comp-griddirection-e.md) | Enumerates the main axis layout directions. |
| [GridItemAlignment](arkts-arkui-grid-comp-griditemalignment-e.md) | Enumerates the alignment modes of grid items. |

## Examples

### Example 1: Creating a Fixed Row and Column Grid Layout

You can use the onGetRectByIndex function in the [GridLayoutOptions](arkts-arkui-grid-comp-gridlayoutoptions-i.md) to specify the position and size of a grid item.

```TypeScript
// xxx.ets
@Entry
@Component
struct GridExample {
  @State numbers1: string[] = ['0', '1', '2', '3', '4'];
  @State numbers2: string[] = ['0', '1', '2', '3', '4', '5'];
  layoutOptions3: GridLayoutOptions = {
    regularSize: [1, 1],
    onGetRectByIndex: (index: number) => {
      if (index == 0) {
        return [0, 0, 1, 1];
      } else if (index == 1) {
        return [0, 1, 2, 2];
      } else if (index == 2) {
        return [0, 3, 3, 3];
      } else if (index == 3) {
        return [3, 0, 3, 3];
      } else if (index == 4) {
        return [4, 3, 2, 2];
      } else {
        return [5, 5, 1, 1];
      }
    }
  };

  build() {
    Column({ space: 5 }) {
      Grid() {
        ForEach(this.numbers1, (day: string) => {
          ForEach(this.numbers1, (day: string) => {
            GridItem() {
              Text(day)
                .fontSize(16)
                .backgroundColor(0xF9CF93)
                .width('100%')
                .height('100%')
                .textAlign(TextAlign.Center)
            }
          }, (day: string) => day)
        }, (day: string) => day)
      }
      .columnsTemplate('1fr 1fr 1fr 1fr 1fr')
      .rowsTemplate('1fr 1fr 1fr 1fr 1fr')
      .columnsGap(10)
      .rowsGap(10)
      .width('90%')
      .backgroundColor(0xFAEEE0)
      .height(300)

      Text('Usage of GridLayoutOptions: onGetRectByIndex.').fontColor(0x000000).fontSize(14).width('90%')

      Grid(undefined, this.layoutOptions3) {
        ForEach(this.numbers2, (day: string) => {
          GridItem() {
            Text(day)
              .fontSize(16)
              .backgroundColor(0xF9CF93)
              .width('100%')
              .height('100%')
              .textAlign(TextAlign.Center)
          }
          .height('100%')
          .width('100%')
        }, (day: string) => day)
      }
      .columnsTemplate('1fr 1fr 1fr 1fr 1fr 1fr')
      .rowsTemplate('1fr 1fr 1fr 1fr 1fr 1fr')
      .columnsGap(10)
      .rowsGap(10)
      .width('90%')
      .backgroundColor(0xFAEEE0)
      .height(300)
    }.width('100%').margin({ top: 5 })
  }
}
```

### Example 2: Implementing a Scrollable Grid with Scroll Events

This example shows a scrollable grid with all its scrolling attributes and events specified.

GridDataSource implements the LazyForEach data source API [IDataSource](ts-rendering-control-lazyforeach.md#idatasource), which is used to provide child components for Grid through LazyForEach.

```TypeScript
// GridDataSource.ets
export class GridDataSource implements IDataSource {
  private list: string[] = [];
  private listeners: DataChangeListener[] = [];

  constructor(list: string[]) {
    this.list = list;
  }

  totalCount(): number {
    return this.list.length;
  }

  getData(index: number): string {
    return this.list[index];
  }

  registerDataChangeListener(listener: DataChangeListener): void {
    if (this.listeners.indexOf(listener) < 0) {
      this.listeners.push(listener);
    }
  }

  unregisterDataChangeListener(listener: DataChangeListener): void {
    const pos = this.listeners.indexOf(listener);
    if (pos >= 0) {
      this.listeners.splice(pos, 1);
    }
  }

  // Notify the controller that the data position has changed.
  notifyDataMove(from: number, to: number): void {
    this.listeners.forEach(listener => {
      listener.onDataMove(from, to);
    })
  }
  
  // Reload all data.
  notifyDataReload(): void {
    this.listeners.forEach(listener => {
      listener.onDataReloaded();
    })
  }

  // Exchange element positions.
  public swapItem(from: number, to: number): void {
    let temp: string = this.list[from];
    this.list[from] = this.list[to];
    this.list[to] = temp;
    this.notifyDataReload()
  }
}
```



```TypeScript
// xxx.ets
import { GridDataSource } from './GridDataSource';

@Entry
@Component
struct GridExample {
  numbers: GridDataSource = new GridDataSource([]);
  scroller: Scroller = new Scroller();
  @State gridPosition: number = 0; // 0 indicates scrolling to the top of the grid, 1 indicates scrolling to the center, and 2 indicates scrolling to the bottom.

  aboutToAppear() {
    let list: string[] = [];
    for (let i = 0; i < 5; i++) {
      for (let j = 0; j < 5; j++) {
        list.push(j.toString());
      }
    }
    this.numbers = new GridDataSource(list);
  }

  build() {
    Column({ space: 5 }) {
      Text('Grid').fontColor(0x000000).fontSize(16).width('90%')
      Grid(this.scroller) {
        LazyForEach(this.numbers, (day: string) => {
          GridItem() {
            Text(day)
              .fontSize(16)
              .backgroundColor(0xF9CF93)
              .width('100%')
              .height(80)
              .textAlign(TextAlign.Center)
          }
        }, (index: number) => index.toString())
      }
      .columnsTemplate('1fr 1fr 1fr 1fr 1fr')
      .columnsGap(10)
      .rowsGap(10)
      .friction(0.6)
      .enableScrollInteraction(true)
      .supportAnimation(false)
      .multiSelectable(false)
      .edgeEffect(EdgeEffect.Spring)
      .scrollBar(BarState.On)
      .scrollBarColor(Color.Grey)
      .scrollBarWidth(4)
      .width('90%')
      .backgroundColor(0xFAEEE0)
      .height(300)
      .onScrollIndex((first: number, last: number) => {
        console.info(first.toString());
        console.info(last.toString());
      })
      .onScrollBarUpdate((index: number, offset: number) => {
        console.info('XXX' + 'Grid onScrollBarUpdate,index : ' + index.toString() + ',offset' + offset.toString());
        return { totalOffset: (index / 5) * (80 + 10) - offset, totalLength: 80 * 5 + 10 * 4 };
      })  // The sample code applies only to the current data source. If the data source changes, modify the code or delete this attribute.
      .onDidScroll((scrollOffset: number, scrollState: ScrollState) => {
        console.info(scrollOffset.toString());
        console.info(scrollState.toString());
      })
      .onScrollStart(() => {
        console.info('XXX' + 'Grid onScrollStart');
      })
      .onScrollStop(() => {
        console.info('XXX' + 'Grid onScrollStop');
      })
      .onReachStart(() => {
        this.gridPosition = 0;
        console.info('XXX' + 'Grid onReachStart');
      })
      .onReachEnd(() => {
        this.gridPosition = 2;
        console.info('XXX' + 'Grid onReachEnd');
      })

      Button('next page')
        .onClick(() => {// Click to go to the next page.
          this.scroller.scrollPage({ next: true });
        })
    }.width('100%').margin({ top: 5 })
  }
}
```

### Example 3: Implementing a Scrollable Grid with Grid Items Spanning Rows and Columns

[GridLayoutOptions](arkts-arkui-grid-comp-gridlayoutoptions-i.md): irregularIndexes and onGetIrregularSizeByIndex.

For details about GridDataSource and the complete code, see [Example 2: Implementing a Scrollable Grid with Scroll Events](#example-2-implementing-a-scrollable-grid-with-scroll-events).



```TypeScript
// xxx.ets
import { GridDataSource } from './GridDataSource';

@Entry
@Component
struct GridExample {
  numbers: GridDataSource = new GridDataSource([]);
  scroller: Scroller = new Scroller();
  layoutOptions1: GridLayoutOptions = {
    regularSize: [1, 1],        // Only [1, 1] is supported.
    irregularIndexes: [0, 6],   // The grid item whose indexes are 0 and 6 occupies one row.
  };

  layoutOptions2: GridLayoutOptions = {
    regularSize: [1, 1],
    irregularIndexes: [0, 7],   // The number of columns occupied by the grid item whose indexes are 0 and 7 is specified by onGetIrregularSizeByIndex.
    onGetIrregularSizeByIndex: (index: number) => {
      if (index === 0) {
        return [1, 5];
      }
      return [1, index % 6 + 1];
    }
  };

  aboutToAppear() {
    let list: string[] = [];
    for (let i = 0; i < 5; i++) {
      for (let j = 0; j < 5; j++) {
        list.push(j.toString());
      }
    }
    this.numbers = new GridDataSource(list);
  }

  build() {
    Column({ space: 5 }) {
      Text('Grid1').fontColor(0x000000).fontSize(16).width('90%')
      Grid(this.scroller, this.layoutOptions1) {
        LazyForEach(this.numbers, (day: string) => {
          GridItem() {
            Text(day)
              .fontSize(16)
              .backgroundColor(0xF9CF93)
              .width('100%')
              .height(80)
              .textAlign(TextAlign.Center)
          }.selectable(false)
        }, (index: number) => index.toString())
      }
      .columnsTemplate('1fr 1fr 1fr 1fr 1fr')
      .columnsGap(10)
      .rowsGap(10)
      .multiSelectable(true)
      .scrollBar(BarState.Off)
      .width('90%')
      .backgroundColor(0xFAEEE0)
      .height(300)

      Text('Grid2').fontColor(0x000000).fontSize(16).width('90%')
      // The grid does not scroll, and undefined is used to reserve space.
      Grid(undefined, this.layoutOptions2) {
        LazyForEach(this.numbers, (day: string) => {
          GridItem() {
            Text(day)
              .fontSize(16)
              .backgroundColor(0xF9CF93)
              .width('100%')
              .height(80)
              .textAlign(TextAlign.Center)
          }
        }, (index: number) => index.toString())
      }
      .columnsTemplate('1fr 1fr 1fr 1fr 1fr')
      .columnsGap(10)
      .rowsGap(10)
      .scrollBar(BarState.Off)
      .width('90%')
      .backgroundColor(0xFAEEE0)
      .height(300)
    }.width('100%').margin({ top: 5 })
  }
}
```

### Example 4: Implementing Nested Scrolling in a Grid

This example demonstrates how to use [nestedScroll](#nestedscroll10) and [onScrollFrameBegin](#onscrollframebegin10).

For details about GridDataSource and the complete code, see [Example 2: Implementing a Scrollable Grid with Scroll Events](#example-2-implementing-a-scrollable-grid-with-scroll-events).



```TypeScript
import { GridDataSource } from './GridDataSource';

@Entry
@Component
struct GridExample {
  @State colors: number[] = [0xFFC0CB, 0xDA70D6, 0x6B8E23, 0x6A5ACD, 0x00FFFF, 0x00FF7F];
  numbers: GridDataSource = new GridDataSource([]);
  @State translateY: number = 0;
  private scroller: Scroller = new Scroller();
  private gridScroller: Scroller = new Scroller();
  private touchDown: boolean = false;
  private listTouchDown: boolean = false;
  private scrolling: boolean = false;

  aboutToAppear() {
    let list: string[] = [];
    for (let i = 0; i < 100; i++) {
      list.push(i.toString());
    }
    this.numbers = new GridDataSource(list);
  }

  build() {
    Stack() {
      Column() {
        Row() {
          Text('Head')
        }

        Column() {
          List({ scroller: this.scroller }) {
            ListItem() {
              Grid() {
                GridItem() {
                  Text('GoodsTypeList1')
                }
                .backgroundColor(this.colors[0])
                .columnStart(0)
                .columnEnd(1)

                GridItem() {
                  Text('GoodsTypeList2')
                }
                .backgroundColor(this.colors[1])
                .columnStart(0)
                .columnEnd(1)

                GridItem() {
                  Text('GoodsTypeList3')
                }
                .backgroundColor(this.colors[2])
                .columnStart(0)
                .columnEnd(1)

                GridItem() {
                  Text('GoodsTypeList4')
                }
                .backgroundColor(this.colors[3])
                .columnStart(0)
                .columnEnd(1)

                GridItem() {
                  Text('GoodsTypeList5')
                }
                .backgroundColor(this.colors[4])
                .columnStart(0)
                .columnEnd(1)
              }
              .scrollBar(BarState.Off)
              .columnsGap(15)
              .rowsGap(10)
              .rowsTemplate('1fr 1fr 1fr 1fr 1fr')
              .columnsTemplate('1fr')
              .width('100%')
              .height(200)
            }

            ListItem() {
              Grid(this.gridScroller) {
                LazyForEach(this.numbers, (item: string) => {
                  GridItem() {
                    Text(item)
                      .fontSize(16)
                      .backgroundColor(0xF9CF93)
                      .width('100%')
                      .height('100%')
                      .textAlign(TextAlign.Center)
                  }
                  .width('100%')
                  .height(40)
                  .shadow({ radius: 10, color: '#909399', offsetX: 1, offsetY: 1 })
                  .borderRadius(10)
                  .translate({ x: 0, y: this.translateY })
                }, (item: string) => item)
              }
              .columnsTemplate('1fr 1fr')
              .friction(0.3)
              .columnsGap(15)
              .rowsGap(10)
              .scrollBar(BarState.Off)
              .width('100%')
              .height('100%')
              .layoutDirection(GridDirection.Column)
              .nestedScroll({
                scrollForward: NestedScrollMode.PARENT_FIRST,
                scrollBackward: NestedScrollMode.SELF_FIRST
              })
              .onTouch((event: TouchEvent) => {
                if (event.type == TouchType.Down) {
                  this.listTouchDown = true;
                } else if (event.type == TouchType.Up) {
                  this.listTouchDown = false;
                }
              })
            }
          }
          .scrollBar(BarState.Off)
          .edgeEffect(EdgeEffect.None)
          .onTouch((event: TouchEvent) => {
            if (event.type == TouchType.Down) {
              this.touchDown = true;
            } else if (event.type == TouchType.Up) {
              this.touchDown = false;
            }
          })
          .onScrollFrameBegin((offset: number, state: ScrollState) => {
            if (this.scrolling && offset > 0) {
              let newOffset = this.scroller.currentOffset().yOffset;
              if (newOffset >= 590) {
                this.gridScroller.scrollBy(0, offset);
                return { offsetRemain: 0 };
              } else if (newOffset + offset > 590) {
                this.gridScroller.scrollBy(0, newOffset + offset - 590);
                return { offsetRemain: 590 - newOffset };
              }
            }
            return { offsetRemain: offset };
          })
          .onScrollStart(() => {
            if (this.touchDown && !this.listTouchDown) {
              this.scrolling = true;
            }
          })
          .onScrollStop(() => {
            this.scrolling = false;
          })
        }
        .width('100%')
        .height('100%')
        .padding({ left: 10, right: 10 })
      }

      Row() {
        Text('Top')
          .width(30)
          .height(30)
          .borderRadius(50)
      }
      .padding(5)
      .borderRadius(50)
      .backgroundColor('#ffffff')
      .shadow({ radius: 10, color: '#909399', offsetX: 1, offsetY: 1 })
      .margin({ right: 22, bottom: 15 })
      .onClick(() => {
        this.scroller.scrollTo({ xOffset: 0, yOffset: 0 });
        this.gridScroller.scrollTo({ xOffset: 0, yOffset: 0 });
      })
    }
    .align(Alignment.BottomEnd)
  }
}
```

### Example 5: Implementing Dragging in a Grid

Set [editMode](#editmode8) to enable edit mode for a grid, where the user can drag grid items.

In the [onItemDragStart](#onitemdragstart8) callback, set the image to be displayed during dragging.

Through [onItemDrop](#onitemdrop8), obtain the initial position of the dragged item and the position to which the dragged item will be dropped. Through [onItemDrop](#onitemdrop8), complete the array position exchange logic.

Set the supportAnimation(true) attribute to support animations.

> NOTE
> 
> The drag and drop action is not displayed in the preview.

For details about GridDataSource and the complete code, see [Example 2: Implementing a Scrollable Grid with Scroll Events](#example-2-implementing-a-scrollable-grid-with-scroll-events).

Below are some examples.

Below shows how the grid looks when dragging of grid items starts.



Below shows how the grid looks when dragging of grid items is in progress.



Below shows how the grid looks after grid item 1 and grid item 6 swap their positions.



Below shows the drag animation.



```TypeScript
import { GridDataSource } from './GridDataSource';

@Entry
@Component
struct GridExample {
  numbers: GridDataSource = new GridDataSource([]);
  scroller: Scroller = new Scroller();
  @State text: string = 'drag';

  @Builder pixelMapBuilder() { // Style for the drag event.
    Column() {
      Text(this.text)
        .fontSize(16)
        .backgroundColor(0xF9CF93)
        .width(80)
        .height(80)
        .textAlign(TextAlign.Center)
    }
  }

  aboutToAppear() {
    let list: string[] = [];
    for (let i = 1; i <= 15; i++) {
      list.push(i + '');
    }
    this.numbers = new GridDataSource(list);
  }

  changeIndex(index1: number, index2: number) { // Exchange the array positions.
    this.numbers.swapItem(index1, index2);
  }

  build() {
    Column({ space: 5 }) {
      Grid(this.scroller) {
        LazyForEach(this.numbers, (day: string) => {
          GridItem() {
            Text(day)
              .fontSize(16)
              .backgroundColor(0xF9CF93)
              .width(80)
              .height(80)
              .textAlign(TextAlign.Center)
          }
        }, (day: string) => day)
      }
      .columnsTemplate('1fr 1fr 1fr')
      .columnsGap(10)
      .rowsGap(10)
      .width('90%')
      .backgroundColor(0xFAEEE0)
      .height(300)
      .editMode(true) // Enable edit mode, where the user can drag the grid items.
      .supportAnimation(true) // Support animations.
      .onItemDragStart((event: ItemDragInfo, itemIndex: number) => { // Triggered when a grid item starts to be dragged.
        this.text = this.numbers.getData(itemIndex);
        return this.pixelMapBuilder(); // Set the image displayed during the dragging.
      })
      .onItemDrop((event: ItemDragInfo, itemIndex: number, insertIndex: number, isSuccess: boolean) => { // Triggered when the dragged item is dropped on the drop target of the grid.
        // If isSuccess is set to false, the item is dropped outside of the grid. If the value of insertIndex is greater than that of length, an item adding event occurs.
        if (!isSuccess || insertIndex >= this.numbers.totalCount()) {
          return;
        }
        console.info('itemIndex:' + itemIndex + ', insertIndex:' + insertIndex); // itemIndex indicates the start position of the drag, and insertIndex indicates the insertion position of the drag.
        this.changeIndex(itemIndex, insertIndex);
      })
    }.width('100%').margin({ top: 5 })
  }
}
```

### Example 6: Implementing Adaptive Grid Layout

This example demonstrates how to use [layoutDirection](#layoutdirection8), [maxCount](#maxcount8), [minCount](#mincount8), and [cellLength](arkts-arkui-grid-comp-attribute.md#celllength).

For details about GridDataSource and the complete code, see [Example 2: Implementing a Scrollable Grid with Scroll Events](#example-2-implementing-a-scrollable-grid-with-scroll-events).



```TypeScript
import { GridDataSource } from './GridDataSource';

@Entry
@Component
struct GridExample {
  numbers: GridDataSource = new GridDataSource([]);

  aboutToAppear() {
    let list: string[] = [];
    for (let i = 1; i <= 30; i++) {
      list.push(i + '');
    }
    this.numbers = new GridDataSource(list);
  }

  build() {
    Scroll() {
      Column({ space: 5 }) {
        Blank()
        Text('The layoutDirection, maxCount, minCount, and cellLength parameters take effect only when neither rowsTemplate nor columnsTemplate is set.')
          .fontSize(16).fontColor(0x000000).width('90%')
        Grid() {
          LazyForEach(this.numbers, (day: string) => {
            GridItem() {
              Text(day).fontSize(16).backgroundColor(0xF9CF93)
            }.width(40).height(80).borderWidth(2).borderColor(Color.Red)
          }, (day: string) => day)
        }
        .height(300)
        .columnsGap(10)
        .rowsGap(10)
        .backgroundColor(0xFAEEE0)
        .maxCount(6)
        .minCount(2)
        .cellLength(0)
        .layoutDirection(GridDirection.Row)
      }
      .width('90%').margin({ top: 5, left: 5, right: 5 })
      .align(Alignment.Center)
    }
  }
}
```

### Example 7: Dynamically Adjusting the Number of Grid Columns with a Pinch Gesture

This example demonstrates how to adjust the number of columns in the grid with a pinch gesture using two fingers.

For details about GridDataSource and the complete code, see [Example 2: Implementing a Scrollable Grid with Scroll Events](#example-2-implementing-a-scrollable-grid-with-scroll-events).



```TypeScript
// xxx.ets
import { GridDataSource } from './GridDataSource';

@Entry
@Component
struct GridExample {
  numbers: GridDataSource = new GridDataSource([]);
  @State columns: number = 2;

  aboutToAppear() {
    let lastCount = AppStorage.get<number>('columnsCount');
    if (typeof lastCount != 'undefined') {
      this.columns = lastCount;
    }

    let list: string[] = [];
    for (let i = 0; i < 20; i++) {
      for (let j = 0; j < 20; j++) {
        list.push(j.toString());
      }
    }
    this.numbers = new GridDataSource(list);
  }

  build() {
    Column({ space: 5 }) {
      Row() {
        Text('Pinch to change the number of columns')
          .height('5%')
          .margin({ top: 10, left: 20 })
      }

      Grid() {
        LazyForEach(this.numbers, (day: string) => {
          GridItem() {
            Text(day)
              .fontSize(16)
              .backgroundColor(0xF9CF93)
              .width('100%')
              .height(80)
              .textAlign(TextAlign.Center)
          }
        }, (index: number) => index.toString())
      }
      .columnsTemplate('1fr '.repeat(this.columns))
      .columnsGap(10)
      .rowsGap(10)
      .width('90%')
      .scrollBar(BarState.Off)
      .backgroundColor(0xFAEEE0)
      .height('100%')
      .cachedCount(3)
      // Switching the number of columns triggers a reordering animation for the item positions.
      .animation({
        duration: 300,
        curve: Curve.Smooth
      })
      .priorityGesture(
        PinchGesture()
          .onActionEnd((event: GestureEvent) => {
            console.info('end scale:' + event.scale);
            // When a user performs a pinch-to-zoom gesture by moving their fingers apart, and the number of columns decreases to a certain threshold (in this case, 2), it will cause the items to enlarge.
            if (event.scale > 2) {
              this.columns--;
            } else if (event.scale < 0.6) {
              this.columns++;
            }
            // You can set the maximum and minimum number of columns based on the device screen width. Here, the minimum number of columns is 1, and the maximum number of columns is 4.
            this.columns = Math.min(4, Math.max(1, this.columns));
            AppStorage.setOrCreate<number>('columnsCount', this.columns);
          })
      )
    }.width('100%').margin({ top: 5 })
  }
}
```

### Example 8: Using Adaptive Column Count Settings

This example shows the usage of auto-fill, auto-fit, and auto-stretch in [columnsTemplate](#columnstemplate).



```TypeScript
@Entry
@Component
struct GridColumnsTemplate {
  data: number[] = [0, 1, 2, 3, 4, 5];
  data1: number[] = [0, 1, 2, 3, 4, 5];
  data2: number[] = [0, 1, 2, 3, 4, 5];

  build() {
    Column({ space: 10 }) {
      Text('auto-fill auto-calculates the number of columns based on the set column width').width('90%')
      Grid() {
        ForEach(this.data, (item: number) => {
          GridItem() {
            Text('N' + item).height(80)
          }
          .backgroundColor(Color.Orange)
        })
      }
      .width('90%')
      .border({ width: 1, color: Color.Black })
      .columnsTemplate('repeat(auto-fill, 70)')
      .columnsGap(10)
      .rowsGap(10)
      .height(150)

      Text('auto-fit calculates the number of columns based on the specified column width, and then any remaining space is evenly distributed across all columns').width('90%')
      Grid() {
        ForEach(this.data1, (item: number) => {
          GridItem() {
            Text('N' + item).height(80)
          }
          .backgroundColor(Color.Orange)
        })
      }
      .width('90%')
      .border({ width: 1, color: Color.Black })
      .columnsTemplate('repeat(auto-fit, 70)')
      .columnsGap(10)
      .rowsGap(10)
      .height(150)

      Text('auto-stretch calculates the number of columns based on the specified column width, and then any remaining space is evenly distributed into the gaps between columns').width('90%')
      Grid() {
        ForEach(this.data2, (item: number) => {
          GridItem() {
            Text('N' + item).height(80)
          }
          .backgroundColor(Color.Orange)
        })
      }
      .width('90%')
      .border({ width: 1, color: Color.Black })
      .columnsTemplate('repeat(auto-stretch, 70)')
      .columnsGap(10)
      .rowsGap(10)
      .height(150)
    }
    .width('100%')
    .height('100%')
  }
}
```

### Example 9: Setting Grid Item Heights Based on the Tallest Item in the Current Row

This example implements a grid that contains two columns. The grid item in each column consists of two Column components with determined heights and one Text component with an undetermined height.

By default, the heights of the left and right grid items may differ; however, after the grid's [alignItems](#alignitems12) attribute is set to GridItemAlignment.STRETCH, the grid item with a shorter height in a row will adopt the height of the taller grid item, aligning their heights within the same row.

For details about GridDataSource and the complete code, see [Example 2: Implementing a Scrollable Grid with Scroll Events](#example-2-implementing-a-scrollable-grid-with-scroll-events).



```TypeScript
import { GridDataSource } from './GridDataSource';

@Entry
@Component
struct Index {
  data: GridDataSource = new GridDataSource([]);
  @State items: number[] = [];

  aboutToAppear(): void {
    let list: string[] = [];
    for (let i = 0; i < 100; i++) {
      list.push(i.toString());
      this.items.push(this.getSize());
    }
    this.data= new GridDataSource(list);
  }

  getSize() {
    let ret = Math.floor(Math.random() * 5);
    return Math.max(1, ret);
  }

  build() {
    Column({ space: 10 }) {
      Text('Grid alignItems sample code')

      Grid() {
        LazyForEach(this.data, (item: string) => {
          // GridItem and Column components, when left without explicitly set heights, will by default adapt to the size of their child components. With alignItems set to STRETCH, they will instead take on the height of the tallest component in the current row.
          // If the height is explicitly set, the component maintains the defined height and will not follow the height of the tallest component in the current row.
          GridItem() {
            Column() {
              Column().height(100).backgroundColor('#D5D5D5').width('100%')
              // The Text component in the center is set with flexGrow(1) to automatically fill the available space within the parent component.
              Text('This is a piece of text.'.repeat(this.items[item]))
                .flexGrow(1).width('100%').align(Alignment.TopStart)
                .backgroundColor('#F7F7F7')
              Column().height(50).backgroundColor('#707070').width('100%')
            }
          }
          .border({ color: Color.Black, width: 1 })
        })
      }
      .columnsGap(10)
      .rowsGap(5)
      .columnsTemplate('1fr 1fr')
      .width('80%')
      .height('100%')
      // When the grid has its alignItems attribute set to STRETCH, it adjusts the height of all grid items in a row to match the height of the tallest grid item in that row.
      .alignItems(GridItemAlignment.STRETCH)
      .scrollBar(BarState.Off)
    }
    .height('100%')
    .width('100%')
  }
}
```

### Example 10: Setting Edge Fading

This example demonstrates how to enable the edge fading effect using [fadingEdge](ts-container-scrollable-common.md#fadingedge14).

For details about GridDataSource and the complete code, see [Example 2: Implementing a Scrollable Grid with Scroll Events](#example-2-implementing-a-scrollable-grid-with-scroll-events).



```TypeScript
// xxx.ets
// This example demonstrates how to implement a Grid component with an edge fading effect and set the length of the fading edge.
import { LengthMetrics } from '@kit.ArkUI';
import { GridDataSource } from './GridDataSource';

@Entry
@Component
struct GridExample {
  numbers: GridDataSource = new GridDataSource([]);
  scroller: Scroller = new Scroller();

  aboutToAppear() {
    let list: string[] = [];
    for (let i = 0; i <= 10; i++) {
      for (let j = 0; j < 5; j++) {
        list.push(j.toString());
      }
    }
    this.numbers = new GridDataSource(list);
  }

  build() {
    Column({ space: 5 }) {
      Text('Grid').fontColor(0x000000).fontSize(16).width('90%')
      Grid(this.scroller) {
        LazyForEach(this.numbers, (day: string) => {
          GridItem() {
            Text(day)
              .fontSize(16)
              .backgroundColor(0xF9CF93)
              .width('100%')
              .height(80)
              .textAlign(TextAlign.Center)
          }
        }, (index: number) => index.toString())
      }
      .columnsTemplate('1fr 1fr 1fr 1fr 1fr')
      .columnsGap(10)
      .rowsGap(20)
      .height('90%')
      .fadingEdge(true, { fadingEdgeLength: LengthMetrics.vp(80) })

    }.width('100%').margin({ top: 5 })
  }
}
```

### Example 11: Setting the Single-Side Edge Effect

This example uses the [edgeEffect](#edgeeffect10) API to set the single-edge effect for the Grid component.

For details about GridDataSource and the complete code, see [Example 2: Implementing a Scrollable Grid with Scroll Events](#example-2-implementing-a-scrollable-grid-with-scroll-events).



```TypeScript
// xxx.ets
import { GridDataSource } from './GridDataSource';

@Entry
@Component
struct GridExample {
  numbers: GridDataSource = new GridDataSource([]);
  scroller: Scroller = new Scroller();

  aboutToAppear() {
    let list: string[] = [];
    for (let i = 0; i <= 10; i++) {
      for (let j = 0; j < 5; j++) {
        list.push(j.toString());
      }
    }
    this.numbers = new GridDataSource(list);
  }

  build() {
    Column({ space: 5 }) {
      Grid(this.scroller) {
        LazyForEach(this.numbers, (day: string) => {
          GridItem() {
            Text(day)
              .fontSize(16)
              .backgroundColor(0xF9CF93)
              .width('100%')
              .height(80)
              .textAlign(TextAlign.Center)
          }
        }, (index: number) => index.toString())
      }
      .columnsTemplate('1fr 1fr 1fr 1fr 1fr')
      .columnsGap(10)
      .rowsGap(20)
      .edgeEffect(EdgeEffect.Spring, { alwaysEnabled: true, effectEdge: EffectEdge.START })
      .width('90%')
      .backgroundColor(0xDCDCDC)
      .height('80%')

    }.width('100%').margin({ top: 5 })
  }
}
```

### Example 12: Moving Focus with Wrap by Arrow Keys

In API version 20 and later versions, this example uses the [focusWrapMode](#focuswrapmode20) API to implement the effect of line-wrapping focus navigation with arrow keys in the Grid component.



```TypeScript
// xxx.ets
@Entry
@Component
struct GridExample {
  scroller: Scroller = new Scroller();
  build() {
    Column() {
      Grid(this.scroller) {
        GridItem() {
          Text('A')
            .focusable(true)
            .fontSize(18)
            .fontWeight(5)
            .backgroundColor(0xF9CF93)
            .width('100%')
            .height(80)
            .textAlign(TextAlign.Center)
        }
        GridItem() {
          Text('B')
            .focusable(true)
            .fontSize(18)
            .fontWeight(5)
            .backgroundColor(0xF9CF93)
            .width('100%')
            .height(80)
            .textAlign(TextAlign.Center)
        }
        GridItem() {
          Text('C')
            .focusable(true)
            .fontSize(18)
            .fontWeight(5)
            .backgroundColor(0xF9CF93)
            .width('100%')
            .height(80)
            .textAlign(TextAlign.Center)
        }
        GridItem() {
          Text('D')
            .focusable(true)
            .fontSize(18)
            .fontWeight(5)
            .backgroundColor(0xF9CF93)
            .width('100%')
            .height(80)
            .textAlign(TextAlign.Center)
        }
        GridItem() {
          Text('E')
            .focusable(true)
            .fontSize(18)
            .fontWeight(5)
            .backgroundColor(0xF9CF93)
            .width('100%')
            .height(80)
            .textAlign(TextAlign.Center)
        }
        GridItem() {
          Text('F')
            .focusable(true)
            .fontSize(18)
            .fontWeight(5)
            .backgroundColor(0xF9CF93)
            .width('100%')
            .height(80)
            .textAlign(TextAlign.Center)
        }
      }
      .focusWrapMode(FocusWrapMode.WRAP_WITH_ARROW)
      .columnsTemplate('1fr 1fr 1fr 1fr 1fr')
      .columnsGap(10)
      .rowsGap(20)
      .backgroundColor(0xDCDCDC)
    }.width('100%').margin({ top: 5 })
  }
}
```

### Example 13: Setting Scrolling Events

This example obtains a [UIGridEvent](arkts-arkui-grid-comp-uigridevent-i.md) instance via getEvent('Grid') on a FrameNode and sets scroll event callbacks for a Grid component. This approach is intended for scenarios where the page code cannot be directly modified to use declarative callbacks.

The UIGridEvent API is added since API version 19.

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
    let gridEvent: UIGridEvent | undefined = typeNode.getEvent(frameNode, 'Grid');
    gridEvent?.setOnWillScroll((scrollOffset: number, scrollState: ScrollState, scrollSource: ScrollSource) => {
      console.info(`onWillScroll scrollOffset = ${scrollOffset}, scrollState = ${scrollState}, scrollSource = ${scrollSource}`);
    });
    gridEvent?.setOnDidScroll((scrollOffset: number, scrollState: ScrollState) => {
      console.info(`onDidScroll scrollOffset = ${scrollOffset}, scrollState = ${scrollState}`);
    });
    gridEvent?.setOnReachStart(() => {
      console.info(`onReachStart`);
    });
    gridEvent?.setOnReachEnd(() => {
      console.info(`onReachEnd`);
    });
    gridEvent?.setOnScrollStart(() => {
      console.info(`onScrollStart`);
    });
    gridEvent?.setOnScrollStop(() => {
      console.info(`onScrollStop`);
    });
    gridEvent?.setOnScrollFrameBegin((offset: number, state: ScrollState) => {
      console.info(`onScrollFrameBegin offset = ${offset}, state = ${state}`);
      return undefined;
    });
    gridEvent?.setOnScrollIndex((first: number, last: number) => {
      console.info(`onScrollIndex start = ${first}, end = ${last}`);
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
    for (let i = 0; i < 5; i++) {
      for (let j = 0; j < 5; j++) {
        this.numbers.push(j.toString());
      }
    }
  }

  build() {
    Column() {
      Button('add CommonEvent to Grid')
        .onClick(() => {
          this.myNodeController!.addCommonEvent(this.myNodeController!.rootNode!.getParent()!.getPreviousSibling()!);
        })
      Grid() {
        ForEach(this.numbers, (day: string, index: number) => {
          GridItem() {
            Text(day)
              .fontSize(16)
              .backgroundColor(0xF9CF93)
              .width('100%')
              .height(80)
              .textAlign(TextAlign.Center)
          }
        }, (day: string, index: number) => index.toString() + day)
      }
      .columnsTemplate('1fr 1fr 1fr 1fr 1fr')
      .columnsGap(10)
      .rowsGap(10)
      .enableScrollInteraction(true)
      .width('90%')
      .backgroundColor(0xFAEEE0)
      .height(300)
      NodeContainer(this.myNodeController)
    }.width('100%')
  }
}
```

### Example 14: Scrolling to a Specified Position

This example uses the [scrollToIndex](ts-container-scroll.md#scrolltoindex) API to scroll the Grid component to a specified position.

For details about GridDataSource and the complete code, see [Example 2: Implementing a Scrollable Grid with Scroll Events](#example-2-implementing-a-scrollable-grid-with-scroll-events).



```TypeScript
import { GridDataSource } from './GridDataSource';
@Entry
@Component
struct GridScrollToIndexSample {
  numbers: GridDataSource = new GridDataSource([]);
  scroller: Scroller = new Scroller();
  aboutToAppear(): void {
    let list: string[] = [];
    for (let i = 0; i < 10; i++) {
      for (let j = 0; j < 10; j++) {
        list.push((i * 5 + j + 1).toString());
      }
    }
    this.numbers =  new GridDataSource(list);
  }

  build() {
    Column({ space: 5 }) {
      Button('scrollToIndex')
        .onClick (() => { // Scroll to the corresponding position.
          this.scroller.scrollToIndex(25, true, ScrollAlign.START);
        })
      Grid(this.scroller) {
        LazyForEach(this.numbers, (day: string) => {
          GridItem() {
            Text(day)
              .fontSize(16)
              .backgroundColor(0xF9CF93)
              .width('100%')
              .height(80)
              .textAlign(TextAlign.Center)
          }
        }, (index: number) => index.toString())
      }
      .columnsTemplate('1fr 1fr 1fr 1fr 1fr')
      .columnsGap(10)
      .rowsGap(10)
      .friction(0.6)
      .enableScrollInteraction(true)
      .supportAnimation(false)
      .multiSelectable(false)
      .edgeEffect(EdgeEffect.Spring)
      .scrollBar(BarState.On)
      .scrollBarColor(Color.Grey)
      .scrollBarWidth(4)
      .width('90%')
      .backgroundColor(0xFAEEE0)
      .height(300)
    }.width('100%').margin({ top: 5 })
  }
}
```

### Example 15: Implementing Panning Selection in Grid

This example uses the [PanGesture](./ts-basic-gestures-pangesture.md#pangesture-1) API to implement the effect of panning while selecting items in a Grid component.

For details about GridDataSource and the complete code, see [Example 2: Implementing a Scrollable Grid with Scroll Events](#example-2-implementing-a-scrollable-grid-with-scroll-events).



```TypeScript
// xxx.ets
import { GridDataSource } from './GridDataSource';
import { display, curves } from '@kit.ArkUI';

enum SlideActionType {
  START,
  UPDATE,
  END
}
// Hot zone
let HOT_AREA_LENGTH: number = 0;
try {
  HOT_AREA_LENGTH =
    Math.round(display.getDefaultDisplaySync().densityDPI * 10 / 25.4 / display.getDefaultDisplaySync().densityPixels);
} catch (error) {
  console.info('Failed to get default display for HOT_AREA_LENGTH:', error);
}
// Scroll curve: Bezier curve
const SLIDE_SELECT_SPEED_CURVE = curves.cubicBezierCurve(0.33, 0, 0.67, 1);
// Scroll speed: maximum speed
let AUTO_SPEED_MAX: number = 0;
try {
  AUTO_SPEED_MAX = Math.round(2400 / display.getDefaultDisplaySync().densityPixels);
} catch (error) {
  console.info('Failed to get default display for AUTO_SPEED_MAX:', error);
}
@Entry
@Component
struct GridExample {
  numbers: GridDataSource = new GridDataSource([]);
  scroller: Scroller = new Scroller();
  @State selectedIndexes: string[] = [];
  // Items selected during panning
  @State updateIndex: number = -1;
  @State lastUpdateIndex: number = -1;
  @State updateTimer: number = new Date().valueOf();
  // Whether items can be selected during panning
  @State canSlideSelect: boolean = false;
  @State isAutoScroll: boolean = false;
  // Stop gesture
  @State stopGesture: boolean = false;
  private scrollStartIndex: number = 0;
  private scrollEndIndex: number = 0;
  // Initial position of panning
  @State startIndex: number = -1;
  @State endIndex: number = -1;
  //Height of the scrolling area
  @State contentHeight: number = 0;
  @State areaY: number = 0;
  // List width
  @State listWidth: number = 0;
  @State oldCheckList: boolean[] = [];
  // Whether to set passed points as selected during panning
  @State setChecked: boolean = false;
  aboutToAppear() {
    let list: string[] = [];
    for (let i = 0; i < 20; i++) {
      for (let j = 0; j < 20; j++) {
        list.push((20 * i + j + 1).toString());
      }
    }
    this.numbers = new GridDataSource(list);
  }
  /**
   * Obtain the current point.
   * @param finger
   * @returns
   */
  getIndex(finger: FingerInfo): number {
    // Initialize data.
    let index = -1;
    try {
      index = this.scroller.getItemIndex(finger.localX, finger.localY);
      if (index === -1) {
        for (let i = this.scrollStartIndex; i <= this.scrollEndIndex; i++) {
          const item = this.scroller.getItemRect(i);
          if (finger.localY < item.y ||
            finger.localY >= item.y && finger.localY <= item.y + item.height && finger.localX < item.x) {
            break;
          }
          index = i;
        }
      }
    } catch {
      this.stopGesture = true;
      return index;
    }
    return index;
  }
  slideActionStart(index: number): void {
    if (index < 0) {
      return;
    }
    console.debug('start index: ' + index.toString());
    const targetIndex = index + 1;
    this.setChecked = !this.selectedIndexes.includes(targetIndex.toString());
    this.startIndex = index;
    this.selectedIndexes.push(targetIndex.toString());
    this.updateIndex = index;

  }
  slideActionUpdate(index: number): void {
    if (!this.canSlideSelect) {
      return;
    }
    if (this.startIndex === -1) {
      // Reconfigure the initial data of panning when the initial contact point is in the gap.
      this.slideActionStart(index);
      return;
    }
    if (index === -1) {
      return;
    }

    this.lastUpdateIndex = this.updateIndex;
    this.setItemChecked(index);
    this.updateIndex = index;
  }
  setItemChecked(index: number):void {
    const start = Math.min(this.startIndex, index);
    const end = Math.max(this.startIndex, index);
    for (let i = start; i < end+1;i++) {
      const item = (i+1).toString();
      if (this.setChecked) {
        this.selectedIndexes.push(item);
      } else {
        if (this.selectedIndexes.includes(item)) {
          this.selectedIndexes = this.selectedIndexes.filter(selectIndex => selectIndex != item);
        }
      }

    }
  }
  /**
   * Panning ends.
   */
  slideActionEnd(): void {
    this.startIndex = -1;
    this.updateIndex = -1;
    this.scroller.scrollBy(0, 0);
    this.isAutoScroll = false;
  }
  /**
   * Automatic scrolling--
   * @param finger
   */
  autoScroll(finger: FingerInfo): void {
    // Multiple selections are not allowed.
    if (!this.canSlideSelect) {
      return;
    }
    let pointY = finger.globalY - this.areaY;
    if (pointY <= HOT_AREA_LENGTH) {
      if (this.isAutoScroll && pointY <= 0) {
        return;
      }
      const speedFlag = pointY > 0 ? SLIDE_SELECT_SPEED_CURVE
        .interpolate(1 - pointY / HOT_AREA_LENGTH) : 1;
      this.scroller.scrollEdge(Edge.Top, {
        velocity: speedFlag * AUTO_SPEED_MAX
      });
      this.isAutoScroll = true;
    } else if (pointY > this.contentHeight - HOT_AREA_LENGTH) {
      if (this.isAutoScroll && pointY >= this.contentHeight) {
        return;
      }
      const speedFlag = pointY < this.contentHeight ? SLIDE_SELECT_SPEED_CURVE
        .interpolate(1 - (this.contentHeight - pointY) / HOT_AREA_LENGTH) : 1;
      this.scroller.scrollEdge(Edge.Bottom, {
        velocity: speedFlag * AUTO_SPEED_MAX
      });
      this.isAutoScroll = true;
    } else {
      if (this.isAutoScroll) {
        this.scroller.scrollBy(0, 0);
        this.isAutoScroll = false;
      }
    }
  }

  panGestureAction(type: SlideActionType, event: GestureEvent | undefined): void {
    if (this.stopGesture || !event) {
      return;
    }
    const finger = event!.fingerList[0];
    const index = this.getIndex(finger);
    switch (type) {
      case SlideActionType.START: {
        this.slideActionStart(index);
        break;
      }
      case SlideActionType.UPDATE: {
        this.slideActionUpdate(index);
        this.autoScroll(finger);
        break;
      }
      case SlideActionType.END: {
        this.slideActionEnd();
        break;
      }
      default: {
      }
    }
  }
  build() {
    Column({ space: 5 }) {
      Grid(this.scroller) {
        LazyForEach(this.numbers, (day: string) => {
          GridItem() {
            Stack() {
              Text(day)
                .fontSize(16)
                .backgroundColor(0xF9CF93)
                .width('100%')
                .height(80)
                .textAlign(TextAlign.Center)
              if (this.canSlideSelect) {
                // Replace $r('app.media.gouxuan') and $r('app.media.weigouxuan') with the image resource files you use.
                Image(this.selectedIndexes.includes(day) ? $r('app.media.gouxuan') :$r('app.media.weigouxuan'))
                  .width(30)
                  .height(30)
                  .position({right:5,top:5})
                  .draggable(false)
              }

            }
          }
        }, (index: number) => index.toString())
      }
      .columnsTemplate('1fr 1fr 1fr')
      .columnsGap(10)
      .rowsGap(10)
      .friction(0.6)
      .enableScrollInteraction(true)
      .supportAnimation(false)
      .multiSelectable(false)
      .edgeEffect(EdgeEffect.Spring)
      .scrollBar(BarState.On)
      .scrollBarColor(Color.Grey)
      .scrollBarWidth(4)
      .width('90%')
      .height('85%')
      .draggable(!this.canSlideSelect)
      .backgroundColor(0xFAEEE0)
      .onAreaChange((oldVal, newVal) => {
        this.listWidth = newVal.width as number;
        this.areaY = newVal.globalPosition.y as number;
        this.contentHeight = newVal.height as number;
      })
      .onScrollIndex((start, end) => {
        this.scrollStartIndex = start;
        this.scrollEndIndex = end;
      })
      .gesture(
        // Pan gesture
        PanGesture({ direction: PanDirection.Vertical })
          .onActionStart((event: GestureEvent | undefined) => {
            this.panGestureAction(SlideActionType.START, event);
          })
          .onActionUpdate((event: GestureEvent | undefined) => {
            this.panGestureAction(SlideActionType.UPDATE, event);
          })
          .onActionEnd((event?: GestureEvent) => {
            this.panGestureAction(SlideActionType.END, event);
          }),
        GestureMask.Normal
      )
      .onGestureRecognizerJudgeBegin((event: BaseGestureEvent, current: GestureRecognizer,
        recognizers: Array<GestureRecognizer>) => {
        if (this.canSlideSelect && current.isBuiltIn() &&
          current.getType() == GestureControl.GestureType.PAN_GESTURE) {
          return GestureJudgeResult.REJECT;
        }
        return GestureJudgeResult.CONTINUE;
      })
      Row() {
        Button('Start Editing').onClick(()=>{
          this.selectedIndexes = [];
          this.canSlideSelect = true;
        })
        Button('End Editing').onClick(()=>{
          this.canSlideSelect = false;
          this.selectedIndexes = [];
        })
      }
      .margin({
        bottom: 30
      })
      Text(`${this.selectedIndexes.join(',')}`)
    }.width('100%').margin({ top: 5 })
  }
}
```

### Example 16: Customizing the Drag Effect for GridItem

This example uses the [gesture](./ts-gesture-settings.md#gesture) API to customize the drag effect for the GridItem component.



```TypeScript
import { curves } from '@kit.ArkUI';

@Entry
@Component
struct GridItemExample {
  @State numbers: number[] = [];
  @State dragItem: number = -1;
  @State scaleItem: number = -1;
  private dragRefOffsetX: number = 0;
  private dragRefOffsetY: number = 0;
  @State offsetX: number = 0;
  @State offsetY: number = 0;
  private FIX_VP_X: number = 108;
  private FIX_VP_Y: number = 120;

  aboutToAppear() {
    for (let i = 1; i <= 11; i++) {
      this.numbers.push(i);
    }
  }

  itemMove(index: number, newIndex: number): void {
    console.info('index:' + index + ' newIndex:' + newIndex);
    if (!this.isDraggable(newIndex)) {
      return;
    }
    let tmp = this.numbers.splice(index, 1);
    this.numbers.splice(newIndex, 0, tmp[0]);
  }

  // Swipe down.
  down(index: number): void {
    // Specify that the fixed GridItem does not respond to events.
    if (!this.isDraggable(index + 3)) {
      return;
    }
    this.offsetY -= this.FIX_VP_Y;
    this.dragRefOffsetY += this.FIX_VP_Y;
    this.itemMove(index, index + 3);
  }

  // Swipe down (in a grid where the lower right corner is empty).
  down2(index: number): void {
    if (!this.isDraggable(index + 3)) {
      return;
    }
    this.offsetY -= this.FIX_VP_Y;
    this.dragRefOffsetY += this.FIX_VP_Y;
    this.itemMove(index, index + 3);
  }

  // Swipe up.
  up(index: number): void {
    if (!this.isDraggable(index - 3)) {
      return;
    }
    this.offsetY += this.FIX_VP_Y;
    this.dragRefOffsetY -= this.FIX_VP_Y;
    this.itemMove(index, index - 3);
  }

  // Swipe left.
  left(index: number): void {
    if (!this.isDraggable(index - 1)) {
      return;
    }
    this.offsetX += this.FIX_VP_X;
    this.dragRefOffsetX -= this.FIX_VP_X;
    this.itemMove(index, index - 1);
  }

  // Swipe right.
  right(index: number): void {
    if (!this.isDraggable(index + 1)) {
      return;
    }
    this.offsetX -= this.FIX_VP_X;
    this.dragRefOffsetX += this.FIX_VP_X;
    this.itemMove(index, index + 1);
  }

  // Swipe to the lower right.
  lowerRight(index: number): void {
    if (!this.isDraggable(index + 4)) {
      return;
    }
    this.offsetX -= this.FIX_VP_X;
    this.dragRefOffsetX += this.FIX_VP_X;
    this.offsetY -= this.FIX_VP_Y;
    this.dragRefOffsetY += this.FIX_VP_Y;
    this.itemMove(index, index + 4);
  }

  // Swipe to the upper right.
  upperRight(index: number): void {
    if (!this.isDraggable(index - 2)) {
      return;
    }
    this.offsetX -= this.FIX_VP_X;
    this.dragRefOffsetX += this.FIX_VP_X;
    this.offsetY += this.FIX_VP_Y;
    this.dragRefOffsetY -= this.FIX_VP_Y;
    this.itemMove(index, index - 2);
  }

  // Swipe to the lower left.
  lowerLeft(index: number): void {
    if (!this.isDraggable(index + 2)) {
      return;
    }
    this.offsetX += this.FIX_VP_X;
    this.dragRefOffsetX -= this.FIX_VP_X;
    this.offsetY -= this.FIX_VP_Y;
    this.dragRefOffsetY += this.FIX_VP_Y;
    this.itemMove(index, index + 2);
  }

  // Swipe to the upper left.
  upperLeft(index: number): void {
    if (!this.isDraggable(index - 4)) {
      return;
    }
    this.offsetX += this.FIX_VP_X;
    this.dragRefOffsetX -= this.FIX_VP_X;
    this.offsetY += this.FIX_VP_Y;
    this.dragRefOffsetY -= this.FIX_VP_Y;
    this.itemMove(index, index - 4);
  }

  isDraggable(index: number): boolean {
    console.info('index:' + index)
    return index > 1;
  }

  build() {
    Column() {
      Grid() {
        ForEach(this.numbers, (item: number) => {
          GridItem() {
            Text(item + '')
              .fontSize(16)
              .width('100%')
              .textAlign(TextAlign.Center)
              .height(100)
              .borderRadius(10)
              .backgroundColor(0xF9CF93)
              .shadow(this.scaleItem == item ? {
                radius: 70,
                color: '#15000000',
                offsetX: 0,
                offsetY: 0
              } :
                {
                  radius: 0,
                  color: '#15000000',
                  offsetX: 0,
                  offsetY: 0
                })
              .animation({ curve: Curve.Sharp, duration: 300 })
          }
          // Specify that the fixed GridItem does not respond to events.
          .hitTestBehavior(this.isDraggable(this.numbers.indexOf(item)) ? HitTestMode.Default : HitTestMode.None)
          .scale({ x: this.scaleItem == item ? 1.05 : 1, y: this.scaleItem == item ? 1.05 : 1 })
          .zIndex(this.dragItem == item ? 1 : 0)
          .translate(this.dragItem == item ? { x: this.offsetX, y: this.offsetY } : { x: 0, y: 0 })
          .padding(10)
          .gesture(
            // The following combined gestures are recognized in sequential recognition mode. If the long press gesture event is not triggered correctly, the drag gesture event will not be triggered.
            GestureGroup(GestureMode.Sequence,
              LongPressGesture({ repeat: true })
                .onAction((event?: GestureEvent) => {
                  this.getUIContext()?.animateTo({ curve: Curve.Friction, duration: 300 }, () => {
                    this.scaleItem = item;
                  })
                })
                .onActionEnd(() => {
                  this.getUIContext()?.animateTo({ curve: Curve.Friction, duration: 300 }, () => {
                    this.scaleItem = -1;
                  })
                }),
              PanGesture({ fingers: 1, direction: null, distance: 0 })
                .onActionStart(() => {
                  this.dragItem = item;
                  this.dragRefOffsetX = 0;
                  this.dragRefOffsetY = 0;
                })
                .onActionUpdate((event: GestureEvent) => {
                  this.offsetY = event.offsetY - this.dragRefOffsetY;
                  this.offsetX = event.offsetX - this.dragRefOffsetX;
                  this.getUIContext()?.animateTo({ curve: curves.interpolatingSpring(0, 1, 400, 38) }, () => {
                    let index = this.numbers.indexOf(this.dragItem);
                    if (this.offsetY >= this.FIX_VP_Y / 2 && (this.offsetX <= 44 && this.offsetX >= -44) &&
                      ![8, 9, 10].includes(index)) {
                      // Swipe down.
                      this.down(index);
                    } else if (this.offsetY <= -this.FIX_VP_Y / 2 && (this.offsetX <= 44 && this.offsetX >= -44) &&
                      ![0, 1, 2].includes(index)) {
                      // Swipe up.
                      this.up(index);
                    } else if (this.offsetX >= this.FIX_VP_X / 2 && (this.offsetY <= 50 && this.offsetY >= -50) &&
                      ![2, 5, 8, 10].includes(index)) {
                      // Swipe right.
                      this.right(index);
                    } else if (this.offsetX <= -this.FIX_VP_X / 2 && (this.offsetY <= 50 && this.offsetY >= -50) &&
                      ![0, 3, 6, 9].includes(index)) {
                      // Swipe left.
                      this.left(index);
                    } else if (this.offsetX >= this.FIX_VP_X / 2 && this.offsetY >= this.FIX_VP_Y / 2 &&
                      ![2, 5, 7, 8, 9, 10].includes(index)) {
                      // Swipe to the lower right.
                      this.lowerRight(index);
                    } else if (this.offsetX >= this.FIX_VP_X / 2 && this.offsetY <= -this.FIX_VP_Y / 2 &&
                      ![0, 1, 2, 5, 8].includes(index)) {
                      // Swipe to the upper right.
                      this.upperRight(index);
                    } else if (this.offsetX <= -this.FIX_VP_X / 2 && this.offsetY >= this.FIX_VP_Y / 2 &&
                      ![0, 3, 6, 9, 10].includes(index)) {
                      // Swipe to the lower left.
                      this.lowerLeft(index);
                    } else if (this.offsetX <= -this.FIX_VP_X / 2 && this.offsetY <= -this.FIX_VP_Y / 2 &&
                      ![0, 1, 2, 3, 6, 9].includes(index)) {
                      // Swipe to the upper left.
                      this.upperLeft(index);
                    } else if (this.offsetX >= this.FIX_VP_X / 2 && this.offsetY >= this.FIX_VP_Y / 2 &&
                    [7].includes(index)) {
                      // Swipe to the lower right (in a grid where the lower right corner is empty).
                      this.down2(index);
                    }
                  })
                })
                .onActionEnd(() => {
                  this.getUIContext()?.animateTo({ curve: curves.interpolatingSpring(0, 1, 400, 38) }, () => {
                    this.dragItem = -1;
                  })
                  this.getUIContext()?.animateTo({
                    curve: curves.interpolatingSpring(14, 1, 170, 17), delay: 150
                  }, () => {
                    this.scaleItem = -1;
                  })
                })
            )
              .onCancel(() => {
                this.getUIContext()?.animateTo({ curve: curves.interpolatingSpring(0, 1, 400, 38) }, () => {
                  this.dragItem = -1;
                })
                this.getUIContext()?.animateTo({
                  curve: curves.interpolatingSpring(14, 1, 170, 17)
                }, () => {
                  this.scaleItem = -1;
                })
              })
          )
        }, (item: number) => item.toString())
      }
      .width('90%')
      .editMode(true)
      .scrollBar(BarState.Off)
      .columnsTemplate('1fr 1fr 1fr')
    }.width('100%').height('100%').backgroundColor('#0D182431').padding({ top: 5 })
  }
}
```

### Example 17: Dragging Grid Items with Drag Events

This example demonstrates dragging GridItem components to the Grid component's edges to trigger automatic scrolling, implemented through [drag events](./ts-universal-events-drag-drop.md).

For details about GridDataSource and the complete code, see [Example 2: Implementing a Scrollable Grid with Scroll Events](#example-2-implementing-a-scrollable-grid-with-scroll-events).



```TypeScript
// xxx.ets
import { GridDataSource } from './GridDataSource';

@Entry
@Component
struct Example {
  numbers: GridDataSource = new GridDataSource([]);

  aboutToAppear(): void {
    let list: string[] = [];
    for (let index = 0; index < 100; index++) {
      list.push(index.toString());
    }
    this.numbers = new GridDataSource(list);
  }

  changeIndex(index1: number, index2: number) { // Exchange the array positions.
    console.info(index1 + 'index2:' + index2);
    this.numbers.swapItem(index1, index2);
  }

  build() {
    Column({ space: 5 }) {
      Grid() {
        LazyForEach(this.numbers, (item: string, index: number) => {
          GridItem() {
            Text(item + '')
              .fontSize(16)
              .backgroundColor(0xF9CF93)
              .width(80)
              .height(80)
              .textAlign(TextAlign.Center)
          }
          .width(90)
          .height(90)
          .selectable(true)
          .selected(true)
          .allowDrop([])
          .onDragStart((event: DragEvent) => {
            return { extraInfo: index + '' };
          })
          .onDragEnter((event: DragEvent, extraParams?: string) => {
            console.info(index + '' + extraParams);
          })
          .onDragEnd((event: DragEvent, extraParams?: string) => {
            console.info('onDragEnd' + index + '' + extraParams);
          })
          .onDrop((event?: DragEvent, extraParams?: string) => {
            console.info('drop:' + item + '' + extraParams + JSON.stringify(event!));
            this.changeIndex(parseInt(JSON.parse(extraParams!).extraInfo), index);
          })
        }, (item: string, index: number) => item + '+' + index)
      }
      .columnsGap(5)
      .rowsGap(5)
      .columnsTemplate('1fr 1fr 1fr')
      .height(300)
    }
    .width('100%')
  }
}
```

### Example 18: Configuring the Number of Columns in the Grid Component Based on Breakpoints

In API version 22 and later versions, this example shows how to configure the number of columns in the Grid component based on breakpoints.

When the grid width is within the breakpoint range of sm or smaller, two columns are displayed.



When the grid width is within the breakpoint range of md, three columns are displayed.



When the grid width is within the breakpoint range of lg or larger, five columns are displayed.



```TypeScript
// Index.ets
// xxx.ets
import { GridDataSource } from './GridDataSource';

@Entry
@Component
struct GridExample {
  numbers: GridDataSource = new GridDataSource([]);

  aboutToAppear() {
    let list: string[] = [];
    for (let i = 0; i < 5; i++) {
      for (let j = 0; j < 5; j++) {
        list.push(j.toString());
      }
    }
    this.numbers = new GridDataSource(list);
  }

  build() {
    Column({ space: 5 }) {
      Grid(undefined) {
        LazyForEach(this.numbers, (day: string) => {
          GridItem() {
            Text(day)
              .fontSize(16)
              .backgroundColor(0xF9CF93)
              .width('100%')
              .height(80)
              .textAlign(TextAlign.Center)
          }
        }, (index: number) => index.toString())
      }
      .columnsTemplate({fillType:PresetFillType.BREAKPOINT_SM2MD3LG5})
      .columnsGap(10)
      .rowsGap(10)
      .scrollBar(BarState.Off)
      .width('100%')
      .backgroundColor(0xFAEEE0)
      .height(300)
    }.width('100%').height('10%').justifyContent(FlexAlign.SpaceBetween)
  }
}
```

### Example 19: Obtaining the Total Content Size

This example demonstrates how to obtain the total content size. This functionality is supported since API version 22.

For details about GridDataSource and the complete code, see [Example 2: Implementing a Scrollable Grid with Scroll Events](#example-2-implementing-a-scrollable-grid-with-scroll-events).



```TypeScript
import { GridDataSource } from './GridDataSource';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct GridExample {
  numbers: GridDataSource = new GridDataSource([]);
  scroller: Scroller = new Scroller();
  @State contentWidth: number = -1;
  @State contentHeight: number = -1;

  aboutToAppear() {
    let list: string[] = [];
    for (let i = 0; i < 10; i++) {
      for (let j = 0; j < 5; j++) {
        list.push(j.toString());
      }
    }
    this.numbers = new GridDataSource(list);
  }

  build() {
    Column({ space: 5 }) {
      Text('Scrollable Grid and LazyForEach')
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
              console.error(`Failed to get contentSize of the grid, code=${err.code}, message=${err.message}`);
            }
          })
        // Display the obtained content size.
        Text('Width: ' + this.contentWidth + ', Height: ' + this.contentHeight)
          .fontColor(Color.Red)
          .height(50)
      }

      Grid(this.scroller) {
        LazyForEach(this.numbers, (day: string) => {
          GridItem() {
            Text(day)
              .fontSize(16)
              .backgroundColor(0xF9CF93)
              .width('100%')
              .height(80)
              .textAlign(TextAlign.Center)
          }
          .margin(20)
        }, (index: number) => index.toString())
      }
      .columnsTemplate('1fr 1fr 1fr 1fr 1fr')
      .columnsGap(10)
      .rowsGap(10)
      .friction(0.6)
      .enableScrollInteraction(true)
      .supportAnimation(false)
      .multiSelectable(false)
      .edgeEffect(EdgeEffect.Spring)
      .scrollBar(BarState.On)
      .scrollBarColor(Color.Grey)
      .scrollBarWidth(4)
      .width('90%')
      .backgroundColor(0xFAEEE0)
      .height(300)
    }.width('100%').margin({ top: 5 })
  }
}
```

### Example 20: Setting the Multi-selection Gather Animation

This example enables the multi-select gather animation switch of the Grid to implement the effect of gathering the selected GridItem items within the display range through [bindContextMenu](ts-universal-attributes-menu.md#bindcontextmenu8) when a context menu is popped up by long pressing a GridItem.

Since API version 23, the [editModeOptions](#editmodeoptions23) API is added to the Grid component to set the multi-selection gather animation switch.

For details about GridDataSource and the complete code, see [Example 2: Implementing a Scrollable Grid with Scroll Events](#example-2-implementing-a-scrollable-grid-with-scroll-events).



```TypeScript
// xxx.ets
import { GridDataSource } from './GridDataSource';

@Entry
@Component
struct GridExample {
  numbers: GridDataSource = new GridDataSource(['1', '2', '3', '4', '5', '6', '7', '8', '9']);
  @State isSelected: boolean[] = [];
  selectedCount: number = 0;

  @Styles
  normalStyles(): void {
    .opacity(1.0)
  }

  @Styles
  selectStyles(): void {
    .opacity(0.4)
  }

  onPageShow(): void {
    let i: number = 0;
    for (i = 0; i < 9; i++) {
      this.isSelected.push(false);
    }
  }

  @Builder
  MenuBuilder() {
    Flex({ direction: FlexDirection.Column, justifyContent: FlexAlign.Center, alignItems: ItemAlign.Center }) {
      Text('menu item 1')
        .fontSize(18)
        .width(120)
        .height(50)
        .textAlign(TextAlign.Center)
      Divider().height(10)
      Text('menu item 2')
        .fontSize(18)
        .width(120)
        .height(50)
        .textAlign(TextAlign.Center)
    }.width(100)
  }

  build() {
    Column({ space: 5 }) {
      Text('Grid')
      Grid() {
        LazyForEach(this.numbers, (day: string, index: number) => {
          GridItem() {
            Text(day)
              .fontSize(16)
              .backgroundColor(0xF9CF93)
              .width('100%')
              .height('100%')
              .textAlign(TextAlign.Center)
          }
          .selected(this.isSelected[index])
          // Set the multi-selection display effects.
          .stateStyles({
            normal: this.normalStyles,
            selected: this.selectStyles
          })
          .bindContextMenu(this.MenuBuilder, ResponseType.LongPress,
            { preview: MenuPreviewMode.IMAGE, hapticFeedbackMode: HapticFeedbackMode.ENABLED })
          .onClick(() => {
            this.isSelected[index] = !this.isSelected[index];
            console.info(`item:${index}, this.isSelected[item]:${this.isSelected[index]}`)
            if (this.isSelected[index]) {
              ++this.selectedCount;
            } else {
              --this.selectedCount;
            }
          })
        }, (day: string) => day)
      }
      .editModeOptions({
        enableGatherSelectedItemsAnimation: true, onGetPreviewBadge: () => {
          return this.selectedCount;
        }
      })
      .columnsTemplate('1fr 1fr 1fr')
      .rowsTemplate('1fr 1fr 1fr')
      .columnsGap(10)
      .rowsGap(10)
      .width('90%')
      .backgroundColor(0xFAEEE0)
      .height(300)
    }.width('100%').margin({ top: 5 })
  }
}
```

### Example 21: Implementing Swipe-based Multi-Selection

This example uses the two-way binding of  and the  event to listen for the notification of entering the multi-select mode by swiping with two fingers on the Grid, implementing the effect of selecting while swiping on the Grid.

Since API version 26.0.0, the Grid component adds the [enableEditMode](#enableeditmode) API and the [onEditModeChange](#oneditmodechange) event.

For details about GridDataSource and the complete code, see [Example 2: Implementing a Scrollable Grid with Scroll Events](#example-2-implementing-a-scrollable-grid-with-scroll-events).



```TypeScript
// xxx.ets
import { GridDataSource } from './GridDataSource';

@Entry
@Component
struct GridExample {
  numbers: GridDataSource = new GridDataSource([]);
  @State @Watch('onEditModeChanged') enableEditMode: boolean = false;
  @State enableTwoFingerSelect: boolean = false;
  @State selectedIndexes: number[] = [];

  onEditModeChanged() {
    console.info(`enableEditMode changed to: ${this.enableEditMode}`);
    if (!this.enableEditMode) {
      console.info('enableEditMode changed to false, clearing selectedIndexes');
      this.selectedIndexes = [];
    }
  }

  aboutToAppear() {
    let list: string[] = [];
    for (let i = 0; i < 20; i++) {
      for (let j = 0; j < 20; j++) {
        list.push((20 * i + j + 1).toString());
      }
    }
    this.numbers = new GridDataSource(list);
  }

  build() {
    Column({ space: 5 }) {
      Grid() {
        LazyForEach(this.numbers, (day: string, index: number) => {
          GridItem() {
            Stack() {
              Text(day)
                .fontSize(16)
                .backgroundColor(0xF9CF93)
                .width('100%')
                .height(80)
                .textAlign(TextAlign.Center)
            }
          }
          .selected(this.selectedIndexes.includes(index))
          .onSelect((isSelected: boolean) => {
            console.info('item ' + index.toString() + ' is ' + (isSelected ? 'selected' : 'unselected'));
            if (isSelected) {
              this.selectedIndexes.push(index);
            } else {
              let deleted = this.selectedIndexes.findIndex((value) => value === index);
              if (deleted !== -1) {
                this.selectedIndexes.splice(deleted, 1);
              }
            }
          })
        }, (index: number) => index.toString())
      }
      .columnsTemplate('1fr 1fr 1fr')
      .columnsGap(10)
      .rowsGap(10)
      .width('90%')
      .height('50%')
      .backgroundColor(0xFAEEE0)
      .enableEditMode(this.enableEditMode!!)
      .onEditModeChange((data: boolean) => {
        // Alternatively, implement the business logic in onEditModeChanged here without using the enableEditMode two-way binding.
        console.info(`onEditModeChange:${data}`)
      })
      .editModeOptions({ useDefaultMultiSelectStyle: true, enableTwoFingerMultiSelect: this.enableTwoFingerSelect })

      Row() {
        Button('EditMode: ' + this.enableEditMode).onClick(() => {
          this.enableEditMode = !this.enableEditMode;
        })
        Button('TwoFinger: ' + this.enableTwoFingerSelect).onClick(() => {
          this.enableTwoFingerSelect = !this.enableTwoFingerSelect;
        })
      }
      .margin({
        bottom: 30
      })
    }.width('100%').margin({ top: 5 })
  }
}
```

### Example 22: Dragging with OnMove

Since API version 26.0.0, this example demonstrates the effect of drag sorting using the [onMove](./ts-universal-attributes-drag-sorting.md#onmove) API of LazyForEach in the Grid. It supports triggering automatic scrolling of the Grid when dragging to the edge, and the Grid contains nodes that span rows and columns.

```TypeScript
// RectGridDataSource.ets
export class Rects {
  id: number = 0
  // rectSize indicates the number of [rows, columns] occupied by the GridItem. The default value [1, 1] indicates a regular node.
  rectSize: [number, number] = [1, 1]
  constructor(id_: number) {
    this.id = id_
  }
}

// Data source of LazyForEach, which implements the IDataSource interface and manages data and notifies the UI to refresh.
export class RectGridDataSource implements IDataSource {
  private list: Array<Rects> = [];
  private listeners: DataChangeListener[] = [];

  constructor(list: Rects[]) {
    this.list = list;
  }

  // Return the total number of data items.
  totalCount(): number {
    return this.list.length;
  }

  // Obtain the corresponding data item by index.
  getData(index: number): Rects {
    return this.list[index];
  }

  // Register a data change listener.
  registerDataChangeListener(listener: DataChangeListener): void {
    if (this.listeners.indexOf(listener) < 0) {
      this.listeners.push(listener);
    }
  }

  // Unregister the data change listener.
  unregisterDataChangeListener(listener: DataChangeListener): void {
    const pos = this.listeners.indexOf(listener);
    if (pos >= 0) {
      this.listeners.splice(pos, 1);
    }
  }

  // Notify the controller of the data position change.
  notifyDataMove(from: number, to: number): void {
    this.listeners.forEach(listener => {
      listener.onDataMove(from, to);
    })
  }

  // Reload all data.
  notifyDataReload(): void {
    this.listeners.forEach(listener => {
      listener.onDataReloaded();
    })
  }

  // Move the element at the from position to the to position, and notify the UI to reload and refresh all data.
  public moveItem(from: number, to: number): void {
    let tmp = this.list.splice(from, 1);  // Remove the dragged item first.
    this.list.splice(to, 0, tmp[0]);      // Insert the dragged item into the target position.
    this.notifyDataReload()
  }
}
```

```TypeScript
// xxx.ets
import { RectGridDataSource, Rects } from './RectGridDataSource';

@Entry
@Component
struct GridOnMoveExample {
  numbers: RectGridDataSource = new RectGridDataSource([]);

  // Grid layout options (actually effective), which declare the indexes of irregular nodes and the number of rows and columns occupied by each.
  @State layoutOptions: GridLayoutOptions = {
    regularSize: [1, 1],
    irregularIndexes: [4, 5, 6, 7, 8, 13],   // Set which indexes correspond to irregular GridItem nodes.
    onGetIrregularSizeByIndex: (index: number) => {
      return this.numbers.getData(index).rectSize
    }
  };

  // Layout options (backup), used to trigger the refresh of layoutOptions through overall assignment during dragging.
  layoutOptions_back: GridLayoutOptions = {
    regularSize: [1, 1],
    irregularIndexes: [4, 5, 6, 7, 8, 13],
    onGetIrregularSizeByIndex: (index: number) => {
      return this.numbers.getData(index).rectSize
    }
  };

  build() {
    Row() {
      Grid(undefined, this.layoutOptions) {
        LazyForEach(this.numbers, (item: Rects) => {
          GridItem() {
            Text(item.id.toString())
              .fontSize(16)
              .textAlign(TextAlign.Center)
              // Set the height. A GridItem spanning multiple rows needs an extra margin (the spacing of a regular GridItem is 2*10) for UI alignment.
              .size({ height: 100 * item.rectSize[0] + (item.rectSize[0] - 1) * 20, width: '100%'})
          }.margin(10)
          .borderRadius(10)
          .backgroundColor(0xF9CF93)
        }, (index: Rects) => index.id.toString())
          // Triggered when the dragged item is released and its landing position differs from the position before dragging. from is the start index, and to is the target index.
          .onMove((from:number, to:number) => {
            console.info("Grid onMove from " + from + " to " + to)
            // Update the data source.
            this.numbers.moveItem(from, to)
            if (from < to) {  // The index of the dragged item is smaller than the target position index.
              // Save the position of the dragged item in the irregularIndexes array first to avoid indexOf locating errors caused by duplicate values generated in subsequent loop updates.
              let from_idx = -1
              if (this.layoutOptions.irregularIndexes?.includes(from)) {
                from_idx = this.layoutOptions.irregularIndexes.indexOf(from)
              }

              // The elements between the dragged item and the target position move forward by one position as a whole (index -1).
              if (this.layoutOptions.irregularIndexes != undefined) {
                let len = this.layoutOptions.irregularIndexes.length
                for (let i = len - 1; i >= 0; i --) {
                  let irregularIndex = this.layoutOptions.irregularIndexes[i]
                  if (irregularIndex > from && irregularIndex <= to) {
                    this.layoutOptions.irregularIndexes[i] --
                  }
                }
              }

              // If the dragged item itself is an irregular node, update its index to the target position.
              if (from_idx != -1 && this.layoutOptions.irregularIndexes != undefined) {
                this.layoutOptions.irregularIndexes[from_idx] = to
              }
            } else {  // The index of the dragged item is greater than or equal to the target position index.
              // Save the position of the dragged item in the irregularIndexes array first to avoid indexOf locating errors caused by duplicate values generated in subsequent loop updates.
              let from_idx = -1
              if (this.layoutOptions.irregularIndexes?.includes(from)) {
                from_idx = this.layoutOptions.irregularIndexes.indexOf(from)
              }

              // The elements between the target position and the dragged item move backward by one position as a whole (index +1).
              if (this.layoutOptions.irregularIndexes != undefined) {
                let len = this.layoutOptions.irregularIndexes.length
                for (let i = 0; i < len; i ++) {
                  let irregularIndex = this.layoutOptions.irregularIndexes[i]
                  if (irregularIndex >= to && irregularIndex < from) {
                    this.layoutOptions.irregularIndexes[i] ++
                  }
                }
              }

              // If the dragged item itself is an irregular node, update its index to the target position.
              if (from_idx != -1 && this.layoutOptions.irregularIndexes != undefined) {
                this.layoutOptions.irregularIndexes[from_idx] = to
              }
            }
            // Assign the backup object as a whole to force layoutOptions to refresh and take effect.
            this.layoutOptions_back.irregularIndexes = this.layoutOptions.irregularIndexes
            this.layoutOptions = this.layoutOptions_back
            console.info("Grid this.layoutOptions.irregularIndexes " + this.layoutOptions.irregularIndexes)
          },
            {
              onLongPress: (index: number) => {
                // Triggered when a GridItem is lifted after a long press.
                console.info('Grid onLongPress: ' + index);
              },
              onDrop: (index: number) => {
                // Triggered when the dragged GridItem is released.
                console.info('Grid onDrop: ' + index);
              },
              onDragStart: (index: number) => {
                // Triggered when a GridItem is lifted after a long press and dragging starts.
                console.info('Grid onDragStart: ' + index);
              },
              onMoveThrough: (from: number, to: number) => {
                // Triggered continuously during the dragging of a GridItem.
                console.info('Grid onMoveThrough From: ' + from + ' to: ' + to);
              }
            })
      }
      .columnsTemplate('1fr 1fr 1fr 1fr')   // Four-column equal-width layout.
      .width('100%')
      .height('100%')
      .backgroundColor(0xFAEEE0)
    }
  }

  aboutToAppear(): void {
    // Initialize 100 rectangle data items and set the spanning size of each irregular node.
    let list: Rects[] = [];
    for (let i = 0; i < 100; i++) {
      list.push(new Rects(i));
    }
    list[4].rectSize = [2, 2] // 2 rows and 2 columns.
    list[5].rectSize = [1, 2] // 1 row and 2 columns.
    list[6].rectSize = [1, 2] // 1 row and 2 columns.
    list[7].rectSize = [2, 1] // 2 rows and 1 column.
    list[8].rectSize = [2, 1] // 2 rows and 1 column.
    list[13].rectSize = [1, 4]  // 1 row and 4 columns.
    this.numbers = new RectGridDataSource(list);
  }
}
```
