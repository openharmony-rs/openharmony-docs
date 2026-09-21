# getAllNotificationEnabledBundles (System API)

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## getAllNotificationEnabledBundles

```TypeScript
function getAllNotificationEnabledBundles(): Promise<Array<BundleOption>>
```

Obtains a list of applications that allow notifications. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[BundleOption](arkts-notification-notificationmanager-bundleoption-t.md)&gt;&gt; | Returns a list of applications that allow notifications. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.getAllNotificationEnabledBundles().then((data: Array<notificationManager.BundleOption>) => {
    console.info(`Enable bundle data is ${JSON.stringify(data)}`);
    data.forEach(element => {
        console.info(`Enable uid is ${JSON.stringify(element.uid)}`);
        console.info(`Enable bundle is ${JSON.stringify(element.bundle)}`);
    });
}).catch((err: BusinessError) => {
    console.error(`getAllNotificationEnabledBundles failed, code is ${err.code}, message is ${err.message}`);
})
```


<a id="getallnotificationenabledbundles-1"></a>

## getAllNotificationEnabledBundles

```TypeScript
function getAllNotificationEnabledBundles(userId: number): Promise<Array<BundleOption>>
```

Obtains the list of applications that are allowed to publish notifications by a specified user. This API uses a promise to return the result.

**Since:** 23

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | Target user. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[BundleOption](arkts-notification-notificationmanager-bundleoption-t.md)&gt;&gt; | Returns a list of applications that allow notifications. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600008](../errorcode-notification.md#1600008-user-not-found) | The user does not exist. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let userId : number = 100;

notificationManager.getAllNotificationEnabledBundles(userId).then((data: Array<notificationManager.BundleOption>) => {
  console.info(`Enable bundle data is ${JSON.stringify(data)}`);
  data.forEach(element => {
    console.info(`Enable uid is ${JSON.stringify(element.uid)}`);
    console.info(`Enable bundle is ${JSON.stringify(element.bundle)}`);
  });
}).catch((err: BusinessError) => {
  console.error(`getAllNotificationEnabledBundles failed, code is ${err.code}, message is ${err.message}`);
});
```
