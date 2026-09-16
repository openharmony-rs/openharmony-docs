# @ohos.arkui.components.ArkLazyColumnLayout

## 导入模块

```TypeScript
import { LazyColumnLayout, LazyColumnLayoutAttribute } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [LazyColumnLayoutAttribute](arkts-arkui-arkui-components-arklazycolumnlayout-lazycolumnlayoutattribute-c.md) | 定义懒加载列布局属性。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [LazyColumnLayoutInterface](arkts-arkui-arkui-components-arklazycolumnlayout-lazycolumnlayoutinterface-i.md) | 定义懒加载列布局组件。 |

### 常量

| 名称 | 说明 |
| --- | --- |
| [LazyColumnLayout](arkts-arkui-arkui-components-arklazycolumnlayout-con.md#lazycolumnlayout) | 定义懒式列布局组件。 |
| [LazyColumnLayoutInstance](arkts-arkui-arkui-components-arklazycolumnlayout-con.md#lazycolumnlayoutinstance) | 定义懒加载列布局组件实例。 |

## 示例

```TypeScript
### 示例1（实现懒加载线性布局）

通过[Scroll](ts-container-scroll.md)和LazyColumnLayout组件实现懒加载线性布局，并通过onVisibleIndexesChange在可视区域发生变化时回调起始和结束索引值。

从API版本26.0.0开始，新增支持LazyColumnLayout组件和onVisibleIndexesChange事件。


```

```TypeScript
### 示例2（设置头部组件或尾部组件及吸附效果）

该示例通过[Scroll](ts-container-scroll.md)嵌套LazyColumnLayout，并通过header、footer、sticky实现顶部和底部吸附效果。滚动过程中header吸附在可视区域顶部，footer吸附在可视区域底部。

从API版本26.0.0开始，新增支持header、footer和sticky属性。
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
