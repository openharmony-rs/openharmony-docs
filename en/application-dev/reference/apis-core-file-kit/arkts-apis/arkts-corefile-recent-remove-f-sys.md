# remove (System API)

## Modules to Import

```TypeScript
import { recent } from '@kit.CoreFileKit';
```

## remove

```TypeScript
function remove(uri: string): void
```

Removes the file of the specified URI from the recent file list.

**Since:** 10

**Deprecated since:** 23

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | File URI. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900002 | No such file or directory |
| 13900020 | Invalid argument |
| 13900042 | Unknown error |

**Examples**

```TypeScript
let uri = 'file://docs/storage/Users/currentUser/<publicPath>';
recent.remove(uri);
```
