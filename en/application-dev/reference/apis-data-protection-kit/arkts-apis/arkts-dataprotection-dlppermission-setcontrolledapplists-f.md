# setControlledAppLists

## Modules to Import

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## setControlledAppLists

```TypeScript
function setControlledAppLists(appLists: Array<string>, userId?: number): Promise<void>
```

Sets the list of applications controlled by enterprise DLP. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.DLP_POLICY_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.DataLossPrevention

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appLists | Array&lt;string&gt; | Yes | List of application identifiers of the controlled applications.<br>The maximum length of the array is 100. If the length exceeds 100, error code 19100001 is returned. <br>Each element in the array is the appIdentifier of the application. The maximum length of a single application identifier is 4096 bytes. If the length exceeds 4096 bytes, error code 19100001 is returned. |
| userId | number | No | ID of the user for whom the controlled application is configured. If this parameter is not specified, the current user is used by default.<br>The value should be an integer. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [19100001](../errorcode-dlp.md#19100001-invalid-parameter) | Invalid parameter value. |
| [19100011](../errorcode-dlp.md#19100011-system-service-abnormal) | The system ability works abnormally. |
| [19100023](../errorcode-dlp.md#19100023-specified-user-id-inconsistent-with-the-current-user-id) | The specified userId is inconsistent with the current userId. |
| [19100024](../errorcode-dlp.md#19100024-personal-space-users-cannot-set-controlled-apps) | The specified userId belongs to a personal space user and cannot be managed. |

**Examples**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { BusinessError } from '@kit.BasicServicesKit';

let appList: Array<string> = ['appId1', 'appId2'];
let userId: number = 100;
dlpPermission.setControlledAppLists(appList, userId).then(() => {
  console.info("Successfully set controlled appLists.");
}).catch((error: BusinessError) => {
  console.error(error.message);
}).finally(() => {
  console.info("Completed set controlled appLists operation.");
});
```
