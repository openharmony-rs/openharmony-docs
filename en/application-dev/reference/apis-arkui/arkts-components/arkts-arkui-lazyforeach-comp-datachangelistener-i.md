# DataChangeListener

```TypeScript
declare interface DataChangeListener
```

Defines the data change listener, used to notify the **LazyForEach** component to perform corresponding rendering updates when the data source changes. It supports listening for multiple data change types, including data addition, deletion, change, move, swap, and reload.

> **NOTE:** 
> 
> In the methods of **DataChangeListener** other than **onDatasetChange**, when a parameter contains index and its
> value is negative, it is replaced with 0 by default. In **onDatasetChange**, when a single **DataOperation**
> parameter contains index and its value is outside the index range of the data source (in **DataAddOperation**,
> **index** can be equal to the data source length), rendering exceptions may occur.

**Since:** 7

<!--Device-unnamed-declare interface DataChangeListener--><!--Device-unnamed-declare interface DataChangeListener-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDataAdd

```TypeScript
onDataAdd(index: number): void
```

Invoked when data is added to the position indicated by the specified index.

> **NOTE:** 
> 
> This API cannot be used together with the **onDatasetChange** API.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DataChangeListener-onDataAdd(index: number): void--><!--Device-DataChangeListener-onDataAdd(index: number): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the position where data is added. The value range is [0, data source length - 1].<br>If the value is less than 0, it is treated as **0**. If the value is greater than the data source length minus 1, it is treated as the data source length minus 1. |

## onDataChange

```TypeScript
onDataChange(index: number): void
```

Notifies components that the data at the **index** position has changed. Called after the data change is complete.

> **NOTE:** 
> 
> This API cannot be used together with the **onDatasetChange** API.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DataChangeListener-onDataChange(index: number): void--><!--Device-DataChangeListener-onDataChange(index: number): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the position where data is changed. The value range is [0, data source length - 1].<br>If the value is less than 0, it is treated as **0**. If the value is greater than the data source length minus 1, it is treated as the data source length minus 1. |

## onDataDelete

```TypeScript
onDataDelete(index: number): void
```

Invoked when data is deleted from the position indicated by the specified index. LazyForEach will update the displayed content accordingly.

> **NOTE:** 
> 
> - Ensure that the corresponding data in **dataSource** has been deleted before **onDataDelete** is called.Otherwise, undefined behavior may occur during page rendering.
> - This API cannot be used together with the **onDatasetChange** API.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DataChangeListener-onDataDelete(index: number): void--><!--Device-DataChangeListener-onDataDelete(index: number): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the position where data is deleted. The value range is [0, data source length - 1].<br>If the value is less than 0, it is treated as **0**. If the value is greater than the data source length minus 1, it is treated as the data source length minus 1. |

## onDataMove

```TypeScript
onDataMove(from: number, to: number): void
```

Invoked when data is moved, that is, when data is swapped between the **from** and **to** positions.

> **NOTE:** 
> 
> - The key must remain unchanged before and after the data move. If the key changes, use the data deletion and data addition APIs instead.
> - This API cannot be used together with the **onDatasetChange** API.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DataChangeListener-onDataMove(from: number, to: number): void--><!--Device-DataChangeListener-onDataMove(from: number, to: number): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| from | number | Yes | Original position of data. The value range is [0, data source length - 1].<br>If the value is less than 0, it is treated as **0**. If the value is greater than the data source length minus 1, it is treated as the data source length minus 1. |
| to | number | Yes | Target position of data. The value range is [0, data source length - 1].<br>If the value is less than 0, it is treated as **0**. If the value is greater than the data source length minus 1, it is treated as the data source length minus 1. |

<a id="ondatareloaded1"></a>

## onDataReloaded

```TypeScript
onDataReloaded(): void
```

Invoked when all data is reloaded. For data items whose key remains unchanged, the original child component is used. For data items whose key changes, a new child component is created.

> **NOTE:** 
> 
> This API cannot be used together with the **onDatasetChange** API.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DataChangeListener-onDataReloaded(): void--><!--Device-DataChangeListener-onDataReloaded(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

<a id="ondatareloaded2"></a>

## onDataReloaded

```TypeScript
onDataReloaded(reuseImmediately: boolean): void
```

Notifies components to reload all data and configures whether old child components can be reused during the update. This API must be used together with **@Reusable/@ReusableV2**. It is invoked after the data reload is complete.

When reuse of old child components during the update is allowed and this API is used together with [@Reusable](../../../ui/state-management/arkts-reusable.md)/[@ReusableV2](../../../ui/state-management/arkts-new-reusableV2.md), components in the reuse pool are used first. If no component in the reuse pool can be reused but there is a reusable component among the old child components of **LazyForEach**, that component is recycled and reused as a new child component. If no reusable component exists among the old child components of **LazyForEach** either, a new child component is created.

When reuse of old child components during the update is allowed but **@Reusable/@ReusableV2** is not used, data items whose keys do not change use the original child components, while those whose keys change have their child components rebuilt.

When reuse of old child components during the update is not allowed, data items whose keys do not change use the original child components. For data items whose keys change, if **@Reusable/@ReusableV2** is used and a component is available in the reuse pool, the old component is reused; otherwise, a new child component is created.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DataChangeListener-onDataReloaded(reuseImmediately: boolean): void--><!--Device-DataChangeListener-onDataReloaded(reuseImmediately: boolean): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| reuseImmediately | boolean | Yes | Whether old child components can be reused during the update.<br>**true**: old child components can be reused during the update. <br>**false**: old child components cannot be reused during the update. |

## onDatasetChange

```TypeScript
onDatasetChange(dataOperations: DataOperation[]): void
```

Invoked when data is processed in batches to notify the component of refreshing.

> **NOTE:** 
> 
> This API cannot be used together with other data operation APIs of **DataChangeListener**. For example, in the
> same **LazyForEach**, if you have called **onDataAdd**, do not call **onDatasetChange**; if you have called
> **onDatasetChange**, do not call **onDataAdd** or other data operation APIs. Different **LazyForEach** instances
> on the page do not affect each other. When data is processed in batches within the same **onDatasetChange**
> callback, if multiple **DataOperation** instances target the same index, only the first **DataOperation** will
> take effect.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DataChangeListener-onDatasetChange(dataOperations: DataOperation[]): void--><!--Device-DataChangeListener-onDatasetChange(dataOperations: DataOperation[]): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dataOperations | [DataOperation](arkts-arkui-lazyforeach-comp-dataoperation-t.md)[] | Yes | Array of data operations performed. |

## onDataAdded

```TypeScript
onDataAdded(index: number): void
```

Invoked when data is added to the position indicated by the specified index.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 8. Use
> [onDataAdd](#ondataadd) instead.

**Since:** 7

**Deprecated since:** 8

**Substitutes:** [onDataAdd](#ondataadd)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-DataChangeListener-onDataAdded(index: number): void--><!--Device-DataChangeListener-onDataAdded(index: number): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the position where data is added. The value range is [0, data source length - 1].<br>If the value is less than 0, it is treated as **0**. If the value is greater than the data source length minus 1, it is treated as the data source length minus 1. |

## onDataChanged

```TypeScript
onDataChanged(index: number): void
```

Invoked when data in the position indicated by the specified index is changed.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 8. Use
> [onDataChange](#ondatachange) instead.

**Since:** 7

**Deprecated since:** 8

**Substitutes:** [onDataChange](#ondatachange)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-DataChangeListener-onDataChanged(index: number): void--><!--Device-DataChangeListener-onDataChanged(index: number): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Listener for data changes. The value range is [0, data source length - 1].<br>If the value is less than 0, it is treated as **0**. If the value is greater than the data source length minus 1, it is treated as the data source length minus 1. |

## onDataDeleted

```TypeScript
onDataDeleted(index: number): void
```

Invoked when data is deleted from the position indicated by the specified index. LazyForEach will update the displayed content accordingly.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 8. Use
> [onDataDelete](#ondatadelete) instead.

**Since:** 7

**Deprecated since:** 8

**Substitutes:** [onDataDelete](#ondatadelete)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-DataChangeListener-onDataDeleted(index: number): void--><!--Device-DataChangeListener-onDataDeleted(index: number): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the position where data is deleted. The value range is [0, data source length - 1].<br>If the value is less than 0, it is treated as **0**. If the value is greater than the data source length minus 1, it is treated as the data source length minus 1. |

## onDataMoved

```TypeScript
onDataMoved(from: number, to: number): void
```

Invoked when data is moved, that is, when data is swapped between the **from** and **to** positions.

> **NOTE:** 
> 
> - This API is supported since API version 7 and deprecated since API version 8. Use [onDataMove](#ondatamove) instead.
> 
> - The ID must remain unchanged before and after data movement. If the ID changes, APIs for deleting and adding data must be called.

**Since:** 7

**Deprecated since:** 8

**Substitutes:** [onDataMove](#ondatamove)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-DataChangeListener-onDataMoved(from: number, to: number): void--><!--Device-DataChangeListener-onDataMoved(from: number, to: number): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| from | number | Yes | Original position of data. The value range is [0, data source length - 1].<br>If the value is less than 0, it is treated as **0**. If the value is greater than the data source length minus 1, it is treated as the data source length minus 1. |
| to | number | Yes | Target position of data. The value range is [0, data source length - 1].<br>If the value is less than 0, it is treated as **0**. If the value is greater than the data source length minus 1, it is treated as the data source length minus 1. |
