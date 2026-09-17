# off (System API)

## Modules to Import

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
```

## off('activeStateChange')

```TypeScript
function off(
    type: 'activeStateChange',
    permissionList: Array<Permissions>,
    callback?: Callback<ActiveChangeResponse>): void
```

Unsubscribes from permission usage status change events for a specified permission list. After a successful unsubscription, status change notifications for the specified permission list will no longer be received.

When unsubscribing, if no callback function is passed in, all callback functions under the permissionList are deleted in batch.

> **NOTE:** 
> This API is typically used in conjunction with [on](arkts-ability-privacymanager-on-f-sys.md) to cancel the listening relationship created by on.

**Since:** 9

**Required permissions:** ohos.permission.PERMISSION_USED_STATS

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'activeStateChange' | Yes | Event type. The value is **'activeStateChange'**, which indicates the permission usage change. |
| permissionList | Array&lt;[Permissions](arkts-ability-permissions-t.md)&gt; | Yes | List of permission names to unsubscribe from. If empty, unsubscribes from all permission status changes. Must be consistent with the input of on.<br>Value constraint: The array length cannot exceed 1024. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ActiveChangeResponse](arkts-ability-privacymanager-activechangeresponse-i-sys.md)&gt; | No | Callback used to return the object for unsubscribing from the status change event of the specified tokenId and permission names. Must be consistent with the callback passed to on. If this parameter is not provided, all callback functions under permissionList will be deleted in batch.<br>Value constraint: The array length cannot exceed 1024. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. Interface caller does not have permission"ohos.permission.PERMISSION_USED_STATS". |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system app. Interface caller is not a system app. |
| [12100001](../errorcode-access-token.md#12100001-invalid-parameters) | Invalid parameter. The permissionList is not in the listening list. |
| [12100004](../errorcode-access-token.md#12100004-listener-apis-not-used-in-pairs) | The API is not used in pair with 'on'. |
| [12100007](../errorcode-access-token.md#12100007-system-service-not-working-properly) | Service exception. |
| [12100008](../errorcode-access-token.md#12100008-out-of-memory) | Out of memory. |

**Examples**

```TypeScript
import { privacyManager, Permissions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let permissionList: Array<Permissions> = [];
try {
    // Unsubscribe from permission usage status change events
    privacyManager.off('activeStateChange', permissionList);
} catch (err) {
    let error = err as BusinessError;
    console.error(`Catch errcode: ${error.code}, message: ${error.message}`);
}
```
