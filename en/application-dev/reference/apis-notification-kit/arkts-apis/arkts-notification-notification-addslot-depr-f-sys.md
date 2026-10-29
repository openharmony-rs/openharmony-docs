# addSlot (System API)

## Modules to Import

```TypeScript
```

## addSlot

```TypeScript
function addSlot(slot: NotificationSlot, callback: AsyncCallback<void>): void
```

Adds a notification slot. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [addSlot](arkts-notification-notificationmanager-addslot-f-sys.md#addslot-1)(slot: NotificationSlot, callback: AsyncCallback&lt;void&gt;)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function addSlot(slot: NotificationSlot, callback: AsyncCallback<void>): void--><!--Device-notification-function addSlot(slot: NotificationSlot, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slot | [NotificationSlot](arkts-notification-notificationslot-i.md) | Yes | Notification slot to add. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

<!--Del-->
**Examples**

```TypeScript
import NotificationManager from '@ohos.notificationManager';
import Base from '@ohos.base';

// addSlot callback
let addSlotCallback = (err: Base.BusinessError) => {
  if (err) {
    console.error("addSlot failed " + JSON.stringify(err));
  } else {
    console.info("addSlot success");
  }
}
// NotificationSlot object
let notificationSlot: NotificationManager.NotificationSlot = {
  type: Notification.SlotType.SOCIAL_COMMUNICATION
};
Notification.addSlot(notificationSlot, addSlotCallback);
```

<!--DelEnd-->


## addSlot

```TypeScript
function addSlot(slot: NotificationSlot): Promise<void>
```

Adds a notification slot. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [addSlot](arkts-notification-notificationmanager-addslot-f-sys.md#addslot-2)(slot: NotificationSlot)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function addSlot(slot: NotificationSlot): Promise<void>--><!--Device-notification-function addSlot(slot: NotificationSlot): Promise<void>-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slot | [NotificationSlot](arkts-notification-notificationslot-i.md) | Yes | Notification slot to add. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

<!--Del-->
**Examples**

```TypeScript
import NotificationManager from '@ohos.notificationManager';
import Base from '@ohos.base';

// NotificationSlot object
let notificationSlot: NotificationManager.NotificationSlot = {
    type: Notification.SlotType.SOCIAL_COMMUNICATION
};
Notification.addSlot(notificationSlot).then(() => {
  console.info("addSlot success");
}).catch((err: Base.BusinessError) => {
  console.error(`addSlot failed, code is ${err}`);
});
```

<!--DelEnd-->
