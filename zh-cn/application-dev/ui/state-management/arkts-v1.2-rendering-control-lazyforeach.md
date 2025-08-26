# ArkTS1.2 LazyForEach迁移规范

本指南介绍ArkTS1.2语言中LazyForEach组件的功能变更和迁移规范。完整Demo见[ArkTS1.2的写法差异示例](#arkts12的写法差异示例)。

> **说明：**
>
> 从API version 20起引入ArkTS1.2。

## 迁移说明

- ArkTS1.2需要加入模块导入语句：
  ```ts
  import { LazyForEach, IDataSource, DataChangeListener } from '@ohos.arkui.component';
  // 如果使用listener.onDatasetChange()进行批量数据修改，按需import以下DataOperation
  import { DataOperation, DataOperationType, DataAddOperation, DataDeleteOperation, DataChangeOperation, DataMoveOperation, DataExchangeOperation, DataReloadOperation } from '@ohos.arkui.component';
  ```
- ArkTS1.2中IDataSource强制要求声明`<T>`类型。
- 使用`listener.onDatasetChange()`进行批量数据修改时，`DataOperation`数组中每一项数据需要转换为对应的类型，见[批量数据修改场景](#批量数据修改场景)。

## API变更

ArkTS1.2中删除`DataChangeListener`的`onDataAdded()`、`onDataMoved()`、`onDataDeleted()`、`onDataChanged()`方法，建议使用`onDataAdd()`、`onDataMove()`、`onDataDelete()`、`onDataChange()`方法（功能一致，仅修改方法名）。

## 写法变更

### 批量数据修改场景

开发者在使用`onDatasetChange()`批量修改数据源时，单次`DataOperation`需要转换为具体的类型。见如下代码片段：

```ts
/** ArkTS1.2 */
import { LazyForEach, IDataSource, DataChangeListener } from '@ohos.arkui.component';
// 如果需要使用listener.onDatasetChange()进行批量数据修改，可以按需import下列DataOperation
import { DataOperation, DataOperationType, DataAddOperation, DataDeleteOperation, DataChangeOperation, DataMoveOperation, DataExchangeOperation, DataReloadOperation } from '@ohos.arkui.component';

/** 省略中间代码 */

class MyDataSource extends BasicDataSource {
  // ...

  public operateData(): void { // 数组批量操作
    this.dataArray.splice(4, 0, this.dataArray[1]);
    this.dataArray.splice(1, 1);
    let temp = this.dataArray[4];
    this.dataArray[4] = this.dataArray[6];
    this.dataArray[6] = temp;
    this.dataArray.splice(8, 0, 'Hello 1', 'Hello 2');
    this.dataArray.splice(12, 2);
    // 数组批量操作结束
    this.notifyDatasetChange([ // 调用listener方法通知LazyForEach数据变化
      { type: DataOperationType.MOVE, index: { from: 1, to: 3 } } as DataMoveOperation, // 将单次DataOperation转换为对应的类型，下同
      { type: DataOperationType.EXCHANGE, index: { start: 4, end: 6 } } as DataExchangeOperation,
      { type: DataOperationType.ADD, index: 8, count: 2 } as DataAddOperation,
      { type: DataOperationType.DELETE, index: 10, count: 2 } as DataDeleteOperation
    ]);
  }

  public init(): void { // 数组初始化
    this.dataArray.splice(0, 0, 'Hello a', 'Hello b', 'Hello c', 'Hello d', 'Hello e', 'Hello f', 'Hello g', 'Hello h',
      'Hello i', 'Hello j', 'Hello k', 'Hello l', 'Hello m', 'Hello n', 'Hello o', 'Hello p', 'Hello q', 'Hello r');
  }
}

// ...
```

### ArkTS1.2的写法差异示例

ArkTS1.1&ArkTS1.2的写法差异：

**ArkTS1.1**

```ts
class BasicDataSource implements IDataSource {
  private listeners: Array<DataChangeListener> = [];
  private originDataArray: Array<string> = [];

  public totalCount(): number {
    return this.originDataArray.length;
  }

  public getData(index: number): string {
    return this.originDataArray[index];
  }

  notifyDataChange(index: number): void {
    this.listeners.forEach(listener => {
      listener.onDataChange(index);
    })
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
}

class TestDataSource extends BasicDataSource {
  private dataArray: Array<string> = [];

  public totalCount(): number {
    return this.dataArray.length;
  }

  public getData(index: number): string {
    return this.dataArray[index];
  }

  public pushData(data: string): void {
    this.dataArray.push(data);
  }

  public changeData(index: number, data: string): void {
    this.dataArray[index] = data;
    this.notifyDataChange(index);
  }
}

@Entry
@Component
struct LazyForEachPage {
  @State data: TestDataSource = new TestDataSource();

  aboutToAppear() {
    for (let i = 0; i < 5000; i++) {
      this.data.pushData(`lazy ${i}`);
    }
  }

  build() {
    Column() {
      Button('change #0').onClick(() => {
        this.data.changeData(0, 'new_value');
      })

      List() {
        LazyForEach(this.data, (item: string, index: number) => {
          ListItem() {
            Text(item)
          }
        }, (item: string, index: number) => `__${item}`)
      }.height('50%')
    }
  }
}
```

**ArkTS1.2**

```ts
import { Entry, Component, Column, Text, List, ListItem, LazyForEach, IDataSource, DataChangeListener, Button, ClickEvent } from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';

class BasicDataSource implements IDataSource<string> { // IDataSource强制要求声明<T>类型
  private listeners: Array<DataChangeListener> = [];
  private originDataArray: Array<string> = [];

  public totalCount(): number {
    return this.originDataArray.length;
  }

  public getData(index: number): string {
    return this.originDataArray[index];
  }

  notifyDataChange(index: number): void {
    this.listeners.forEach(listener => {
      listener.onDataChange(index);
    })
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
}

class TestDataSource extends BasicDataSource {
  private dataArray: Array<string> = [];

  public totalCount(): number {
    return this.dataArray.length;
  }

  public getData(index: number): string {
    return this.dataArray[index];
  }

  public pushData(data: string): void {
    this.dataArray.push(data);
  }

  public changeData(index: number, data: string): void {
    this.dataArray[index] = data;
    this.notifyDataChange(index);
  }
}

@Entry
@Component
struct LazyForEachPage {
  @State data: TestDataSource = new TestDataSource();

  aboutToAppear() {
    for (let i = 0; i < 5000; i++) {
      this.data.pushData(`lazy ${i}`);
    }
  }

  build() {
    Column() {
      Button('change #0').onClick((e: ClickEvent) => { // onClick必须声明参数
        this.data.changeData(0, 'new_value');
      })

      List() {
        LazyForEach(this.data, (item: string, index: number) => {
          ListItem() {
            Text(item)
          }
        }, (item: string, index: number) => `__${item}`)
      }.height('50%')
    }
  }
}
```
