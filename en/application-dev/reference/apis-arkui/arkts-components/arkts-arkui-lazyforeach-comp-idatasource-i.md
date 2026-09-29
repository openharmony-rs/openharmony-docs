# IDataSource

```TypeScript
declare interface IDataSource
```

Defines the data source of **LazyForEach**. The developer needs to implement this API to provide data access and data change notification capabilities, including obtaining the total number of data items, obtaining data by index, and registering and unregistering data change listeners.

**Since:** 7

<!--Device-unnamed-declare interface IDataSource--><!--Device-unnamed-declare interface IDataSource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getData

```TypeScript
getData(index: number): any
```

Obtains the data item that matches the specified index.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-IDataSource-getData(index: number): any--><!--Device-IDataSource-getData(index: number): any-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the data. The value range is [0, data source length - 1]. When the value exceeds the range, the behavior is determined by the data source implementation. Developers are advised to perform boundary checks. |

**Return value:**

| Type | Description |
| --- | --- |
| any | Data item that matches the specified index. The actual type is determined by the data source implementation. |

## registerDataChangeListener

```TypeScript
registerDataChangeListener(listener: DataChangeListener): void
```

Registers a listener for data changes.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-IDataSource-registerDataChangeListener(listener: DataChangeListener): void--><!--Device-IDataSource-registerDataChangeListener(listener: DataChangeListener): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| listener | [DataChangeListener](arkts-arkui-lazyforeach-comp-datachangelistener-i.md) | Yes | Data change listener, used to notify components to refresh when the data source changes. |

## totalCount

```TypeScript
totalCount(): number
```

Obtains the total number of data items.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-IDataSource-totalCount(): number--><!--Device-IDataSource-totalCount(): number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Total number of data items, which is subject to the data source. |

## unregisterDataChangeListener

```TypeScript
unregisterDataChangeListener(listener: DataChangeListener): void
```

Unregisters the listener for data changes.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-IDataSource-unregisterDataChangeListener(listener: DataChangeListener): void--><!--Device-IDataSource-unregisterDataChangeListener(listener: DataChangeListener): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| listener | [DataChangeListener](arkts-arkui-lazyforeach-comp-datachangelistener-i.md) | Yes | Data change listener, used to notify components to refresh when the data source changes. |
