# DelayedDataLoadHandler

```TypeScript
type DelayedDataLoadHandler = (acceptableInfo?: DataLoadInfo) => Promise<UnifiedData | null>
```

Defines a handler for lazy data loading. The data sender can dynamically generate data based on the information passed by the data receiver to implement more flexible and precise data interaction policies.

This API is an asynchronous function, which uses a promise to return the result. It does not block the main thread and can be used to process time-consuming tasks with complex service logic.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| acceptableInfo | [DataLoadInfo](arkts-arkdata-unifieddatachannel-dataloadinfo-i.md) | No | Data type and quantity to receive. The default value is empty. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[UnifiedData](arkts-arkdata-unifieddatachannel-unifieddata-c.md) &#124; null&gt; | Promise used to return the result. |
