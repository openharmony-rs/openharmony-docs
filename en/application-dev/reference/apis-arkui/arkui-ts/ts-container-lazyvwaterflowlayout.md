# LazyVWaterFlowLayout

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yylong-->
<!--Designer: @yylong-->
<!--Tester: @leiyuqian-->
<!--Adviser: @Brilliantry_Rui-->

This component is used to implement the waterfall layout that supports lazy loading. Its parent component can only be [List](ts-container-list.md), [Scroll](ts-container-scroll.md), [WaterFlow](ts-container-waterflow.md), **FlowItem**, or **LazyColumnLayout**. It can also be encapsulated by using a custom component or [NodeContainer](ts-basic-components-nodecontainer.md) component and then applied to the preceding components.

It supports lazy loading only when the [List](ts-container-list.md) component, [Scroll](ts-container-scroll.md) component, and [WaterFlow](ts-container-waterflow.md) component are in single-column mode or single-column segmented layout and the layout direction is **FlexDirection.Column**. If this component is used in the multi-column mode of the [WaterFlow](ts-container-waterflow.md) component or when the layout direction is **FlexDirection.RowReverse** or **FlexDirection.Row**, lazy loading is not supported. In addition, if this component is used in the [WaterFlow](ts-container-waterflow.md) component whose layout direction is **FlexDirection.ColumnReverse**, the display will be abnormal. When lazy loading is enabled, the component only loads child components within the visible area, with pre-loading of half-screen content above and below the visible area during frame idle periods.

> **NOTE**
>
> This component's height adapts to content by default. You are advised not to set the height, height constraint, or aspect ratio. Otherwise, the display may be abnormal.

**Since:** 26.0.0

## Modules to Import

```ts
import { LazyVWaterFlowLayout } from '@kit.ArkUI';
```

## APIs

LazyVWaterFlowLayout()

Creates a vertical lazy-loading waterfall layout container.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Attributes

In addition to the [universal attributes](ts-component-general-attributes.md), the following attributes are supported.

### columnsTemplate

columnsTemplate(value: string | ItemFillPolicy | undefined)

Sets the number of columns in the waterfall layout. If this attribute is not set, one column is used by default.

When the **value** is of the string type, you can use **columnsTemplate('1fr 1fr 2fr')** to divide the **LazyVWaterFlowLayout** component into three columns, with the first column taking up 1/4 of the component's full width, the second column 1/4, and the third column 2/4.

You can use **columnsTemplate('repeat(auto-fill,track-size)')** to automatically calculate the number of rows based on the specified row height **track-size**. **repeat** and **auto-fill** are keywords. The units for **track-size** can be px, vp (default), %, or a valid number.

When the value is of the **ItemFillPolicy** type, the number of columns is determined based on the [breakpoint type](../../../ui/arkts-layout-development-grid-layout.md#breakpoints) corresponding to the width of the **LazyVWaterFlowLayout** component.

For example, **ItemFillPolicy.BREAKPOINT_DEFAULT** displays two columns on devices with a width equivalent to sm or smaller, three columns on devices with a width equivalent to md, and five columns on devices with a width equivalent to lg or larger. Each column is **1fr**.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                              |
| ------ | ------ | ---- | ---------------------------------- |
| value  | string \| [ItemFillPolicy](./ts-types.md#itemfillpolicy22) \| undefined | Yes  | Number of columns or minimum column width of the waterfall layout.<br>If the input parameter is **undefined**, the default value (one column) is used.|

**Return value**

| Type| Description          |
| --- | -------------- |
| T | Current component.|

### columnsGap

columnsGap(value: LengthMetrics | undefined): T

Sets the gap between columns. The default value is **0vp**. If this parameter is set to a value less than 0, the default value is used.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                        | Mandatory| Description                        |
| ------ | ---------------------------- | ---- | ---------------------------- |
| value  |  [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) \| undefined | Yes  | Gap between columns.<br>If the input parameter is **undefined**, the default value (**0vp**) is used.|

**Return value**

| Type| Description          |
| --- | -------------- |
| T | Current component.|

### rowsGap

rowsGap(value: LengthMetrics | undefined): T

Sets the gap between rows. The default value is **0vp**. If this parameter is set to a value less than 0, the default value is used.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                        | Mandatory| Description                        |
| ------ | ---------------------------- | ---- | ---------------------------- |
| value  | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) \| undefined | Yes  | Gap between rows.<br>If the input parameter is **undefined**, the default value (**0vp**) is used.|

**Return value**

| Type| Description          |
| --- | -------------- |
| T | Current component.|

## Events

In addition to the [universal events](ts-component-general-events.md), the following events are supported.

### onVisibleIndexesChange

onVisibleIndexesChange(callback: onVisibleIndexesChangeCallback | undefined): T

Triggered when the child component at the start or end position of the current waterfall layout changes. It is triggered once when the component is initialized.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                 |
| ------ | ------ | ---- | ------------------------------------- |
| callback  | [onVisibleIndexesChangeCallback](#onvisibleindexeschangecallback) \| undefined | Yes  | Callback function, which is triggered when the index of a child component in the visible area changes.<br>If the input parameter is **undefined**, the listening is canceled.|

**Return value**

| Type| Description          |
| --- | -------------- |
| T | Current component.|

## onVisibleIndexesChangeCallback

type onVisibleIndexesChangeCallback = (start: number, end: number) => void

Triggered when the index of the child component displayed in the current waterfall layout changes.

> **NOTE**
>
> - If **LazyVWaterFlowLayout** has no child components, both **start** and **end** return **-1**.
> - If **LazyVWaterFlowLayout** has no visible child components in the visible area, both **start** and **end** return **-1**.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                 |
| ------ | ------ | ---- | ------------------------------------- |
| start  | number | Yes  | Index of the start position in the visible area.<br>Value range: [0, total number of child nodes - 1].|
| end    | number | Yes  | Index of the end position in the visible area.<br>Value range: [0, total number of child nodes - 1].|

## Examples

### Example 1: Implementing Lazy-Loading Waterfall Layout

This example shows how to use the [Scroll](ts-container-scroll.md) and **LazyVWaterFlowLayout** components to implement the lazy-loading waterfall layout.

**MyDataSource** implements the **LazyForEach** data source API [IDataSource](ts-rendering-control-lazyforeach.md#idatasource), which is used to provide child components for **LazyVWaterFlowLayout** through **LazyForEach**.

Since API version 26.0.0, the **LazyVWaterFlowLayout** component is supported.

<!--code_no_check-->
```ts
import { LengthMetrics, LazyVWaterFlowLayout, LazyVWaterFlowLayoutAttribute } from '@kit.ArkUI';
import { MyDataSource } from './MyDataSource';

@Entry
@Component
struct LazyVWaterFlowLayoutSample1 {
  private arr : MyDataSource<number> = new MyDataSource<number>();

  // Return a random height.
  private itemHeight(index: number): number {
    return 80 + (index * 37 % 121)
  }

  private itemColor(index: number): string {
    const colors: string[] = ['#FFE0B2', '#C8E6C9', '#BBDEFB', '#F8BBD0', '#D1C4E9', '#FFF9C4']
    return colors[index % colors.length]
  }

  build() {
    Column() {
      Scroll() {
        LazyVWaterFlowLayout() {
          LazyForEach(this.arr, (item: number) => {
            Column() {
              Text('item ' + item.toString())
                .fontSize(16)
                .fontColor(Color.Black)
            }
            .height(this.itemHeight(item))
            .width('100%')
            .borderRadius(8)
            .backgroundColor(this.itemColor(item))
            .justifyContent(FlexAlign.Center)
          })
        }
        .columnsTemplate('1fr 1fr')
        .rowsGap(LengthMetrics.vp(10))
        .columnsGap(LengthMetrics.vp(10))
        .onVisibleIndexesChange((start: number, end: number) => {
          // Scroll listener: Load more data when the scroll is about to reach the bottom.
          if (end + 20 >= this.arr.totalCount()) {
            // Add 100 new items to the data source.
            let currentCount = this.arr.totalCount();
            for (let i = currentCount; i < currentCount + 100; i++) {
              this.arr.pushData(i);
            }
          }
        })
      }
      .padding(10)
      .layoutWeight(1)
    }
    .width('100%')
    .height('100%')
    .backgroundColor('#DCDCDC')
  }

  aboutToAppear(): void {
    for (let i = 0; i < 100; i++) {
      this.arr.pushData(i);
    }
  }
}
```

<!--code_no_check-->
```ts
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
![scroll_lazyvwaterflowlayout.png](figures/scroll_lazyvwaterflowlayout.png)
