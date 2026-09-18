# getSecurityLabelSync

## Modules to Import

```TypeScript
import { securityLabel } from '@kit.CoreFileKit';
```

## getSecurityLabelSync

```TypeScript
function getSecurityLabelSync(path: string): string
```

Obtains the data security level of a file or directory in synchronous mode. If no data security level has been set, **s3** is returned by default.

**Since:** 9

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | File path. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Promise used to return the data security level. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900007 | Arg list too long |
| 13900015 | File exists |
| 13900020 | Invalid argument |
| 13900025 | No space left on device |
| 13900037 | No data available |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

**Examples**

```TypeScript
let filePath = pathDir + '/test.txt';
let type = securityLabel.getSecurityLabelSync(filePath);
console.info("getSecurityLabel successfully, Label: " + type);
```
