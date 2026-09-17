# getCoreFileSyncState

## Modules to Import

```TypeScript
import { cloudSync } from '@kit.CoreFileKit';
```

## getCoreFileSyncState

```TypeScript
function getCoreFileSyncState(uri: string): FileState
```

Obtains the upload sync state of a cloud file. This API returns the result synchronously.

**Since:** 20

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the file whose sync state is to be obtained. |

**Return value:**

| Type | Description |
| --- | --- |
| [FileState](arkts-corefile-cloudsync-filestate-e.md) | Upload sync state of the given cloud file. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13600001 | IPC error. Possible causes:<br>1.IPC failed or timed out. 2.Failed to load the service. |
| 13900002 | No such file or directory. |
| 13900004 | Interrupted system call |
| 13900010 | Try again |
| 13900012 | Permission denied by the file system |
| 13900020 | Invalid argument. Possible causes:<br>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 13900031 | Function not implemented |
| 14000002 | Invalid URI. |
| 22400005 | Inner error. Possible causes:<br>1.Failed to access the database or execute the SQL statement. <br>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);
try {
  let state = cloudSync.getCoreFileSyncState(uri);
} catch (err) {
  let error:BusinessError = err as BusinessError;
  console.error(`getCoreFileSyncState failed with error ${error.code}, message is ${error.message}`);
}
```
