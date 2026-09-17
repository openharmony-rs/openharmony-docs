# @ohos.arkui.components.ArkLazyColumnLayout

## Modules to Import

```TypeScript
import { LazyColumnLayout, LazyColumnLayoutAttribute } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [LazyColumnLayoutAttribute](arkts-arkui-arkui-components-arklazycolumnlayout-lazycolumnlayoutattribute-c.md) | Defines the lazy column layout attribute. |

### Interfaces

| Name | Description |
| --- | --- |
| [LazyColumnLayoutInterface](arkts-arkui-arkui-components-arklazycolumnlayout-lazycolumnlayoutinterface-i.md) | Defines the lazy column layout component. |

### Constants

| Name | Description |
| --- | --- |
| [LazyColumnLayout](arkts-arkui-arkui-components-arklazycolumnlayout-con.md#lazycolumnlayout) | Defines the lazy column layout component. |
| [LazyColumnLayoutInstance](arkts-arkui-arkui-components-arklazycolumnlayout-con.md#lazycolumnlayoutinstance) | Defines the lazy column layout component instance. |

## Examples

```TypeScript
### Example 1: Implementing Lazy-Loading Linear Layout

This example demonstrates how to use the [Scroll](ts-container-scroll.md) and LazyColumnLayout components to implement lazy-loading linear layout, and how to use onVisibleIndexesChange to return the start and end indexes when the viewport changes.

Since API version 26.0.0, the LazyColumnLayout component and the onVisibleIndexesChange event are supported.


```

```TypeScript
### Example 2: Setting Header or Footer Components and Sticky Styles

This example nests LazyColumnLayout in [Scroll](ts-container-scroll.md) and implements top and bottom sticky styles through header, footer, and sticky. During scrolling, the header sticks to the top of the viewport and the footer sticks to the bottom of the viewport.

Since API version 26.0.0, the header, footer, and sticky attributes are supported.
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
