# LazyVWaterFlowLayout

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @rongShao-Z; @guozejun-->
<!--Designer: @guozejun-->
<!--Tester: @leiyuqian-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=057d01f6f3eda137deed36d7923522b51696942a translatedAt=2026-11-17T04:09:40.742Z pushedAt=2026-11-19T08:20:04.881Z nl=1 -->

The **LazyVWaterFlowLayout** component is used to implement a waterfall layout that supports lazy loading, suitable for displaying a large number of list items with varying heights, such as image walls and product lists. Through the lazy loading mechanism, this component only loads content in and near the visible area, reducing memory usage and rendering overhead, and improving scrolling smoothness. This component should be placed under a vertical [List](ts-container-list.md), [Scroll](ts-container-scroll.md), or [WaterFlow](ts-container-waterflow.md) component, and supports being used after being wrapped in [FlowItem](ts-container-flowitem.md), [LazyColumnLayout](ts-container-lazycolumnlayout.md), a [custom component](../../../ui/state-management/arkts-create-custom-components.md), or [NodeContainer](ts-basic-components-nodecontainer.md).

For more usage scenarios and complete examples of lazy loading layouts, see [Creating Lazy Layouts](../../../ui/arkts-layout-development-create-lazy-layout.md).

> **NOTE**
>
> - The height of the **LazyVWaterFlowLayout** component is adaptive to content by default. It is not recommended to set attributes that fix or constrain the vertical direction size of the component, because setting them will cause display abnormalities or failure to scroll normally. The involved attributes include [height](ts-universal-attributes-size.md#height), the **height** in [size](ts-universal-attributes-size.md#size), the **minHeight**/**maxHeight** in [constraintSize](ts-universal-attributes-size.md#constraintsize), [aspectRatio](ts-universal-attributes-layout-constraints.md#aspectratio), [layoutWeight](ts-universal-attributes-size.md#layoutweight), and the scenario where [height](ts-universal-attributes-size.md#height15) takes a [LayoutPolicy](ts-universal-attributes-size.md#layoutpolicy15) value.
> - When the parent component sets the size in the main axis direction, **LazyVWaterFlowLayout** performs lazy loading according to the visible area of the parent component. When the parent component does not set the size in the main axis direction, **LazyVWaterFlowLayout** will be stretched by content, causing all child components to be loaded and laid out.
> - The conditions under which this component supports lazy loading under different parent components are as follows:
>   1. Under the **List** component, the layout direction of the **List** component must be the vertical direction (that is, the [listDirection](ts-container-list.md#listdirection) attribute set to **Axis.Vertical**). Using this component in a **List** whose direction is not vertical will cause the application to crash. When the List sets any one or more of the [lanes](ts-container-list.md#lanes9), [chainAnimation](ts-container-list.md#chainanimation), and [scrollSnapAlign](ts-container-list.md#scrollsnapalign10) attributes, the lazy loading feature of this component will be invalidated.
>   2. Under the **Scroll** component, the layout direction of the **Scroll** component must be the vertical direction (that is, the [scrollable](ts-container-scroll.md#scrollable) attribute set to **ScrollDirection.Vertical**). Using this component in a **Scroll** whose direction is not vertical will cause the application to crash.
>   3. Under the **WaterFlow** component, lazy loading is supported only in the single-column mode of the **WaterFlow** component or in a single-column segment of a segmented layout, and when the [layoutDirection](ts-container-waterflow.md#layoutdirection) attribute is set to **FlexDirection.Column**. When the **WaterFlow** is in multi-column mode or the layout direction is **FlexDirection.Row** or **FlexDirection.RowReverse**, the lazy loading feature of this component will be invalidated. In addition, using this component under a **WaterFlow** component whose layout direction is **FlexDirection.ColumnReverse** will cause display abnormalities.
>   4. When encapsulated through **FlowItem**, **LazyColumnLayout**, a custom component, or **NodeContainer**, the lazy loading behavior depends on the configuration conditions of the upper-level scroll component (such as **WaterFlow**, **Scroll**, or **List**).
> - When the lazy loading feature is effective, this component only loads the child components within the visible area of the parent component, and preloads the content of half a screen above and below the visible area during idle time slots between frames.
> - The parent component here refers to the upper-level scroll component closest to the current component. For the specific meaning in other documents, refer to the corresponding content.

**Since:** 26.0.0

## Modules to Import

```ts
import { LazyVWaterFlowLayout } from '@kit.ArkUI';
```

## APIs

LazyVWaterFlowLayout()

Creates a vertical **LazyVWaterFlowLayout** component. This component should be placed under a vertical [List](ts-container-list.md), [Scroll](ts-container-scroll.md), or [WaterFlow](ts-container-waterflow.md) component, and supports being used after being wrapped by [FlowItem](ts-container-flowitem.md), [LazyColumnLayout](ts-container-lazycolumnlayout.md), a custom component, or [NodeContainer](ts-basic-components-nodecontainer.md). You are advised not to set the height, height constraint, or aspect ratio. Setting these may cause display exceptions.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Attributes

In addition to the [universal attributes](ts-component-general-attributes.md), the following attributes are supported.

### columnsTemplate

columnsTemplate(value: string | ItemFillPolicy | undefined)

Sets the number of columns, fixed column width, or minimum column width of the current **LazyVWaterFlowLayout**. If this attribute is not set, one column is used by default.

- When **value** is of the string type, you can set the number of columns, fixed column width, or minimum column width of the current **LazyVWaterFlowLayout**. Typical values and their meanings are as follows. For usage effects, see [Example 3](#example-3-setting-adaptive-column-count):
  1. **columnsTemplate('1fr 1fr 2fr')** divides the **LazyVWaterFlowLayout** into three columns, with the component width divided into four equal parts: the first column takes up one part, the second column takes up one part, and the third column takes up two parts.
  2. **columnsTemplate('repeat(auto-fit, track-size)')**: The layout automatically calculates the number of columns and their actual widths while respecting the minimum column width specified by **track-size**.
  3. **columnsTemplate('repeat(auto-fill, track-size)')**: The layout automatically calculates the number of columns based on the fixed column width specified by **track-size**.
  4. **columnsTemplate('repeat(auto-stretch, track-size)')** sets a fixed column width of **track-size**, uses [columnsGap](#columnsgap) as the minimum column gap, and automatically calculates the number of columns and the actual column gap.

  Here, **repeat**, **auto-fit**, **auto-fill**, and **auto-stretch** are keywords. **track-size** is the column width, which supports units including px, vp, %, or a valid number. The default unit is vp. **track-size** must include at least one valid column width.

  The **auto-fit** mode and **auto-stretch** mode support only one valid column width value for **track-size**, and in the **auto-stretch** mode, **track-size** supports only px, vp, and valid numbers, not %. The **auto-fill** mode supports one or more valid column widths, for example, **columnsTemplate('repeat(auto-fill, 20)')** and **columnsTemplate('repeat(auto-fill, 20 80px)')**.

  In a non-repeat template string, each item supports only the following three formats: 'number+fr', 'number+px', and 'number+%'. The vp unit is not supported (for example, **columnsTemplate('100vp 100vp')**). To automatically calculate the number of columns based on a fixed vp size, use **repeat(auto-fill, track-size)**.

  If this attribute is set to **'0fr'**, the column width is 0, and child components are not displayed. If this attribute is set to an invalid value, the child components are displayed in a fixed column.
- When **value** is of the **ItemFillPolicy** type, the number of columns is determined based on the [breakpoint type](../../../ui/arkts-layout-development-grid-layout.md#breakpoints) corresponding to the width of the **LazyVWaterFlowLayout** component. For example, when the **fillType** attribute of **ItemFillPolicy** is set to **PresetFillType.BREAKPOINT_DEFAULT**, two columns are displayed when the component width falls within the sm or smaller breakpoint interval, three columns when within the md breakpoint interval, and five columns when within the lg or larger breakpoint interval, with each column set to **1fr** (meaning each column takes up one equal portion of the available width).
- When **value** is set to **undefined**, the default value (one column) is restored.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters** 

| Name| Type  | Mandatory| Description                              |
| ------ | ------ | ---- | ---------------------------------- |
| value  | string \| [ItemFillPolicy](ts-types.md#itemfillpolicy22) \| undefined | Yes   | Number of columns, fixed column width, minimum column width value, or breakpoint fill policy of **LazyVWaterFlowLayout**. |

### columnsGap

columnsGap(value: LengthMetrics | undefined): T

Sets the gap between columns. The default value is **LengthMetrics.vp(0)**. If a value less than 0 is set, **LengthMetrics.vp(0)** is used. When used together with the **repeat(auto-stretch, track-size)** mode of [columnsTemplate](#columnstemplate), this value serves as the minimum column spacing, and the system automatically calculates the actual column gap and number of columns.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters** 

| Name| Type                        | Mandatory| Description                        |
| ------ | ---------------------------- | ---- | ---------------------------- |
| value  |  [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) \| undefined | Yes   | Spacing between columns.<br/>Default value: **LengthMetrics.vp(0)**<br/>Value range: [0, +∞)<br/>When the value is set to less than 0, it is handled as **LengthMetrics.vp(0)**.<br/>When the method input parameter is **undefined**, the value is restored to the default value **(LengthMetrics.vp(0))**. |

**Return value**

| Type| Description          |
| --- | -------------- |
| T | Current **LazyVWaterFlowLayout** component itself, used to support chained calls. |

### rowsGap

rowsGap(value: LengthMetrics | undefined): T

Sets the gap between rows. The default value is **LengthMetrics.vp(0)**. If a value less than 0 is set, **LengthMetrics.vp(0)** is used.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters** 

| Name| Type                        | Mandatory| Description                        |
| ------ | ---------------------------- | ---- | ---------------------------- |
| value  | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) \| undefined | Yes   | Spacing between rows.<br/>Default value: **LengthMetrics.vp(0)**<br/>Value range: [0, +∞)<br/>When the value is set to less than 0, it is handled as **LengthMetrics.vp(0)**.<br/>When the method input parameter is **undefined**, the default value **(LengthMetrics.vp(0))** is restored. |

**Return value**

| Type| Description          |
| --- | -------------- |
| T | Current **LazyVWaterFlowLayout** component itself, used to support chained calls. |

### header

header(builder: CustomBuilder | undefined): T

Sets the header component of the current **LazyVWaterFlowLayout**. If this API is not used, no header component is set by default. The sticky style of the header component takes effect only after being set through the [sticky](#sticky) attribute.

> **NOTE**
>
> The header component is located at the top of the container and is typically used to display titles, group descriptions, or other elements fixed before the content.
>
> When this component scrolls into the visible area along with the scroll container and the header stick-to-top mode is set through [sticky](#sticky), the header sticks to the top of the visible area of the scroll container.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                                     | Mandatory | Description                                                         |
| ------ | -------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| builder | [CustomBuilder](ts-types.md#custombuilder8) \| undefined | Yes   | Constructor of the header component.<br/>When the input parameter is **undefined**, the header component is not set. If a header component already exists, it will also be removed. |

**Return value**

| Type | Description           |
| --- | -------------- |
| T | Current **LazyVWaterFlowLayout** component itself, used to support chained calls. |

### footer

footer(builder: CustomBuilder | undefined): T

Sets the footer component of the current **LazyVWaterFlowLayout**. If this API is not used, no footer component is set by default. The sticky style of the footer component takes effect only after being set through the [sticky](#sticky) attribute.

> **NOTE**
>
> The footer component is located at the bottom of the container and is typically used to display supplementary information, loading status, or other elements fixed after the content.
>
> When this component scrolls into the visible area along with the scroll container and the footer stick-to-bottom mode is set through [sticky](#sticky), the footer sticks to the bottom of the visible area of the scroll container.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                 |
| ------ | ------ | ---- | ------------------------------------- |
| builder | [CustomBuilder](ts-types.md#custombuilder8) \| undefined | Yes | Constructor of the footer component.<br/>When the input parameter is **undefined**, the footer component is not set. If a footer component already exists, it will also be removed. |

**Return value**

| Type| Description          |
| --- | -------------- |
| T | Current **LazyVWaterFlowLayout** component itself, used to support chained calls. |

### sticky

sticky(sticky: StickyStyle | undefined): T

Sets the sticky style of [header](#header) and [footer](#footer).

When this component scrolls into the visible area with the scroll container, and the optional **sticky** attribute is set for header stick-to-top or footer stick-to-bottom, the header will stick to the top of the visible area of the scroll container, and the footer will stick to the bottom of the visible area of the scroll container. If **sticky** is not set, the header component does not stick to the top and the footer component does not stick to the bottom by default.

> **NOTE**
>
> Due to floating-point calculation precision, gaps may appear during scrolling after **sticky** is set. You can use [pixelRound](ts-universal-attributes-pixelRoundForComponent.md#pixelround) to specify downward pixel rounding for the current component to resolve this issue.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                                              | Mandatory | Description                                                         |
| ------ | ----------------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| sticky | [StickyStyle](ts-container-list.md#stickystyle9) \| undefined | Yes   | Sticking mode of the header component and the footer component. The **sticky** attribute can be set to **StickyStyle.Header** (the header component sticks to the top), **StickyStyle.Footer** (the footer component sticks to the bottom), **StickyStyle.BOTH** (supports both the header component sticking to the top and the footer component sticking to the bottom at the same time), or **StickyStyle.None** (the sticking effect is not enabled).<br/>When the input parameter is **undefined**, the default value **StickyStyle.None** is restored.<br/>When not set through this API, by default, the header component does not stick to the top and the footer component does not stick to the bottom. |

**Return value**

| Type | Description           |
| --- | -------------- |
| T | Current **LazyVWaterFlowLayout** component itself, used to support chained calls. |

## Events

In addition to the [universal events](ts-component-general-events.md), the following events are supported.

### onVisibleIndexesChange

onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined): T

Sets the **onVisibleIndexesChange** callback. When the indexes of child components in the visible area of **LazyVWaterFlowLayout** change, the callback is triggered, returning the start index and end index of the child components in the visible area.

> **NOTE**
>
> When the parent component sets the size in the main axis direction, **LazyVWaterFlowLayout** performs lazy loading according to the visible area of the parent component. In this case, in the **onVisibleIndexesChange** callback, **start** returns the index of the child component at the initial position of the current visible area, and **end** returns the index of the child component at the end position of the current visible area.
>
> When the parent component does not set the size in the main axis direction, **LazyVWaterFlowLayout** will be stretched by content, causing all child components to be loaded and laid out. In this case, in the **onVisibleIndexesChange** callback, **start** returns 0, and **end** returns the index of the last child component in the data source.
>
> When the lazy loading feature of this component is invalidated due to the preceding parent component configuration conditions, all child components will be loaded and laid out. In this case, in the **onVisibleIndexesChange** callback, **start** returns 0, and **end** returns the index of the last child component in the data source.
>
> The parent component here refers to the nearest **List**, Scroll, or WaterFlow component found upward from the current component. FlowItem, LazyColumnLayout, custom components, and NodeContainer serve only as intermediate encapsulation layers and are not considered the parent component here. For the specific meaning in other documents, refer to the corresponding content.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters** 

| Name| Type  | Mandatory| Description                                 |
| ------ | ------ | ---- | ------------------------------------- |
| callback  | [OnVisibleIndexesChangeCallback](ts-container-scrollable-common.md#onvisibleindexeschangecallback) \| undefined | Yes   | Callback invoked when the index of a child component in the visible area changes.<br/>When the input parameter is **undefined**, the listening is canceled. |

**Return value**

| Type | Description |
| --- | -------------- |
| T | Current **LazyVWaterFlowLayout** component itself, used to support chained calls. |

## Examples

### Example 1: Implementing Lazy-Loading Waterfall Layout

This example shows how to use the [Scroll](ts-container-scroll.md) and **LazyVWaterFlowLayout** components to implement the lazy-loading waterfall layout.

**MyDataSource** implements the **LazyForEach** data source API [IDataSource](ts-rendering-control-lazyforeach.md#idatasource), which is used to provide child components for **LazyVWaterFlowLayout** through **LazyForEach**. 

Since API version 26.0.0, the **LazyVWaterFlowLayout** component is supported.

<!--code_no_check-->
```ts
import { LengthMetrics, LazyVWaterFlowLayout, LazyVWaterFlowLayoutAttribute } from '@kit.ArkUI';
// MyDataSource is a custom data source class that implements the IDataSource API required by LazyForEach.
import { MyDataSource } from './MyDataSource';

@Entry
@Component
struct LazyVWaterFlowLayoutSample1 {
  private arr : MyDataSource<number> = new MyDataSource<number>();

  // Return a random height.
  private itemHeight(index: number): number {
    return 80 + (index * 37 % 121);
  }

  private itemColor(index: number): string {
    const colors: string[] = ['#FFE0B2', '#C8E6C9', '#BBDEFB', '#F8BBD0', '#D1C4E9', '#FFF9C4'];
    return colors[index % colors.length];
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
          console.info('LazyVWaterFlowLayout visible indexes: start: ' + start + ', end: ' + end);
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
    });
  }

  notifyDataAdd(index: number): void {
    this.listeners.forEach(listener => {
      listener.onDataAdd(index);
    });
  }

  notifyDataChange(index: number): void {
    this.listeners.forEach(listener => {
      listener.onDataChange(index);
    });
  }

  notifyDataDelete(index: number): void {
    this.listeners.forEach(listener => {
      listener.onDataDelete(index);
    });
  }

  notifyDataMove(from: number, to: number): void {
    this.listeners.forEach(listener => {
      listener.onDataMove(from, to);
    });
  }

  notifyDatasetChange(operations: DataOperation[]): void {
    this.listeners.forEach(listener => {
      listener.onDatasetChange(operations);
    });
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
    const deleteIndex = this.dataArray.length - 1;
    this.dataArray.pop();
    this.notifyDataDelete(deleteIndex);
  }

  public clearData(): void {
    this.dataArray = [];
    this.notifyDataReload();
  }
}
```
![scroll_lazyvwaterflowlayout.png](figures/scroll_lazyvwaterflowlayout.png)

### Example 2: Setting a Header or Footer Component and Sticky Styles

This example nests **LazyVWaterFlowLayout** inside [Scroll](ts-container-scroll.md), and implements sticky styles at the top and bottom of the waterfall layout through [header](#header), [footer](#footer), and [sticky](#sticky). During scrolling, the header sticks to the top of the visible area, and the footer sticks to the bottom of the visible area.

Since API version 26.0.0, the **header**, **footer**, and **sticky** attributes are newly supported.

<!--code_no_check-->
```ts
import { LengthMetrics, LazyVWaterFlowLayout, LazyVWaterFlowLayoutAttribute } from '@kit.ArkUI';
// MyDataSource is a custom data source class that implements the IDataSource API required by LazyForEach.
import { MyDataSource } from './MyDataSource';

@Entry
@Component
struct LazyVWaterFlowLayoutStickyDemo {
  private arr : MyDataSource<number> = new MyDataSource<number>();

  // Return a random height.
  private itemHeight(index: number): number {
    return 80 + (index * 37 % 121);
  }

  private itemColor(index: number): string {
    const colors: string[] = ['#FFE0B2', '#C8E6C9', '#BBDEFB', '#F8BBD0', '#D1C4E9', '#FFF9C4'];
    return colors[index % colors.length];
  }

  // Build the header component.
  @Builder
  HeaderBuilder() {
    Column() {
      Text('Header')
        .fontSize(16)
        .fontColor(Color.Black)
    }
    .height(50)
    .width('100%')
    .borderRadius(8)
    .backgroundColor('#BBDEFB')
    .justifyContent(FlexAlign.Center)
  }

  @Builder
  FooterBuilder() {
    Column() {
      Text('Footer')
        .fontSize(16)
        .fontColor(Color.Black)
    }
    .height(40)
    .width('100%')
    .borderRadius(8)
    .backgroundColor('#D1C4E9')
    .justifyContent(FlexAlign.Center)
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
        .header(this.HeaderBuilder)
        .footer(this.FooterBuilder)
        // Set the header and footer to stick at the same time.
        .sticky(StickyStyle.BOTH)
        .onVisibleIndexesChange((start: number, end: number) => {
          console.info('LazyVWaterFlowLayout visible indexes: start: ' + start + ', end: ' + end);
          // Scroll listening: load more data in advance when about to reach the bottom.
          if (end + 20 >= this.arr.totalCount()) {
            // Add 100 new data items to the data source.
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
![scroll_lazyvwaterflowlayout_header_footer.gif](figures/scroll_lazyvwaterflowlayout_header_footer.gif)

### Example 3: Setting Adaptive Column Count

This example uses [columnsTemplate](#columnstemplate) to set **repeat(auto-fill, track-size)** and **ItemFillPolicy**, implementing adaptive column count for **LazyVWaterFlowLayout**.

Since API version 26.0.0, the [columnsTemplate](#columnstemplate) interface is supported.

<!--code_no_check-->
```ts
import {
  LengthMetrics,
  LazyColumnLayout,
  LazyColumnLayoutAttribute,
  LazyVWaterFlowLayout,
  LazyVWaterFlowLayoutAttribute,
} from '@kit.ArkUI';
// MyDataSource is a custom data source class that implements the IDataSource API required by LazyForEach.
import { MyDataSource } from './MyDataSource';

@Entry
@Component
struct LazyVWaterFlowLayoutColumnsTemplateDemo {
  private autoFillData: MyDataSource<number> = new MyDataSource<number>();
  private breakpointData: MyDataSource<number> = new MyDataSource<number>();
  private breakpointPolicy: ItemFillPolicy = { fillType: PresetFillType.BREAKPOINT_DEFAULT };

  aboutToAppear(): void {
    // Initialize a fixed number of data items without loading when reaching the bottom.
    for (let i = 0; i < 18; i++) {
      this.autoFillData.pushData(i);
      this.breakpointData.pushData(i);
    }
  }

  private itemHeight(index: number): number {
    return 80 + (index * 37 % 121)
  }

  private itemColor(index: number): string {
    const colors: string[] = ['#CDE7FF', '#D8F5D0', '#FFE6A8', '#F8D7DA', '#E4D7FF', '#D2F4EA']
    return colors[index % colors.length]
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
    this.ModeTitle('repeat(auto-fill, 96vp)',
      'The fixed column width is 96vp, and LazyVWaterFlowLayout automatically calculates the number of waterfall flow columns based on the available width.')
  }

  @Builder
  BreakpointHeader() {
    this.ModeTitle('ItemFillPolicy: BREAKPOINT_DEFAULT',
      'Determine the number of columns based on the breakpoint type corresponding to the component width: 2 columns for sm and below, 3 columns for md, and 5 columns for lg and above.')
  }

  @Builder
  WaterFlowItemBuilder(item: number) {
    Text('item ' + item)
      .height(this.itemHeight(item))
      .width('100%')
      .borderRadius(8)
      .backgroundColor(this.itemColor(item))
      .fontColor('#182230')
      .textAlign(TextAlign.Center)
  }

  build() {
    Column() {
      Scroll() {
        LazyColumnLayout() {
          // repeat(auto-fill, 96vp): the fixed column width is 96vp, and the number of waterfall flow columns is automatically calculated based on the available width.
          LazyVWaterFlowLayout() {
            LazyForEach(this.autoFillData, (item: number) => {
              this.WaterFlowItemBuilder(item)
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

          // ItemFillPolicy: determine the number of columns based on the breakpoint type corresponding to the component width.
          LazyVWaterFlowLayout() {
            LazyForEach(this.breakpointData, (item: number) => {
              this.WaterFlowItemBuilder(item)
            })
          }
          .columnsTemplate(this.breakpointPolicy)
          .rowsGap(LengthMetrics.vp(8))
          .columnsGap(LengthMetrics.vp(8))
          .header(this.BreakpointHeader)
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
<!--Del--> <!--DelEnd-->
