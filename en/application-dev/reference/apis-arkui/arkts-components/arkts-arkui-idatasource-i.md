# IDataSource

Data source of **LazyForEach**.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getData

```TypeScript
getData(index: number): any
```

Obtains the data item that matches the specified index.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the data record to obtain. The value range is [0, data source length - 1]. |

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

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| listener | [DataChangeListener](arkts-arkui-datachangelistener-i.md) | Yes | Listener for data changes. |

## totalCount

```TypeScript
totalCount(): number
```

Obtains the total number of data items.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

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

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| listener | [DataChangeListener](arkts-arkui-datachangelistener-i.md) | Yes | Listener for data changes. |
