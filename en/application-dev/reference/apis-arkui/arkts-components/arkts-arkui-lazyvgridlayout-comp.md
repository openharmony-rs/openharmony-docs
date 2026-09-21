# LazyVGridLayout

Implements a grid layout that supports lazy loading.

In versions earlier than API version 26.0.0, the parent component of the **LazyVGridLayout** component supports the WaterFlow and FlowItem components. You can also encapsulate the parent component using a custom component or NodeContainer component and use it in **WaterFlow** or **FlowItem**.

Since API version 26.0.0, the parent component of this component also supports List, Scroll, or [LazyColumnLayout](../../../reference/apis-arkui/arkui-ts/ts-container-lazycolumnlayout.md). Additionally, custom components or NodeContainer components can be encapsulated and then used in **List**, **Scroll**, or **LazyColumnLayout**.

> **NOTE** > > - This component is supported since API version 19. Updates will be marked with a superscript to indicate their > earliest API version. > > - This component's height adapts to content by default. Setting the height, height constraints, or aspect ratio > causes display anomalies. > > - The lazy loading conditions of this component in different parent components are as follows: > > 1. In the **WaterFlow** component, lazy loading is supported only when it uses single-column mode or single- > column segments in segmented layout and [FlexDirection](../arkts-apis/arkts-arkui-flexdirection-e.md) is set to **FlexDirection.Column**. > Lazy loading is not supported if the **WaterFlow** component is in multi-column mode or the layout direction is > **FlexDirection.Row** or **FlexDirection.RowReverse**. Using this component with **FlexDirection.ColumnReverse** in > the **WaterFlow** component causes display anomalies. > > 2. In the **List** component, the layout direction must be vertical (that is, the > [listDirection](arkts-arkui-list-comp-attribute.md#listdirection) property is set to **Axis.Vertical**). Using this component in a > non-vertical **List** component will cause an application crash. If any of the **lanes**, **chainAnimation**, and > **scrollSnapAlign** properties is set for the **List** component, the lazy loading of this component will become > invalid. > > 3. In the **Scroll** component, the layout direction must be vertical (that is, the value of the > [scrollable](arkts-arkui-scroll-comp-attribute.md#scrollable) property is **ScrollDirection.Vertical**). Using this component in a > non-vertical **Scroll** component will cause an application crash. > > - When lazy loading is enabled, the component only loads child components within the visible area of the parent > component, with pre-loading of half-screen content above and below the viewport during frame idle periods.

## LazyVGridLayout

```TypeScript
LazyVGridLayout()
```

Creates a vertical lazy-loading grid layout container.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Summary

## Examples

### Example 1: Implementing a Lazy-Loading Grid Layout

This example uses [WaterFlow](ts-container-waterflow.md) and LazyVGridLayout to implement a lazy loading grid layout, and triggers a callback through [onVisibleIndexesChange](#onvisibleindexeschange) when the visible area changes, returning the start index and end index of the child components in the current visible area.

MyDataSource implements the [IDataSource](ts-rendering-control-lazyforeach.md#idatasource) API for [LazyForEach](ts-rendering-control-lazyforeach.md), which provides child components for LazyVGridLayout through LazyForEach.

The onVisibleIndexesChange event is added since API version 26.0.0.

```TypeScript
import { LengthMetrics } from '@kit.ArkUI';
// MyDataSource is a custom data source class that implements the IDataSource interface required by LazyForEach.
import { MyDataSource } from './MyDataSource';

@Entry
@Component
struct LazyVGridLayoutSample1 {
  private arr1:MyDataSource<number> = new MyDataSource<number>();
  private arr2:MyDataSource<number> = new MyDataSource<number>();
  build() {
    Column() {
      WaterFlow() {
        // First LazyVGridLayout: single-column layout
        LazyVGridLayout() {
          LazyForEach(this.arr1, (item:number)=>{
            Text('item' + item.toString())
              .height(64)
              .width('100%')
              .borderRadius(5)
              .backgroundColor(Color.White)
              .textAlign(TextAlign.Center)
          })
        }
        .columnsTemplate('1fr') // Single-column layout
        .rowsGap(LengthMetrics.vp(10)) // Row gap of 10 vp
        // The onVisibleIndexesChange event is added since API version 26.0.0.
        .onVisibleIndexesChange((start: number, end: number) => {
          console.info('visible indexes: start: ' + start + ', end: ' + end);
        })

        // Second LazyVGridLayout: two-column layout
        LazyVGridLayout() {
          LazyForEach(this.arr2, (item:number)=>{
            Text('item' + item.toString())
              .height(128)
              .width('100%')
              .borderRadius(5)
              .backgroundColor(Color.White)
              .textAlign(TextAlign.Center)
          })
        }
        .columnsTemplate('1fr 1fr') // Two-column layout with equal column width
        .rowsGap(LengthMetrics.vp(10)) // Row gap of 10 vp
        .columnsGap(LengthMetrics.vp(10)) // Column gap of 10 vp
      }.padding(10)
      .rowsGap(10)
    }
    .width('100%').height('100%')
    .backgroundColor('#DCDCDC')
  }

  // Initialize the data source.
  aboutToAppear(): void {
    for (let i = 0; i < 6; i++) {
      this.arr1.pushData(i);
    }
    for (let i = 0; i < 100; i++) {
      this.arr2.pushData(i);
    }
  }
}
```



```TypeScript
// MyDataSource.ets
export class BasicDataSource<T> implements IDataSource {
  private listeners: DataChangeListener[] = [];
  protected dataArray: T[] = [];

  public totalCount(): number {
    return this.dataArray.length;
  }

  public getData(index: number): T {
    return this.dataArray[index];
  }

  registerDataChangeListener(listener: DataChangeListener): void {
    if (this.listeners.indexOf(listener) < 0) {
      console.info('add listener');
      this.listeners.push(listener);
    }
  }

  unregisterDataChangeListener(listener: DataChangeListener): void {
    const pos = this.listeners.indexOf(listener);
    if (pos >= 0) {
      console.info('remove listener');
      this.listeners.splice(pos, 1);
    }
  }

  notifyDataReload(): void {
    this.listeners.forEach(listener => {
      listener.onDataReloaded();
    })
  }

  notifyDataAdd(index: number): void {
    this.listeners.forEach(listener => {
      listener.onDataAdd(index);
    })
  }

  notifyDataChange(index: number): void {
    this.listeners.forEach(listener => {
      listener.onDataChange(index);
    })
  }

  notifyDataDelete(index: number): void {
    this.listeners.forEach(listener => {
      listener.onDataDelete(index);
    })
  }

  notifyDataMove(from: number, to: number): void {
    this.listeners.forEach(listener => {
      listener.onDataMove(from, to);
    })
  }

  notifyDatasetChange(operations: DataOperation[]): void {
    this.listeners.forEach(listener => {
      listener.onDatasetChange(operations);
    })
  }
}

export class MyDataSource<T> extends BasicDataSource<T> {
  public shiftData(): void {
    this.dataArray.shift();
    this.notifyDataDelete(0);
  }
  public unshiftData(data: T): void {
    this.dataArray.unshift(data);
    this.notifyDataAdd(0);
  }
  public pushData(data: T): void {
    this.dataArray.push(data);
    this.notifyDataAdd(this.dataArray.length - 1);
  }
  public popData(): void {
    this.dataArray.pop();
    this.notifyDataDelete(this.dataArray.length);
  }
  public clearData(): void {
    this.dataArray = [];
    this.notifyDataReload();
  }
}
```

### Example 2: Setting a Header or Footer Component and Sticky Styles

This example nests LazyVGridLayout inside [WaterFlow](ts-container-waterflow.md), and implements sticky styles at the top and bottom of the grid through [header](#header), [footer](#footer), and [sticky](#sticky). During scrolling, the header sticks to the top of the visible area, and the footer sticks to the bottom of the visible area.

Since API version 26.0.0, the header, footer, and sticky attributes are newly supported.



```TypeScript
import { LengthMetrics } from '@kit.ArkUI';
// MyDataSource is a custom data source class that implements the IDataSource interface required by LazyForEach.
import { MyDataSource } from './MyDataSource';

@Entry
@Component
struct LazyVGridLayoutStickyDemo {
  private arr:MyDataSource<number> = new MyDataSource<number>();

  // Build the header component.
  @Builder
  HeaderBuilder() {
    Column() {
      Text('Header')
        .fontSize(16)
    }
    .width('100%')
    .height(64)
    .borderRadius(5)
    .backgroundColor(Color.White)
    .justifyContent(FlexAlign.Center)
  }

  @Builder
  FooterBuilder() {
    Column() {
      Text('Footer')
        .fontSize(16)
    }
    .width('100%')
    .height(64)
    .borderRadius(5)
    .backgroundColor(Color.White)
    .justifyContent(FlexAlign.Center)
  }

  build() {
    Column() {
      WaterFlow() {
        LazyVGridLayout() {
          LazyForEach(this.arr, (item:number)=>{
            Text('item' + item.toString())
              .height(128)
              .width('100%')
              .borderRadius(5)
              .backgroundColor(Color.White)
              .textAlign(TextAlign.Center)
          })
        }
        .columnsTemplate('1fr 1fr')
        .rowsGap(LengthMetrics.vp(10))
        .columnsGap(LengthMetrics.vp(10))
        .header(this.HeaderBuilder)
        .footer(this.FooterBuilder)
        // Set both the header and footer to sticky.
        .sticky(StickyStyle.BOTH)
      }.padding(10)
      .rowsGap(10)
    }
    .width('100%').height('100%')
    .backgroundColor('#DCDCDC')
  }

  aboutToAppear(): void {
    for (let i = 0; i < 100; i++) {
      this.arr.pushData(i);
    }
  }
}
```

### Example 3: Setting Adaptive Column Count

This example implements adaptive column count for the LazyVGridLayout component by setting the [columnsTemplate](#columnstemplate) attribute, and uses auto-fill, auto-fit, and auto-stretch in the [columnsTemplate](#columnstemplate) attribute.

Since API version 19, the [columnsTemplate](#columnstemplate) API is newly supported.

```TypeScript
import { LazyColumnLayout, LazyColumnLayoutAttribute, LengthMetrics } from '@kit.ArkUI';
// MyDataSource is a custom data source class that implements the IDataSource interface required by LazyForEach.
import { MyDataSource } from './MyDataSource';

@Entry
@Component
struct LazyVGridLayoutColumnsTemplateDemo {
  private autoFillData: MyDataSource<number> = new MyDataSource<number>();
  private autoFitData: MyDataSource<number> = new MyDataSource<number>();
  private autoStretchData: MyDataSource<number> = new MyDataSource<number>();

  aboutToAppear(): void {
    // Initialize a fixed amount of data without loading more on scroll to bottom.
    for (let i = 0; i < 12; i++) {
      this.autoFillData.pushData(i);
      this.autoFitData.pushData(i);
      this.autoStretchData.pushData(i);
    }
  }

  @Builder
  ModeTitle(title: string, description: string) {
    Column() {
      Text(title)
        .fontSize(16)
        .fontWeight(FontWeight.Medium)
        .fontColor('#182230')
      Text(description)
        .fontSize(12)
        .fontColor('#667085')
    }
    .alignItems(HorizontalAlign.Start)
    .width('100%')
    .padding({ bottom: 8 })
  }

  @Builder
  AutoFillHeader() {
    this.ModeTitle('auto-fill', 'auto-fill: fixed column width of 96 vp, auto-calculate the column count, and keep the remaining space at the end of the row.')
  }

  @Builder
  AutoFitHeader() {
    this.ModeTitle('auto-fit', 'auto-fit: minimum column width of 96 vp, distribute the remaining space evenly to each column, and the column width will be stretched.')
  }

  @Builder
  AutoStretchHeader() {
    this.ModeTitle('auto-stretch', 'auto-stretch: fixed column width of 96 vp, distribute the remaining space evenly to the column gaps, and the column gaps will be stretched.')
  }

  @Builder
  GridItemBuilder(item: number, backgroundColor: string) {
    Text(item.toString())
      .height(56)
      .width('100%')
      .borderRadius(6)
      .backgroundColor(backgroundColor)
      .fontColor('#182230')
      .textAlign(TextAlign.Center)
  }

  build() {
    Column() {
      Scroll() {
        LazyColumnLayout() {
          // auto-fill: fixed column width of 96 vp, auto-calculate the column count based on the available width.
          LazyVGridLayout() {
            LazyForEach(this.autoFillData, (item: number) => {
              this.GridItemBuilder(item, '#CDE7FF')
            })
          }
          .columnsTemplate('repeat(auto-fill, 96)')
          .rowsGap(LengthMetrics.vp(8))
          .columnsGap(LengthMetrics.vp(8))
          .header(this.AutoFillHeader)
          .padding(8)
          .backgroundColor('#F7F9FC')
          .border({ width: 1, color: '#D0D5DD' })
          .borderRadius(8)

          // auto-fit: minimum column width of 96 vp, distribute the remaining space evenly to each column.
          LazyVGridLayout() {
            LazyForEach(this.autoFitData, (item: number) => {
              this.GridItemBuilder(item, '#D8F5D0')
            })
          }
          .columnsTemplate('repeat(auto-fit, 96)')
          .rowsGap(LengthMetrics.vp(8))
          .columnsGap(LengthMetrics.vp(8))
          .header(this.AutoFitHeader)
          .padding(8)
          .backgroundColor('#F7F9FC')
          .border({ width: 1, color: '#D0D5DD' })
          .borderRadius(8)

          // auto-stretch: fixed column width of 96 vp, distribute the remaining space evenly to the column gaps.
          LazyVGridLayout() {
            LazyForEach(this.autoStretchData, (item: number) => {
              this.GridItemBuilder(item, '#FFE6A8')
            })
          }
          .columnsTemplate('repeat(auto-stretch, 96)')
          .rowsGap(LengthMetrics.vp(8))
          .columnsGap(LengthMetrics.vp(8))
          .header(this.AutoStretchHeader)
          .padding(8)
          .backgroundColor('#F7F9FC')
          .border({ width: 1, color: '#D0D5DD' })
          .borderRadius(8)
        }
        .space(LengthMetrics.vp(16))
        .width('100%')
      }
      .width('100%')
      .scrollable(ScrollDirection.Vertical)
      .layoutWeight(1)
    }
    .width('100%')
    .height('100%')
    .padding({ top: 48, left: 12, right: 12, bottom: 12 })
  }
}
```
