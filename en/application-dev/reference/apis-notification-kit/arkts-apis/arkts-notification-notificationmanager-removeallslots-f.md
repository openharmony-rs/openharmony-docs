# removeAllSlots

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## removeAllSlots

```TypeScript
function removeAllSlots(callback: AsyncCallback<void>): void
```

Removes all notification slots for this application. This API uses an asynchronous callback to return the result.

After deletion, all notification slots and their configurations of the current application will be permanently removed. When notifications are published subsequently, the system will automatically create slots of the corresponding types. Notifications already published through these slots are not affected and can still be viewed in the notification center. This is suitable for scenarios where all slot configurations need to be cleared at once.

**Since:** 9

**System capability:** SystemCapability.Notification.Notification

**See also:**

[addSlot](arkts-notification-notificationmanager-addslot-f.md) adds a notification slot of a specified type.

[getSlot](arkts-notification-notificationmanager-getslot-f.md) obtains a notification slot of a specified type.

[removeSlots](arkts-notification-notificationmanager-removeslot-f.md) removes all notification slots for this application.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

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

let removeAllSlotsCallback = (err: BusinessError): void => {
  if (err) {
    console.error(`Failed to remove all slots. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in removing all slots.`);
  }
}
notificationManager.removeAllSlots(removeAllSlotsCallback);
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.removeAllSlots().then(() => {
  console.info(`Succeeded in removing all slots.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to remove all slots. Code is ${err.code}, message is ${err.message}`);
});
```


## removeAllSlots

```TypeScript
function removeAllSlots(): Promise<void>
```

Removes all notification slots for this application. This API uses a promise to return the result.

After deletion, all notification slots and their configurations of the current application will be permanently removed. When notifications are published subsequently, the system will automatically create slots of the corresponding types. Notifications already published through these slots are not affected and can still be viewed in the notification center. This is suitable for scenarios where all slot configurations need to be cleared at once.

**Since:** 9

**System capability:** SystemCapability.Notification.Notification

**See also:**

[addSlot](arkts-notification-notificationmanager-addslot-f.md) adds a notification slot of a specified type.

[getSlot](arkts-notification-notificationmanager-getslot-f.md) obtains a notification slot of a specified type.

[removeSlot](arkts-notification-notificationmanager-removeslot-f.md) removes a notification slot of a specified type for this application.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |

**Examples**

See [removeAllSlots](#removeallslots)
