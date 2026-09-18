# setDlpFeature (System API)

## Modules to Import

```TypeScript
import { dlpSetDlpFeature } from '@kit.DataProtectionKit';
```

## setDlpFeature

```TypeScript
function setDlpFeature(status: DlpFeatureStatus): Promise<StatusInfoResult>
```

Sets the DLP status. This API uses a promise to return the result. The system enables or disables the DLP protection function based on the DLP status specified using this API.

When this feature is enabled, right-click the file to be encrypted, and the encryption option is displayed in the shortcut menu. Files in .txt,pdf,xls,xlsx,ppt,pptx,doc, and .docx formats can be encrypted.

This API is used to enable or disable the DLP function in enterprise policies.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.DataLossPrevention

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| status | [DlpFeatureStatus](arkts-dataprotection-dlpsetdlpfeature-dlpfeaturestatus-e-sys.md) | Yes | DLP status. The value **ENABLED_FEATURE** indicates the DLP feature is enabled, and the encryption option is displayed in the menu. The value **NOT_ENABLED_FEATURE** indicates the DLP feature is disabled, and the encryption option is not displayed in the menu. If the value is out of range, error code 401 is thrown. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[StatusInfoResult](arkts-dataprotection-dlpsetdlpfeature-statusinforesult-i-sys.md)&gt; | Promise used to return the DLP status that is set. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because car not support DLP feature.<br>**Applicable version:** 26.1.0 and later |
| [19100001](../errorcode-dlp.md#19100001-invalid-parameter) | Invalid parameter value. |
| [19100011](../errorcode-dlp.md#19100011-system-service-abnormal) | The system ability works abnormally. |

**Examples**

```TypeScript
import { dlpSetDlpFeature } from '@kit.DataProtectionKit';

async function exampleFunction() {
  let statusInfoResult: dlpSetDlpFeature.StatusInfoResult =
    await dlpSetDlpFeature.setDlpFeature(dlpSetDlpFeature.DlpFeatureStatus.ENABLED_FEATURE);
  console.info('setDlpFeature result: ', JSON.stringify(statusInfoResult)); 
} // Set the DLP status.

exampleFunction();
```
