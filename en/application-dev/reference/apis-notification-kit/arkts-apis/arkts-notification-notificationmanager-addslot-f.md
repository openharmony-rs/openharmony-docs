# addSlot

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

<a id="addslot-2"></a>

## addSlot

```TypeScript
function addSlot(type: SlotType, callback: AsyncCallback<void>): void
```

Adds a notification slot of a specified type. This API uses an asynchronous callback to return the result.

The notification slot NotificationSlot defines the reminder type (such as alert sound, vibration, and banner) and level of a notification. Before publishing a notification, the application needs to create a corresponding type of notification slot first, or the system will automatically create a corresponding type of notification slot when the notification is published. Only one notification slot of the same type can be created.

**Since:** 9

**System capability:** SystemCapability.Notification.Notification

**See also:**

[getSlot](arkts-notification-notificationmanager-getslot-f.md) obtains a notification slot of a specified type.

[removeSlot](arkts-notification-notificationmanager-removeslot-f.md) removes a notification slot of a specified type for this application.

[removeAllSlots](arkts-notification-notificationmanager-removeallslots-f.md) removes all notification slots for this application.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SlotType](arkts-notification-notificationmanager-slottype-e.md) | Yes | Notification slot type to create. Different slot types correspond to different default SlotLevel values, which affect the notification alert method. For example, **SOCIAL_COMMUNICATION** corresponds to **LEVEL_HIGH** (status bar icon + banner + sound), and **CONTENT_INFORMATION** corresponds to **LEVEL_MIN** (no status bar icon + no banner + no sound). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600012](../errorcode-notification.md#1600012-insufficient-memory-space) | No memory space. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// addSlot callback
let addSlotCallBack = (err: BusinessError): void => {
  if (err) {
    console.error(`Failed to add slot. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in adding slot.`);
  }
}
notificationManager.addSlot(notificationManager.SlotType.SOCIAL_COMMUNICATION, addSlotCallBack);
```


<a id="addslot-3"></a>

## addSlot

```TypeScript
function addSlot(type: SlotType): Promise<void>
```

Adds a notification slot of a specified type. This API uses a promise to return the result.

The notification slot NotificationSlot defines the reminder type (such as alert sound, vibration, and banner) and level of a notification. Before publishing a notification, the application needs to create a corresponding type of notification slot first, or the system will automatically create a corresponding type of notification slot when the notification is published. Only one notification slot of the same type can be created.

**Since:** 9

**System capability:** SystemCapability.Notification.Notification

**See also:**

[getSlot](arkts-notification-notificationmanager-getslot-f.md) obtains a notification slot of a specified type.

[removeSlot](arkts-notification-notificationmanager-removeslot-f.md#removeslot-1) removes a notification slot of a specified type for this application.

[removeAllSlots](arkts-notification-notificationmanager-removeallslots-f.md) removes all notificationslots for this application.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SlotType](arkts-notification-notificationmanager-slottype-e.md) | Yes | Notification slot type to create. Different slot types correspond to different default SlotLevel values, which affect the notification alert method. For example, **SOCIAL_COMMUNICATION** corresponds to **LEVEL_HIGH** (status bar icon + banner + sound), and **CONTENT_INFORMATION** corresponds to **LEVEL_MIN** (no status bar icon + no banner + no sound). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600012](../errorcode-notification.md#1600012-insufficient-memory-space) | No memory space. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.addSlot(notificationManager.SlotType.SOCIAL_COMMUNICATION).then(() => {
  console.info(`Succeeded in adding slot.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to add slot. Code is ${err.code}, message is ${err.message}`);
});
```
