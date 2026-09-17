# scanFile

## Modules to Import

```TypeScript
import { identifySensitiveContent } from '@kit.DataProtectionKit';
```

## scanFile

```TypeScript
function scanFile(filePath: string, identifyPolicies: Array<Policy>): Promise<Array<MatchResult>>
```

Identifies sensitive content in a specified file based on the configured policy and returns the identified result array, including the matched sensitivity labels, matched content, and number of matched items. This API uses a promise to return the result.

**Since:** 21

**Required permissions:** ohos.permission.ENTERPRISE_DATA_IDENTIFY_FILE

**System capability:** SystemCapability.Security.DataLossPrevention

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filePath | string | Yes | File path identified. The path must be a physical path. The file to which the path points must exist and can be accessed. |
| identifyPolicies | Array&lt;[Policy](arkts-dataprotection-identifysensitivecontent-policy-i.md)&gt; | Yes | An array of policies used to identify sensitive content. Each policy defines an identification rule (tags, keywords, and regular expressions). The system scans file content based on these rules and returns the matching result. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[MatchResult](arkts-dataprotection-identifysensitivecontent-matchresult-i.md)&gt;&gt; | Promise used to return the identification result of sensitive content. If the operation is successful, the matching result array is returned. If the operation fails, an error code is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [19110001](../errorcode-dlp.md#19110001-invalid-parameter) | Parameter error. Possible causes: 1. Incorrect policy format. 2. Invalid parameter range. |
| [19110002](../errorcode-dlp.md#19110002-file-sensitive-content-identification-timed-out) | Sensitive file content identification timed out. |
| [19110003](../errorcode-dlp.md#19110003-file-not-supported) | The file is not supported. Possible causes: 1. The file path does not exist. 2. The file type is not supported. 3. The file permission is not supported. |
| [19110004](../errorcode-dlp.md#19110004-system-function-abnormal) | A system error has occurred. |

**Examples**

```TypeScript
import { identifySensitiveContent } from '@kit.DataProtectionKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Define the physical file path to be scanned.
const filePath = '/data/service/el2/100/hmdfs/account/files/Docs/Documents/test.txt';

// Configure the policy for sensitive content identification.
const policies: Array<identifySensitiveContent.Policy> = [
  {"sensitiveLabel":"name", "keywords":["name"], "regex":""},
  {"sensitiveLabel":"phone", "keywords":[], "regex":"phone"},
  {"sensitiveLabel":"address", "keywords":["address"], "regex":"xx City, xx Province"}
];
try {
  identifySensitiveContent.scanFile(filePath, policies).then(records => {
    console.info('scanFile finish');
    for (let i = 0; i < records.length; ++i) {
      const sensitiveLabel = records[i].sensitiveLabel;
      const matchContent = records[i].matchContent;
      const matchNumber = records[i].matchNumber;
      console.info(`scanFile result sensitiveLabel: ${sensitiveLabel} matchNumber ${matchNumber} matchContent ${matchContent}`);
    }
  }).catch((err: BusinessError) => {
    // Identification fails.
    console.error(`Failed to scanFile. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  console.error(`Failed to scanFile. Code: ${err.code}, message: ${err.message}`);
}
```
