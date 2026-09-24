# setBadgeNumber

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## setBadgeNumber

```TypeScript
function setBadgeNumber(badgeNumber: number, callback: AsyncCallback<void>): void
```

Sets the notification badge number. This API uses an asynchronous callback to return the result.

A badge is a numeric identifier displayed in the upper right corner of an application's desktop icon, used to prompt the user about the number of unprocessed notifications. After setting, the desktop icon will display the corresponding badge number. This is suitable for scenarios where the number of pending messages needs to be prompted on the desktop icon, such as the number of unread messages and to-do items.

This API can be properly called on devices other than wearables. If it is called on wearables, error code 801 is returned.

**Since:** 10

**System capability:** SystemCapability.Notification.Notification

**See also:** [getActiveNotificationCount](arkts-notification-notificationmanager-getactivenotificationcount-f.md) obtains the number of active notifications of this application.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| badgeNumber | number | Yes | Notification badge number to set. If **badgeNumber** is set to a value less than or equal to **0**, badges are cleared; if the value is greater than **99**, **99+** is displayed on the badge. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600012](../errorcode-notification.md#1600012-insufficient-memory-space) | No memory space. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let setBadgeNumberCallback = (err: BusinessError): void => {
  if (err) {
    console.error(`Failed to set badge number. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in setting badge number.`);
  }
}
let badgeNumber: number = 10;
notificationManager.setBadgeNumber(badgeNumber, setBadgeNumberCallback);
```


<a id="setbadgenumber-1"></a>

## setBadgeNumber

```TypeScript
function setBadgeNumber(badgeNumber: number): Promise<void>
```

Sets the notification badge number. This API uses a promise to return the result.

A badge is a numeric identifier displayed in the upper right corner of an application's desktop icon, used to prompt the user about the number of unprocessed notifications. After setting, the desktop icon will display the corresponding badge number. This is suitable for scenarios where the number of pending messages needs to be prompted on the desktop icon, such as the number of unread messages and to-do items.

This API can be properly called on devices other than wearables. If it is called on wearables, error code 801 is returned.

**Since:** 10

**System capability:** SystemCapability.Notification.Notification

**See also:** [getActiveNotificationCount](arkts-notification-notificationmanager-getactivenotificationcount-f.md) obtains the number of active notifications of this application.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| badgeNumber | number | Yes | Notification badge number to set. If **badgeNumber** is set to a value less than or equal to **0**, badges are cleared; if the value is greater than **99**, **99+** is displayed on the badge. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600012](../errorcode-notification.md#1600012-insufficient-memory-space) | No memory space. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let badgeNumber: number = 10;
notificationManager.setBadgeNumber(badgeNumber).then(() => {
  console.info(`Succeeded in setting badge number.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set badge number. Code is ${err.code}, message is ${err.message}`);
});
```
