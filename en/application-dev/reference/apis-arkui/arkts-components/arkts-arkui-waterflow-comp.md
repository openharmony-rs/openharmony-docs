# WaterFlow

The **WaterFlow** component is a water flow container that consists of cells formed by rows and columns and arranges items of different sizes from top to bottom according to the preset rules.

> **NOTE**

> The **WaterFlow** component supports the waterfall layout but does not support the edit mode or dragging of child > elements. > > The component has been bound with gestures to implement functions such as following the finger. If you need to add > custom gestures, refer to Enhanced Gesture Interception.

## Child Components

Only the FlowItem child component and custom components are supported. When a custom component is used in **WaterFlow**, you are advised to use **FlowItem** as the top-level component of the custom component. You are not advised to set attributes and event methods for the custom component.

Child components can be dynamically generated using rendering control types [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md), [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), and [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md). **LazyForEach** or **Repeat** is recommended to optimize performance.

> **NOTE:** 
> 
> When the **visibility** attribute of a child component of **WaterFlow** is set to **None**, this child component is
> not displayed in the container, but its **columnsGap**, **rowsGap**, and **margin** settings are still effective.
> 
> If there are a large number of child components, you are advised to adopt methods such as lazy loading, data
> caching, component reuse, fixed dimensions, and layout optimization to improve performance and reduce memory usage.
> For best practices, see
> [Optimizing Frame Loss for Waterfall Loading](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-waterflow-performance-optimization).
> 
> In vertical layout mode, **WaterFlow** calculates the cumulative height of child components in each column and
> places new child components in the column with the smallest cumulative height to maintain a compact overall layout.
> 
> If the heights of multiple columns are the same, the leftmost column is prioritized. In RTL mode, the rightmost
> column is prioritized.
> 
> Starting from API version 21, the maximum width or height for a single child component inside a **WaterFlow**
> container is 16,777,216 px. In API version 20 and earlier versions, the limit was 1,000,000 px. If a child
> component exceeds the applicable size limit, scrolling or display behavior may become abnormal.

## WaterFlow

```TypeScript
WaterFlow(options?: WaterFlowOptions)
```

Creates a **WaterFlow** component.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [WaterFlowOptions](arkts-arkui-waterflow-comp-waterflowoptions-i.md) | No | Parameters of the **WaterFlow** component. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [UIWaterFlowEvent](arkts-arkui-waterflow-comp-uiwaterflowevent-i.md) | Represents the return value of the [getEvent('WaterFlow')](../arkts-apis/arkts-arkui-typenode-getevent-f.md#getevent-2) method in **frameNode**, which can be used to set scroll events for a **WaterFlow** node. |
| [WaterFlowOptions](arkts-arkui-waterflow-comp-waterflowoptions-i.md) | Provides parameters of the **WaterFlow** component. |

### Types

| Name | Description |
| --- | --- |
| [GetItemMainSizeByIndex](arkts-arkui-waterflow-comp-getitemmainsizebyindex-t.md) | Obtains the main axis size of a specified water flow item based on its index. |
| [OnWaterFlowScrollIndexCallback](arkts-arkui-waterflow-comp-onwaterflowscrollindexcallback-t.md) | Represents a callback for item changes in the visible area of the **WaterFlow** component. |

### Enums

| Name | Description |
| --- | --- |
| [WaterFlowLayoutMode](arkts-arkui-waterflow-comp-waterflowlayoutmode-e.md) | Enumerates the layout modes of the **WaterFlow** component. |

## Examples

### Example 1: Using a Basic WaterFlow Component

This example demonstrates the basic usage of the WaterFlow component, including data loading, attribute setting, and event callbacks.

WaterFlowDataSource implements the [IDataSource](ts-rendering-control-lazyforeach.md#idatasource) data source interface of [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), and is used to provide child components to WaterFlow through LazyForEach.

When a field that affects the width and height of FlowItem in the [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md) data changes, you need to notify [DataChangeListener](ts-rendering-control-lazyforeach.md#datachangelistener) after modifying the data, for example, by calling [onDataChange](ts-rendering-control-lazyforeach.md#ondatachange8) or [onDataReloaded](ts-rendering-control-lazyforeach.md#ondatareloaded). If only the data content is modified without triggering a data change notification, LazyForEach may not refresh the corresponding FlowItem.

```TypeScript
// WaterFlowDataSource.ets

// An object that implements the IDataSource interface, which is used by the WaterFlow component to load data.
export class WaterFlowDataSource implements IDataSource {
  private dataArray: number[] = [];
  private listeners: DataChangeListener[] = [];

  constructor() {
    for (let i = 0; i < 100; i++) {
      this.dataArray.push(i);
    }
  }

  // Obtain the data corresponding to the specified index.
  public getData(index: number): number {
    return this.dataArray[index];
  }

  // Notify the controller of data reloading.
  notifyDataReload(): void {
    this.listeners.forEach(listener => {
      listener.onDataReloaded();
    });
  }

  // Notify the controller of data addition.
  notifyDataAdd(index: number): void {
    this.listeners.forEach(listener => {
      listener.onDataAdd(index);
    });
  }

  // Notify the controller of data changes.
  notifyDataChange(index: number): void {
    this.listeners.forEach(listener => {
      listener.onDataChange(index);
    });
  }

  // Notify the controller of data deletion.
  notifyDataDelete(index: number): void {
    this.listeners.forEach(listener => {
      listener.onDataDelete(index);
    });
  }

  // Notify the controller of the data location change.
  notifyDataMove(from: number, to: number): void {
    this.listeners.forEach(listener => {
      listener.onDataMove(from, to);
    });
  }

  // Notify the controller of batch data modification.
  notifyDatasetChange(operations: DataOperation[]): void {
    this.listeners.forEach(listener => {
      listener.onDatasetChange(operations);
    });
  }

  // Obtain the total number of data records.
  public totalCount(): number {
    return this.dataArray.length;
  }

  // Register the data change listener.
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

  // Add data.
  public add1stItem(): void {
    this.dataArray.splice(0, 0, this.dataArray.length);
    this.notifyDataAdd(0);
  }

  // Add an item to the end of the data.
  public addLastItem(): void {
    this.dataArray.splice(this.dataArray.length, 0, this.dataArray.length);
    this.notifyDataAdd(this.dataArray.length - 1);
  }

  // Add an item to the position corresponding to the specified index.
  public addItem(index: number): void {
    this.dataArray.splice(index, 0, this.dataArray.length);
    this.notifyDataAdd(index);
  }

  // Delete the first item.
  public delete1stItem(): void {
    this.dataArray.splice(0, 1);
    this.notifyDataDelete(0);
  }

  // Delete the second item.
  public delete2ndItem(): void {
    this.dataArray.splice(1, 1);
    this.notifyDataDelete(1);
  }

  // Delete the last item.
  public deleteLastItem(): void {
    this.dataArray.splice(-1, 1);
    this.notifyDataDelete(this.dataArray.length);
  }

  // Delete an item at the specified index position.
  public deleteItem(index: number): void {
    this.dataArray.splice(index, 1);
    this.notifyDataDelete(index);
  }

  // Reload data.
  public reload(): void {
    this.dataArray.splice(1, 1);
    this.dataArray.splice(3, 2);
    this.notifyDataReload();
  }

  // Add items according to the value of count to the end of the data.
  public addNewItems(count: number): void {
    let len = this.dataArray.length;
    for (let i = 0; i < count; i++) {
      this.dataArray.push(this.dataArray[len - 1] + i + 1);
      this.notifyDataAdd(this.dataArray.length - 1);
    }
  }

  //Refresh all elements.
  public refreshItems(): void {
    let newDataArray: number[] = [];
    for (let i = 0; i < 100; i++) {
      newDataArray.push(this.dataArray[0] + i + 1000);
    }
    this.dataArray = newDataArray;
    this.notifyDataReload();
  }
}
```



```TypeScript
// Index.ets
import { WaterFlowDataSource } from './WaterFlowDataSource';

enum FooterState {
  LOADING = 0,
  END = 1
}

@Entry
@Component
struct WaterFlowDemo {
  @State minSize: number = 80;
  @State maxSize: number = 180;
  @State colors: number[] = [0xFFC0CB, 0xDA70D6, 0x6B8E23, 0x6A5ACD, 0x00FFFF, 0x00FF7F];
  @State footerState: FooterState = FooterState.LOADING;
  dataSource: WaterFlowDataSource = new WaterFlowDataSource();
  private itemHeightArray: number[] = [];

  // Calculate the width and height of a flow item.
  getSize() {
    let ret = Math.floor(Math.random() * this.maxSize);
    return (ret > this.minSize ? ret : this.minSize);
  }

  // Set the width and height array of the water flow item.
  setItemSizeArray() {
    for (let i = 0; i < 100; i++) {
      this.itemHeightArray.push(this.getSize());
    }
  }

  // Component lifecycle: Initialize the size array when the component is about to appear.
  aboutToAppear() {
    this.setItemSizeArray();
  }

  @Builder
  itemFoot() {
    // Note: Do not use the IfElse node as the root node of the footer.
    // The IfElse node must be wrapped by a container (such as Column, Row, or Stack) to ensure correct layout.
    Column() {
      if (this.footerState == FooterState.LOADING) {
        Text('Loading...')
          .fontSize(10)
          .backgroundColor(Color.Red)
          .width(50)
          .height(50)
          .align(Alignment.Center)
          .margin({ top: 2 })
      } else if (this.footerState == FooterState.END) {
        Text('End')
          .fontSize(10)
          .backgroundColor(Color.Red)
          .width(50)
          .height(50)
          .align(Alignment.Center)
          .margin({ top: 2 })
      } else {
        Text(`Footer`)
          .fontSize(10)
          .backgroundColor(Color.Red)
          .width(50)
          .height(50)
          .align(Alignment.Center)
          .margin({ top: 2 })
      }
    }
  }

  build() {
    Column({ space: 2 }) {
      WaterFlow({ footer: this.itemFoot() }) {
        LazyForEach(this.dataSource, (item: number) => {
          FlowItem() {
            Column() {
              Text('N' + item).fontSize(12).height('16')
              // Note: Ensure that the corresponding JPG file exists.
              Image('res/waterFlowTest(' + item % 5 + ').jpg')
                .objectFit(ImageFit.Fill)
                .width('100%')
                .layoutWeight(1)
            }
          }
          .width('100%')
          .height(this.itemHeightArray[item % 100])
          .backgroundColor(this.colors[item % this.colors.length])
        }, (item: number) => item.toString())
      }
      .columnsTemplate('1fr 1fr')    // Set the layout of two columns with equal width.
      .columnsGap(10)
      .rowsGap(5)
      .backgroundColor(0xFAEEE0)
      .width('100%')
      .height('100%')
      .itemConstraintSize({minWidth:80,maxWidth:180,minHeight:80,maxHeight:180})
      // Load data when the scroll reaches the bottom.
      .onReachEnd(() => {
        console.info('onReachEnd');

        // Simulate pagination loading. The loading stops when the number of data records exceeds 200.
        if (this.dataSource.totalCount() > 200) {
          this.footerState = FooterState.END;
          return;
        }
        setTimeout(() => {
          for (let i = 0; i < 100; i++) {
            this.dataSource.addLastItem();
          }
        }, 1000);
      })
      .onReachStart(() => {
        // Triggered when the scroll reaches the top.
        console.info('waterFlow reach start');
      })
      .onScrollStart(() => {
        // Triggered when the scroll starts.
        console.info('waterFlow scroll start');
      })
      .onScrollStop(() => {
        // Triggered when the scroll stops.
        console.info('waterFlow scroll stop');
      })
      .onScrollFrameBegin((offset: number, state: ScrollState) => {
        // Triggered when the scroll frame starts. You can control the scroll behavior.
        // offset: scroll offset; state: scroll state
        console.info('waterFlow scrollFrameBegin offset: ' + offset + ' state: ' + state.toString());
        return { offsetRemain: offset }; // Return the actual scroll offset you expect.
      })
    }
  }
}
```

### Example 2: Implementing Automatic Column Count Calculation

This example showcases how to implement automatic column count calculation using the auto-fill feature.

For details about WaterFlowDataSource and the complete code, see [Example 1: Using a Basic WaterFlow Component](#example-1-using-a-basic-waterflow-component).



```TypeScript
// Index.ets
import { WaterFlowDataSource } from './WaterFlowDataSource';

@Entry
@Component
struct WaterFlowDemo {
  @State minSize: number = 80;
  @State maxSize: number = 180;
  @State colors: number[] = [0xFFC0CB, 0xDA70D6, 0x6B8E23, 0x6A5ACD, 0x00FFFF, 0x00FF7F];
  dataSource: WaterFlowDataSource = new WaterFlowDataSource();
  private itemWidthArray: number[] = [];
  private itemHeightArray: number[] = [];

  // Calculate the width and height of a flow item.
  getSize() {
    let ret = Math.floor(Math.random() * this.maxSize);
    return (ret > this.minSize ? ret : this.minSize);
  }

  // Set the width and height array of the flow item.
  setItemSizeArray() {
    for (let i = 0; i < 100; i++) {
      this.itemWidthArray.push(this.getSize());
      this.itemHeightArray.push(this.getSize());
    }
  }

  // Component lifecycle: Initialize the size array when the component is about to appear.
  aboutToAppear() {
    this.setItemSizeArray();
  }

  build() {
    Column({ space: 2 }) {
      WaterFlow() {
        LazyForEach(this.dataSource, (item: number) => {
          FlowItem() {
            Column() {
              Text('N' + item).fontSize(12).height('16')
              // The image is displayed only when the corresponding JPG file exists.
              Image('res/waterFlowTest(' + item % 5 + ').jpg')
            }
          }
          .width('100%')
          .height(this.itemHeightArray[item % 100])
          .backgroundColor(this.colors[item % this.colors.length])
        }, (item: number) => item.toString())
      }
      // auto-fill: automatically calculates the number of columns.
      // repeat (auto-fill, 80) indicates that the number of columns that can be placed is automatically calculated based on the container width.
      // For example, if the container width is 400 px, the number of columns is automatically calculated as 5 (400/80 = 5).
      .columnsTemplate('repeat(auto-fill,80)')
      .columnsGap(10)
      .rowsGap(5)
      .padding({left:5})
      .backgroundColor(0xFAEEE0)
      .width('100%')
      .height('100%')
    }
  }
}
```

### Example 3: Using WaterFlowSections

This example demonstrates the initialization of groups and the different effects of the splice, update, values, and length APIs.

For usage with state management V2, see [WaterFlow and makeObserved](../../../ui/state-management/arkts-v1-v2-migration-inner-object.md#scrollable-component).

For details about WaterFlowDataSource and the complete code, see [Example 1: Using a Basic WaterFlow Component](#example-1-using-a-basic-waterflow-component).



```TypeScript
// Index.ets
import { WaterFlowDataSource } from './WaterFlowDataSource';

// Reusable component: optimizes performance and reduces the overhead of creating and destroying components.
@Reusable
@Component
struct ReusableFlowItem {
  @State item: number = 0;

  // Component reuse lifecycle: called when data is obtained from the reuse cache.
  // Update the component status and display new content.
  aboutToReuse(params: Record<string, number>) {
    this.item = params.item;
    console.info('Reuse item:' + this.item);
  }

  // Record the component creation log.
  aboutToAppear() {
    console.info('new item:' + this.item);
  }

  build() {
    Column() {
      // Note: Ensure that the corresponding JPG file exists.
      Image('res/waterFlowTest(' + this.item % 5 + ').jpg')
        .overlay('N' + this.item, { align: Alignment.Top })
        .objectFit(ImageFit.Fill)
        .width('100%')
        .layoutWeight(1)
    }
  }
}

@Entry
@Component
struct WaterFlowDemo {
  minSize: number = 80;
  maxSize: number = 180;
  colors: number[] = [0xFFC0CB, 0xDA70D6, 0x6B8E23, 0x6A5ACD, 0x00FFFF, 0x00FF7F];
  scroller: Scroller = new Scroller();
  dataSource: WaterFlowDataSource = new WaterFlowDataSource();
  dataCount: number = this.dataSource.totalCount();
  private itemWidthArray: number[] = [];
  private itemHeightArray: number[] = [];
  // Section management: core feature of WaterFlow. Different numbers of columns can be used in different areas.
  @State sections: WaterFlowSections = new WaterFlowSections();
  // Section margin configuration: unified outer margin setting.
  sectionMargin: Margin = { top: 10, left: 5, bottom: 10, right: 5 };

  oneColumnSection: SectionOptions = {
    itemsCount: 4,                     // The section contains four FlowItem components.
    crossCount: 1,                     // Use the one-column layout.
    columnsGap: 5,
    rowsGap: 10,
    margin: this.sectionMargin,
    // Callback: dynamically set the height of each item.
    onGetItemMainSizeByIndex: (index: number) => {
      return this.itemHeightArray[index % 100];
    }
  };

  // Second type of section: two-column layout, which is suitable for displaying list content.
  twoColumnSection: SectionOptions = {
    itemsCount: 2,                     // The section contains two FlowItem components.
    crossCount: 2,                     // Use the two-column layout.
    // Callback: fixed height of 100px
    onGetItemMainSizeByIndex: (index: number) => {
      return 100;
    }
  };

  // Last section: used to process remaining data.
  lastSection: SectionOptions = {
    itemsCount: 20,                    // The section contains 20 FlowItem components.
    crossCount: 2,                     // Use the two-column layout.
    // Callback: random height.
    onGetItemMainSizeByIndex: (index: number) => {
      return this.itemHeightArray[index % 100];
    }
  };

  // Calculate the height for FlowItem.
  getSize() {
    let ret = Math.floor(Math.random() * this.maxSize);
    return (ret > this.minSize ? ret : this.minSize);
  }

  // Set the height array for FlowItem.
  setItemSizeArray() {
    for (let i = 0; i < 100; i++) {
      this.itemHeightArray.push(this.getSize());
    }
  }

  // Initialize the data and WaterFlow group configuration.
  aboutToAppear() {
    this.setItemSizeArray();

    // Initialize the section information: Use the single-column and dual-column layouts alternately.
    let sectionOptions: SectionOptions[] = [];
    let count = 0;                     // Number of allocated FlowItem components.
    let oneOrTwo = 0;                  // Select the section type alternately.

    while (count < this.dataCount) {
      // If there are less than 20 remaining items, use the last section for processing.
      if (this.dataCount - count < 20) {
        this.lastSection.itemsCount = this.dataCount - count;
        sectionOptions.push(this.lastSection);
        break;
      }

      // Use the single-column and dual-column layouts alternately.
      if (oneOrTwo++ % 2 == 0) {
        sectionOptions.push(this.oneColumnSection);
        count += this.oneColumnSection.itemsCount;
      } else {
        sectionOptions.push(this.twoColumnSection);
        count += this.twoColumnSection.itemsCount;
      }
    }

    // Add the configured section to WaterFlow.
    this.sections.splice(0, 0, sectionOptions);
  }

  build() {
    Column({ space: 2 }) {
      Row() {
        Button('splice')
          .height('5%')
          .onClick(() => {
            // Important: The total number of data items in LazyForEach must be consistent with the cumulative sum of itemsCount in the new section.
            let totalCount: number = this.dataSource.totalCount();
            let newSection: SectionOptions = {
              itemsCount: totalCount,
              crossCount: 2,
              onGetItemMainSizeByIndex: (index: number) => {
                return this.itemHeightArray[index % 100];
              }
            };
            let oldLength: number = this.sections.length();
            this.sections.splice(0, oldLength, [newSection]); // Replace all sections.
          })
          .margin({ top: 10, left: 20 })

        Button('update')
          .height('5%')
          .onClick(() => {
            // Add four FlowItem components to the first section.
            // Important: Ensure that the data source and itemsCount are updated synchronously.
            const sections: Array<SectionOptions> = this.sections.values();
            let newSection: SectionOptions = sections[0];

            // Add four new items to the data source.
            this.dataSource.addItem(this.oneColumnSection.itemsCount);
            this.dataSource.addItem(this.oneColumnSection.itemsCount + 1);
            this.dataSource.addItem(this.oneColumnSection.itemsCount + 2);
            this.dataSource.addItem(this.oneColumnSection.itemsCount + 3);

            // Update itemsCount of the section.
            newSection.itemsCount += 4;
            const result: boolean = this.sections.update(0, newSection);
            console.info('update:' + result);
          })
          .margin({ top: 10, left: 20 })
      }.margin({ bottom: 20 })

      Row() {
        Button('delete')
          .height('5%')
          .onClick(() => {
            // Delete four FlowItem components from the first section.
            // Important: Ensure that the data source and itemsCount are updated synchronously.
            const sections: Array<SectionOptions> = this.sections.values();
            let newSection: SectionOptions = sections[0];

            // Check whether there are sufficient items to be deleted.
            if (newSection.itemsCount < 4) {
              return;
            }

            //Delete four items from the data source.
            this.dataSource.deleteItem(this.oneColumnSection.itemsCount - 1);
            this.dataSource.deleteItem(this.oneColumnSection.itemsCount - 2);
            this.dataSource.deleteItem(this.oneColumnSection.itemsCount - 3);
            this.dataSource.deleteItem(this.oneColumnSection.itemsCount - 4);

            // Update itemsCount of the section.
            newSection.itemsCount -= 4;
            this.sections.update(0, newSection);
          })
          .margin({ top: 10, left: 20 })

        Button('values')
          .height('5%')
          .onClick(() => {
            const sections: Array<SectionOptions> = this.sections.values();
            for (const value of sections) {
              console.info(JSON.stringify(value));
            }
            console.info('count:' + this.sections.length());
          })
          .margin({ top: 10, left: 20 })
      }

      WaterFlow({ scroller: this.scroller, sections: this.sections }) {
        LazyForEach(this.dataSource, (item: number) => {
          FlowItem() {
            // Use reusable components to improve performance.
            ReusableFlowItem({ item: item })
          }
          .width('100%')
          // Note: If both onGetItemMainSizeByIndex and height are set,
          // the main-axis size is subject to the return result of onGetItemMainSizeByIndex.
          .height(this.itemHeightArray[item % 100])
          .backgroundColor(this.colors[item % this.colors.length])
        }, (item: number) => item.toString())
      }
      .columnsTemplate('1fr 1fr')
      .columnsGap(10)
      .rowsGap(5)
      .backgroundColor(0xFAEEE0)
      .width('100%')
      .height('100%')
      .layoutWeight(1)
      .onScrollIndex((first: number, last: number) => {
        // Scroll listener: Load more data when the scroll is about to reach the bottom.
        if (last + 20 >= this.dataSource.totalCount()) {
          // Add 100 new items to the data source.
          for (let i = 0; i < 100; i++) {
            this.dataSource.addLastItem();
          }

          // Important: After the data source is updated, sections must be updated synchronously.
          // Change the number of flow items in the last section.
          const sections: Array<SectionOptions> = this.sections.values();
          let newSection: SectionOptions = sections[this.sections.length() - 1];
          newSection.itemsCount += 100;
          this.sections.update(-1, newSection); // -1 indicates the last section.
        }
      })
    }
  }
}
```

### Example 4: Using the Pinch Gesture to Change the Column Count

This example demonstrates how to use [priorityGesture](ts-gesture-settings.md#prioritygesture) and [PinchGesture](ts-basic-gestures-pinchgesture.md) to implement the feature of using a pinch gesture to change the number of columns in a layout.

For details about WaterFlowDataSource and the complete code, see [Example 1: Using a Basic WaterFlow Component](#example-1-using-a-basic-waterflow-component).



```TypeScript
// Index.ets
import { WaterFlowDataSource } from './WaterFlowDataSource';
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Reusable component: optimizes performance and reduces the overhead of creating and destroying components.
@Reusable
@Component
struct ReusableFlowItem {
  @State item: number = 0;

  // Invoked when a reusable custom component is added to the component tree from the reuse cache. The component's state variable can be updated here to display the correct content.
  aboutToReuse(params: Record<string, number>) {
    this.item = params.item;
  }

  build() {
    Column() {
      Text('N' + this.item).fontSize(12).height('16')
      // Note: Ensure that the corresponding JPG file exists.
      Image('res/waterFlow(' + this.item % 5 + ').jpg')
        .objectFit(ImageFit.Fill)
        .width('100%')
        .layoutWeight(1)
    }
  }
}

@Entry
@Component
struct WaterFlowDemo {
  minSize: number = 80;
  maxSize: number = 180;
  colors: number[] = [0xFFC0CB, 0xDA70D6, 0x6B8E23, 0x6A5ACD, 0x00FFFF, 0x00FF7F];
  dataSource: WaterFlowDataSource = new WaterFlowDataSource();
  private itemWidthArray: number[] = [];
  private itemHeightArray: number[] = [];
  @State columns: number = 2;
  @State waterFlowScale: number = 1;
  @State imageScale: number = 1;
  @State waterFlowOpacity: number = 1;
  @State waterFlowSnapshot: image.PixelMap | undefined = undefined;
  private columnChanged: boolean = false;
  private oldColumn: number = this.columns;
  private pinchTime: number = 0;

  // Calculate the width and height of a flow item.
  getSize() {
    let ret = Math.floor(Math.random() * this.maxSize);
    return (ret > this.minSize ? ret : this.minSize);
  }

  // Set the width and height array of the water flow item.
  setItemSizeArray() {
    for (let i = 0; i < 100; i++) {
      this.itemWidthArray.push(this.getSize());
      this.itemHeightArray.push(this.getSize());
    }
  }

  // Component lifecycle: Initialize data and restore the previous column settings.
  aboutToAppear() {
    // Read the last column count.
    let lastCount = AppStorage.get<number>('columnsCount');
    if (typeof lastCount != 'undefined') {
      this.columns = lastCount;
    }
    this.setItemSizeArray();
  }

  // Change the number of columns based on the scale threshold and trigger re-layout for the WaterFlow component.
  changeColumns(scale: number) {
    if (scale > (this.columns / (this.columns - 0.5)) && this.columns > 1) {
      this.columns--;
      this.columnChanged = true;
    } else if (scale < 1 && this.columns < 4) {
      this.columns++;
      this.columnChanged = true;
    }
  }

  build() {
    Column({ space: 2 }) {
      Row() {
        Text('Pinch to change the number of columns')
          .height('5%')
          .margin({ top: 10, left: 20 })
      }

      Stack() {
        // Display the WaterFlow snapshot before scaling.
        Image(this.waterFlowSnapshot)
          .width('100%')
          .height('100%')
          .scale({
            x: this.imageScale,
            y: this.imageScale,
            centerX: 0,
            centerY: 0
          })
        
        WaterFlow() {
          LazyForEach(this.dataSource, (item: number) => {
            FlowItem() {
              // Use reusable components to improve performance.
              ReusableFlowItem({ item: item })
            }
            .width('100%')
            .aspectRatio(this.itemHeightArray[item % 100] / this.itemWidthArray[item%100])
            .backgroundColor(this.colors[item % this.colors.length])
          }, (item: number) => item.toString())
        }
        .id('waterflow') // Set the ID for capturing snapshots.
        .columnsTemplate('1fr '.repeat(this.columns))  // Dynamically generate a column template. For example, '1fr 1fr 1fr' indicates three columns with the same width.
        .backgroundColor(0xFAEEE0)
        .width('100%')
        .height('100%')
        .layoutWeight(1)
        .opacity(this.waterFlowOpacity)
        .scale({
          x: this.waterFlowScale,
          y: this.waterFlowScale,
          centerX: 0,
          centerY: 0
        })
        .priorityGesture(
          PinchGesture()
            .onActionStart((event: GestureEvent) => {
              // Take a snapshot when the pinch gesture is recognized.
              this.pinchTime = event.timestamp;
              this.columnChanged = false;
              this.oldColumn = this.columns;
              this.getUIContext().getComponentSnapshot().get('waterflow', (error: Error, pixmap: image.PixelMap) => {
                if (error) {
                  const err: BusinessError = error as BusinessError;
                  console.error(`Failed to get component snapshot. Code: ${err.code}, message: ${err.message}`);
                  return;
                }
                this.waterFlowSnapshot = pixmap;
              });
            })
            .onActionUpdate((event: GestureEvent) => {
              // Gesture update: Process the scaling logic and visual effect.
              // Boundary restriction: Prevent scaling when the column number exceeds the range.
              if ((this.oldColumn === 1 && event.scale > 1) || (this.oldColumn === 4 && event.scale < 1)) {
                return;
              }

              // Throttling: Prevent frequent updates to improve performance.
              if (event.timestamp - this.pinchTime < 10000000) {
                return;
              }
              this.pinchTime = event.timestamp;

              this.waterFlowScale = event.scale;
              this.imageScale = event.scale;
              // Set the WaterFlow opacity based on the scale factor.
              this.waterFlowOpacity = (this.waterFlowScale > 1) ? (this.waterFlowScale - 1) : (1 - this.waterFlowScale);
              this.waterFlowOpacity *= 3;
              if (!this.columnChanged) {
                this.changeColumns(event.scale);
              }

              // Adjust the scale factor after the number of columns changes to avoid blank areas.
              if (this.columnChanged) {
                this.waterFlowScale = this.imageScale * this.columns / this.oldColumn;

                // Limit the scale range to ensure natural visual effects.
                if (event.scale < 1) {
                  this.waterFlowScale = this.waterFlowScale > 1 ? this.waterFlowScale : 1;
                } else {
                  this.waterFlowScale = this.waterFlowScale < 1 ? this.waterFlowScale : 1;
                }
              }
            })
            .onActionEnd((event: GestureEvent) => {
              // End the gesture: Perform the animation of returning to the original position and save the status.
              // Perform the animation of returning to the original position: Smoothly transition to the normal state.
              this.getUIContext()?.animateTo({ duration: 300 }, () => {
                this.waterFlowScale = 1;
                this.waterFlowOpacity = 1;
              });

              // Persistently save the current number of columns. Restore the number of columns when the application is started next time.
              AppStorage.setOrCreate<number>('columnsCount', this.columns);
            })
        )
      }
    }
  }
}
```

### Example 5: Setting the Edge Fading Effect

This example demonstrates how to enable the edge fading effect for the WaterFlow component using the [fadingEdge](ts-container-scrollable-common.md#fadingedge14) API and set the length of the fading edge using the fadingEdgeLength parameter.

For details about WaterFlowDataSource and the complete code, see [Example 1: Using a Basic WaterFlow Component](#example-1-using-a-basic-waterflow-component).



```TypeScript
// Index.ets
import { LengthMetrics } from '@kit.ArkUI';
import { WaterFlowDataSource } from './WaterFlowDataSource';

@Entry
@Component
struct WaterFlowDemo {
  @State minSize: number = 80;
  @State maxSize: number = 180;
  @State colors: number[] = [0xFFC0CB, 0xDA70D6, 0x6B8E23, 0x6A5ACD, 0x00FFFF, 0x00FF7F];
  dataSource: WaterFlowDataSource = new WaterFlowDataSource();
  scroller: Scroller = new Scroller();
  private itemWidthArray: number[] = [];
  private itemHeightArray: number[] = [];

  // Calculate the width and height of a flow item.
  getSize() {
    let ret = Math.floor(Math.random() * this.maxSize);
    return (ret > this.minSize ? ret : this.minSize);
  }

  // Set the width and height array of the flow item.
  setItemSizeArray() {
    for (let i = 0; i < 100; i++) {
      this.itemWidthArray.push(this.getSize());
      this.itemHeightArray.push(this.getSize());
    }
  }

  // Component lifecycle: Initialize the size array when the component is about to appear.
  aboutToAppear() {
    this.setItemSizeArray();
  }

  build() {
    Column({ space: 2 }) {
      WaterFlow({ scroller: this.scroller }) {
        LazyForEach(this.dataSource, (item: number) => {
          FlowItem() {
            Column() {
              Text('N' + item).fontSize(12).height('16')
            }
          }
          .width('100%')
          .height(this.itemHeightArray[item % 100])
          .backgroundColor(this.colors[item % 5])
        }, (item: number) => item.toString())
      }
      // auto-fill: Calculate the number of columns that can be placed based on the container width.
      .columnsTemplate('repeat(auto-fill,80)')
      .columnsGap(10)
      .rowsGap(5)
      .height('90%')
      .scrollBar(BarState.On)
      // Edge fading effect: Create a fade transition effect at the scrolling edges.
      // true: Enable the fading effect.
      // fadingEdgeLength: LengthMetrics.vp(80): The fading area is 80 vp in length.
      // Effect: There is a fading transition area of 80 vp at the top and bottom edges of the waterflow.
      .fadingEdge(true, { fadingEdgeLength: LengthMetrics.vp(80) })
    }
  }
}
```

### Example 6: Setting the Single-Side Edge Effect

This example uses the [edgeEffect](ts-container-scrollable-common.md#edgeeffect11) API to set the single-side edge effect for the WaterFlow component.

For details about WaterFlowDataSource and the complete code, see [Example 1: Using a Basic WaterFlow Component](#example-1-using-a-basic-waterflow-component).



```TypeScript
// Index.ets
import { WaterFlowDataSource } from './WaterFlowDataSource';

@Entry
@Component
struct WaterFlowDemo {
  @State minSize: number = 80;
  @State maxSize: number = 180;
  @State colors: number[] = [0xFFC0CB, 0xDA70D6, 0x6B8E23, 0x6A5ACD, 0x00FFFF, 0x00FF7F];
  dataSource: WaterFlowDataSource = new WaterFlowDataSource();
  scroller: Scroller = new Scroller();
  private itemWidthArray: number[] = [];
  private itemHeightArray: number[] = [];

  // Calculate the width and height of a flow item.
  getSize() {
    let ret = Math.floor(Math.random() * this.maxSize);
    return (ret > this.minSize ? ret : this.minSize);
  }

  // Set the width and height array of the flow item.
  setItemSizeArray() {
    for (let i = 0; i < 100; i++) {
      this.itemWidthArray.push(this.getSize());
      this.itemHeightArray.push(this.getSize());
    }
  }

  // Component lifecycle: Initialize the size array when the component is about to appear.
  aboutToAppear() {
    this.setItemSizeArray();
  }

  build() {
    Column({ space: 2 }) {
      WaterFlow({ scroller: this.scroller }) {
        LazyForEach(this.dataSource, (item: number) => {
          FlowItem() {
            Column() {
              Text('N' + item).fontSize(12).height('16')
            }
          }
          .width('100%')
          .height(this.itemHeightArray[item % 100])
          .backgroundColor(this.colors[item % 5])
        }, (item: number) => item.toString())
      }
      // auto-fill: Calculate the number of columns that can be placed based on the container width.
      .columnsTemplate('repeat(auto-fill,80)')
      .columnsGap(10)
      .rowsGap(5)
      .height('90%')
      // Single-side edge effect: Set the spring effect, which takes effect only at the top.
      // EdgeEffect.Spring: spring rebound effect that provides an elastic bounce when sliding to the boundary.
      // alwaysEnabled: true: The edge effect is always enabled, even if the content is not enough to scroll.
      // effectEdge: EffectEdge.START: The effect takes effect only at the start edge (top).
      // Effect: The spring rebound effect is displayed only when scrolling up to the top, but not when scrolling down to the bottom.
      .edgeEffect(EdgeEffect.Spring, { alwaysEnabled: true, effectEdge: EffectEdge.START })

    }
  }
}
```

### Example 7: Setting and Changing the Footer Component in the WaterFlow Component

In API version 18 and later versions, this example demonstrates how to set the footer component in the WaterFlow component using the footerContent API of [WaterFlowOptions](arkts-arkui-waterflow-comp-waterflowoptions-i.md). The footer component is updated using the update function of ComponentContent.

For details about WaterFlowDataSource and the complete code, see [Example 1: Using a Basic WaterFlow Component](#example-1-using-a-basic-waterflow-component).



```TypeScript
// Index.ets
import { ComponentContent, UIContext } from '@kit.ArkUI';
import { WaterFlowDataSource } from './WaterFlowDataSource';

class Params {
  text: string = '';

  constructor(text: string) {
    this.text = text;
  }
}

// Builder function: builds the UI structure of the footer component.
@Builder
function buildText(params: Params) {
  Column() {
    Text(params.text)
      .fontSize(20)
      .fontWeight(FontWeight.Bold)
      .margin(20)
  }
}

@Entry
@Component
struct Index {
  @State message1: string = 'End';
  @State message2: string = 'Load more';
  @State colors: number[] = [0xD5D5D5, 0x7F7F7F, 0xF7F7F7];
  @State minSize: number = 80;
  @State maxSize: number = 180;

  // UI context: used to create ComponentContent.
  context: UIContext = this.getUIContext();

  // Dynamic footer component: Use ComponentContent to create an updatable footer component.
  // ComponentContent<Params>: generic parameter type
  // wrapBuilder<[Params]>(buildText): builder function
  // new Params(this.message1): initial parameter, which displays "End".
  footerContent: ComponentContent<Params> = new ComponentContent<Params>(
    this.context,
    wrapBuilder<[Params]>(buildText),
    new Params(this.message1)
  );

  dataSource: WaterFlowDataSource = new WaterFlowDataSource();
  private itemWidthArray: number[] = [];
  private itemHeightArray: number[] = [];

  // Calculate the width and height of a flow item.
  getSize() {
    let ret = Math.floor(Math.random() * this.maxSize);
    return (ret > this.minSize ? ret : this.minSize);
  }

  // Set the width and height array of the flow item.
  setItemSizeArray() {
    for (let i = 0; i < 100; i++) {
      this.itemWidthArray.push(this.getSize());
      this.itemHeightArray.push(this.getSize());
    }
  }

  // Component lifecycle: Initialize the size array when the component is about to appear.
  aboutToAppear() {
    this.setItemSizeArray();
  }

  build() {
    Row() {
      Column() {
        Button('Update Footer').width('90%').margin(20)
          .onClick((event?: ClickEvent) => {
            // Call the update method of ComponentContent to update the footer component.
            // Pass a new Params object, and change the text content from "End" to "Load more".
            this.footerContent.update(new Params(this.message2));
          })
        WaterFlow({ footerContent: this.footerContent }) {
          LazyForEach(this.dataSource, (item: number) => {
            FlowItem() {
              Column() {
                Text('N' + item).fontSize(12).height('16')
              }
              .width('100%')
              .height(this.itemHeightArray[item % 100])
              .backgroundColor(this.colors[item % 3])
              .justifyContent(FlexAlign.Center)
              .alignItems(HorizontalAlign.Center)
            }
          }, (item: number) => item.toString())
        }
        .columnsTemplate('1fr')
        .height('90%')
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```

### Example 8: Implementing Pull-to-Refresh for a WaterFlow Component

This example demonstrates how to implement the pull-to-refresh function for the data source of the WaterFlow component via [Refresh](ts-container-refresh.md).

For details about WaterFlowDataSource and the complete code, see [Example 1: Using a Basic WaterFlow Component](#example-1-using-a-basic-waterflow-component).



```TypeScript
// Index.ets
import { WaterFlowDataSource } from './WaterFlowDataSource';

@Entry
@Component
struct WaterFlowDemo {
  @State minSize: number = 80;
  @State maxSize: number = 180;
  @State colors: number[] = [0xFFC0CB, 0xDA70D6, 0x6B8E23, 0x6A5ACD, 0x00FFFF, 0x00FF7F];
  @State isRefreshing: boolean = false;
  dataSource: WaterFlowDataSource = new WaterFlowDataSource();
  scroller: Scroller = new Scroller();
  private itemWidthArray: number[] = [];
  private itemHeightArray: number[] = [];

  // Calculate the width and height of a flow item.
  getSize() {
    let ret = Math.floor(Math.random() * this.maxSize);
    return (ret > this.minSize ? ret : this.minSize);
  }

  // Set the width and height array of the flow item.
  setItemSizeArray() {
    for (let i = 0; i < 100; i++) {
      this.itemWidthArray.push(this.getSize());
      this.itemHeightArray.push(this.getSize());
    }
  }

  // Component lifecycle: Initialize the size array when the component is about to appear.
  aboutToAppear() {
    this.setItemSizeArray();
  }

  build() {
    Column({ space: 2 }) {
      // refreshing: $$this.isRefreshing: bidirectional binding of the refresh status.
      Refresh({ refreshing: $$this.isRefreshing }) {
        WaterFlow({ scroller: this.scroller }) {
          LazyForEach(this.dataSource, (item: number) => {
            FlowItem() {
              Column() {
                Text('N' + item).fontSize(12).height('16')
              }
            }
            .width('100%')
            .height(this.itemHeightArray[item % 100])
            .backgroundColor(this.colors[item % this.colors.length])
          }, (item: number) => item.toString())
        }
        // auto-fill: Calculate the number of columns that can be placed based on the container width.
        .columnsTemplate('repeat(auto-fill,80)')
        .columnsGap(10)
        .rowsGap(5)
        .height('90%')
        // Edge effect: spring rebound effect.
        .edgeEffect(EdgeEffect.Spring, { alwaysEnabled: true })
        .onReachEnd(() => {
          // Load more data when the bottom is reached.
          setTimeout(() => {
            this.dataSource.addNewItems(100);
          }, 1000);
        })
      }
      .onStateChange((refreshStatus: RefreshStatus) => {
        // Refresh status change listener: Process different refresh status.
        if (refreshStatus === RefreshStatus.Done) {
          // When the refresh is complete: Call the refresh method of the data source to update all data.
          this.dataSource.refreshItems();
        }
      })
      .onRefreshing(() => {
        // Callback when the refresh is in progress: Simulate the refresh process.
        setTimeout(() => {
          this.isRefreshing = false;
        }, 1000);
      })
    }
  }
}
```

### Example 9: Configuring the Number of Columns in the WaterFlow Component Based on Breakpoints

In API version 22 and later versions, this example shows how to configure the number of columns in the WaterFlow component based on breakpoints.

When the WaterFlow width is within the breakpoint range of sm or smaller, two columns are displayed.



When the WaterFlow width is within the breakpoint range of md, three columns are displayed.



When the WaterFlow width is within the breakpoint range of lg or larger, five columns are displayed.



```TypeScript
// Index.ets
import { WaterFlowDataSource } from './WaterFlowDataSource';

@Entry
@Component
struct WaterFlowDemo {
  minSize: number = 80;
  maxSize: number = 180;
  colors: number[] = [0xFFC0CB, 0xDA70D6, 0x6B8E23, 0x6A5ACD, 0x00FFFF, 0x00FF7F];
  dataSource: WaterFlowDataSource = new WaterFlowDataSource();
  private itemHeightArray: number[] = [];

  // Calculate the width and height of a flow item.
  getSize() {
    let ret = Math.floor(Math.random() * this.maxSize);
    return (ret > this.minSize ? ret : this.minSize);
  }

  // Set the height array of FlowItem.
  setItemSizeArray() {
    for (let i = 0; i < 100; i++) {
      this.itemHeightArray.push(this.getSize());
    }
  }

  // Component lifecycle: Initialize the size array when the component is about to appear.
  aboutToAppear() {
    this.setItemSizeArray();
  }

  build() {
    Column({ space: 2 }) {
      WaterFlow() {
        LazyForEach(this.dataSource, (item: number) => {
          FlowItem() {
            Column() {
              Text('N' + item).fontSize(12).height('16')
              // Note: Ensure that the corresponding JPG file exists.
              Image('res/waterFlowTest(' + item % 5 + ').jpg')
                .objectFit(ImageFit.Fill)
                .width('100%')
                .layoutWeight(1)
            }
          }
          .width('100%')
          .height(this.itemHeightArray[item % 100])
          .backgroundColor(this.colors[item % this.colors.length])
        }, (item: number) => item.toString())
      }
      .key('waterFlow')
      // Set the number of columns for WaterFlow based on breakpoints.
      .columnsTemplate({fillType:PresetFillType.BREAKPOINT_SM2MD3LG5})
      .columnsGap(10)
      .rowsGap(5)
      .backgroundColor(0xFAEEE0)
      .margin('20vp')
      .width('100%')
      .height('30%')
    }
  }
}
```

### Example 10: Obtaining the Content Height for the WaterFlow Component

From API version 22, this example uses the WaterFlow component to obtain the content height.

For details about WaterFlowDataSource and the complete code, see [Example 1: Using a Basic WaterFlow Component](#example-1-using-a-basic-waterflow-component).



```TypeScript
// Index.ets
import { WaterFlowDataSource } from './WaterFlowDataSource';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WaterFlowContentSizeDemo {
  @State minSize: number = 80;
  @State maxSize: number = 180;
  @State colors: number[] = [0xFFC0CB, 0xDA70D6, 0x6B8E23, 0x6A5ACD, 0x00FFFF, 0x00FF7F];
  @State contentWidth: number = -1;
  @State contentHeight: number = -1;
  scroller: Scroller = new Scroller();
  dataSource: WaterFlowDataSource = new WaterFlowDataSource();
  private itemWidthArray: number[] = [];
  private itemHeightArray: number[] = [];

  // Calculate the width and height of a flow item.
  getSize() {
    let ret = Math.floor(Math.random() * this.maxSize);
    return (ret > this.minSize ? ret : this.minSize);
  }

  // Set the width and height array of the water flow item.
  setItemSizeArray() {
    for (let i = 0; i < 100; i++) {
      this.itemWidthArray.push(this.getSize());
      this.itemHeightArray.push(this.getSize());
    }
  }

  // Component lifecycle: Initialize the size array when the component is about to appear.
  aboutToAppear() {
    this.setItemSizeArray();
  }

  @Builder
  itemFoot() {
    Column() {
      Text('End')
        .fontSize(10)
        .backgroundColor(Color.Red)
        .width(50)
        .height(50)
        .align(Alignment.Center)
        .margin({ top: 2 })
    }
  }

  build() {
    Column({ space: 2 }) {
      // Button to obtain the content size by calling contentSize.
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
            console.error(`Failed to get contentSize of the WaterFlow. Code: ${err.code}, message: ${err.message}`);
          }
        }).margin(5)
      // Display the obtained content size.
      Text('Width:' + this.contentWidth)
        .fontColor(Color.Red)
        .height(30)
      Text('Height:' + this.contentHeight)
        .fontColor(Color.Red)
        .height(30)

      WaterFlow({ scroller: this.scroller, footer: this.itemFoot() }) {
        LazyForEach(this.dataSource, (item: number) => {
          FlowItem() {
            Column() {
              Text('N' + item).fontSize(12).height('16')
            }
          }
          .width('100%')
          .height(this.itemHeightArray[item % 100])
          .backgroundColor(this.colors[item % this.colors.length])
        }, (item: number) => item.toString())
      }
      .columnsTemplate('1fr 1fr') // Set the layout of two columns with equal width.
      .columnsGap(10)
      .rowsGap(5)
      .backgroundColor(0xFAEEE0)
      .width('100%')
      .height('80%')
    }
  }
}
```

### Example 11: Setting a Scrolling Event

This example obtains a [UIWaterFlowEvent](arkts-arkui-waterflow-comp-uiwaterflowevent-i.md) instance via getEvent('WaterFlow') on a FrameNode and sets scroll event callbacks for a WaterFlow component. This approach is intended for scenarios where the page code cannot be directly modified to use declarative callbacks.

The UIWaterFlowEvent API is added since API version 19.

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
    // Obtain the WaterFlow event.
    let waterFlowEvent: UIWaterFlowEvent | undefined = typeNode.getEvent(frameNode, 'WaterFlow');

    // Set the OnWillScroll callback.
    waterFlowEvent?.setOnWillScroll((scrollOffset: number, scrollState: ScrollState, scrollSource: ScrollSource) => {
      console.info(`onWillScroll scrollOffset = ${scrollOffset}, scrollState = ${scrollState}, scrollSource = ${scrollSource}`);
    });

    // Set the OnDidScroll callback.
    waterFlowEvent?.setOnDidScroll((scrollOffset: number, scrollState: ScrollState) => {
      console.info(`onDidScroll scrollOffset = ${scrollOffset}, scrollState = ${scrollState}`);
    });

    // Set the OnReachStart callback.
    waterFlowEvent?.setOnReachStart(() => {
      console.info('onReachStart');
    });

    // Set the OnReachEnd callback.
    waterFlowEvent?.setOnReachEnd(() => {
      console.info('onReachEnd');
    });

    // Set the OnScrollStart callback.
    waterFlowEvent?.setOnScrollStart(() => {
      console.info('onScrollStart');
    });

    // Set the OnScrollStop callback.
    waterFlowEvent?.setOnScrollStop(() => {
      console.info('onScrollStop');
    });

    // Set the OnScrollFrameBegin callback.
    waterFlowEvent?.setOnScrollFrameBegin((offset: number, state: ScrollState) => {
      console.info(`onScrollFrameBegin offset = ${offset}, state = ${state}`);
      return undefined;
    });

    // Set the OnScrollIndex event.
    waterFlowEvent?.setOnScrollIndex((first: number, last: number) => {
      console.info(`onScrollIndex start = ${first}, end = ${last}`);
    });
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();
  @State numbers: string[] = [];
  @State heights: number[] = [];

  aboutToAppear() {
    for (let i = 0; i < 30; i++) {
      this.numbers.push(`${i + 1}`);
      this.heights.push(70 + Math.floor(Math.random() * 60));
    }
  }

  build() {
    Column() {
      Button('add CommonEvent to WaterFlow')
        .onClick(() => {
          this.myNodeController!.addCommonEvent(this.myNodeController!.rootNode!.getParent()!.getPreviousSibling()!)
        })
      WaterFlow() {
        ForEach(this.numbers, (day: string, index: number) => {
          FlowItem() {
            Text(day)
              .fontSize(16)
              .backgroundColor(0xF9CF93)
              .width('100%')
              .height(this.heights[index])
              .textAlign(TextAlign.Center)
          }
          .width('100%')
        }, (day: string, index: number) => index.toString() + day)
      }
      .columnsTemplate('1fr 1fr')
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
