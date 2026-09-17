# deletePartition (System API)

## Modules to Import

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
```

## deletePartition

```TypeScript
function deletePartition(diskId: string, partitionNum: number): Promise<void>
```

Deletes a partition on a disk. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.MOUNT_FORMAT_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| diskId | string | Yes | Disk ID. |
| partitionNum | number | Yes | Partition number. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| 13600001 | IPC error. |
| 13600005 | Incorrect volume state. |
| 13600008 | No such object. |
| 13600010 | The input parameter is invalid. |
| 13600023 | Delete partition failed. |
