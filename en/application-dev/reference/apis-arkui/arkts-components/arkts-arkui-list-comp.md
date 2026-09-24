# List

The **List** component provides a list container that presents a series of list items arranged in a column with the same width. It supports presentations of the same type of data in a multiple and coherent row style, for example, images or text.

Lazy loading of **List** loads the child components in the visible area as required. Compared with full loading, lazy loading can improve the app startup speed and reduce the memory usage. The lazy loading capabilities vary when the **List** component is used together with [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), or [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md).

- When **List** is used together with **ForEach**, all child nodes are created at a time. The nodes within the screen
range are laid out and rendered when needed. When a user swipes, the nodes that are out of the screen range are not removed from the tree, and the nodes that are within the screen range are laid out and rendered.
- When **List** is used together with **LazyForEach**, all nodes within the screen range are created, laid out, and
rendered at a time. When a user swipes, the nodes that are out of the screen range are removed from the tree, and the nodes that are within the screen range are created, laid out, and rendered.
- When the **List** component is used together with **Repeat** with
[virtualScroll](arkts-arkui-repeat-comp-attribute.md#virtualscroll), the lazy loading behavior is the same as that of **LazyForEach**. When the **List** component is used together with **Repeat** without **virtualScroll**, the lazy loading behavior is the same as that of **ForEach**.

If a scrollable component is nested in a **List** component, their scrolling directions are the same, and the main axis size is not set for the **List** component, the **List** component loads all child components. As a result, lazy loading does not take effect. In this scenario, you are advised to use the ListItemGroup component to optimize the performance.

Preloading in **List** refers to loading not only the visible child components within the display area but also some invisible child components outside the display area during idle time. Preloading can reduce frame loss during scrolling and improve smoothness. Preloading takes effect only when lazy loading is used. You can set the number of components to be preloaded for the **List** component using [cachedCount](arkts-arkui-list-comp-attribute.md#cachedcount). By default, child components equivalent to one screen above and below the visible area are preloaded (up to a maximum of 16 rows). The preloading capabilities vary when the **List** component is used together with [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), or [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md).

- When the **List** component is used together with **ForEach** and **cachedCount** is set, in addition to laying out
child components within the visible area, child components within the range of **cachedCount** outside the visible area are pre-laid out during idle time.
- When the **List** component is used together with **LazyForEach** and **cachedCount** is set, in addition to
creating and laying out child components within the display area, child components within the range of **cachedCount** outside the display area are pre-created and pre-laid out during idle time.
- When the **List** component is used together with **Repeat** with
[virtualScroll](arkts-arkui-repeat-comp-attribute.md#virtualscroll), the preloading behavior is the same as that of **LazyForEach**. When the **List** component is used together with **Repeat** without **virtualScroll**, the preloading behavior is the same as that of **ForEach**.

> **NOTE**

> The component has been bound with gestures to implement functions such as follow-up scrolling. If you need to add > custom gestures, refer to Gesture Blocking Enhancement.

## Child Components

Only the ListItem and ListItemGroup child components and custom components are supported. When using custom components inside **List**, you are advised to wrap the custom component with a **ListItem** or **ListItemGroup** as the top-level container. Setting attributes or event methods directly on custom components is not recommended.

Child components can be dynamically generated using rendering control types [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md), [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), and [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md). **LazyForEach** or **Repeat** is recommended to optimize performance.

> **NOTE:** 
> 
> If performance lag occurs when you process a large number of child components, consider using lazy loading, list
> item caching, dynamic preloading, component reuse, and layout optimization. For best practices, see
> [Optimizing Frame Loss for Long List Loading](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-best-practices-long-list).
> 
> Starting from API version 21, the maximum width or height for a single child component inside a **List** container
> is 16,777,216 px. In API version 20 and earlier versions, the limit was 1,000,000 px. If a child component exceeds
> the applicable size limit, scrolling or display behavior may become abnormal.
> 
> Below are the rules for calculating the indexes of the child components of **List**:
> 
> - The index increases in ascending order of child components.
> 
> - In the **if/else** statement, only the child components for which the condition evaluates to true participate in the index calculation.
> 
> - In the **ForEach**, **LazyForEach**, or **Repeat** statement, the indexes of all expanded subnodes are calculated.
> 
> - After changes occur in [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md),[ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md),[LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), and [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md), index values are updated accordingly for child components.
> 
> - Each **ListItemGroup** component is taken as a whole and assigned an index, and the indexes of the list items within are not included in the index calculation.
> 
> - Child components of **List** whose **visibility** attribute is set to **Hidden** or **None** are included in the index calculation.

## List

```TypeScript
List(options?: ListOptions)
```

Creates a list container.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ListOptions](arkts-arkui-list-comp-listoptions-i.md) | No | Options of the **List** component. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [ChainAnimationOptions](arkts-arkui-list-comp-chainanimationoptions-i-sys.md) | Defines the chain animation options. |
| [CloseSwipeActionOptions](arkts-arkui-list-comp-closeswipeactionoptions-i.md) | Implements the callbacks and events for the ListItem in the [expanded](arkts-arkui-listitem-comp-swipeactionstate-e.md) state. |
| [ListBackPressBehavior](arkts-arkui-list-comp-listbackpressbehavior-i.md) | Defines the system back button behavior of the **List** component. |
| [ListDividerOptions](arkts-arkui-list-comp-listdivideroptions-i.md) | Defines the divider style of the list or list item group. |
| [ListOptions](arkts-arkui-list-comp-listoptions-i.md) | Defines the options of the **List** component. |
| [UIListEvent](arkts-arkui-list-comp-uilistevent-i.md) | Represents the return value of the [getEvent('List')](../arkts-apis/arkts-arkui-typenode-getevent-f.md#getevent-1) method in **frameNode**, which can be used to set scroll events for a **List** node. |
| [VisibleListContentInfo](arkts-arkui-list-comp-visiblelistcontentinfo-i.md) | Describes the details of the child components in the visible area of a list. |

### Types

| Name | Description |
| --- | --- |
| [OnListScrollIndexCallback](arkts-arkui-list-comp-onlistscrollindexcallback-t.md) | Represents a callback for item changes in the visible area of the **List** component. |
| [OnScrollVisibleContentChangeCallback](arkts-arkui-list-comp-onscrollvisiblecontentchangecallback-t.md) | Triggered when a child component enters or leaves the list display area. |

### Enums

| Name | Description |
| --- | --- |
| [ChainEdgeEffect](arkts-arkui-list-comp-chainedgeeffect-e-sys.md) | Declare edge effect of chain animation. |
| [ListItemAlign](arkts-arkui-list-comp-listitemalign-e.md) | Sets the alignment mode of child components in the cross-axis direction of the list. |
| [ListItemGroupArea](arkts-arkui-list-comp-listitemgrouparea-e.md) | Enumerates the areas of **ListItemGroup**. |
| [ScrollSnapAlign](arkts-arkui-list-comp-scrollsnapalign-e.md) | Enumerates the alignment modes of list items when scrolling ends. |
| [ScrollSnapAnimationSpeed](arkts-arkui-list-comp-scrollsnapanimationspeed-e.md) | Enumerates the speeds of the snap animation for list scrolling. |
| [ScrollState](arkts-arkui-list-comp-scrollstate-e.md) | Enumerates the scrolling states. |
| [StickyStyle](arkts-arkui-list-comp-stickystyle-e.md) | Enumerates the sticky styles. |

## Examples

### Example 1: Adding a Scroll Event

In this example, a vertical list is implemented, and a callback is invoked when the first or last item displayed in the list changes.

ListDataSource implements the LazyForEach data source API [IDataSource](ts-rendering-control-lazyforeach.md#idatasource), which is used to provide child components for List through LazyForEach.

```TypeScript
// ListDataSource.ets
export class ListDataSource implements IDataSource {
  private list: number[] = [];
  private listeners: DataChangeListener[] = [];

  constructor(list: number[]) {
    this.list = list;
  }

  totalCount(): number {
    return this.list.length;
  }

  getData(index: number): number {
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

  // Notify LazyForEach that all child components need to be reloaded.
  notifyDataReload(): void {
    this.listeners.forEach(listener => {
      listener.onDataReloaded();
    });
  }

  // Notify the controller of data deletion.
  notifyDataDelete(index: number): void {
    this.listeners.forEach(listener => {
      listener.onDataDelete(index);
    });
  }

  // Notify the controller of data insertion.
  notifyDataAdd(index: number): void {
    this.listeners.forEach(listener => {
      listener.onDataAdd(index);
    });
  }

  // Delete an element at the specified index.
  public deleteItem(index: number): void {
    this.list.splice(index, 1);
    this.notifyDataDelete(index);
  }

  // Insert an element at the specified index.
  public insertItem(index: number, data: number): void {
    this.list.splice(index, 0, data);
    this.notifyDataAdd(index);
  }

  public reloadData(): void {
    this.notifyDataReload();
  }
}
```



```TypeScript
// xxx.ets
import { ListDataSource } from './ListDataSource';

@Entry
@Component
struct ListExample {
  private arr: ListDataSource = new ListDataSource([0, 1, 2, 3, 4, 5, 6, 7, 8, 9]);

  build() {
    Column() {
      List({ space: 20, initialIndex: 0 }) {
        LazyForEach(this.arr, (item: number) => {
          ListItem() {
            Text('' + item)
              .width('100%').height(100).fontSize(16)
              .textAlign(TextAlign.Center).borderRadius(10).backgroundColor(0xFFFFFF)
          }
        }, (item: number) => item.toString())
      }
      .listDirection(Axis.Vertical) // Arrangement direction
      .scrollBar(BarState.Off)
      .friction(0.6)
      .divider({ strokeWidth: 2, color: 0xFFFFFF, startMargin: 20, endMargin: 20 }) // Divider
      .edgeEffect(EdgeEffect.Spring) // Set the edge scrolling effect to Spring.
      .onScrollIndex((firstIndex: number, lastIndex: number, centerIndex: number) => {
        console.info('first' + firstIndex);
        console.info('last' + lastIndex);
        console.info('center' + centerIndex);
      })
      .onScrollVisibleContentChange((start: VisibleListContentInfo, end: VisibleListContentInfo) => {
        console.info(' start index: ' + start.index +
                    ' start item group area: ' + start.itemGroupArea +
                    ' start index in group: ' + start.itemIndexInGroup);
        console.info(' end index: ' + end.index +
                    ' end item group area: ' + end.itemGroupArea +
                    ' end index in group: ' + end.itemIndexInGroup);
      })
      .onDidScroll((scrollOffset: number, scrollState: ScrollState) => {
        console.info(`onScroll scrollState = ScrollState` + scrollState + `, scrollOffset = ` + scrollOffset);
      })
      .width('90%')
    }
    .width('100%')
    .height('100%')
    .backgroundColor(0xDCDCDC)
    .padding({ top: 5 })
  }
}
```

### Example 2: Setting Child Element Alignment

This example showcases the alignment effects of child elements in the cross-axis direction of the List component using different ListItemAlign enumeration values.

For details about ListDataSource and the complete code, see [Example 1: Adding a Scroll Event](#example-1-adding-a-scroll-event).



```TypeScript
// xxx.ets
import { ListDataSource } from './ListDataSource';

@Entry
@Component
struct ListLanesExample {
  arr: ListDataSource = new ListDataSource([0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19]);
  @State alignListItem: ListItemAlign = ListItemAlign.Start;

  build() {
    Column() {
      List({ space: 20, initialIndex: 0 }) {
        LazyForEach(this.arr, (item: number) => {
          ListItem() {
            Text('' + item)
              .width('100%')
              .height(100)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .borderRadius(10)
              .backgroundColor(0xFFFFFF)
          }
          .border({ width: 2, color: Color.Green })
        }, (item: number) => item.toString())
      }
      .height(300)
      .width('90%')
      .friction(0.6)
      .border({ width: 3, color: Color.Red })
      .lanes({ minLength: 40, maxLength: 40 })
      .alignListItem(this.alignListItem)
      .scrollBar(BarState.Off)

      Button('Change alignListItem:' + this.alignListItem).onClick(() => {
        if (this.alignListItem == ListItemAlign.Start) {
          this.alignListItem = ListItemAlign.Center;
        } else if (this.alignListItem == ListItemAlign.Center) {
          this.alignListItem = ListItemAlign.End;
        } else {
          this.alignListItem = ListItemAlign.Start;
        }
      })
    }.width('100%').height('100%').backgroundColor(0xDCDCDC).padding({ top: 5 })
  }
}
```

### Example 3: Customizing Edit and Delete Mode

This example shows how to control the display and hiding of the delete button through a custom state variable and update the data source in the click event of the delete button to implement the list item deletion effect.

For details about ListDataSource and the complete code, see [Example 1: Adding a Scroll Event](#example-1-adding-a-scroll-event).



```TypeScript
// xxx.ets
import { ListDataSource } from './ListDataSource';

@Entry
@Component
struct ListExample {
  arr: ListDataSource = new ListDataSource([0, 1, 2, 3, 4, 5, 6, 7, 8, 9]);
  @State editFlag: boolean = false;

  build() {
    Stack({ alignContent: Alignment.TopStart }) {
      Column() {
        List({ space: 20, initialIndex: 0 }) {
          LazyForEach(this.arr, (item: number, index: number) => {
            ListItem() {
              Flex({ direction: FlexDirection.Row, alignItems: ItemAlign.Center }) {
                Text('' + item)
                  .width('100%')
                  .height(80)
                  .fontSize(20)
                  .textAlign(TextAlign.Center)
                  .borderRadius(10)
                  .backgroundColor(0xFFFFFF)
                  .flexShrink(1)
                if (this.editFlag) {
                  Button() {
                    Text('delete').fontSize(16)
                  }.width('30%').height(40)
                  .onClick(() => {
                    if (index != undefined) {
                      console.info(this.arr.getData(index) + 'Delete');
                      this.arr.deleteItem(index);
                      this.arr.reloadData();
                      console.info(JSON.stringify(this.arr));
                      this.editFlag = false;
                    }
                  }).stateEffect(true)
                }
              }
            }
          }, (item: number, index: number) => item.toString() + index.toString())
        }.width('90%')
        .scrollBar(BarState.Off)
        .friction(0.6)
      }.width('100%')

      Button('edit list')
        .onClick(() => {
          this.editFlag = !this.editFlag;
        }).margin({ top: 5, left: 20 })
    }.width('100%').height('100%').backgroundColor(0xDCDCDC).padding({ top: 5 })
  }
}
```

### Example 4: Setting the Alignment Mode for the Scroll Snap Position

This example shows how to configure the List component to align the scroll snap position to the center.

For details about ListDataSource and the complete code, see [Example 1: Adding a Scroll Event](#example-1-adding-a-scroll-event).



```TypeScript
// xxx.ets
import { ListDataSource } from './ListDataSource';

@Entry
@Component
struct ListExample {
  private arr: ListDataSource=new ListDataSource([]);
  private scrollerForList: Scroller = new Scroller();

  aboutToAppear() {
    let list: number[] = [];
    for (let i = 0; i < 20; i++) {
      list.push(i);
    }
    this.arr = new ListDataSource(list);
  }

  build() {
    Column() {
      Row() {
        List({ space: 20, initialIndex: 3, scroller: this.scrollerForList }) {
          LazyForEach(this.arr, (item: number) => {
            ListItem() {
              Text('' + item)
                .width('100%').height(100).fontSize(16)
                .textAlign(TextAlign.Center)
            }
            .borderRadius(10).backgroundColor(0xFFFFFF)
            .width('60%')
            .height('80%')
          }, (item: number) => JSON.stringify(item))
        }
        .chainAnimation(true)
        .edgeEffect(EdgeEffect.Spring)
        .listDirection(Axis.Horizontal)
        .height('100%')
        .width('100%')
        .scrollSnapAlign(ScrollSnapAlign.CENTER)
        .borderRadius(10)
        .backgroundColor(0xDCDCDC)
      }
      .width('100%')
      .height('100%')
      .backgroundColor(0xDCDCDC)
      .padding({ top: 10 })
    }
  }
}
```

### Example 5: Implementing Accurate Scrolling

This example shows that, by setting the [childrenMainSize](#childrenmainsize12) attribute, the list can jump to an exact specific location when the scrollTo API is called, even when the heights of the child components are inconsistent.

For usage with state management V2, see [List and makeObserved](../../../ui/state-management/arkts-v1-v2-migration-inner-object.md#scrollable-component).

For details about ListDataSource and the complete code, see [Example 1: Adding a Scroll Event](#example-1-adding-a-scroll-event).



```TypeScript
// xxx.ets
import { BusinessError } from '@kit.BasicServicesKit';
import { ListDataSource } from './ListDataSource';

@Entry
@Component
struct ListExample {
  private arr: ListDataSource = new ListDataSource([]);
  private scroller: ListScroller = new ListScroller();
  @State listSpace: number = 10;
  @State listChildrenSize: ChildrenMainSize = new ChildrenMainSize(100);
  aboutToAppear(){
    // Initialize the data source.
    let list: number[] = [];
    for (let i = 0; i < 10; i++) {
      list.push(i);
    }
    this.arr = new ListDataSource(list);
    // The first five items do not have a default main axis size of 100; therefore, it is necessary to inform the list through the ChildrenMainSize.
    try {
      this.listChildrenSize.splice(0, 5, [300, 300, 300, 300, 300]);
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`Failed to splice childrenMainSize for first 5 items. Code: ${err.code}, message: ${err.message}`);
    }
  }

  build() {
    Column() {
      List({ space: this.listSpace, initialIndex: 4, scroller: this.scroller }) {
        LazyForEach(this.arr, (item: number) => {
          ListItem() {
            Text('item-' + item)
              .height( item < 5 ? 300 : this.listChildrenSize.childDefaultSize)
              .width('90%')
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .borderRadius(10)
              .backgroundColor(0xFFFFFF)
          }
        }, (item: number) => item.toString())
      }
      .backgroundColor(Color.Gray)
      .layoutWeight(1)
      .scrollBar(BarState.On)
      .childrenMainSize(this.listChildrenSize)
      .alignListItem(ListItemAlign.Center)
      Row({ space: 18 }) {
        Button() { Text('item size + 50') }.onClick(()=>{
          this.listChildrenSize.childDefaultSize += 50;
        }).height('50%').width('30%').backgroundColor(0xADD8E6)
        Button() { Text('item size - 50') }.onClick(()=>{
          if (this.listChildrenSize.childDefaultSize === 0) {
            return;
          }
          this.listChildrenSize.childDefaultSize -= 50;
        }).height('50%').width('30%').backgroundColor(0xADD8E6)
        Button() { Text('scrollTo (0, 310)') }.onClick(()=>{
          // 310: Jump to the position where the top of item 1 is aligned with the top of the list.
          // If childrenMainSize is not set, the scrollTo API may not work correctly when the heights of the list items are inconsistent.
          this.scroller.scrollTo({ xOffset: 0, yOffset: 310 })
        }).height('50%').width('30%').backgroundColor(0xADD8E6)
      }.height('20%')
    }
  }
}
```

### Example 6: Obtaining Child Component Index Information

This example demonstrates how to obtain index information of list items in a List component when groups are involved.



```TypeScript
// xxx.ets
import { BusinessError } from '@kit.BasicServicesKit';

class TimeTableDataSource implements IDataSource {
  private list: TimeTable[] = [];

  constructor(list: TimeTable[]) {
    this.list = list;
  }

  totalCount(): number {
    return this.list.length;
  }

  getData(index: number): TimeTable {
    return this.list[index];
  }

  registerDataChangeListener(listener: DataChangeListener): void {
  }

  unregisterDataChangeListener(listener: DataChangeListener): void {
  }
}

class ProjectsDataSource implements IDataSource {
  private list: string[] = [];

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
  }

  unregisterDataChangeListener(listener: DataChangeListener): void {
  }
}

@Entry
@Component
struct ListItemGroupExample {
  private timeTable: TimeTable[] = [
  {
    title: 'Monday',
    projects: ['Language', 'Math', 'English']
  },
  {
    title: 'Tuesday',
    projects: ['Physics', 'Chemistry', 'Biology']
  },
  {
    title: 'Wednesday',
    projects: ['History', 'Geography', 'Politics']
  },
  {
    title: 'Thursday',
    projects: ['Art', 'Music', 'Sports']
  }
];
  private scroller: ListScroller = new ListScroller();
  @State listIndexInfo: VisibleListContentInfo = { index: -1 };
  @State mess:string = 'null';
  @State itemBackgroundColorArr: boolean[] = [false];
  @Builder
  itemHead(text: string) {
    Text(text)
      .fontSize(20)
      .backgroundColor(0xAABBCC)
      .width('100%')
      .padding(10)
  }

  @Builder
  itemFoot(num: number) {
    Text('Total lessons: ' + num)
      .fontSize(16)
      .backgroundColor(0xAABBCC)
      .width('100%')
      .padding(5)
  }

  build() {
    Column() {
      List({ space: 20, scroller: this.scroller}) {
        LazyForEach(new TimeTableDataSource(this.timeTable), (item: TimeTable, index: number) => {
          ListItemGroup({ header: this.itemHead(item.title), footer: this.itemFoot(item.projects.length) }) {
            LazyForEach(new ProjectsDataSource(item.projects), (project: string, subIndex: number) => {
              ListItem() {
                Text(project)
                  .width('100%')
                  .height(100)
                  .fontSize(20)
                  .textAlign(TextAlign.Center)
                  .backgroundColor(this.itemBackgroundColorArr[index * 3 +subIndex] ? 0x68B4FF: 0xFFFFFF)
              }
            }, (item: string) => item)
          }
          .divider({ strokeWidth: 1, color: Color.Blue }) // Divider between lines
        }, (item: TimeTable) => item.title)
      }
      .width('90%')
      .sticky(StickyStyle.Header | StickyStyle.Footer)
      .scrollBar(BarState.Off)
      .gesture(
        PanGesture()
          .onActionUpdate((event: GestureEvent) => {
            if (event.fingerList[0] != undefined && event.fingerList[0].localX != undefined && event.fingerList[0].localY != undefined) {
              try {
                this.listIndexInfo =
                  this.scroller.getVisibleListContentInfo(event.fingerList[0].localX, event.fingerList[0].localY);
              } catch (error) {
                let err: BusinessError = error as BusinessError;
                console.error(`Failed to get visible list content info. Code: ${err.code}, message: ${err.message}`);
              }
              let itemIndex:string = 'undefined';
              if (this.listIndexInfo.itemIndexInGroup != undefined ) {
                itemIndex = this.listIndexInfo.itemIndexInGroup.toString();
                if (this.listIndexInfo.index != undefined && this.listIndexInfo.index >= 0 &&
                  this.listIndexInfo.itemIndexInGroup >= 0 ) {
                  this.itemBackgroundColorArr[this.listIndexInfo.index * 3 + this.listIndexInfo.itemIndexInGroup] = true;
                }
              }
              this.mess = 'index:' + this.listIndexInfo.index.toString() + ' itemIndex:' + itemIndex;
            }
          }))
      .gesture(
        TapGesture({ count: 1 })
          .onAction((event: GestureEvent) => {
            if (event) {
              this.itemBackgroundColorArr.splice(0,this.itemBackgroundColorArr.length);
            }
          })
      )
      Text('You are currently at index '+ this.mess)
        .fontColor(Color.Red)
        .height(50)
    }.width('100%').height('90%').backgroundColor(0xDCDCDC).padding({ top: 5 })
  }
}

interface TimeTable {
  title: string;
  projects: string[];
}
```

### Example 7: Setting Edge Fading

This example demonstrates how to implement a List component with an edge fading effect and set the length of the fading edge.

For details about ListDataSource and the complete code, see [Example 1: Adding a Scroll Event](#example-1-adding-a-scroll-event).



```TypeScript
import { LengthMetrics } from '@kit.ArkUI'
import { ListDataSource } from './ListDataSource';
@Entry
@Component
struct ListExample {
  private arr: ListDataSource=new ListDataSource([0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11]);
  scrollerForList: Scroller = new Scroller();

  build() {
    Column() {

      List({ space: 20, initialIndex: 0, scroller: this.scrollerForList }) {
        LazyForEach(this.arr, (item: number) => {
          ListItem() {
            Text('' + item)
              .width('100%').height(100).fontSize(16)
              .textAlign(TextAlign.Center).borderRadius(10).backgroundColor(0xFFFFFF)
          }
        }, (item: number) => item.toString())
      }
      .fadingEdge(true, { fadingEdgeLength: LengthMetrics.vp(80) })
    }
    .width('100%')
    .height('100%')
    .backgroundColor(0xDCDCDC)
    .padding({ top: 5 })
  }
}
```

### Example 8: Setting the Single-Side Edge Effect

This example demonstrates how to set a single-side edge effect for the List component using the edgeEffect API.

For details about ListDataSource and the complete code, see [Example 1: Adding a Scroll Event](#example-1-adding-a-scroll-event).



```TypeScript
// xxx.ets
import { ListDataSource } from './ListDataSource';

@Entry
@Component
struct ListExample {
  private arr: ListDataSource = new ListDataSource([0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11]);
  scrollerForList: Scroller = new Scroller();
  build() {
    Column() {
      List({ space: 20, initialIndex: 0, scroller: this.scrollerForList }) {
        LazyForEach(this.arr, (item: number) => {
          ListItem() {
            Text('' + item)
              .width('100%').height(100).fontSize(16)
              .textAlign(TextAlign.Center).borderRadius(10).backgroundColor(0xFFFFFF)
          }
        }, (item: number) => item.toString())
      }
      .edgeEffect(EdgeEffect.Spring, {alwaysEnabled: true, effectEdge: EffectEdge.START})
      .width('90%').height('90%')
    }
    .width('100%')
    .height('100%')
    .backgroundColor(0xDCDCDC)
    .padding({ top: 5 })
  }
}
```

### Example 9: Setting Focus Wrap on a List

In API version 20 and later versions, this example uses the [focusWrapMode](#focuswrapmode20) API to implement the effect of line-wrapping focus navigation with arrow keys in the List component.



```TypeScript
@Entry
@Component
struct ListExample {
  @State arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
  build() {
    Stack({ alignContent: Alignment.TopStart }) {
      Column() {
        List({ space: 40, initialIndex: 0 }) {
          ForEach(this.arr, (item: number, index: number) => {
            ListItem() {
              Flex({ direction: FlexDirection.Row, alignItems: ItemAlign.Center }) {
                Text('' + item)
                  .width(150)
                  .height(93)
                  .fontSize(30)
                  .textAlign(TextAlign.Center)
                  .borderRadius(10)
                  .backgroundColor(0xFFFFFF)
                  .flexShrink(1)
                  .focusable(true)
                  .offset({ left: 5 })
              }
            }
          }, (item: number, index: number) => item.toString() + index.toString())
        }
        .lanes(2)
        .contentStartOffset(20)
        .contentEndOffset(20)
        .width('100%')
        .scrollBar(BarState.Off)
        .friction(0.6)
        .focusWrapMode(FocusWrapMode.WRAP_WITH_ARROW)
        .alignListItem(ListItemAlign.Center)
        .offset({ left: 20 })
      }.width('90%')
    }.width('100%').height('100%').backgroundColor(0xDCDCDC).padding({ top: 5 })
  }
}
```

### Example 10: Keeping the Display Content Unchanged When Data Is Inserted Outside the Display Area

This example uses the maintainVisibleContentPosition API to implement infinite loading of historical messages when the screen is swiped up.

For details about ListDataSource and the complete code, see [Example 1: Adding a Scroll Event](#example-1-adding-a-scroll-event).



```TypeScript
import { ListDataSource } from './ListDataSource';

@Entry
@Component
struct ListExample {
  private arr: ListDataSource = new ListDataSource([990, 991, 992, 993, 994, 995, 996, 997, 998, 999]);
  build() {
    Column() {
      List({ space: 20, initialIndex: 9 }) {
        LazyForEach(this.arr, (item: number) => {
          ListItem() {
            Text('message:' + item)
              .width('100%').height(100)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .borderRadius(10)
              .backgroundColor(0xFFFFFF)
          }
        }, (item: number) => item.toString())
      }
      .maintainVisibleContentPosition(true)
      .onScrollIndex((start:number)=>{
        if (start < 5) {
          for (let i = 0; i < 10; i++) {
            this.arr.insertItem(0, this.arr.getData(0) - 1);
          }
        }
      })
    }
    .width('100%')
    .height('100%')
    .backgroundColor(0xDCDCDC)
    .padding(12)
  }
}
```

### Example 11: Setting the Margin of the Scrollbar

Starting from API version 20, this example shows how to use the [scrollBarMargin](./ts-container-scrollable-common.md#scrollbarmargin20) attribute to set the scrollbar margin and avoid the [contentStartOffset](#contentstartoffset11) and [contentEndOffset](#contentendoffset11) areas.



```TypeScript
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct ListScrollBarMarginExample {
  @State arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];

  build() {
    Column() {
      List({ space: 40, initialIndex: 0 }) {
        ForEach(this.arr, (item: number, index: number) => {
          ListItem() {
            Text('' + item)
              .width('100%')
              .height(100)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .borderRadius(10)
              .backgroundColor(0xFFFFFF)
          }
        }, (item: number, index: number) => item.toString() + index.toString())
      }
      .contentStartOffset(20)
      .contentEndOffset(20)
      .scrollBar(BarState.On)
      .scrollBarMargin({ start: LengthMetrics.vp(20), end: LengthMetrics.vp(20) })
      .width('90%')
    }
    .width('100%')
    .height('100%')
    .backgroundColor(0xDCDCDC)
    .padding({ top: 5 })
  }
}
```

### Example 12: Implementing Dragging with OnMove

Starting from API version 12, this example demonstrates how to use the [onMove](./ts-universal-attributes-drag-sorting.md#onmove) API of ForEach to sort items by dragging them. The list can automatically scroll when an item is dragged to the edge of the list.



```TypeScript
@Entry
@Component
struct ForEachSort {
  @State arr: Array<string> = [];

  build() {
    Row() {
      List() {
        ForEach(this.arr, (item: string) => {
          ListItem() {
            Text(item.toString())
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .size({ height: 100, width: '100%' })
          }.margin(10)
          .borderRadius(10)
          .backgroundColor('#FFFFFFFF')
        }, (item: string) => item)
          .onMove((from: number, to: number) => {
            let tmp = this.arr.splice(from, 1);
            this.arr.splice(to, 0, tmp[0]);
          })
      }
      .width('100%')
      .height('100%')
      .backgroundColor('#FFDCDCDC')
    }
  }

  aboutToAppear(): void {
    for (let i = 0; i < 100; i++) {
      this.arr.push(i.toString());
    }
  }
}
```

### Example 13: Configuring Lanes Based on Breakpoints

In API version 22 and later versions, this example shows how to configure lanes in the List component based on breakpoints.

For details about ListDataSource and the complete code, see [Example 1: Adding a Scroll Event](#example-1-adding-a-scroll-event).

When the list width is within the breakpoint range of sm or smaller, two columns are displayed.



When the list width is within the breakpoint range of md, three columns are displayed.



When the list width is within the breakpoint range of lg or larger, five columns are displayed.



```TypeScript
// xxx.ets
import { ListDataSource } from './ListDataSource';

@Entry
@Component
struct ListExample {
  private arr: ListDataSource = new ListDataSource([0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11]);
  scrollerForList: Scroller = new Scroller();

  build() {
    Column() {
      List({ space: 20, initialIndex: 0, scroller: this.scrollerForList }) {
        LazyForEach(this.arr, (item: number) => {
          ListItem() {
            Text('' + item)
              .width('100%').height(100).fontSize(16)
              .textAlign(TextAlign.Center).borderRadius(10).backgroundColor(0xFFFFFF)
          }
        }, (item: number) => item.toString())
      }
      .lanes({ fillType: PresetFillType.BREAKPOINT_SM2MD3LG5}, 10)
      .width('90%').height(600)
    }
    .width('100%')
    .height('100%')
    .backgroundColor(0xDCDCDC)
    .padding({ top: 5 })
  }
}
```

### Example 14: Obtaining the Total Content Size

This example demonstrates how to obtain the total content size of the List component. This functionality is supported since API version 22.



```TypeScript
// xxx.ets
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct ListExample {
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11]
  scrollerForList: Scroller = new Scroller()
  @State contentWidth: number = -1;
  @State contentHeight: number = -1;

  build() {
    Column() {
      List({ space: 20, initialIndex: 0, scroller: this.scrollerForList }) {
        ForEach(this.arr, (item: number) => {
          ListItem() {
            Text('' + item)
              .width('100%')
              .height(100)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .borderRadius(10)
              .backgroundColor(0xFFFFFF)
          }
        }, (item: number) => item.toString())
      }
      .width('90%').height('90%')

      // Button to obtain the content size.
      Button('GetContentSize')
        .onClick(() => {
          // Scroller throws an exception when not bound to a component; wrap with try-catch for safety.
          try {
            // Obtain the content width using contentSize.
            this.contentWidth = this.scrollerForList.contentSize().width;
            // Obtain the content height using contentSize.
            this.contentHeight = this.scrollerForList.contentSize().height;
          } catch (error) {
            let err: BusinessError = error as BusinessError;
            console.error(`Failed to get contentSize of the List. Code: ${err.code}, message: ${err.message}`);
          }
        })
      // Display the obtained content size.
      Text('Width: ' + this.contentWidth + ', Height: ' + this.contentHeight)
        .fontColor(Color.Red)
        .height(50)
    }
    .width('100%')
    .height('100%')
    .backgroundColor(0xDCDCDC)
    .padding({ top: 5 })
  }
}
```

### Example 15: Dragging Between Two Lists

This example implements the dragging effect of ListItem between two List components through events such as onItemDragStart.



```TypeScript
// xxx.ets
@ObservedV2
class ListData {
  @Trace public title: string = '';
  @Trace public data: string[] = [];

  constructor(title: string, data: string[]) {
    this.title = title;
    this.data = data;
  }
}

class DraggingData {
  public data?: string;
}

@ComponentV2
struct DraggableList {
  @Require @Param data: string[];
  @Require @Param draggingData: DraggingData;

  @Builder
  ItemBuilder(data: string, size: SizeOptions, event: ItemDragInfo): void {
    Stack() {
      Text(data)
    }
    .backgroundColor(Color.White)
    .borderRadius(4)
    .size(size)
  }

  viewWidth: number = 0;
  lastInsertIndex: number = 0;
  scroller: Scroller = new Scroller();

  build() {
    List({ scroller: this.scroller }) {
      ForEach(this.data, (item: string) => {
        ListItem() {
          Text(item)
        }
        .width('100%')
        .height('10%')
        .margin(10)
        .backgroundColor(Color.White)
        .borderRadius(4)
        .aspectRatio(1)
      }, (item: string) => item)
    }
    .width('50%')
    .layoutWeight(1)
    .padding(10)
    .onItemDragStart((event: ItemDragInfo, itemIndex: number) => {
      let rect = this.scroller.getItemRect(itemIndex);
      let size: SizeOptions = {
        width: rect.width,
        height: rect.height
      };
      this.lastInsertIndex = itemIndex;
      this.draggingData.data = this.data[itemIndex];
      this.data.splice(itemIndex, 1);

      return this.ItemBuilder(this.draggingData.data, size, event);
    })
    .onItemDragEnter((event: ItemDragInfo) => {
      console.info('Item drag enter at position:', event.x, event.y);
    })
    .onItemDragMove((event: ItemDragInfo, itemIndex: number, insertIndex: number) => {
      if (this.lastInsertIndex != insertIndex){
        console.info('insertIndex change from ', this.lastInsertIndex, 'to', insertIndex);
        this.lastInsertIndex = insertIndex;
      }
    })
    .onItemDragLeave((event: ItemDragInfo, itemIndex: number) => {
      console.info('Item ' + itemIndex + ' drag leave at position:', event.x, event.y);
    })
    .onItemDrop((event: ItemDragInfo, itemIndex: number, insertIndex: number, isSuccess: boolean) => {
      if (!isSuccess) {
        this.draggingData.data = undefined;
        return;
      }
      if (insertIndex >= 0) {
        this.data.splice(insertIndex, 0, this.draggingData.data!);
      }
      this.draggingData.data = undefined;
    })
    .onSizeChange((oldValue: SizeOptions, newValue: SizeOptions) => {
      this.viewWidth = newValue.width as number;
    })
  }
}

@Entry
@ComponentV2
struct Index {
  @Local data: ListData[] = [
    new ListData('A', ['A1', 'A2', 'A3', 'A4', 'A5', 'A6', 'A7', 'A8']),
    new ListData('B', ['B1', 'B2', 'B3', 'B4', 'B5', 'B6', 'B7', 'B8']),
  ]
  @Local draggingData: DraggingData = new DraggingData();

  build() {
    Stack() {
      Row() {
        DraggableList({ data: this.data[0].data, draggingData: this.draggingData })
        DraggableList({ data: this.data[1].data, draggingData: this.draggingData })
      }
    }
    .backgroundColor('#FFDCDCDC')
  }
}
```

### Example 16: Centering the Clicked Item in ListItemGroup

This example uses the [scrollToItemInGroup](arkts-arkui-list-comp-listscroller-c.md#scrolltoitemingroup) API to implement the effect of centering the [ListItem](./ts-container-listitem.md) component in the [ListItemGroup](./ts-container-listitemgroup.md) when the ListItem is clicked.



```TypeScript
import { util } from '@kit.ArkTS';

class Contact {
  key: string = util.generateRandomUUID(true);
  name: string;
  icon: Resource;

  constructor(name: string, icon: Resource) {
    this.name = name;
    this.icon = icon;
  }
}

class ContactsGroup {
  title: string = '';
  contacts: Array<object> | null = null;
  key: string = '';
}

@Entry
@Component
struct ContactsList {
  private scroller: ListScroller = new ListScroller();
  private contactsGroups: ContactsGroup[] = [
    {
      title: 'A',
      contacts: [
        new Contact('Alice', $r('app.media.icon')),  // Replace $r('app.media.icon') with the image resource file you use.
        new Contact('Ann', $r('app.media.icon')),
        new Contact('Angela', $r('app.media.icon'))
        // ...
      ],
      key: util.generateRandomUUID(true)
    } as ContactsGroup,
    {
      title: 'B',
      contacts: [
        new Contact('Ben', $r('app.media.icon')),
        new Contact('Bryan', $r('app.media.icon'))
        // ...
      ],
      key: util.generateRandomUUID(true)
    } as ContactsGroup,
    // ...
  ]

  @Builder
  itemHead(text: string) {
    Text(text)
      .fontSize(20)
      .backgroundColor('#fff1f3f5')
      .width('100%')
      .padding(5)
  }

  build() {
    List({ scroller: this.scroller }) {
      ForEach(this.contactsGroups, (item: ContactsGroup, index: number) => {
        ListItemGroup({ header: this.itemHead(item.title) }) {
          ForEach(item.contacts, (contact: Contact, subIndex: number) => {
            ListItem() {
              Row() {
                Image(contact.icon)
                  .width(40)
                  .height(40)
                  .margin(10)
                Text(contact.name).fontSize(20)
              }
              .width('100%')
              .justifyContent(FlexAlign.Start)
              .margin(10)
            }
            .gesture(
              TapGesture({ count: 1 })
                .onAction((event: GestureEvent) => {
                  if (event) {
                    const itemRect = this.scroller.getItemRectInGroup(index, subIndex);
                    console.info('The', index + 1, 'ListItemGroup of the', subIndex + 1, 'ListItem', x:', itemRect.x,
                      ' y:', itemRect.y, ' width:', itemRect.width, ' height:', itemRect.height)
                    this.scroller.scrollToItemInGroup(index, subIndex, true, ScrollAlign.CENTER);
                  }
                })
            )
          }, (contact: Contact) => JSON.stringify(contact))
        }
        .divider({ strokeWidth: 4 })
        .width('100%')
      }, (item: ContactsGroup) => JSON.stringify(item))
    }
    .onScrollFrameBegin((offset: number, state: ScrollState) => {
      console.info('List scrollFrameBegin offset: ' + offset + ' state: ' + state.toString());
      return { offsetRemain: offset };
    })
  }
}
```

### Example 17: Setting the Multi-Selection Gather Animation

This example demonstrates how to gather selected list items in the visible area when a long press is performed on list items using [bindContextMenu](ts-universal-attributes-menu.md#bindcontextmenu8), with the multi-selection gather animation switch enabled for List.

Since API version 23, the [editModeOptions](#editmodeoptions23) API is added to the List component  to set the multi-selection gather animation switch.

For details about ListDataSource and the complete code, see [Example 1: Adding a Scroll Event](#example-1-adding-a-scroll-event).



```TypeScript
// xxx.ets
import { ListDataSource } from './ListDataSource';

@Entry
@Component
struct ListExample {
  private arr: ListDataSource = new ListDataSource([0, 1, 2, 3, 4, 5, 6, 7, 8, 9]);
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
    for (i = 0; i < 10; i++) {
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
      List({ space: 10 }) {
        LazyForEach(this.arr, (item: number) => {
            ListItem() {
              Text(item.toString())
                .fontSize(16)
                .backgroundColor(Color.White)
                .width('100%')
                .height(50)
                .textAlign(TextAlign.Center)
            }
            .selected(this.isSelected[item])
            // Set the multi-selection display effects.
            .stateStyles({
              normal: this.normalStyles,
              selected: this.selectStyles
            })
            .bindContextMenu(this.MenuBuilder, ResponseType.LongPress,
              { preview: MenuPreviewMode.IMAGE, hapticFeedbackMode: HapticFeedbackMode.ENABLED })
            .onClick(() => {
              this.isSelected[item] = !this.isSelected[item];
              console.info(`item:${item}, this.isSelected[item]:${this.isSelected[item]}`)
              if (this.isSelected[item]) {
                ++this.selectedCount;
              } else {
                --this.selectedCount;
              }
            })
        }, (item: number) => item.toString())
      }
      .editModeOptions({
        enableGatherSelectedItemsAnimation: true, onGetPreviewBadge: () => {
          return this.selectedCount;
        }
      })
      .width('90%')
      .height(300)
      .scrollBar(BarState.Off)
    }.width('100%').margin({ top: 5 }).backgroundColor('#FFDCDCDC')
  }
}
```
