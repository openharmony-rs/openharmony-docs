# LazyForEach

**LazyForEach** is a lazy loading rendering control component that iterates data on demand from the provided data source and creates corresponding components. In scenarios with a large number of child components, **LazyForEach**, when used together with methods such as cached list items, dynamic preloading, and component reuse, can further improve the sliding frame rate and reduce the memory usage of the application. For best practices, see [Optimizing Frame Loss for Long List Loading](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-best-practices-long-list).

For details about the development, see [LazyForEach: Lazy Data Loading](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md).

## LazyForEach

```TypeScript
LazyForEach(
    dataSource: IDataSource,
    itemGenerator: (item: any, index: number) => void,
    keyGenerator?: (item: any, index: number) => string
  )
```

**LazyForEach** iterates over provided data sources and creates corresponding components during each iteration. When **LazyForEach** is used in a scrolling container, the framework creates components as required within the visible area of the scrolling container. When a component is out of the visible area, the framework destroys and reclaims the component to reduce memory usage.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-LazyForEachInterface-(    dataSource: IDataSource,    itemGenerator: (item: any, index: number) => void,    keyGenerator?: (item: any, index: number) => string  ): LazyForEachAttribute--><!--Device-LazyForEachInterface-(    dataSource: IDataSource,    itemGenerator: (item: any, index: number) => void,    keyGenerator?: (item: any, index: number) => string  ): LazyForEachAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dataSource | [IDataSource](arkts-arkui-lazyforeach-comp-idatasource-i.md) | Yes | **LazyForEach** data source. You need to implement related APIs. |
| itemGenerator | (item: any, index: number) =&gt; void | Yes | Child component generation function, which generates a child component for each data item in the array.<br>**NOTE:** <br>- (Optional) **item**: data item. <br>(Optional) **index**: index of the data item. <br>- The function body of **itemGenerator** must be included in braces {...}. <br>- **itemGenerator** can and must generate only one child component for each iteration. <br>- The **if** statement is allowed in **itemGenerator**, but you must ensure that each branch of the **if** statement creates a child component of the same type. |
| keyGenerator | (item: any, index: number) =&gt; string | No | ID generation function, which generates a unique and fixed ID for each data item in the data source. Components are updated only when their generated key changes. The **keyGenerator** parameter is optional, but you are advised to provide it so that the development framework can better identify array changes and update components correctly.<br>The default value is an empty callback. <br>**NOTE:** <br>- (Optional) **item**: data item. <br>(Optional) **index**: index of the data item. <br>- When **keyGenerator** is omitted, the default function **(item: Object, index: number) =&gt; { return viewId + '-' + index.toString(); }** is used, where key generation is affected by the index value only (**viewId** is compiler-generated and consistent within the same **LazyForEach** component). <br>- To ensure correct and efficient child component updates, avoiding rendering anomalies or performance degradation, keys must meet the following requirements: <br>1. Uniqueness: Each data item must have a distinct key. <br>2. Consistency: Keys must remain unchanged for unmodified data items. |

## LazyForEach

```TypeScript
LazyForEach(
    dataSource: IDataSource,
    itemGenerator: (item: any, index: number) => void,
    keyGenerator?: (item: any, index: number) => string,
    options?: LazyForEachOptions
  )
```

Enter the value to obtain the LazyForEach.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyForEachInterface-(    dataSource: IDataSource,    itemGenerator: (item: any, index: number) => void,    keyGenerator?: (item: any, index: number) => string,    options?: LazyForEachOptions  ): LazyForEachAttribute--><!--Device-LazyForEachInterface-(    dataSource: IDataSource,    itemGenerator: (item: any, index: number) => void,    keyGenerator?: (item: any, index: number) => string,    options?: LazyForEachOptions  ): LazyForEachAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dataSource | [IDataSource](arkts-arkui-lazyforeach-comp-idatasource-i.md) | Yes |  |
| itemGenerator | (item: any, index: number) =&gt; void | Yes |  |
| keyGenerator | (item: any, index: number) =&gt; string | No |  |
| options | [LazyForEachOptions](arkts-arkui-lazyforeach-comp-lazyforeachoptions-i.md) | No |  |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [DataAddOperation](arkts-arkui-lazyforeach-comp-dataaddoperation-i.md) | Represents an operation for adding data. |
| [DataChangeListener](arkts-arkui-lazyforeach-comp-datachangelistener-i.md) | Defines the data change listener, used to notify the **LazyForEach** component to perform corresponding rendering updates when the data source changes. It supports listening for multiple data change types, including data addition, deletion, change, move, swap, and reload. |
| [DataChangeOperation](arkts-arkui-lazyforeach-comp-datachangeoperation-i.md) | Represents an operation for changing data. |
| [DataDeleteOperation](arkts-arkui-lazyforeach-comp-datadeleteoperation-i.md) | Represents an operation for deleting data. |
| [DataExchangeOperation](arkts-arkui-lazyforeach-comp-dataexchangeoperation-i.md) | Represents an operation for exchanging data. |
| [DataMoveOperation](arkts-arkui-lazyforeach-comp-datamoveoperation-i.md) | Represents an operation for moving data. |
| [DataReloadOperation](arkts-arkui-lazyforeach-comp-datareloadoperation-i.md) | Reloads all data operations and configures whether to allow reuse of old child components during the update. When **onDatasetChange** contains a **DataOperationType.RELOAD** operation, all other operations become invalid, and the framework calls **keyGenerator** to compare keys. |
| [ExchangeIndex](arkts-arkui-lazyforeach-comp-exchangeindex-i.md) | Defines position of exchange data. |
| [ExchangeKey](arkts-arkui-lazyforeach-comp-exchangekey-i.md) | Defines new key of exchange data. |
| [IDataSource](arkts-arkui-lazyforeach-comp-idatasource-i.md) | Defines the data source of **LazyForEach**. The developer needs to implement this API to provide data access and data change notification capabilities, including obtaining the total number of data items, obtaining data by index, and registering and unregistering data change listeners. |
| [LazyForEachOptions](arkts-arkui-lazyforeach-comp-lazyforeachoptions-i.md) | Configures the resource release strategy and memory optimization strategy of **LazyForEach**, and whether to enable custom component freezing. |
| [MoveIndex](arkts-arkui-lazyforeach-comp-moveindex-i.md) | Defines position of moved data. |

### Types

| Name | Description |
| --- | --- |
| [DataOperation](arkts-arkui-lazyforeach-comp-dataoperation-t.md) | All data operation types. |

### Enums

| Name | Description |
| --- | --- |
| [DataOperationType](arkts-arkui-lazyforeach-comp-dataoperationtype-e.md) | Enumerates the data operation types. |
| [LazyForEachCustomComponentFreezeMode](arkts-arkui-lazyforeach-comp-lazyforeachcustomcomponentfreezemode-e.md) | Selects whether to enable custom component freezing. |
| [LazyForEachMemOptStrategy](arkts-arkui-lazyforeach-comp-lazyforeachmemoptstrategy-e.md) | Enumerates the memory optimization strategies of **LazyForEach**. |
| [LazyForEachReleaseStrategy](arkts-arkui-lazyforeach-comp-lazyforeachreleasestrategy-e.md) | Selects the resource release strategy of **LazyForEach**. |

## Examples

### Example 1: Using the Automatic Memory Optimization Strategy

In the following example, the automatic memory optimization strategy is used through the memoryOptimizationStrategy attribute of [LazyForEachOptions](arkts-arkui-lazyforeach-comp-lazyforeachoptions-i.md). When the application moves to the background, the cache is cleared. When the application returns to the foreground, the cache is restored.

Since API version 26.0.0, the LazyForEachOptions API is added.

For the BasicDataSource code, see the BasicDataSource sample code at the end of the LazyForEach developer guide: [BasicDataSource implementation for the string array](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md#basicdatasource-implementation-for-the-string-array).

```TypeScript
import { BasicDataSource } from './BasicDataSource';

class DataSource extends BasicDataSource {
  public dataArray: string[] = [];
  public totalCount(): number {
    return this.dataArray.length;
  }
  public getData(index: number): string {
    return this.dataArray[index];
  }
  public pushData(data: string): void {
    this.dataArray.push(data);
    this.notifyDataAdd(this.dataArray.length - 1);
  }
}

@Component
struct ChildComponent {
  aboutToAppear() {
    console.info('ChildComponent aboutToAppear');
  }
  aboutToDisappear() {
    console.info('ChildComponent aboutToDisappear');
  }
  build() {
    Text('ChildComponent')
  }
}

@Entry
@Component
struct MemoryOptimizeDemo {
  private data: DataSource = new DataSource();
  aboutToAppear() {
    for (let i = 0; i < 100; i++) {
      this.data.pushData(`item ${i}`);
    }
  }
  build() {
    Column() {
      List() {
        LazyForEach(this.data,
          (item: string, index: number) => {
            ListItem() {
              ChildComponent()
            }
          },
          (item: string, index: number) => item,
          { memoryOptimizationStrategy: LazyForEachMemOptStrategy.ENABLE_AUTO_CACHE_OPTIMIZATION } // Use the automatic memory optimization strategy.
        )
      }
      .cachedCount(5)
    }
  }
}
```
