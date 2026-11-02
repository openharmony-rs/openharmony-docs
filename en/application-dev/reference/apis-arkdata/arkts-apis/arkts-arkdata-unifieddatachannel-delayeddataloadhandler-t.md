# DelayedDataLoadHandler

```TypeScript
type DelayedDataLoadHandler = (acceptableInfo?: DataLoadInfo) => Promise<UnifiedData | null>
```

Defines the handler for delayed data loading. It allows the data sender to dynamically generate data based on the information passed in by the receiver, enabling a more flexible and precise data interaction strategy. The result is returned asynchronously through a promise.

This handler is an asynchronous function that does not block the main thread. It can handle complex business logic and execute long-running tasks.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-unifiedDataChannel-type DelayedDataLoadHandler = (acceptableInfo?: DataLoadInfo) => Promise<UnifiedData | null>--><!--Device-unifiedDataChannel-type DelayedDataLoadHandler = (acceptableInfo?: DataLoadInfo) => Promise<UnifiedData | null>-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| acceptableInfo | [DataLoadInfo](arkts-arkdata-unifieddatachannel-dataloadinfo-i.md) | No | Data types and quantity that the data receiver can accept. The default value is empty. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[UnifiedData](arkts-arkdata-unifieddatachannel-unifieddata-c.md) &#124; null&gt; | Promise used to return the UnifiedData object generated based on the receiver information, or null. Rejects with error information on failure. |
