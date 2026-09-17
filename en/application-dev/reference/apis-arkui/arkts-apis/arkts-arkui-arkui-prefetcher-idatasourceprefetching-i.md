# IDataSourcePrefetching

Extends the [IDataSource](../arkts-components/arkts-arkui-idatasource-i.md) API to provide a data source that can be prefetched.

**Inheritance/Implementation:** IDataSourcePrefetching extends [IDataSource](../arkts-components/arkts-arkui-idatasource-i.md)

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { IDataSourcePrefetching, IPrefetcher, BasicPrefetcher } from '@kit.ArkUI';
```

## cancel

```TypeScript
cancel?(index: number): Promise<void> | void
```

Cancels the prefetching of a specified data item from the dataset. This API can be either synchronous or asynchronous. This API is optional. If the data source does not implement this API, the prefetching cancellation operation will not be performed.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the data item whose prefetching is to be canceled. The value range is [0, **totalCount()** – 1]. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; &#124; void | Promise when this API is executed asynchronously; no return value when this API is executed synchronously. The promise only indicates that the operation is completed and contains no actual return content. |

## prefetch

```TypeScript
prefetch(index: number): Promise<void> | void
```

Prefetches a specified data item from the dataset. This API can be either synchronous or asynchronous. When the visible area changes, the prefetching algorithm calls this API if it determines that the data item about to enter the visible area needs to be prefetched.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the data item to be prefetched. The value range is [0, **totalCount()** – 1]. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; &#124; void | Promise when this API is executed asynchronously; no return value when this API is executed synchronously. The promise only indicates that the operation is completed and contains no actual return content. |
