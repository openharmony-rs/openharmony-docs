# on (System API)

## Modules to Import

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
```

## on('activeStateChange')

```TypeScript
function on(type: 'activeStateChange',
    permissionList: Array<Permissions>,
    callback: Callback<ActiveChangeResponse>): void
```

Subscribes to permission usage status change events for a specified permission list. Permission usage status changes are triggered by calls to [startUsingPermission](arkts-ability-privacymanager-startusingpermission-f-sys.md) and [stopUsingPermission](arkts-ability-privacymanager-stopusingpermission-f-sys.md). After a successful subscription, when the permission usage status changes, the callback function is triggered, returning an [ActiveChangeResponse](arkts-ability-privacymanager-activechangeresponse-i-sys.md) object containing details of the permission usage status change. This API uses an asynchronous callback to return the result.

Multiple callback functions are allowed to be subscribed for the same permissionList.

> **NOTE:** 
> It is not allowed to subscribe the same callback function using two permissionLists that have an intersection.
> That is, if two permissionLists contain the same permission name, the same callback function cannot be used for subscription.
> This API is typically used in conjunction with [off](arkts-ability-privacymanager-off-f-sys.md).
> When listening is no longer needed, off should be called to unsubscribe.

**Since:** 9

**Required permissions:** ohos.permission.PERMISSION_USED_STATS

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'activeStateChange' | Yes | Event type. The value is **'activeStateChange'**, which indicates the permission usage change. |
| permissionList | Array&lt;[Permissions](arkts-ability-permissions-t.md)&gt; | Yes | List of subscribed permission names. An empty value indicates subscription to the usage status changes of all permissions. Passing an invalid value returns error code 12100001.<br>Value constraint: The array length cannot exceed 1024. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ActiveChangeResponse](arkts-ability-privacymanager-activechangeresponse-i-sys.md)&gt; | Yes | Callback used to return the object of subscribing to state changes of the specified permission. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. Interface caller does not have permission"ohos.permission.PERMISSION_USED_STATS". |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system app. Interface caller is not a system app. |
| [12100001](../errorcode-access-token.md#12100001-invalid-parameters) | Invalid parameter. The permissionList exceeds the size limit, or the permissionNames in the list are all invalid. |
| [12100004](../errorcode-access-token.md#12100004-listener-apis-not-used-in-pairs) | The API is used repeatedly with the same input. |
| [12100005](../errorcode-access-token.md#12100005-listener-overflows) | The registration time has exceeded the limit. |
| [12100007](../errorcode-access-token.md#12100007-system-service-not-working-properly) | Service exception. |
| [12100008](../errorcode-access-token.md#12100008-out-of-memory) | Out of memory. |

**Examples**

```TypeScript
import { privacyManager, Permissions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let permissionList: Array<Permissions> = [];
try {
    // Subscribe to permission usage status change events
    privacyManager.on('activeStateChange', permissionList, (data: privacyManager.ActiveChangeResponse) => {
        console.debug(`receive permission state change, data: ${data}`);
    });
} catch (err) {
    let error = err as BusinessError;
    console.error(`Catch errcode: ${error.code}, message: ${error.message}`);
}
```
