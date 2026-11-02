# DataProgressListener

```TypeScript
type DataProgressListener = (progressInfo: ProgressInfo, data: UnifiedData | null) => void
```

Defines the listener callback used to obtain progress information and data.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-unifiedDataChannel-type DataProgressListener = (progressInfo: ProgressInfo, data: UnifiedData | null) => void--><!--Device-unifiedDataChannel-type DataProgressListener = (progressInfo: ProgressInfo, data: UnifiedData | null) => void-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| progressInfo | [ProgressInfo](arkts-arkdata-unifieddatachannel-progressinfo-i.md) | Yes | Progress information reported for the drag-and-drop task, including the progress status and progress percentage. It contains two fields: progress (progress percentage, ranging from -1 to 100) and status (task status code). A progress value of -1 indicates a failure to obtain data, and 100 indicates that data obtaining is complete. |
| data | [UnifiedData](arkts-arkdata-unifieddatachannel-unifieddata-c.md) &#124; null | Yes | Data obtained when the progress reaches 100. Returns null when the progress has not reached 100. |
