# getOriginalFileName

## Modules to Import

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## getOriginalFileName

```TypeScript
function getOriginalFileName(fileName: string): string
```

Obtains the original name of a DLP file. This API returns the result synchronously.

Determine the file type based on the original file name extension and select an application to open the file.

**Since:** 10

**System capability:** SystemCapability.Security.DataLossPrevention

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fileName | string | Yes | Name of the target DLP file. The value contains 1 to 255 bytes. If the value is out of range, error code 401 is thrown. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Original name of the DLP file obtained. For example, if the DLP file name is **test.txt.dlp**, the original file name returned is **test.txt**. The value contains up to 255 bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because car not support DLP feature.<br>**Applicable version:** 26.1.0 and later |
| [19100001](../errorcode-dlp.md#19100001-invalid-parameter) | Invalid parameter value. |
| [19100011](../errorcode-dlp.md#19100011-system-service-abnormal) | The system ability works abnormally. |

**Examples**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

let originalFileName = dlpPermission.getOriginalFileName('test.txt.dlp'); // Obtain the original file name.
console.info('originalFileName:', originalFileName);
```
