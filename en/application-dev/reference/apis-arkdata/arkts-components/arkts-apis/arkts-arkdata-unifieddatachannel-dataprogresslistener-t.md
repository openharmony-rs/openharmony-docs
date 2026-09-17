# DataProgressListener

```TypeScript
type DataProgressListener = (progressInfo: ProgressInfo, data: UnifiedData | null) => void
```

Defines the callback used to return the data retrieval progress information and data obtained.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| progressInfo | [ProgressInfo](arkts-arkdata-unifieddatachannel-progressinfo-i.md) | Yes | Progress information to report. |
| data | [UnifiedData](arkts-arkdata-unifieddatachannel-unifieddata-c.md) &#124; null | Yes | Data obtained when the progress reaches 100. If the progress does not reach 10 0, **null** is returned. |
