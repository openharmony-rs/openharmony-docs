# VirtualFileOnCancel

```TypeScript
type VirtualFileOnCancel = (idList: Array<string>) => Promise<void>
```

Callback that cancels pending work for the specified virtual file identifiers.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-uniformDataStruct-type VirtualFileOnCancel = (idList: Array<string>) => Promise<void>--><!--Device-uniformDataStruct-type VirtualFileOnCancel = (idList: Array<string>) => Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| idList | Array&lt;string&gt; | Yes | Identifiers of the virtual files to cancel. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |
