# DataLoadHandler

```TypeScript
type DataLoadHandler = (acceptableInfo?: DataLoadInfo) => UnifiedData | null
```

Defines a handler for lazy data loading. The data sender can dynamically generate data based on the information passed by the data receiver to implement more flexible and precise data interaction policies.

This API is a synchronous function and is applicable to simple service logic. If the service logic is complex and the execution time lasts for more than 3s, you are advised to use the asynchronous handler [DelayedDataLoadHandler](arkts-arkdata-unifieddatachannel-delayeddataloadhandler-t.md).

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| acceptableInfo | [DataLoadInfo](arkts-arkdata-unifieddatachannel-dataloadinfo-i.md) | No | Data type and quantity to receive. The default value is empty. |

**Return value:**

| Type | Description |
| --- | --- |
| [UnifiedData](arkts-arkdata-unifieddatachannel-unifieddata-c.md) &#124; null | Returns **UnifiedData** or **null** when the processing function for lazy data loading is triggered. |
