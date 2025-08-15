# ArkTS1.2 渲染控制组件迁移规范

本指南介绍ArkTS1.2语言中渲染控制组件的变更。if/else组件功能规格和使用方式与ArkTS1.1一致；ForEach、LazyForEach和Repeat组件功能规格与ArkTS1.1一致，但使用方式略有不同，下文将详细说明这些组件使用方式的迁移规范。

## ForEach迁移规范

### 迁移说明

ArkTS1.2需要加入模块导入语句：

```ts
import { ForEach } from '@ohos.arkui.component';
```

### 类型一致性校验

ArkTS1.1 ForEach允许的写法：

```ts
arr: Array<Type1 | Type2> = [];

ForEach(this.arr, (item: Type1) => {...}, (item: Type2) => item.toString()) // 只使用一种类型
```

ArkTS1.2 ForEach的API声明：

```ts
ForEach<T>(
  arr: Array<T>,
  itemGenerator: (item: T, index: number) => void,
  keyGenerator?: (item: T, index: number) => string
): ForEachAttribute
```

在ArkTS1.2中，ForEach数组类型需要与itemGenerator、keyGenerator的参数item的类型保持一致，否则会报编译错误。

正确写法：

```ts
arr: Array<Type1 | Type2> = [];

ForEach(this.arr, (item: Type1 | Type2) => {...}, (item: Type1 | Type2) => item.toString()) // 类型保持一致
```

## LazyForEach迁移规范

### 迁移说明

ArkTS1.2需要加入模块导入语句：

```ts
import { LazyForEach, IDataSource, DataChangeListener } from '@ohos.arkui.component';
// 如果需要使用listener.onDatasetChange()进行批量数据修改，可以按需import以下DataOperation
import { DataOperation, DataOperationType, DataAddOperation, DataDeleteOperation, DataChangeOperation, DataMoveOperation, DataExchangeOperation, DataReloadOperation } from '@ohos.arkui.component';
```

- ArkTS1.2中IDataSource强制要求声明`<T>`类型，
- 从API version 20开始，删除API中`DataChangeListener`的`onDataAdded()`、`onDataMoved()`、`onDataDeleted()`、`onDataChanged()`方法（从API version 8开始，上述接口被废弃，建议使用`onDataAdd()`、`onDataMove()`、`onDataDelete()`、`onDataChange()`方法）。
- 使用listener.onDatasetChange()进行批量数据修改时，DataOperation数组中每一项数据需要转换为对应的类型，见[批量数据修改场景](#批量数据修改场景)。

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

### 批量数据修改场景


## Repeat迁移规范

### 迁移说明

ArkTS1.2需要加入模块导入语句：

```ts
import { Repeat, RepeatItem } from '@ohos.arkui.component';
```

- ArkTS1.2中Repeat()强制要求声明数组类型`<T>`。
- 新增API：ArkTS1.1中，当`Repeat.virtualScroll()`属性缺省时，Repeat渲染方式默认为全量加载，需要添加`.virtualScroll()`开启懒加载。ArkTS1.2中，当该属性缺省时，Repeat渲染方式默认为懒加载。需要使用[disableVirtualScroll](../reference/apis-arkui/arkui-ts/ts-rendering-control-repeat.md#virtualscrolloptions对象说明)配置项开启懒加载，默认值为false。

### ArkTS1.2的写法差异示例

1. 全量加载模式

**ArkTS1.1**

```ts
@Entry
@Component
struct Index {
  @State simpleList: Array<string> = ['one', 'two', 'three'];

  build() {
    Column() {
      Repeat(this.simpleList)
        .each((ri) => { // RepeatItem可以省略
          Text(`#${ri.index}: ${ri.item}`)
        })
        .key((item: string) => item)
    }
  }
}
```

**ArkTS1.2**

```ts
import { Entry, Component, Column, Text, Repeat, RepeatItem } from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';

@Entry
@Component
struct Index {
  @State simpleList: Array<string> = ['one', 'two', 'three'];

  build() {
    Column() {
      Repeat<string>(this.simpleList) // 必须声明数据类型<T>
        .each((ri: RepeatItem<string>) => { // RepeatItem可以省略
          Text(`#${ri.index}: ${ri.item}`)
        })
        .key((item: string) => item)
        .virtualScroll({
          disableVirtualScroll: true // 关闭懒加载
        })
    }
  }
}
```

2. 懒加载模式

**ArkTS1.1**

```ts
@Entry
@Component
struct Index {
  @State simpleList: Array<string> = [];

  aboutToAppear(): void {
    for (let i = 0; i < 50; i++) {
      this.simpleList.push(`data_${i}`); // 向数组中添加一些数据
    }
  }

  build() {
    Column() {
      List() {
        Repeat(this.simpleList) // 数据类型<T>可以省略
          .each((ri) => { // RepeatItem可以省略
            ListItem() {
              Text(`#${ri.index}: ${ri.item}`).fontColor(Color.Red)
            }
          })
          .key((item: string) => item)
          .virtualScroll() // 懒加载模式必须声明.virtualScroll()
          .template('ttype_a', (ri) => { // RepeatItem可以省略
            ListItem() {
              Text(`#${ri.index}: ${ri.item}`).fontColor(Color.Blue)
            }
          }, { cachedCount: 1 })
          .templateId((item: string, index: number) => index % 2 === 0 ? 'ttype_a' : '')
      }.height('40%')
    }
  }
}
```

**ArkTS1.2**

```ts
import { Entry, Component, Column, Text, Color, Repeat, RepeatItem, List, ListItem } from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';

@Entry
@Component
struct Index {
  @State simpleList: Array<string> = new Array<string>();

  aboutToAppear(): void {
    for (let i = 0; i < 50; i++) {
      this.simpleList.push(`data_${i}`); // 向数组中添加一些数据
    }
  }

  build() {
    Column() {
      List() {
        Repeat<string>(this.simpleList) // 必须声明数据类型<T>
          .each((ri: RepeatItem<string>) => { // RepeatItem可以省略
            ListItem() {
              Text(`#${ri.index}: ${ri.item}`).fontColor(Color.Red)
            }
          })
          .key((item: string) => item)
          .virtualScroll() // 可以省略
          .template('ttype_a', (ri: RepeatItem<string>) => { // RepeatItem可以省略
            ListItem() {
              Text(`#${ri.index}: ${ri.item}`).fontColor(Color.Blue)
            }
          }, { cachedCount: 1 })
          .templateId((item: string, index: number) => index % 2 === 0 ? 'ttype_a' : '')
      }.height('40%')
    }
  }
}
```