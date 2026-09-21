# removeDoNotDisturbProfile (System API)

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## removeDoNotDisturbProfile

```TypeScript
function removeDoNotDisturbProfile(templates: Array<DoNotDisturbProfile>): Promise<void>
```

Deletes the Do Not Disturb profile. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| templates | Array&lt;[DoNotDisturbProfile](arkts-notification-notificationmanager-donotdisturbprofile-i-sys.md)&gt; | Yes | Do Not Disturb profile. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600012](../errorcode-notification.md#1600012-insufficient-memory-space) | No memory space. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let templates: Array<notificationManager.DoNotDisturbProfile> = [
  {
    id: 3,
    name: 'working mode'
  }
]
notificationManager.removeDoNotDisturbProfile(templates).then(() => {
  console.info("removeDoNotDisturbProfile success.");
}).catch((err: BusinessError) => {
  console.error(`removeDoNotDisturbProfile failed, code is ${err.code}, message is ${err.message}`);
});
```


<a id="removedonotdisturbprofile-1"></a>

## removeDoNotDisturbProfile

```TypeScript
function removeDoNotDisturbProfile(templates: Array<DoNotDisturbProfile>, userId: number): Promise<void>
```

Deletes the Do Not Disturb profile of a specified user. This API uses a promise to return the result.

**Since:** 23

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| templates | Array&lt;[DoNotDisturbProfile](arkts-notification-notificationmanager-donotdisturbprofile-i-sys.md)&gt; | Yes | Do Not Disturb profile. |
| userId | number | Yes | ID of the target user. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600008](../errorcode-notification.md#1600008-user-not-found) | The user does not exist. |
| [1600012](../errorcode-notification.md#1600012-insufficient-memory-space) | No memory space. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let userId : number = 100;
let templates: Array<notificationManager.DoNotDisturbProfile> = [
  {
    id: 3,
    name: 'working mode'
  }
]
notificationManager.removeDoNotDisturbProfile(templates, userId).then(() => {
  console.info("removeDoNotDisturbProfile success.");
}).catch((err: BusinessError) => {
  console.error(`removeDoNotDisturbProfile failed, code is ${err.code}, message is ${err.message}`);
});
```
