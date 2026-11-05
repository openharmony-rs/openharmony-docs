# VirtualFileOnStat

```TypeScript
type VirtualFileOnStat = (id: string) => Promise<VirtualFileItem>
```

Callback that obtains current metadata for a virtual file.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-uniformDataStruct-type VirtualFileOnStat = (id: string) => Promise<VirtualFileItem>--><!--Device-uniformDataStruct-type VirtualFileOnStat = (id: string) => Promise<VirtualFileItem>-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | Identifier of the virtual file. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[VirtualFileItem](arkts-arkdata-uniformdatastruct-virtualfileitem-i.md)&gt; | Virtual file metadata returned through a promise. |
