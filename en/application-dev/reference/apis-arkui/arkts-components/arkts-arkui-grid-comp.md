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

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scroller | [Scroller](arkts-arkui-scroller-c.md) | No | Controller, which can be bound to scrollable components.<br>**NOTE:** <br>It cannot be bound to the same scrolling control object as other scrollable components, such as ArcList, List, Grid, Scroll, and WaterFlow. |
| layoutOptions | [GridLayoutOptions](arkts-arkui-gridlayoutoptions-i.md) | No | Grid layout options. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [ComputedBarAttribute](arkts-arkui-computedbarattribute-i.md) | Provides information about the position and length of the scrollbar. |
| [GridLayoutOptions](arkts-arkui-gridlayoutoptions-i.md) | Defines the grid layout options. In this API, **irregularIndexes** and **onGetIrregularSizeByIndex** can be used for grids where either **rowsTemplate** or **columnsTemplate** is set. These properties allow you to specify an index array and set the number of rows and columns to be occupied by a grid item at the specified index. For details about the usage, see [Example 3](../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#example-3-implementing-a-scrollable-grid-with-grid-items-spanning-rows-and-columns). On the other hand, **onGetRectByIndex** can be used for grids where both **rowsTemplate** and **columnsTemplate** are set. It allows you to specify the position and size for the grid item at the specified index. For details about the usage, see [Example 1](../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#example-1-creating-a-fixed-row-and-column-grid-layout). |
| [StartLineInfo](arkts-arkui-startlineinfo-i-sys.md) | Define start line info used in GridLayoutOptions. |
| [UIGridEvent](arkts-arkui-uigridevent-i.md) | Represents the return value of the [getEvent('Grid')](../arkts-apis/arkts-arkui-typenode-getevent-f.md) method in **frameNode**, which can be used to set scroll events for a **Grid** node. |

### Types

| Name | Description |
| --- | --- |
| [OnGetStartIndexByIndexCallback](arkts-arkui-ongetstartindexbyindexcallback-t-sys.md) | Defines the callback type used in onGetStartIndexByIndex of GridLayoutOptions. |
| [OnGetStartIndexByOffsetCallback](arkts-arkui-ongetstartindexbyoffsetcallback-t-sys.md) | Defines the callback type used in onGetStartIndexByOffset of GridLayoutOptions. |
| [OnGridScrollIndexCallback](arkts-arkui-ongridscrollindexcallback-t.md) | Represents a callback for item changes in the visible area of the **Grid** component. |

### Enums

| Name | Description |
| --- | --- |
| [GridDirection](arkts-arkui-griddirection-e.md) | Enumerates the main axis layout directions. |
| [GridItemAlignment](arkts-arkui-griditemalignment-e.md) | Enumerates the alignment modes of grid items. |

## Examples

```TypeScript
### Example 1: Creating a Fixed Row and Column Grid Layout

You can use the onGetRectByIndex function in the [GridLayoutOptions](arkts-arkui-gridlayoutoptions-i.md) to specify the position and size of a grid item.
```

```TypeScript
### Example 2: Implementing a Scrollable Grid with Scroll Events

This example shows a scrollable grid with all its scrolling attributes and events specified.

GridDataSource implements the LazyForEach data source API [IDataSource](ts-rendering-control-lazyforeach.md#idatasource), which is used to provide child components for Grid through LazyForEach.
```

```TypeScript

```

```TypeScript
### Example 3: Implementing a Scrollable Grid with Grid Items Spanning Rows and Columns

[GridLayoutOptions](arkts-arkui-gridlayoutoptions-i.md): irregularIndexes and onGetIrregularSizeByIndex.

For details about GridDataSource and the complete code, see [Example 2: Implementing a Scrollable Grid with Scroll Events](#example-2-implementing-a-scrollable-grid-with-scroll-events).


```

```TypeScript
### Example 4: Implementing Nested Scrolling in a Grid

This example demonstrates how to use [nestedScroll](#nestedscroll10) and [onScrollFrameBegin](#onscrollframebegin10).

For details about GridDataSource and the complete code, see [Example 2: Implementing a Scrollable Grid with Scroll Events](#example-2-implementing-a-scrollable-grid-with-scroll-events).


```

```TypeScript
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


```

```TypeScript
### Example 6: Implementing Adaptive Grid Layout

This example demonstrates how to use [layoutDirection](#layoutdirection8), [maxCount](#maxcount8), [minCount](#mincount8), and [cellLength](arkts-arkui-grid-comp-attribute.md#celllength).

For details about GridDataSource and the complete code, see [Example 2: Implementing a Scrollable Grid with Scroll Events](#example-2-implementing-a-scrollable-grid-with-scroll-events).


```

```TypeScript
### Example 7: Dynamically Adjusting the Number of Grid Columns with a Pinch Gesture

This example demonstrates how to adjust the number of columns in the grid with a pinch gesture using two fingers.

For details about GridDataSource and the complete code, see [Example 2: Implementing a Scrollable Grid with Scroll Events](#example-2-implementing-a-scrollable-grid-with-scroll-events).


```

```TypeScript
### Example 8: Using Adaptive Column Count Settings

This example shows the usage of auto-fill, auto-fit, and auto-stretch in [columnsTemplate](#columnstemplate).


```

```TypeScript
### Example 9: Setting Grid Item Heights Based on the Tallest Item in the Current Row

This example implements a grid that contains two columns. The grid item in each column consists of two Column components with determined heights and one Text component with an undetermined height.

By default, the heights of the left and right grid items may differ; however, after the grid's [alignItems](#alignitems12) attribute is set to GridItemAlignment.STRETCH, the grid item with a shorter height in a row will adopt the height of the taller grid item, aligning their heights within the same row.

For details about GridDataSource and the complete code, see [Example 2: Implementing a Scrollable Grid with Scroll Events](#example-2-implementing-a-scrollable-grid-with-scroll-events).


```

```TypeScript
### Example 10: Setting Edge Fading

This example demonstrates how to enable the edge fading effect using [fadingEdge](ts-container-scrollable-common.md#fadingedge14).

For details about GridDataSource and the complete code, see [Example 2: Implementing a Scrollable Grid with Scroll Events](#example-2-implementing-a-scrollable-grid-with-scroll-events).


```

```TypeScript
### Example 11: Setting the Single-Side Edge Effect

This example uses the [edgeEffect](#edgeeffect10) API to set the single-edge effect for the Grid component.

For details about GridDataSource and the complete code, see [Example 2: Implementing a Scrollable Grid with Scroll Events](#example-2-implementing-a-scrollable-grid-with-scroll-events).


```

```TypeScript
### Example 12: Moving Focus with Wrap by Arrow Keys

In API version 20 and later versions, this example uses the [focusWrapMode](#focuswrapmode20) API to implement the effect of line-wrapping focus navigation with arrow keys in the Grid component.


```

```TypeScript
### Example 13: Setting Scrolling Events

This example obtains a [UIGridEvent](arkts-arkui-uigridevent-i.md) instance via getEvent('Grid') on a FrameNode and sets scroll event callbacks for a Grid component. This approach is intended for scenarios where the page code cannot be directly modified to use declarative callbacks.

The UIGridEvent API is added since API version 19.
```

```TypeScript
### Example 14: Scrolling to a Specified Position

This example uses the [scrollToIndex](ts-container-scroll.md#scrolltoindex) API to scroll the Grid component to a specified position.

For details about GridDataSource and the complete code, see [Example 2: Implementing a Scrollable Grid with Scroll Events](#example-2-implementing-a-scrollable-grid-with-scroll-events).


```

```TypeScript
### Example 15: Implementing Panning Selection in Grid

This example uses the [PanGesture](./ts-basic-gestures-pangesture.md#pangesture-1) API to implement the effect of panning while selecting items in a Grid component.

For details about GridDataSource and the complete code, see [Example 2: Implementing a Scrollable Grid with Scroll Events](#example-2-implementing-a-scrollable-grid-with-scroll-events).


```

```TypeScript
### Example 16: Customizing the Drag Effect for GridItem

This example uses the [gesture](./ts-gesture-settings.md#gesture) API to customize the drag effect for the GridItem component.


```

```TypeScript
### Example 17: Dragging Grid Items with Drag Events

This example demonstrates dragging GridItem components to the Grid component's edges to trigger automatic scrolling, implemented through [drag events](./ts-universal-events-drag-drop.md).

For details about GridDataSource and the complete code, see [Example 2: Implementing a Scrollable Grid with Scroll Events](#example-2-implementing-a-scrollable-grid-with-scroll-events).


```

```TypeScript
### Example 18: Configuring the Number of Columns in the Grid Component Based on Breakpoints

In API version 22 and later versions, this example shows how to configure the number of columns in the Grid component based on breakpoints.

When the grid width is within the breakpoint range of sm or smaller, two columns are displayed.



When the grid width is within the breakpoint range of md, three columns are displayed.



When the grid width is within the breakpoint range of lg or larger, five columns are displayed.


```

```TypeScript
### Example 19: Obtaining the Total Content Size

This example demonstrates how to obtain the total content size. This functionality is supported since API version 22.

For details about GridDataSource and the complete code, see [Example 2: Implementing a Scrollable Grid with Scroll Events](#example-2-implementing-a-scrollable-grid-with-scroll-events).


```

```TypeScript
### Example 20: Setting the Multi-selection Gather Animation

This example enables the multi-select gather animation switch of the Grid to implement the effect of gathering the selected GridItem items within the display range through [bindContextMenu](ts-universal-attributes-menu.md#bindcontextmenu8) when a context menu is popped up by long pressing a GridItem.

Since API version 23, the [editModeOptions](#editmodeoptions23) API is added to the Grid component to set the multi-selection gather animation switch.

For details about GridDataSource and the complete code, see [Example 2: Implementing a Scrollable Grid with Scroll Events](#example-2-implementing-a-scrollable-grid-with-scroll-events).


```

```TypeScript
### Example 21: Implementing Swipe-based Multi-Selection

This example uses the two-way binding of  and the  event to listen for the notification of entering the multi-select mode by swiping with two fingers on the Grid, implementing the effect of selecting while swiping on the Grid.

Since API version 26.0.0, the Grid component adds the [enableEditMode](#enableeditmode) API and the [onEditModeChange](#oneditmodechange) event.

For details about GridDataSource and the complete code, see [Example 2: Implementing a Scrollable Grid with Scroll Events](#example-2-implementing-a-scrollable-grid-with-scroll-events).


```

```TypeScript
### Example 22: Dragging with OnMove

Since API version 26.0.0, this example demonstrates the effect of drag sorting using the [onMove](./ts-universal-attributes-drag-sorting.md#onmove) API of LazyForEach in the Grid. It supports triggering automatic scrolling of the Grid when dragging to the edge, and the Grid contains nodes that span rows and columns.
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
