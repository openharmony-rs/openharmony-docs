# registerChange

## Modules to Import

```TypeScript
import { cloudSync } from '@kit.CoreFileKit';
```

## registerChange

```TypeScript
function registerChange(uri: string, recursion: boolean, callback: Callback<ChangeData>): void
```

Subscribes to the change of a file. The callback returns the changed data.

**Since:** 12

**System capability:** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the file to download. |
| recursion | boolean | Yes | Whether to listen for the change of the URI, subfiles, and subdirectories. The value **true** means to listen for the change of the URI, subfiles, and subdirectories; the value **false** means to only listen for the change of the URI. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ChangeData](arkts-corefile-cloudsync-changedata-i.md)&gt; | Yes | Callback used to return the changed data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory. |
| 13900012 | Permission denied |
| 14000002 | Invalid uri. |

**Examples**

```TypeScript
import { fileUri } from '@kit.CoreFileKit';

let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);
let onCallback1 = (changeData: cloudSync.ChangeData) => {
  if (changeData.type == cloudSync.NotifyType.NOTIFY_ADDED) {
    // file has been added, do something
  } else if (changeData.type== cloudSync.NotifyType.NOTIFY_DELETED) {
    // file has been removed, do something
  }
}
cloudSync.registerChange(uri, false, onCallback1);
// Unregister the listener.
cloudSync.unregisterChange(uri);
```
