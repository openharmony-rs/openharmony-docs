# @ohos.dlpSetDlpFeature (DLP) (System API)
<!--Kit: Data Protection Kit-->
<!--Subsystem: Security-->
<!--Owner: @winnieHuYu-->
<!--Designer: @QRF-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

This module controls the Data Loss Prevention (DLP) feature, including enabling or disabling DLP and returning the DLP status.

**Use scenarios**
- Data security compliance requirements must be met.
- Access control and encryption protection are provided for confidential files.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 26. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The APIs provided by this module are system APIs.

## Key Classes and APIs

### Key Enums

- **DlpFeatureStatus**: enumerates the DLP statuses, which is used to enable or disable the DLP feature.

### Key APIs

- **StatusInfoResult**: provides information about the DLP settings, including the DLP status.

## Modules to Import

```ts
import { dlpSetDlpFeature } from '@kit.DataProtectionKit';
```

## dlpSetDlpFeature.setDlpFeature

setDlpFeature(status: DlpFeatureStatus): Promise&lt;StatusInfoResult&gt;

Sets the DLP status. This API uses a promise to return the result. The system enables or disables the DLP protection function based on the DLP status specified using this API.

When this feature is enabled, right-click the file to be encrypted, and the encryption option is displayed in the shortcut menu. Files in .txt, .pdf, .xls, .xlsx, .ppt, .pptx, .doc, and .docx formats can be encrypted.

This API is used to enable or disable the DLP function in enterprise policies.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System API:** This is a system API.

**System capability:** SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| status | [DlpFeatureStatus](#dlpfeaturestatus) | Yes| DLP status. The value **ENABLED_FEATURE** indicates the DLP feature is enabled, and the encryption option is displayed in the menu. The value **NOT_ENABLED_FEATURE** indicates the DLP feature is disabled, and the encryption option is not displayed in the menu. If the value is out of range, error code 19100001 is thrown.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;[StatusInfoResult](#statusinforesult)&gt; | Promise used to return the DLP status that is set. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Service Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
| -------- | -------- |
| 202 | Non-system applications use system APIs. |
| 19100001 | Invalid parameter value. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpSetDlpFeature } from '@kit.DataProtectionKit';

async function exampleFunction() {
  let statusInfoResult: dlpSetDlpFeature.StatusInfoResult =
    await dlpSetDlpFeature.setDlpFeature(dlpSetDlpFeature.DlpFeatureStatus.ENABLED_FEATURE); // Record the execution result.
  console.info('setDlpFeature result: ', JSON.stringify(statusInfoResult));
} // Set the DLP status.

exampleFunction();
```

## StatusInfoResult

Describes the DLP settings.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System API:** This is a system API.

**System capability:** SystemCapability.Security.DataLossPrevention

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| isSuccess | boolean | No| No| Whether the DLP setting is successful. The value **true** indicates that the setting is successful, and the value **false** indicates that the setting fails.|

## DLPFeatureInfo

Sets the DLP status.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System API:** This is a system API.

**System capability:** SystemCapability.Security.DataLossPrevention

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| dlpFeatureStatus | [DlpFeatureStatus](#dlpfeaturestatus) | No| No| DLP status, which can be set to **NOT_ENABLED_FEATURE** or **ENABLED_FEATURE**.|

## DlpFeatureStatus

Enumerates DLP statuses.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System API:** This is a system API.

**System capability:** SystemCapability.Security.DataLossPrevention

| Name| Value| Description|
| -------- | -------- | -------- |
| NOT_ENABLED_FEATURE | 0 | DLP disabled.|
| ENABLED_FEATURE | 1 | DLP enabled.|
