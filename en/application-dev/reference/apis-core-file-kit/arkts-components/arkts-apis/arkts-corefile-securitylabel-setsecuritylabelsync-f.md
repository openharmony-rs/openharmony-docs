# setSecurityLabelSync

## Modules to Import

```TypeScript
import { securityLabel } from '@kit.CoreFileKit';
```

## setSecurityLabelSync

```TypeScript
function setSecurityLabelSync(path: string, type: DataLevel): void
```

Sets the data security level for a file or directory in synchronous mode. The level can only be adjusted from low to high, or set to the same level.

**Since:** 9

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | File path. |
| type | [DataLevel](arkts-corefile-securitylabel-datalevel-t.md) | Yes | Data security level. The value can only be **s0**, **s1**, **s2**, **s3**, or **s4**. |

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
securityLabel.setSecurityLabelSync(filePath, "s0");
```
