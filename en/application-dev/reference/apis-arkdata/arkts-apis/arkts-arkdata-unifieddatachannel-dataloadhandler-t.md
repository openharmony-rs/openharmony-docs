# DataLoadHandler

```TypeScript
type DataLoadHandler = (acceptableInfo?: DataLoadInfo) => UnifiedData | null
```

Defines the handler for delayed data loading. It allows the data sender to dynamically generate data based on the information passed in by the receiver, enabling more flexible and precise data interaction strategies. This handler is a synchronous function and is suitable for simple business logic. If the business logic is complex or takes a long time to execute (more than 3 seconds), use the asynchronous handler [DelayedDataLoadHandler](arkts-arkdata-unifieddatachannel-delayeddataloadhandler-t.md).

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-unifiedDataChannel-type DataLoadHandler = (acceptableInfo?: DataLoadInfo) => UnifiedData | null--><!--Device-unifiedDataChannel-type DataLoadHandler = (acceptableInfo?: DataLoadInfo) => UnifiedData | null-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| acceptableInfo | [DataLoadInfo](arkts-arkdata-unifieddatachannel-dataloadinfo-i.md) | No | Data types and quantity that the data receiver can accept. The default value is empty. |

**Return value:**

| Type | Description |
| --- | --- |
| [UnifiedData](arkts-arkdata-unifieddatachannel-unifieddata-c.md) &#124; null | UnifiedData object generated based on the receiver information when the delayed handler is triggered, used for data transfer. If the data cannot be generated or generation fails, null is returned. |
