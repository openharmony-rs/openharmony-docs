# LazyForEach
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @maorh-->
<!--Designer: @keerecles-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=e7b735b321b909a4f33274a48567a7c7d00b5e61 translatedAt=2026-09-01T11:42:37.150Z pushedAt=2026-09-02T11:24:51.743Z -->

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

For details about the development, see [LazyForEach: Lazy Data Loading](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md).

**LazyForEach** is a lazy loading rendering control component that iterates data on demand from the provided data source and creates corresponding components. In scenarios with a large number of child components, **LazyForEach**, when used together with methods such as cached list items, dynamic preloading, and component reuse, can further improve the sliding frame rate and reduce the memory usage of the application. For best practices, see [Optimizing Frame Loss for Long List Loading](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-best-practices-long-list).

## APIs

### LazyForEach

LazyForEach(dataSource: IDataSource, itemGenerator: (item: any, index: number) => void, keyGenerator?: (item: any, index: number) => string)

**LazyForEach** iterates over provided data sources and creates corresponding components during each iteration. When **LazyForEach** is used in a scrolling container, the framework creates components as required within the visible area of the scrolling container. When a component is out of the visible area, the framework destroys and reclaims the component to reduce memory usage.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Atomic service API**: This API can be used in atomic services since API version 11.

**Parameters**

| Name       | Type                                                     | Mandatory| Description                                                        |
| ------------- | --------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| dataSource    | [IDataSource](#idatasource)                       | Yes  | **LazyForEach** data source. You need to implement related APIs.                 |
| itemGenerator | (item:&nbsp;any, index: number)&nbsp;=&gt;&nbsp;void   | Yes   | Child component generation function, which creates a child component for each data item in the array.<br>**Note:**<br>- **item** is the current data item (optional), and **index** is the data item index value (optional).<br>- It is recommended that the data type of item remains consistent with the data type of the data source. Otherwise, when there exists in **itemGenerator** an operation strongly related to the data type, it will cause the child component to fail to render normally, or even crash at runtime.<br>- The function body of **itemGenerator** must use braces {...}.<br>- **itemGenerator** can and must generate only one child component in each iteration.<br>- An if statement can be used in **itemGenerator**, but you must ensure that each branch of the if statement creates a child component of the same type. |
| keyGenerator  | (item:&nbsp;any, index: number)&nbsp;=&gt;&nbsp;string | No   | Key generation function, used to generate a unique and fixed key for each data item from the data source. If modifying a data item in the data source does not affect its generated key, the corresponding component will not be updated; otherwise, the corresponding component will be rebuilt and updated. The `keyGenerator` parameter is optional, but it is recommended to provide it so that the development framework can better identify array changes and update components correctly.<br>Uses by default the built-in key generation function of the framework (see the description below for details).<br>**Note:**<br>- **item** is the current data item (optional), and **index** is the data item index value (optional).<br>- It is recommended that the data type of **item** remains consistent with the data type of the data source. Otherwise, when there exists in **keyGenerator** an operation strongly related to the data type, it will cause the child component to fail to render normally, or even crash at runtime.<br>- When `keyGenerator` is not specified, use the default key generation function, that is, `(item: Object, index: number) => { return viewId + '-' + index.toString(); }`. The generated key is affected only by the index value (**viewId** is generated during compiler conversion, and the **viewId** within the same **LazyForEach** component is consistent).<br>- To ensure that `LazyForEach` updates child components correctly and efficiently and to avoid issues such as abnormal rendering results and reduced rendering efficiency, the key should meet the following conditions.<br>1. Keys are unique, and the keys corresponding to different data items are different from each other.<br>2. Keys are consistent, and the key corresponding to a data item remains unchanged when the data item does not change. |

<!--RP1--><!--RP1End-->

### LazyForEach

LazyForEach(dataSource: IDataSource, itemGenerator: (item: any, index: number) => void, keyGenerator?: (item: any, index: number) => string, options?: LazyForEachOptions)

Iterates data on demand from the provided data source and creates the corresponding component during each iteration. When **LazyForEach** is used in a scrolling container, the framework creates components on demand based on the visible area of the scrolling container. When a component slides out of the visible area, the framework destroys and recycles it to reduce memory usage.

> **NOTE**
>
> Since API version 26.0.0, **LazyForEach** supports passing [LazyForEachOptions](#lazyforeachoptions) to enable custom component freezing and configure the memory optimization strategy and resource release strategy.

**Since**: 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name        | Type                                                      | Mandatory | Description                                                         |
| ------------- | --------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| dataSource    | [IDataSource](#idatasource)                       | Yes   | Data source of **LazyForEach**. The developer needs to implement the related APIs.  |
| itemGenerator | (item:&nbsp;any, index: number)&nbsp;=&gt;&nbsp;void   | Yes   | Child component generation function, which creates a child component for each data item in the array.<br>**NOTE**<br>- **item** is the current data item (optional), and **index** is the index of the data item (optional).<br>- It is recommended that the data type of item remains consistent with the data type of the data source. Otherwise, when there exists in **itemGenerator** an operation strongly related to the data type, the child component cannot render normally, or even crashes at runtime.<br>- The function body of **itemGenerator** must use braces {...}.<br>- **itemGenerator** can and must generate only one child component in each iteration.<br>- An if statement can be used in **itemGenerator**, but each branch of the if statement must create a child component of the same type. |
| keyGenerator  | (item:&nbsp;any, index: number)&nbsp;=&gt;&nbsp;string | No   | Key generation function, used to generate a unique and fixed key for each data item in the data source. If modifying a data item in the data source does not affect its generated key, the corresponding component is not updated; otherwise, the corresponding component is rebuilt and updated. The `keyGenerator` parameter is optional, but it is recommended to provide it so that the development framework can better identify array changes and correctly update components.<br>Uses by default the built-in key generation function of the framework (see the description below for details).<br>**NOTE**<br>- **item** is the current data item (optional), and **index** is the index of the data item (optional).<br>- It is recommended that the data type of item remains consistent with the data type of the data source. Otherwise, when there exists in **keyGenerator** an operation strongly related to the data type, the child component cannot render normally, or even crashes at runtime.<br>- When `keyGenerator` is not specified, use the default key generation function, that is, `(item: Object, index: number) => { return viewId + '-' + index.toString(); }`. The generated key is affected only by the index value (**viewId** is generated during compiler conversion, and **viewId** is the same within the same **LazyForEach** component).<br>- To ensure that `LazyForEach` updates child components correctly and efficiently and to avoid issues such as abnormal rendering results and reduced rendering efficiency, the key should meet the following conditions.<br>1. Keys are unique, and the keys corresponding to different data items are different from each other.<br>2. Keys are consistent, and the key remains unchanged when the data item is unchanged. |
| options   | [LazyForEachOptions](#lazyforeachoptions)   | No   | Developer configuration item, used to enable custom component freezing and configure the memory optimization strategy and resource release strategy. When this configuration item is used, the key generation function must be set; otherwise, compilation fails. When it is not passed, the default configuration is used (the custom component freezing mode defaults to **AUTO**, the resource release strategy defaults to **BATCH** , and the memory optimization strategy defaults to **DEFAULT**).   |

## Attributes

The [drag-and-drop sorting](./ts-universal-attributes-drag-sorting.md) attribute is supported.

## IDataSource

Defines the data source of **LazyForEach**. The developer needs to implement this API to provide data access and data change notification capabilities, including obtaining the total number of data items, obtaining data by index, and registering and unregistering data change listeners.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### totalCount

totalCount(): number

Obtains the total number of data items.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type               | Description       |
| ------------------- | --------- |
| number | Total number of data items, which is subject to the data source.|

### getData

getData(index:&nbsp;number): any

Obtains the data item that matches the specified index.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                |
| ------ | ------ | ---- | -------------------- |
| index  | number  | Yes   | Index of the data. The value range is [0, data source length - 1]. When the value exceeds the range, the behavior is determined by the data source implementation. Developers are advised to perform boundary checks. |

**Return value**

| Type               | Description       |
| ------------------- | --------- |
| any | Data item that matches the specified index. The actual type is determined by the data source implementation.|

> **NOTE**
>
> Avoid performing time-consuming operations in the `getData` function to reduce frame freezing and dropping during application swiping. For best practices, see [Optimizing Time-Consuming Operations in the Main Thread - Repeated Rendering](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-time-optimization-of-the-main-thread#section4551193714439).

### registerDataChangeListener

registerDataChangeListener(listener: DataChangeListener): void

Registers a listener for data changes.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                       | Mandatory| Description          |
| -------- | ------------------------------------------- | ---- | -------------- |
| listener | [DataChangeListener](#datachangelistener) | Yes   | Data change listener, used to notify components to refresh when the data source changes. |

### unregisterDataChangeListener

unregisterDataChangeListener(listener: DataChangeListener): void

Unregisters the listener for data changes.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                       | Mandatory| Description          |
| -------- | ------------------------------------------- | ---- | -------------- |
| listener | [DataChangeListener](#datachangelistener) | Yes | Data change listener, used to notify components to refresh when the data source changes. |

## DataChangeListener

Defines the data change listener, used to notify the **LazyForEach** component to perform corresponding rendering updates when the data source changes. It supports listening for multiple data change types, including data addition, deletion, change, move, swap, and reload.

> **NOTE**
>
> In the methods of **DataChangeListener** other than **onDatasetChange**, when a parameter contains index and its value is negative, it is replaced with 0 by default. In **onDatasetChange**, when a single **DataOperation** parameter contains index and its value is outside the index range of the data source (in **DataAddOperation**, **index** can be equal to the data source length), rendering exceptions may occur.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### onDataReloaded

onDataReloaded(): void

Invoked when all data is reloaded. For data items whose key remains unchanged, the original child component is used. For data items whose key changes, a new child component is created.  

> **NOTE**
>
> This API cannot be used together with the **onDatasetChange** API.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### onDataReloaded

onDataReloaded(reuseImmediately: boolean): void

Notifies components to reload all data and configures whether old child components can be reused during the update. This API must be used together with **@Reusable/@ReusableV2**. It is invoked after the data reload is complete.

When reuse of old child components during the update is allowed and this API is used together with [@Reusable](../../../ui/state-management/arkts-reusable.md)/[@ReusableV2](../../../ui/state-management/arkts-new-reusableV2.md), components in the reuse pool are used first. If no component in the reuse pool can be reused but there is a reusable component among the old child components of **LazyForEach**, that component is recycled and reused as a new child component. If no reusable component exists among the old child components of **LazyForEach** either, a new child component is created.

When reuse of old child components during the update is allowed but **@Reusable/@ReusableV2** is not used, data items whose keys do not change use the original child components, while those whose keys change have their child components rebuilt.

When reuse of old child components during the update is not allowed, data items whose keys do not change use the original child components. For data items whose keys change, if **@Reusable/@ReusableV2** is used and a component is available in the reuse pool, the old component is reused; otherwise, a new child component is created.

**Since:** 26.1.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ------ | ---- | -------------------- |
| reuseImmediately | boolean | Yes | Whether old child components can be reused during the update.<br/>**true**: old child components can be reused during the update.<br/>**false**: old child components cannot be reused during the update. |

### onDataAdded<sup>(deprecated)</sup>

onDataAdded(index: number): void

Invoked when data is added to the position indicated by the specified index.  

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 8. You are advised to use [onDataAdd](#ondataadd8) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                |
| ------ | ------ | ---- | -------------------- |
| index  | number  | Yes   | Index of the position where the data is added. The value range is [0, data source length - 1].<br>If the value is less than 0, it is set to 0; if it is greater than data source length - 1, it is set to data source length - 1. |

### onDataMoved<sup>(deprecated)</sup>

onDataMoved(from: number, to: number): void

Invoked when data is moved, that is, when data is swapped between the **from** and **to** positions.

> **NOTE**
>
> - This API is supported since API version 7 and deprecated since API version 8. You are advised to use [onDataMove](#ondatamove8) instead.
>
> - The key must remain unchanged before and after the data move. If the key changes, use the data deletion and data addition APIs instead. This API is called after the data at the move start position and the data at the move target position are swapped.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description            |
| ------ | ------ | ---- | ---------------- |
| from   | number | Yes   | Start position of data movement. The value range is [0, data source length - 1].<br>If the value is less than 0, it is set to 0; if it is greater than data source length - 1, it is set to data source length - 1. |
| to     | number | Yes   | Target position of data movement. The value range is [0, data source length - 1].<br>If the value is less than 0, it is set to 0; if it is greater than data source length - 1, it is set to data source length - 1. |

### onDataDeleted<sup>(deprecated)</sup>

onDataDeleted(index: number): void

Invoked when data is deleted from the position indicated by the specified index. LazyForEach will update the displayed content accordingly.  

> **NOTE**
>
> - This API is supported since API version 7 and deprecated since API version 8. You are advised to use [onDataDelete](#ondatadelete8) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                |
| ------ | ------ | ---- | -------------------- |
| index  | number  | Yes   | Index of the position where the data is deleted. The value range is [0, data source length - 1].<br>If the value is less than 0, it is set to 0; if it is greater than data source length - 1, it is set to data source length - 1. |

### onDataChanged<sup>(deprecated)</sup>

onDataChanged(index: number): void

Invoked when data in the position indicated by the specified index is changed.  

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 8. You are advised to use [onDataChange](#ondatachange8) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| index  | number  | Yes   | Index of the position where the data changes. The value range is [0, data source length - 1].<br>If the value is less than 0, it is set to 0; if it is greater than data source length - 1, it is set to data source length - 1. |

### onDataAdd<sup>8+</sup>

onDataAdd(index: number): void

Invoked when data is added to the position indicated by the specified index.  

> **NOTE**
>
> This API cannot be used together with the **onDatasetChange** API.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| index  | number | Yes  | Index of the position where the data is added. The value range is [0, data source length - 1].<br>If the value is less than 0, it is set to 0; if it is greater than data source length - 1, it is set to data source length - 1. |

### onDataMove<sup>8+</sup>

onDataMove(from: number, to: number): void

Invoked when data is moved, that is, when data is swapped between the **from** and **to** positions.  

> **NOTE**
>
> - The key must remain unchanged before and after the data move. If the key changes, use the data deletion and data addition APIs instead.
> - This API cannot be used together with the **onDatasetChange** API.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description            |
| ------ | ------ | ---- | ---------------- |
| from   | number | Yes   | Start position of data movement. The value range is [0, data source length - 1].<br>If the value is less than 0, it is set to 0; if it is greater than data source length - 1, it is set to data source length - 1. |
| to     | number | Yes   | Target position of data movement. The value range is [0, data source length - 1].<br>If the value is less than 0, it is set to 0; if it is greater than data source length - 1, it is set to data source length - 1. |

### onDataDelete<sup>8+</sup>

onDataDelete(index: number): void

Invoked when data is deleted from the position indicated by the specified index. LazyForEach will update the displayed content accordingly.  

> **NOTE**
>
> - Ensure that the corresponding data in **dataSource** has been deleted before **onDataDelete** is called. Otherwise, undefined behavior may occur during page rendering.
> - This API cannot be used together with the **onDatasetChange** API.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                |
| ------ | ------ | ---- | -------------------- |
| index  | number | Yes   | Index of the position where the data is deleted. The value range is [0, data source length - 1].<br>If the value is less than 0, it is set to 0; if it is greater than data source length - 1, it is set to data source length - 1. |

### onDataChange<sup>8+</sup>

onDataChange(index: number): void

Notifies components that the data at the **index** position has changed. Called after the data change is complete.

> **NOTE**
>
> This API cannot be used together with the **onDatasetChange** API.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                |
| ------ | ------ | ---- | -------------------- |
| index  | number  | Yes   | Index of the position where the data changes. The value range is [0, data source length - 1].<br>If the value is less than 0, it is set to 0; if it is greater than data source length - 1, it is set to data source length - 1. |

### onDatasetChange<sup>12+</sup>

onDatasetChange(dataOperations: DataOperation[]): void

Invoked when data is processed in batches to notify the component of refreshing.

> **NOTE**
>
> This API cannot be used together with other data operation APIs of **DataChangeListener**. For example, in the same **LazyForEach**, if you have called **onDataAdd**, do not call **onDatasetChange**; if you have called **onDatasetChange**, do not call **onDataAdd** or other data operation APIs. Different **LazyForEach** instances on the page do not affect each other. When data is processed in batches within the same **onDatasetChange** callback, if multiple **DataOperation** instances target the same index, only the first **DataOperation** will take effect.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name        | Type               | Mandatory| Description              |
| -------------- | ------------------- | ---- | ------------------ |
| dataOperations | [DataOperation](#dataoperation12)[] | Yes | A collection of operations for batch data processing. The developer places the data operations to be processed (add, delete, change, move, exchange, reload, etc.) into this array, and the component refreshes the displayed content in the order of the operations in the array. |

## DataOperation<sup>12+</sup>

type DataOperation = DataAddOperation | DataDeleteOperation | DataChangeOperation | DataMoveOperation | DataExchangeOperation | DataReloadOperation

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### DataAddOperation<sup>12+</sup>

Represents an operation for adding data.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type                     | Read-Only| Optional| Description                |
| ------ | ------------------------- | ---- | ---- | -------------------- |
| type   | [DataOperationType](#dataoperationtype12).ADD     | No | No   | Data addition type.         |
| index  | number                    | No | No   | Index of the added data. The value range is [0, data source length]. Rendering is abnormal when the value exceeds the range. |
| count  | number                    | No | Yes   | Number of added data items. It must be a positive integer (greater than 0), and the default value is **1**. Passing 0 or a negative number may cause abnormal rendering.   |
| key    | string \| Array\<string\> | No | Yes   | Assigns a key to the added data. The original key is used by default. The key supports the string or Array\<string\> type. If the key is an array whose length is greater than **count**, an invalid parameter error is reported. |

### DataDeleteOperation<sup>12+</sup>

Represents an operation for deleting data.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type                     | Read-Only| Optional| Description                |
| ------ | ------------------------- | ---- | ---- | -------------------- |
| type   | [DataOperationType](#dataoperationtype12).DELETE     | No | No   | Data deletion type.         |
| index  | number                    | No | No   | Index of the start position for deletion. The value range is [0, data source length - 1]. Rendering is abnormal when the value exceeds the value range.|
| count  | number                    | No | Yes   | Number of data items to delete. It must be a positive integer (greater than 0), and the sum of **index** and **count** must not exceed the data source length. The default value is 1. If a negative number is passed in, this operation is ignored. If 0 is passed in, the data item at the **index** position is abnormally marked for deletion. If the sum of **index** and **count** exceeds the data source length, rendering may be abnormal.    |

### DataChangeOperation<sup>12+</sup>

Represents an operation for changing data.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type                     | Read-Only| Optional| Description                |
| ------ | ------------------------- | ---- | ---- | -------------------- |
| type   | [DataOperationType](#dataoperationtype12).CHANGE     | No | No   | Data change type.         |
| index  | number                    | No | No   | Index of the changed data. The value range is [0, data source length - 1]. Rendering is abnormal when the value exceeds the value range.|
| key  | string                    | No| Yes  | New key to assign to the changed data. The original key is used by default.   |

### DataMoveOperation<sup>12+</sup>

Represents an operation for moving data.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type                     | Read-Only| Optional| Description                |
| ------ | ------------------------- | ---- | ---- | -------------------- |
| type   | [DataOperationType](#dataoperationtype12).MOVE     | No | No   | Data move type. |
| index  | [MoveIndex](#moveindex12)        | No | No   | Move position. The value range is [0, data source length - 1]. Rendering is abnormal when the value exceeds the value range. |
| key | string              | No| Yes  | New key to assign to the moved data. The original key is used by default.|

### DataExchangeOperation<sup>12+</sup>

Represents an operation for exchanging data.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type                      | Read-Only| Optional| Description                        |
| ------ | -------------------------- | ---- | ---- | ---------------------------- |
| type   | [DataOperationType](#dataoperationtype12).EXCHANGE | No | No   | Data exchange type.                 |
| index  | [ExchangeIndex](#exchangeindex12)            | No | No   | Exchange position. The value range is [0, data source length - 1]. Rendering is abnormal when the value exceeds the value range.|
| key    | [ExchangeKey](#exchangekey12)              | No| Yes  | New keys to assign to the exchanged data. The original keys are used by default.|

### DataReloadOperation<sup>12+</sup>

Reloads all data operations and configures whether to allow reuse of old child components during the update. When **onDatasetChange** contains a **DataOperationType.RELOAD** operation, all other operations become invalid, and the framework calls **keyGenerator** to compare keys.

When reuse of old child components during the update is allowed and used together with [@Reusable](../../../ui/state-management/arkts-reusable.md)/[@ReusableV2](../../../ui/state-management/arkts-new-reusableV2.md), components in the reuse pool are used first. If no reusable component is available in the reuse pool but a reusable component exists among the old child components of **LazyForEach**, that component will be recycled and reused as a new child component. If no reusable component exists among the old child components of **LazyForEach** either, a new child component will be created.

When reuse of old child components during the update is allowed but **@Reusable/@ReusableV2** is not used, data items whose keys do not change will use the original child components, while those whose keys change will have their child components rebuilt.

When reuse of old child components during the update is not allowed, data items whose keys do not change will use the original child components. For data items whose keys change, if **@Reusable/@ReusableV2** is used and a component is available in the reuse pool, the old component will be reused; otherwise, a new child component will be created.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type                    | Read-Only| Optional| Description            |
| ------ | ------------------------ | ---- | ---- | ---------------- |
| type   | [DataOperationType](#dataoperationtype12).RELOAD | No | No   | Type for reloading all data. |
| reuseImmediately   | boolean | No | Yes   | Whether to reuse the old child components during the update.<br/>**true**: allows reusing the old child components during the update.<br/>**false**: does not allow reusing the old child components during the update.<br/>Default value: false<br/>When the value is **undefined** or **null**, the default value is used.<br/>**Since:** 26.1.0<br/>**Model constraints:** this API is only used under the Stage model.<br/>**Atomic service API:** since API version 26.1.0, this API supports use in atomic services. |

### DataOperationType<sup>12+</sup>

Enumerates the data operation types.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value                   | Description                |
| ------ | ------------------- | -------------------- |
| ADD   |   add       | Data addition.  |
| DELETE  | delete    | Data deletion.   |
| CHANGE  | change     | Data change.   |
| MOVE | move | Data movement.|
| EXCHANGE | exchange | Data exchange.|
| RELOAD | reload | Data reloading.|

## MoveIndex<sup>12+</sup>

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type                      | Read-Only| Optional| Description           |
| ------ | --------------- | ---- | ---- | ------- |
| from   | number | No | No   | Start position of the move. The value range is [0, data source length - 1]. Rendering is abnormal when the value exceeds the value range.|
| to  | number           | No | No   | Target position of the move. The value range is [0, data source length - 1]. Rendering is abnormal when the value exceeds the value range.|

## ExchangeIndex<sup>12+</sup>

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type                      | Read-Only| Optional| Description           |
| ------ | --------------- | ---- | ---- | ------- |
| start   | number | No | No   | First swap position. The value range is [0, data source length - 1]. Rendering is abnormal when the value exceeds the value range.|
| end  | number           | No | No   | Second swap position. The value range is [0, data source length - 1]. Rendering is abnormal when the value exceeds the value range.|

## ExchangeKey<sup>12+</sup>

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type                      | Read-Only| Optional| Description           |
| ------ | --------------- | ---- | ---- | ------- |
| start   | string | No| No  | New key to assign to the first position in the exchange. The original key is used by default.       |
| end  | string   | No| No  | New key to assign to the second position in the exchange. The original key is used by default.          |

## LazyForEachOptions

Configures the resource release strategy and memory optimization strategy of **LazyForEach**, and whether to enable custom component freezing.

> **NOTE**
>
> 1. Note: When using **LazyForEachOptions**, ensure that the **keyGenerator** function has been defined; otherwise, compilation will fail.
>
> 2. Custom component freezing: When a custom component is directly used under **LazyForEach**, this configuration determines whether to enable the freezing feature of the custom component. Once enabled, when the custom component is outside the visible area, the framework pauses the processing logic such as state variable updates of the component to reduce resource consumption; when the component re-enters the visible area, normal processing resumes.
>
> 3. Resource release strategy: **LazyForEach** manages the nodes in the on-screen area and the preloading area. When a node slides out of the preloading area and leaves the management scope of **LazyForEach**, **LazyForEach** no longer manages the node, and the node resources are released. The **BATCH** mode is used by default, in which **LazyForEach** releases all nodes to be released in the current frame. The **PROGRESSIVE** mode releases resources one by one, and when releasing the resources of each node, it checks whether the time of the current frame is sufficient; if not, the release is postponed to subsequent frames. Under this strategy, **LazyForEach** may hold node resources, and the nodes in the cache pool cannot be replenished in time, which reduces the reuse rate in scenarios where nodes are obtained quickly. Developers should select an appropriate resource release strategy based on the application scenario.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name | Type                       | Read-only | Optional | Description            |
| ------ | --------------- | ---- | ---- | ------- |
| customComponentFreezeMode   | [LazyForEachCustomComponentFreezeMode](#lazyforeachcustomcomponentfreezemode) | No | Yes   | Whether to enable custom component freezing. It takes effect only when a custom component is directly used under **LazyForEach**, and does not apply to other cases.<br>The default value is [AUTO](#lazyforeachcustomcomponentfreezemode).        |
| releaseStrategy  | [LazyForEachReleaseStrategy](#lazyforeachreleasestrategy)   | No | Yes   | Resource release strategy for **LazyForEach**.<br>The [BATCH](#lazyforeachreleasestrategy) mode is used by default, which releases nodes in batches.           |
| memoryOptimizationStrategy   | [LazyForEachMemOptStrategy](#lazyforeachmemoptstrategy) | No | Yes   | Memory optimization strategy of **LazyForEach**. This parameter is set when **LazyForEach** is created and does not support dynamic modification.<br>Default value: [DEFAULT](#lazyforeachmemoptstrategy) |

## LazyForEachCustomComponentFreezeMode

Selects whether to enable custom component freezing.

> **NOTE**
>
> This configuration is added only when a custom component is directly used under **LazyForEach**. It is not applicable in other cases.


**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name | Value | Description |
| ------ | ------------------- | -------------------- |
| AUTO   |   0       | Follows the **metadata** settings in the **module.json5** configuration file.   |
| DISABLED  | 1    | Does not enable custom component freezing.    |
| ENABLED  | 2     | Enables custom component freezing.    |

## LazyForEachReleaseStrategy

Selects the resource release strategy of **LazyForEach**.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name | Value | Description |
| ------ | ------------------- | -------------------- |
| BATCH   |   0       | **BATCH** is the resource release strategy used by default. This strategy releases the resources of all discarded nodes in the current frame. If node reuse exists, the node reuse rate can be maximized. However, if a node has a deep component hierarchy or a large number of child components, releasing the resources of a single node takes a long time. Releasing a large number of nodes in the current frame may cause an oversized frame and affect performance.   |
| PROGRESSIVE  | 1    | **PROGRESSIVE** is a strategy that automatically adjusts node release based on the node release time and the remaining time of the current frame. If the remaining time of the current frame is insufficient to release the remaining nodes, the release is postponed to subsequent frames, avoiding oversized frames and optimizing performance. In this case, **LazyForEach** continues to hold the nodes, which may reduce the reuse rate. When a large number of nodes are generated and cannot be released in time, memory usage increases accordingly. Developers need to pay attention to the impact on performance and memory and select a proper resource release strategy.    |

## LazyForEachMemOptStrategy

Enumerates the memory optimization strategies of **LazyForEach**.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name | Value | Description |
| --- | --- | --- |
| DEFAULT | 0 | No memory optimization strategy. |
| ENABLE_AUTO_CACHE_OPTIMIZATION | 1 << 0 | Automatic memory optimization strategy. When the number of list items carried by **LazyForEach** is large (for example, hundreds or more) or the structure of a single child component is complex (for example, containing multiple nested layers or dozens of child nodes), resulting in high memory usage (which can be detected through a performance analysis tool), it is recommended to use this strategy to reduce memory usage.<br>When the application moves to the background, when the component where **LazyForEach** resides is invisible (the [visibility](./ts-universal-attributes-visibility.md#visibility) attribute is set to a value other than [Visible](./ts-appendix-enums.md#visibility), or the component area is 0, regardless of occlusion), or when the device is low on memory ([MemoryLevel](../../apis-ability-kit/js-apis-app-ability-abilityConstant.md#memorylevel) reaches **MEMORY_LEVEL_LOW** or **MEMORY_LEVEL_CRITICAL**), for devices with memory greater than 6 GB, some nodes in the [preload area](../../../ui/rendering-control/arkts-rendering-control-overview.md#basic-concepts) are released until the number of nodes in both the upper and lower preload areas does not exceed 2; for devices with memory less than or equal to 6 GB, all nodes in the preload area are released.<br>When the application returns to the foreground, when the component where **LazyForEach** resides becomes visible again, or when **LazyForEach** scrolls, the nodes in the preload area are restored.<br>Releasing and restoring nodes triggers the [custom component lifecycle](../../../ui/state-management/arkts-page-custom-components-lifecycle.md). |

## Examples

### Example 1: Using the Automatic Memory Optimization Strategy

In the following example, the automatic memory optimization strategy is used through the **memoryOptimizationStrategy** attribute of [LazyForEachOptions](#lazyforeachoptions). When the application moves to the background, the cache is cleared. When the application returns to the foreground, the cache is restored.

Since API version 26.0.0, the **LazyForEachOptions** API is added.

For the **BasicDataSource** code, see the **BasicDataSource** sample code at the end of the **LazyForEach** developer guide: [BasicDataSource implementation for the string array](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md#basicdatasource-implementation-for-the-string-array).

<!--code_no_check-->
```ts
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

