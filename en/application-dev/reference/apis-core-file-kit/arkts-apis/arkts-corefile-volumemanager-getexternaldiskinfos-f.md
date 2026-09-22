# getExternalDiskInfos

## Modules to Import

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
```

## getExternalDiskInfos

```TypeScript
function getExternalDiskInfos(): Promise<Array<ExternalDiskInfo>>
```

Obtains information about all external storage physical disks. This API uses a promise to return the result.

**Since:** 26.0.1

**Required permissions:** ohos.permission.GET_STORAGE_VOLUME_INFO

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[ExternalDiskInfo](arkts-corefile-volumemanager-externaldiskinfo-i.md)&gt;&gt; | Promise used to return the external storage physical disk information list. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| 13600001 | IPC error. |
