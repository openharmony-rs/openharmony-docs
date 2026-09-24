# getExternalVolumeInfos

## Modules to Import

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
```

## getExternalVolumeInfos

```TypeScript
function getExternalVolumeInfos(): Promise<Array<ExternalVolumeInfo>>
```

Obtains information about all external storage volumes. This API uses a promise to return the result.

**Since:** 26.0.1

**Required permissions:** ohos.permission.GET_STORAGE_VOLUME_INFO

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[ExternalVolumeInfo](arkts-corefile-volumemanager-externalvolumeinfo-i.md)&gt;&gt; | Promise used to return the external storage volume information list. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| 13600001 | IPC error. |
