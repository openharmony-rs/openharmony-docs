# LazyForEach

For details about the development, see [LazyForEach: Lazy Data Loading](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md).

In scenarios involving a large number of child components, LazyForEach, when combined with techniques such as cached list items, dynamic preloading, and component reuse, can significantly improve scrolling frame rates while reducing memory usage. For best practices, see [Optimizing Frame Loss for Long List Loading](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-best-practices-long-list).

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

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dataSource | [IDataSource](arkts-arkui-idatasource-i.md) | Yes | **LazyForEach** data source. You need to implement related APIs. |
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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dataSource | [IDataSource](arkts-arkui-idatasource-i.md) | Yes |  |
| itemGenerator | (item: any, index: number) =&gt; void | Yes |  |
| keyGenerator | (item: any, index: number) =&gt; string | No |  |
| options | [LazyForEachOptions](arkts-arkui-lazyforeachoptions-i.md) | No |  |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [DataAddOperation](arkts-arkui-dataaddoperation-i.md) | Represents an operation for adding data. |
| [DataChangeListener](arkts-arkui-datachangelistener-i.md) | Listener for data changes. |
| [DataChangeOperation](arkts-arkui-datachangeoperation-i.md) | Represents an operation for changing data. |
| [DataDeleteOperation](arkts-arkui-datadeleteoperation-i.md) | Represents an operation for deleting data. |
| [DataExchangeOperation](arkts-arkui-dataexchangeoperation-i.md) | Represents an operation for exchanging data. |
| [DataMoveOperation](arkts-arkui-datamoveoperation-i.md) | Represents an operation for moving data. |
| [DataReloadOperation](arkts-arkui-datareloadoperation-i.md) | Represents an operation for reloading data. If the **onDatasetChange** event contains a **DataOperationType.RELOAD** operation, all other operations in the event are ineffective. In such cases, the framework will call **keyGenerator** to perform a comparison of keys with their corresponding values. |
| [ExchangeIndex](arkts-arkui-exchangeindex-i.md) | Defines position of exchange data. |
| [ExchangeKey](arkts-arkui-exchangekey-i.md) | Defines new key of exchange data. |
| [IDataSource](arkts-arkui-idatasource-i.md) | Data source of **LazyForEach**. |
| [LazyForEachOptions](arkts-arkui-lazyforeachoptions-i.md) | Defines the options for LazyForEach. |
| [MoveIndex](arkts-arkui-moveindex-i.md) | Defines position of moved data. |

### Types

| Name | Description |
| --- | --- |
| [DataOperation](arkts-arkui-dataoperation-t.md) | All data operation types. |

### Enums

| Name | Description |
| --- | --- |
| [DataOperationType](arkts-arkui-dataoperationtype-e.md) | Enumerates the data operation types. |
| [LazyForEachCustomComponentFreezeMode](arkts-arkui-lazyforeachcustomcomponentfreezemode-e.md) | Enumerates the freeze modes for cached custom nodes that have been removed from the component tree in LazyForEach. |
| [LazyForEachMemOptStrategy](arkts-arkui-lazyforeachmemoptstrategy-e.md) | Defines a type for memory optimization strategy. |
| [LazyForEachReleaseStrategy](arkts-arkui-lazyforeachreleasestrategy-e.md) | Enumerates the release strategies for LazyForEach discarded nodes. |

## Examples

```TypeScript
### Example 1: Using the Automatic Memory Optimization Strategy

In the following example, the automatic memory optimization strategy is used through the memoryOptimizationStrategy attribute of [LazyForEachOptions](arkts-arkui-lazyforeachoptions-i.md). When the application moves to the background, the cache is cleared. When the application returns to the foreground, the cache is restored.

Since API version 26.0.0, the LazyForEachOptions API is added.

For the BasicDataSource code, see the BasicDataSource sample code at the end of the LazyForEach developer guide: [BasicDataSource implementation for the string array](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md#basicdatasource-implementation-for-the-string-array).
```
