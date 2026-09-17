# recover (System API)

## Modules to Import

```TypeScript
import { trash } from '@kit.CoreFileKit';
```

## recover

```TypeScript
function recover(uri: string): void
```

Recovers a file or directory from the trash.

**Since:** 10

**Deprecated since:** 23

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the file or directory. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900002 | No such file or directory |
| 13900020 | Invalid argument |
| 13900042 | Unknown error |

**Examples**

```TypeScript
let fileinfos = trash.listFile();
let uri = fileinfos[0].uri;
trash.recover(uri);
```
