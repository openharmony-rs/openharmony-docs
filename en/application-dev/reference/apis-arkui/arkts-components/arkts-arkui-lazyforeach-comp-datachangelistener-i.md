# DataChangeListener

```TypeScript
declare interface DataChangeListener
```

Listener for data changes.

> **NOTE:** 
> 
> In APIs of **DataChangeListener** other than **onDatasetChange**, if the value of **index** is negative, the value
> is treated as **0** by default. In **onDatasetChange**, if the specified index in a **DataOperation** is outside
> the data source index range, the corresponding **DataOperation** does not take effect. (In **DataAddOperation**,
> the value of **index** can equal the data source length.)

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDataAdd

```TypeScript
onDataAdd(index: number): void
```

Invoked when data is added to the position indicated by the specified index.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the position where data is added. The value range is [0, data source length - 1].<br>If the value is less than 0, it is treated as **0**. If the value is greater than the data source length minus 1, it is treated as the data source length minus 1. |

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the position where data is added. The value range is [0, data source length - 1].<br>If the value is less than 0, it is treated as **0**. If the value is greater than the data source length minus 1, it is treated as the data source length minus 1. |

## onDataChange

```TypeScript
onDataChange(index: number): void
```

Invoked when data in the position indicated by the specified index is changed.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the position where data is changed. The value range is [0, data source length - 1].<br>If the value is less than 0, it is treated as **0**. If the value is greater than the data source length minus 1, it is treated as the data source length minus 1. |

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Listener for data changes. The value range is [0, data source length - 1].<br>If the value is less than 0, it is treated as **0**. If the value is greater than the data source length minus 1, it is treated as the data source length minus 1. |

## onDataDelete

```TypeScript
onDataDelete(index: number): void
```

Invoked when data is deleted from the position indicated by the specified index. LazyForEach will update the displayed content accordingly.

> **NOTE:** 
> 
> Before **onDataDelete** is called, ensure that the corresponding data in **dataSource** has been deleted.
> Otherwise, undefined behavior will occur during page rendering.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the position where data is deleted. The value range is [0, data source length - 1].<br>If the value is less than 0, it is treated as **0**. If the value is greater than the data source length minus 1, it is treated as the data source length minus 1. |

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
> The ID must remain unchanged before and after data movement. If the ID changes, APIs for deleting and adding data
> must be called.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| from | number | Yes | Original position of data. The value range is [0, data source length - 1].<br>If the value is less than 0, it is treated as **0**. If the value is greater than the data source length minus 1, it is treated as the data source length minus 1. |
| to | number | Yes | Target position of data. The value range is [0, data source length - 1].<br>If the value is less than 0, it is treated as **0**. If the value is greater than the data source length minus 1, it is treated as the data source length minus 1. |

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| from | number | Yes | Original position of data. The value range is [0, data source length - 1].<br>If the value is less than 0, it is treated as **0**. If the value is greater than the data source length minus 1, it is treated as the data source length minus 1. |
| to | number | Yes | Target position of data. The value range is [0, data source length - 1].<br>If the value is less than 0, it is treated as **0**. If the value is greater than the data source length minus 1, it is treated as the data source length minus 1. |

## onDataReloaded

```TypeScript
onDataReloaded(): void
```

Invoked when all data is reloaded. For data items whose key remains unchanged, the original child component is used. For data items whose key changes, a new child component is created.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

<a id="ondatareloaded-1"></a>

## onDataReloaded

```TypeScript
onDataReloaded(reuseImmediately: boolean): void
```

Invoked when all data is reloaded. When \@Reuseable or \@ReuseableV2 is used and recycle pool is empty, old child components will be recycled and then be reused as new child components. If no old child component can be reused, new child components will be created.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| reuseImmediately | boolean | Yes | Whether to enable the feature that reuse old child components when \@Reuseable or \@ReuseableV2 is used and recycle pool is empty.<br> **true**: Enable the feature. <br>**false**: Disable the feature. |

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dataOperations | [DataOperation](arkts-arkui-lazyforeach-comp-dataoperation-t.md)[] | Yes | Array of data operations performed. |
