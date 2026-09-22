# @ohos.arkui.components.ArkLazyDynamicLayout

## Modules to Import

```TypeScript
import { LazyDynamicLayout, LazyDynamicLayoutAttribute } from '@kit.ArkUI';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [LazyDynamicLayout](arkts-arkui-arkui-components-arklazydynamiclayout-lazydynamiclayout-f.md) | Defines LazyDynamicLayout Component. |

### Classes

| Name | Description |
| --- | --- |
| [LazyDynamicLayoutAttribute](arkts-arkui-arkui-components-arklazydynamiclayout-lazydynamiclayoutattribute-c.md) | Defines the LazyDynamicLayout attribute functions. |

### Constants

| Name | Description |
| --- | --- |
| [LazyDynamicLayoutInstance](arkts-arkui-arkui-components-arklazydynamiclayout-con.md#lazydynamiclayoutinstance) | Defines LazyDynamicLayout Component instance. |

## Examples

### Example 1: Implementing Lazy-Loading Custom Layout

A custom lazy-loading list layout is implemented through the [List](ts-container-list.md) and LazyDynamicLayout components, and the index is called back through onVisibleIndexesChange when the visible area changes.

LazyListLayout implements a custom lazy loading list layout algorithm. In the layout algorithm, the [setAdjustedOffset](arkts-arkui-lazylayoutalgorithm-lazylayouthelper-c.md#setadjustedoffset) API is used to ensure that the position of the first child component in the visible area remains unchanged when the spacing between child components changes.

MyDataSource implements the [LazyForEach](ts-rendering-control-lazyforeach.md) data source API [IDataSource](ts-rendering-control-lazyforeach.md#idatasource), which is used to provide child components to LazyDynamicLayout through LazyForEach.

The LazyDynamicLayout component is added since API version 26.0.0.

```TypeScript
import { LazyDynamicLayout, LazyDynamicLayoutAttribute } from '@kit.ArkUI';
import { MyDataSource } from './MyDataSource';
import { LazyListLayout } from './LazyListLayout';

// Custom lazy-loading list layout component.
@Component
struct MyLazyListLayout {
  // Spacing size. Use @Watch to monitor changes, triggering the onSpaceChange method when changed.
  @Prop @Watch('onSpaceChange') space: number;
  arr: MyDataSource<string> = new MyDataSource<string>();
  private itemHeight: number = 100;
  // Lazy layout algorithm instance. Convert the height to pixel units.
  private lazyAlgorithm: LazyListLayout = new LazyListLayout(this.getUIContext().vp2px(this.itemHeight));

  // Update the spacing value in the layout algorithm when the spacing changes.
  onSpaceChange(): void {
    this.lazyAlgorithm.setSpace(this.getUIContext().vp2px(this.space));
  }

  aboutToAppear(): void {
    this.lazyAlgorithm.setSpace(this.getUIContext().vp2px(this.space));
  }

  build() {
    // Use the LazyDynamicLayout component and pass in the lazy layout algorithm.
    LazyDynamicLayout(this.lazyAlgorithm) {
      LazyForEach(this.arr, (item: string) => {
        Text(item)
          .height(this.itemHeight)
          .width('100%')
          .borderRadius(8)
          .backgroundColor('#E0E0FF')
          .padding(10)
      })
    }
    // Listen for changes in the indexes of child components in the visible area.
    .onVisibleIndexesChange((child: number[]) => {
      console.info(`onVisibleIndexesChange:start:${child}`);
    })
  }
}

// Define the group data interface.
interface GroupData {
  title: string;
  data: MyDataSource<string>;
}

// Main page component.
@Entry
@Component
struct CustomListLayoutTest {
  @State groupArr: GroupData[] = []; // Group data array.
  @State space: number = 5; // List item spacing.

  aboutToAppear(): void {
    for (let i = 0; i < 3; i++) {
      let data = new MyDataSource<string>();
      for (let j = 0; j < 10; j++) {
        data.pushData('item' + j.toString());
      }
      this.groupArr.push({ title: 'group' + i.toString(), data: data });
    }
  }

  build() {
    Stack({ alignContent: Alignment.Bottom }) {
      List() {
        ForEach(this.groupArr, (item: GroupData) => {
          ListItem() {
            Text(item.title).margin({ top: 20, bottom: 8 })
          }
          // Use the custom lazy-loading layout component.
          MyLazyListLayout({ arr: item.data, space: this.space })
        })
      }
      .layoutWeight(1)
      .padding({ left: 12, right: 12 })
      .height('100%')
      .width('100%')

      Button('Space:' + this.space.toString())
        .onClick(() => {
          // Switch the spacing between 5 and 10, and keep the position of the first child component in the visible area unchanged before and after the switch.
          this.space = this.space === 5 ? 10 : 5;
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

```TypeScript
// LazyListLayout.ets
// Import layout-related interfaces and classes.
import { LayoutConstraint, LazyLayoutHelper, LazyCustomLayoutAlgorithm, ExpandMode, ChildrenCountMode,
  LazyLayoutDirection } from '@kit.ArkUI';

// Custom lazy-loading list layout algorithm, inherited from LazyCustomLayoutAlgorithm.
export class LazyListLayout extends LazyCustomLayoutAlgorithm {
  private itemHeight: number = 320; // Height of each list item (in pixels).
  private totalHeight: number = 0; // Total height of the list.
  private childCnt: number = 0; // Total number of child components.
  private startIndex: number = -1; // Start index of the current visible area.
  private endIndex: number = -1; // End index of the current visible area.
  private space: number = 0; // Current spacing size.
  private prevSpace: number = 0; // Previous spacing value.
  selfNode?: FrameNode; // Reference to the own FrameNode.

  // Constructor that receives the list item height parameter.
  constructor(itemHeight: number) {
    super();
    this.itemHeight = itemHeight;
  }

  // Set the list item spacing.
  setSpace(value: number): void {
    if (this.space == value) {
      return;
    }
    this.prevSpace = this.space;
    this.space = value;
    // Trigger layout recalculation.
    this.selfNode?.setNeedsLayout();
  }

  // Measure child components and calculate the component size.
  onMeasure(self: FrameNode, constraint: LayoutConstraint, helper?: LazyLayoutHelper): void {
    // Obtain the total number of child components. The getChildrenCount API uses ChildrenCountMode.ALL_NOT_EXPAND to avoid full loading of child components when obtaining the total count, which would cause lazy loading to fail.
    this.childCnt = self.getChildrenCount(ChildrenCountMode.ALL_NOT_EXPAND);
    this.selfNode = self;
    // If no lazy loading helper is available, measure all child components.
    if (!helper) {
      this.measureAllChildren(self, constraint);
      self.setMeasuredSize({ width: constraint.maxSize.width, height: this.totalHeight });
      this.prevSpace = this.space;
      return;
    }

    // Obtain the start and end positions of the visible area.
    let viewStart = helper.getViewStart();
    let viewEnd = helper.getViewEnd();
    let prevTotalHeight = this.totalHeight;
    // Calculate the total list height: child component count * (child component height + spacing) - last spacing.
    this.totalHeight = Math.max(this.childCnt * (this.itemHeight + this.space) - this.space, 0);
    // Forward layout (top to bottom).
    if (helper.getLazyLayoutDirection() == LazyLayoutDirection.FORWARD) {
      // If the spacing changes, adjust the offset to keep the position of the first child component in the visible area unchanged.
      if (this.startIndex > 0 && this.startIndex < this.childCnt && this.prevSpace != this.space) {
        let adjustStartOffset = this.startIndex * (this.prevSpace - this.space);
        console.info(`Top setAdjustedOffset:${adjustStartOffset}`);
        helper.setAdjustedOffset(adjustStartOffset);
        viewStart -= adjustStartOffset;
        viewEnd -= adjustStartOffset;
      }
    } else {
      // Reverse layout (bottom to top).
      if (this.endIndex >= 0 && this.endIndex < this.childCnt - 1 && this.prevSpace != this.space) {
        let adjustEndOffset = (this.childCnt - 1 - this.endIndex) * (this.space - this.prevSpace);
        let adjustStartOffset = this.totalHeight - prevTotalHeight - adjustEndOffset;
        console.info(`Bottom setAdjustedOffset:${adjustEndOffset}`);
        helper.setAdjustedOffset(adjustEndOffset);
        viewStart += adjustStartOffset;
        viewEnd += adjustStartOffset;
      } else if (this.totalHeight != prevTotalHeight) {
        let adjustOffset = this.totalHeight - prevTotalHeight;
        viewStart += adjustOffset;
        viewEnd += adjustOffset;
      }
    }
    this.prevSpace = this.space;

    // If the visible area is not within the content range, clear the indexes.
    if (viewStart > this.totalHeight || viewEnd < 0 || this.childCnt == 0) {
      this.startIndex = -1;
      this.endIndex = -1;
      this.totalHeight = Math.max(this.childCnt * (this.itemHeight + this.space) - this.space, 0);
      self.setMeasuredSize({ width: constraint.maxSize.width, height: this.totalHeight });
      return;
    }

    // Calculate the start and end indexes of the visible area.
    let prevStartIndex = this.startIndex;
    let prevEndIndex = this.endIndex;
    this.startIndex = Math.floor(viewStart / (this.itemHeight + this.space));
    this.startIndex = Math.max(this.startIndex, 0);
    this.endIndex = Math.floor(viewEnd / (this.itemHeight + this.space));
    this.endIndex = Math.min(this.endIndex, this.childCnt - 1);

    // Measure child components in the visible area.
    for (let i = this.startIndex; i <= this.endIndex; i++) {
      // Use the ExpandMode.LAZY_NOT_EXPAND parameter when calling getChild to avoid full loading of child components, which would cause lazy loading to fail.
      let child = self.getChild(i, ExpandMode.LAZY_NOT_EXPAND);
      if (child) {
        child.measure(constraint);
      } else {
        console.error(`Get child[${i}] error`);
      }
    }

    // Collect the indexes of child components to be recycled.
    let recycleList: number[] = [];
    // If the start index moves backward, recycle the previous child components.
    if (prevStartIndex < this.startIndex) {
      for (let i = prevStartIndex; i < this.startIndex; i++) {
        recycleList.push(i);
      }
    }
    // If the end index moves forward, recycle the subsequent child components.
    if (prevEndIndex > this.endIndex) {
      for (let i = this.endIndex + 1; i <= prevEndIndex; i++) {
        recycleList.push(i);
      }
    }
    // Set the child components that are no longer visible to the inactive state.
    helper.setChildrenInactive(recycleList);
    // Set the measured size.
    self.setMeasuredSize({ width: constraint.maxSize.width, height: this.totalHeight });
  }

  // Measure all child components (non-lazy loading mode).
  private measureAllChildren(self: FrameNode, constraint: LayoutConstraint): void {
    for (let i = 0; i < this.childCnt; i++) {
      let child = self.getChild(i, ExpandMode.LAZY_NOT_EXPAND);
      if (child) {
        child.measure(constraint);
      } else {
        console.error(`Get child[${i}] error`);
      }
    }

    this.startIndex = 0;
    this.endIndex = this.childCnt - 1;
    this.totalHeight = Math.max(this.childCnt * (this.itemHeight + this.space) - this.space, 0);
  }

  // Layout method that determines the position of each child component.
  onLayout(self: FrameNode): void {
    if (this.childCnt == 0) {
      return;
    }
    // Layout the child components within the visible area.
    for (let i = this.startIndex; i <= this.endIndex; i++) {
      let child = self.getChild(i, ExpandMode.LAZY_NOT_EXPAND);

      child?.layout({ x: 0, y: i * (this.itemHeight + this.space) });
    }
  }
}
```

```TypeScript
// MyDataSource.ets
// Basic data source class that implements the IDataSource interface.
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
    if (this.dataArray.length > 0) {
      this.dataArray.pop();
      this.notifyDataDelete(this.dataArray.length);
    }
  }

  public clearData(): void {
    this.dataArray = [];
    this.notifyDataReload();
  }
}
```
