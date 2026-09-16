# @ohos.arkui.components.ArkLazyDynamicLayout

## 导入模块

```TypeScript
import { LazyDynamicLayout, LazyDynamicLayoutAttribute } from '@kit.ArkUI';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [LazyDynamicLayout](arkts-arkui-arkui-components-arklazydynamiclayout-lazydynamiclayout-f.md) | 定义LazyDynamicLayout组件。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [LazyDynamicLayoutAttribute](arkts-arkui-arkui-components-arklazydynamiclayout-lazydynamiclayoutattribute-c.md) | 定义LazyDynamicLayout组件。 |

### 常量

| 名称 | 说明 |
| --- | --- |
| [LazyDynamicLayoutInstance](arkts-arkui-arkui-components-arklazydynamiclayout-con.md#lazydynamiclayoutinstance) | 定义LazyDynamicLayout组件实例。 |

## 示例

```TypeScript
### 示例1（实现懒加载自定义布局）

通过[List](ts-container-list.md)和LazyDynamicLayout组件实现自定义的懒加载列表布局，并通过onVisibleIndexesChange在可视区域发生变化时回调索引。

LazyListLayout实现了一个自定义懒加载列表布局算法，布局算法中通过setAdjustedOffset接口，确保子组件布局间隔变化时可视区域内第一个子组件的位置不变。

MyDataSource实现了[LazyForEach](ts-rendering-control-lazyforeach.md)数据源接口[IDataSource](ts-rendering-control-lazyforeach.md#idatasource)，用于通过LazyForEach给LazyDynamicLayout提供子组件。

从API版本26.0.0开始，新增LazyDynamicLayout组件。
```

```TypeScript
// LazyListLayout.ets
// 导入布局相关的接口和类
import { LayoutConstraint, LazyLayoutHelper, LazyCustomLayoutAlgorithm, ExpandMode, ChildrenCountMode,
  LazyLayoutDirection } from '@kit.ArkUI';

// 自定义懒加载列表布局算法，继承自LazyCustomLayoutAlgorithm
export class LazyListLayout extends LazyCustomLayoutAlgorithm {
  private itemHeight: number = 320; // 每个列表项的高度（像素）
  private totalHeight: number = 0; // 列表总高度
  private childCnt: number = 0; // 子组件总数
  private startIndex: number = -1; // 当前可视区域的起始索引
  private endIndex: number = -1; // 当前可视区域的结束索引
  private space: number = 0; // 当前间隔大小
  private prevSpace: number = 0; // 上一次的间隔大小
  selfNode?: FrameNode; // 自身FrameNode节点引用

  // 构造函数，接收列表项高度参数
  constructor(itemHeight: number) {
    super();
    this.itemHeight = itemHeight;
  }

  // 设置列表项间隔大小
  setSpace(value: number): void {
    if (this.space == value) {
      return;
    }
    this.prevSpace = this.space;
    this.space = value;
    // 触发布局重新计算
    this.selfNode?.setNeedsLayout();
  }

  // 测量方法，测量子组件和计算组件大小
  onMeasure(self: FrameNode, constraint: LayoutConstraint, helper?: LazyLayoutHelper): void {
    // 获取子组件总数，getChildrenCount接口使用ChildrenCountMode.ALL_NOT_EXPAND，避免获取子组件总数时全量加载子组件导致懒加载失效。
    this.childCnt = self.getChildrenCount(ChildrenCountMode.ALL_NOT_EXPAND);
    this.selfNode = self;
    // 如果没有懒加载helper，则测量所有子组件
    if (!helper) {
      this.measureAllChildren(self, constraint);
      self.setMeasuredSize({ width: constraint.maxSize.width, height: this.totalHeight });
      this.prevSpace = this.space;
      return;
    }

    // 获取可视区域的起始和结束位置
    let viewStart = helper.getViewStart();
    let viewEnd = helper.getViewEnd();
    let prevTotalHeight = this.totalHeight;
    // 计算列表总高度：子组件数量 * (子组件高度 + 间隔) - 最后一个间隔
    this.totalHeight = Math.max(this.childCnt * (this.itemHeight + this.space) - this.space, 0);
    // 正向布局（从上到下）
    if (helper.getLazyLayoutDirection() == LazyLayoutDirection.FORWARD) {
      // 如果间隔变化，需要调整偏移量以保持可视区域第一个子组件位置不变
      if (this.startIndex > 0 && this.startIndex < this.childCnt && this.prevSpace != this.space) {
        let adjustStartOffset = this.startIndex * (this.prevSpace - this.space);
        console.info(`Top setAdjustedOffset:${adjustStartOffset}`);
        helper.setAdjustedOffset(adjustStartOffset);
        viewStart -= adjustStartOffset;
        viewEnd -= adjustStartOffset;
      }
    } else {
      // 反向布局（从下到上）
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

    // 如果可视区域不在内容范围内，清空索引
    if (viewStart > this.totalHeight || viewEnd < 0 || this.childCnt == 0) {
      this.startIndex = -1;
      this.endIndex = -1;
      this.totalHeight = Math.max(this.childCnt * (this.itemHeight + this.space) - this.space, 0);
      self.setMeasuredSize({ width: constraint.maxSize.width, height: this.totalHeight });
      return;
    }

    // 计算可视区域的起始和结束索引
    let prevStartIndex = this.startIndex;
    let prevEndIndex = this.endIndex;
    this.startIndex = Math.floor(viewStart / (this.itemHeight + this.space));
    this.startIndex = Math.max(this.startIndex, 0);
    this.endIndex = Math.floor(viewEnd / (this.itemHeight + this.space));
    this.endIndex = Math.min(this.endIndex, this.childCnt - 1);

    // 测量可视区域内的子组件
    for (let i = this.startIndex; i <= this.endIndex; i++) {
      // 调用getChild时使用ExpandMode.LAZY_NOT_EXPAND参数，避免获取子组件时全量加载导致懒加载失效。
      let child = self.getChild(i, ExpandMode.LAZY_NOT_EXPAND);
      if (child) {
        child.measure(constraint);
      } else {
        console.error(`Get child[${i}] error`);
      }
    }

    // 收集需要回收的子组件索引
    let recycleList: number[] = [];
    // 如果起始索引后移，回收之前的子组件
    if (prevStartIndex < this.startIndex) {
      for (let i = prevStartIndex; i < this.startIndex; i++) {
        recycleList.push(i);
      }
    }
    // 如果结束索引前移，回收之后的子组件
    if (prevEndIndex > this.endIndex) {
      for (let i = this.endIndex + 1; i <= prevEndIndex; i++) {
        recycleList.push(i);
      }
    }
    // 将不再可见的子组件设置为非激活态
    helper.setChildrenInactive(recycleList);
    // 设置测量后的尺寸
    self.setMeasuredSize({ width: constraint.maxSize.width, height: this.totalHeight });
  }

  // 测量所有子组件（非懒加载模式）
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

  // 布局方法，确定每个子组件的位置
  onLayout(self: FrameNode): void {
    if (this.childCnt == 0) {
      return;
    }
    // 布局可视区域内的子组件
    for (let i = this.startIndex; i <= this.endIndex; i++) {
      let child = self.getChild(i, ExpandMode.LAZY_NOT_EXPAND);

      child?.layout({ x: 0, y: i * (this.itemHeight + this.space) });
    }
  }
}
```

```TypeScript
// MyDataSource.ets
// 基础数据源类，实现IDataSource接口
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
