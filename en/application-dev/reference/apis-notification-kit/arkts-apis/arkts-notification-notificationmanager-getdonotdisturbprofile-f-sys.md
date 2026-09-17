# getDoNotDisturbProfile (System API)

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## getDoNotDisturbProfile

```TypeScript
function getDoNotDisturbProfile(id: number): Promise<DoNotDisturbProfile>
```

Queries the Do Not Disturb profile. This API uses a promise to return the result.

**Since:** 13

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | number | Yes | ID of the Do Not Disturb profile. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DoNotDisturbProfile](arkts-notification-notificationmanager-donotdisturbprofile-i-sys.md)&gt; | Promise used to return the result. |

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
| [1600019](../errorcode-notification.md#1600019-no-configuration-information-for-a-do-not-disturb-profile) | The do-not-disturb profile does not exist. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.getDoNotDisturbProfile(1).then((data: notificationManager.DoNotDisturbProfile) => {
  console.info(`getDoNotDisturbProfile success: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`getDoNotDisturbProfile failed, code is ${err.code}, message is ${err.message}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let id : number = 101;
let userId : number = 100;

notificationManager.getDoNotDisturbProfile(id, userId).then((data: notificationManager.DoNotDisturbProfile) => {
  console.info(`getDoNotDisturbProfile success: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`getDoNotDisturbProfile failed, code is ${err.code}, message is ${err.message}`);
});
```


## getDoNotDisturbProfile

```TypeScript
function getDoNotDisturbProfile(id: number, userId: number): Promise<DoNotDisturbProfile>
```

Queries the Do Not Disturb profile of a specified user. This API uses a promise to return the result.

**Since:** 23

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | number | Yes | ID of the Do Not Disturb profile. |
| userId | number | Yes | Target user. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DoNotDisturbProfile](arkts-notification-notificationmanager-donotdisturbprofile-i-sys.md)&gt; | Promise used to return the result. |

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
| [1600019](../errorcode-notification.md#1600019-no-configuration-information-for-a-do-not-disturb-profile) | The do-not-disturb profile does not exist. |

**Examples**

See [getDoNotDisturbProfile](#getdonotdisturbprofile)
