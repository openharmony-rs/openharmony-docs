# GetDelayData

```TypeScript
type GetDelayData = (type: string) => UnifiedData
```

A deferred wrapper for UnifiedData that supports deferred data retrieval. When the data receiver requests a specific type of data, the system triggers this callback, and the data sender can dynamically generate the data in the callback instead of preparing all data in advance. Currently, only the same-device clipboard scenario is supported.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-unifiedDataChannel-type GetDelayData = (type: string) => UnifiedData--><!--Device-unifiedDataChannel-type GetDelayData = (type: string) => UnifiedData-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Identifier of the deferred data type, used to distinguish different types of data. For the values, see [UniformDataType](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md). For example, 'general.plain-text' indicates the plain text type. |

**Return value:**

| Type | Description |
| --- | --- |
| [UnifiedData](arkts-arkdata-unifieddatachannel-unifieddata-c.md) | UnifiedData object that contains the data of the corresponding type and is returned when the deferred callback is triggered. It can be used for cross-application data sharing and transfer. |
