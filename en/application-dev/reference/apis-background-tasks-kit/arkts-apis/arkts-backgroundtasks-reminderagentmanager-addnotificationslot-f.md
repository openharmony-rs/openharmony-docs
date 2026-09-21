# addNotificationSlot

## Modules to Import

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

## addNotificationSlot

```TypeScript
function addNotificationSlot(slot: NotificationSlot, callback: AsyncCallback<void>): void
```

Adds a notification slot. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slot | [NotificationSlot](../../apis-notification-kit/arkts-apis/arkts-notification-notificationslot-notificationslot-i.md) | Yes | Notification slot instance. Only the **notificationType** property can be set. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the notification slot is added, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

let mySlot: notificationManager.NotificationSlot = {
  notificationType: notificationManager.SlotType.SOCIAL_COMMUNICATION
}

reminderAgentManager.addNotificationSlot(mySlot, (err: BusinessError) => {
  if (err.code) {
    console.error("callback err code:" + err.code + " message:" + err.message);
  } else {
    console.info("addNotificationSlot callback");
  }
});
```


<a id="addnotificationslot-1"></a>

## addNotificationSlot

```TypeScript
function addNotificationSlot(slot: NotificationSlot): Promise<void>
```

Adds a notification slot. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slot | [NotificationSlot](../../apis-notification-kit/arkts-apis/arkts-notification-notificationslot-notificationslot-i.md) | Yes | Notification slot instance. Only the **notificationType** property can be set. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

let mySlot: notificationManager.NotificationSlot = {
  notificationType: notificationManager.SlotType.SOCIAL_COMMUNICATION
}
reminderAgentManager.addNotificationSlot(mySlot).then(() => {
  console.info("addNotificationSlot promise");
}).catch((err: BusinessError) => {
  console.error("promise err code:" + err.code + " message:" + err.message);
});
```
