# VirtualFileOnRead

```TypeScript
type VirtualFileOnRead = (id: string, offset: number, length: number) => Promise<Uint8Array>
```

Callback that reads at most **length** bytes from a virtual file. A single request is at most 5 MiB.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-uniformDataStruct-type VirtualFileOnRead = (id: string, offset: long, length: int) => Promise<Uint8Array>--><!--Device-uniformDataStruct-type VirtualFileOnRead = (id: string, offset: long, length: int) => Promise<Uint8Array>-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | Identifier of the virtual file. |
| offset | number | Yes | Zero-based byte offset to read. |
| length | number | Yes | Maximum number of bytes to read. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Uint8Array&gt; | File bytes returned through a promise. An empty array indicates end of file. |
