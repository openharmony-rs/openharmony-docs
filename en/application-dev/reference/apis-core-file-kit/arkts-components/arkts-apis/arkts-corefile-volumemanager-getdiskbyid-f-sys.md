# getDiskById (System API)

## Modules to Import

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
```

## getDiskById

```TypeScript
function getDiskById(diskId: string): Promise<Disk>
```

Querying disk information based on the disk ID.

**Since:** 26.0.0

**Required permissions:** ohos.permission.MOUNT_UNMOUNT_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| diskId | string | Yes | The diskId of disk. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Disk](arkts-corefile-volumemanager-disk-i-sys.md)&gt; | return Promise |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| 13600001 | IPC error. |
| 13600008 | No such object. |
| 13600010 | The input parameter is invalid. |
