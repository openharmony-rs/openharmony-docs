# getPermissionUsedRecordToggleStatus (System API)

## Modules to Import

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
```

## getPermissionUsedRecordToggleStatus

```TypeScript
function getPermissionUsedRecordToggleStatus(): Promise<boolean>
```

A system application can call this API to obtain the current user's permission usage record toggle status, for example, to display the current toggle setting status on the permission management interface. This API uses a promise to return the result.

**Since:** 18

**Required permissions:** ohos.permission.PERMISSION_USED_STATS

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the switch status value of the current user is on, and **false** indicates that the switch status value of the current user is off. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. Interface caller does not have permission"ohos.permission.PERMISSION_USED_STATS". |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system app. Interface caller is not a system app. |
| [12100004](../errorcode-access-token.md#12100004-listener-apis-not-used-in-pairs) | This API must be used together with [setPermissionUsedRecordToggleStatus](arkts-ability-privacymanager-setpermissionusedrecordtogglestatus-f-sys.md).<br>**Applicable version:** 26.0.1 and later |
| [12100007](../errorcode-access-token.md#12100007-system-service-not-working-properly) | Service exception. |

**Examples**

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Query permission usage record switch status
privacyManager.getPermissionUsedRecordToggleStatus().then((status) => {
  console.info('getPermissionUsedRecordToggleStatus success');
  if (status == true) {
    console.info('get status is TRUE');
  } else {
    console.info('get status is FALSE');
  }
}).catch((err: BusinessError): void => {
  console.error(`getPermissionUsedRecordToggleStatus fail, code: ${err.code}, message: ${err.message}`);
});
```


<a id="getpermissionusedrecordtogglestatus-1"></a>

## getPermissionUsedRecordToggleStatus

```TypeScript
function getPermissionUsedRecordToggleStatus(subProfileId: number): Promise<boolean>
```

A system application can call this API to obtain the permission usage record toggle status for a specified sub-profile, for example, to display the current toggle setting status on the permission management interface. This API uses a promise to return the result.

**Since:** 26.0.1

**Required permissions:** ohos.permission.PERMISSION_USED_STATS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| subProfileId | number | Yes | ID of the sub-profile. It can be obtained from [OsAccountSubProfile.id](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-osaccountsubprofile-i-sys.md#id). <br>The value should be an integer. Value constraint: This parameter must be an integer greater than 0. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the toggle is enabled for the specified sub-profile, and **false** indicates that it is disabled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. Interface caller does not have permission"ohos.permission.PERMISSION_USED_STATS". |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system app. Interface caller is not a system app. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [12100001](../errorcode-access-token.md#12100001-invalid-parameters) | Invalid parameter. The specified subProfileId does not exist for the current user. |
| [12100007](../errorcode-access-token.md#12100007-system-service-not-working-properly) | Service exception. |

**Examples**

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let subProfileId: number = 100001; // Replace with the valid ID of the current user's sub-profile.
privacyManager.getPermissionUsedRecordToggleStatus(subProfileId).then((status: boolean) => {
  console.info(`getPermissionUsedRecordToggleStatus success, status: ${status}`);
}).catch((err: BusinessError): void => {
  console.error(`getPermissionUsedRecordToggleStatus fail, code: ${err.code}, message: ${err.message}`);
});
```
