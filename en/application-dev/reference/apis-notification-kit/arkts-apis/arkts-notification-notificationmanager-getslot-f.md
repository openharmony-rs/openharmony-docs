# getSlot

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## getSlot

```TypeScript
function getSlot(slotType: SlotType, callback: AsyncCallback<NotificationSlot>): void
```

Obtains a notification slot of a specified type. This API uses an asynchronous callback to return the result.

This API is used to query the detailed configuration information of a created notification slot, including settings such as reminder method, level, and lock screen display. A corresponding type of notification slot must be created first through addSlot, otherwise the obtained result will be empty.

**Since:** 9

**System capability:** SystemCapability.Notification.Notification

**See also:**

[addSlot](arkts-notification-notificationmanager-addslot-f.md) adds a notification slot of a specified type.

[removeSlot](arkts-notification-notificationmanager-removeslot-f.md) removes a notification slot of a specified type for this application.

[removeAllSlots](arkts-notification-notificationmanager-removeallslots-f.md) removes all notification slots for this application.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotType | [SlotType](arkts-notification-notificationmanager-slottype-e.md) | Yes | Notification slot type, such as social communication, service reminder, and content consultation. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[NotificationSlot](arkts-notification-notificationmanager-notificationslot-t.md)&gt; | Yes | Callback used to return the result. If the notification slot is obtained successfully, **err** is **undefined** and **data** is the obtained **NotificationSlot**; otherwise, **err** is an error object. |

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

// getSlot callback
let getSlotCallback = (err: BusinessError, data: notificationManager.NotificationSlot): void => {
  if (err) {
    console.error(`Failed to get slot. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in getting slot, data is ${JSON.stringify(data)}`);
  }
}
let slotType: notificationManager.SlotType = notificationManager.SlotType.SOCIAL_COMMUNICATION;
notificationManager.getSlot(slotType, getSlotCallback);
```


<a id="getslot-2"></a>

## getSlot

```TypeScript
function getSlot(slotType: SlotType): Promise<NotificationSlot>
```

Obtains a notification slot of a specified type. This API uses a promise to return the result.

This API is used to query the detailed configuration information of a created notification slot, including settings such as reminder method, level, and lock screen display. A corresponding type of notification slot must be created first through addSlot, otherwise the obtained result will be empty.

**Since:** 9

**System capability:** SystemCapability.Notification.Notification

**See also:**

[addSlot](arkts-notification-notificationmanager-addslot-f.md) adds a notification slot of a specified type.

[removeSlot](arkts-notification-notificationmanager-removeslot-f.md#removeslot-1) removes a notification slot of a specified type for this application.

[removeAllSlots](arkts-notification-notificationmanager-removeallslots-f.md) removes all notification slots for this application.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotType | [SlotType](arkts-notification-notificationmanager-slottype-e.md) | Yes | Notification slot type, such as social communication, service reminder, and content consultation. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[NotificationSlot](arkts-notification-notificationmanager-notificationslot-t.md)&gt; | Promise used to return the result. |

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

let slotType: notificationManager.SlotType = notificationManager.SlotType.SOCIAL_COMMUNICATION;
notificationManager.getSlot(slotType).then((data: notificationManager.NotificationSlot) => {
  console.info(`Succeeded in getting slot, data is ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get slot. Code is ${err.code}, message is ${err.message}`);
});
```
