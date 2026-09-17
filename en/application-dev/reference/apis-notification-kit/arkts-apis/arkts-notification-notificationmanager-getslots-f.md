# getSlots

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## getSlots

```TypeScript
function getSlots(callback: AsyncCallback<Array<NotificationSlot>>): void
```

Obtains all notification slots of this application. This API uses an asynchronous callback to return the result.

This API is used to batch query the configuration information of all notification slots created by the current application, including settings such as the type, reminder method, and level of each slot. This is suitable for scenarios where all slot configurations need to be viewed. The corresponding notification slots must be created through addSlot first; otherwise, the obtained result will be empty.

**Since:** 9

**System capability:** SystemCapability.Notification.Notification

**See also:**

[addSlot](arkts-notification-notificationmanager-addslot-f.md) adds a notification slot of a specified type.

[removeSlot](arkts-notification-notificationmanager-removeslot-f.md) removes a notification slot of a specified type for this application.

[removeAllSlots](arkts-notification-notificationmanager-removeallslots-f.md) removes all notification slots for this application.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[NotificationSlot](arkts-notification-notificationmanager-notificationslot-t.md)&gt;&gt; | Yes | Callback used to return the result. If the notification slots are obtained successfully, **err** is **undefined** and **data** is the obtained **NotificationSlot** array. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// getSlots callback
let getSlotsCallback = (err: BusinessError, data: Array<notificationManager.NotificationSlot>): void => {
  if (err) {
    console.error(`Failed to get slots. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in getting slots, data is ${JSON.stringify(data)}`);
  }
}
notificationManager.getSlots(getSlotsCallback);
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.getSlots().then((data: Array<notificationManager.NotificationSlot>) => {
  console.info(`Succeeded in getting slots, data is ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get slots. Code is ${err.code}, message is ${err.message}`);
});
```


## getSlots

```TypeScript
function getSlots(): Promise<Array<NotificationSlot>>
```

Obtains all notification slots of this application. This API uses a promise to return the result.

This API is used to batch query the configuration information of all notification slots created by the current application, including settings such as the type, reminder method, and level of each slot. This is suitable for scenarios where all slot configurations need to be viewed. The corresponding notification slots must be created through addSlot first; otherwise, the obtained result will be empty.

**Since:** 9

**System capability:** SystemCapability.Notification.Notification

**See also:**

[addSlot](arkts-notification-notificationmanager-addslot-f.md) adds a notification slot of a specified type.

[removeSlot](arkts-notification-notificationmanager-removeslot-f.md) removes a notification slot of a specified type for this application.

[removeAllSlots](arkts-notification-notificationmanager-removeallslots-f.md) removes all notification slots for this application.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[NotificationSlot](arkts-notification-notificationmanager-notificationslot-t.md)&gt;&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |

**Examples**

See [getSlots](#getslots)
