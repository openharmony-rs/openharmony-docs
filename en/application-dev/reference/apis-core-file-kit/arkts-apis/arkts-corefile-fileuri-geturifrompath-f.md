# getUriFromPath

## Modules to Import

```TypeScript
import { fileUri } from '@kit.CoreFileKit';
```

## getUriFromPath

```TypeScript
function getUriFromPath(path: string): string
```

Get the uri from the path of file in app sandbox

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.FileManagement.AppFileService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | the path of file in app sandbox |

**Return value:**

| Type | Description |
| --- | --- |
| string | Return the file uri |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The input parameter is invalidPossible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |

**Examples**

```TypeScript
let filePath = pathDir + "/test";
let uri = fileUri.getUriFromPath(filePath);
```
