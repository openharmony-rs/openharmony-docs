# addSlots (System API)

## Modules to Import

```TypeScript
```

## addSlots

```TypeScript
function addSlots(slots: Array<NotificationSlot>, callback: AsyncCallback<void>): void
```

Adds an array of notification slots. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [addSlots](arkts-notification-notificationmanager-addslots-f-sys.md#addslots-1)(slots: Array&lt;NotificationSlot&gt;, callback: AsyncCallback&lt;void&gt;)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function addSlots(slots: Array<NotificationSlot>, callback: AsyncCallback<void>): void--><!--Device-notification-function addSlots(slots: Array<NotificationSlot>, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slots | Array&lt;[NotificationSlot](arkts-notification-notificationslot-i.md)&gt; | Yes | Notification slots to add. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

<!--Del-->
**Examples**

```TypeScript
import NotificationManager from '@ohos.notificationManager';
import Base from '@ohos.base';

// addSlots callback
let addSlotsCallback = (err: Base.BusinessError) => {
  if (err) {
    console.error("addSlots failed " + JSON.stringify(err));
  } else {
    console.info("addSlots success");
  }
}
// NotificationSlot object
let notificationSlot: NotificationManager.NotificationSlot = {
  type: Notification.SlotType.SOCIAL_COMMUNICATION
};
// NotificationSlotArray object
let notificationSlotArray: NotificationManager.NotificationSlot[] = new Array();
notificationSlotArray[0] = notificationSlot;

Notification.addSlots(notificationSlotArray, addSlotsCallback);
```

<!--DelEnd-->


## addSlots

```TypeScript
function addSlots(slots: Array<NotificationSlot>): Promise<void>
```

Adds an array of notification slots. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [addSlots](arkts-notification-notificationmanager-addslots-f-sys.md#addslots-2)(slots: Array&lt;NotificationSlot&gt;)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function addSlots(slots: Array<NotificationSlot>): Promise<void>--><!--Device-notification-function addSlots(slots: Array<NotificationSlot>): Promise<void>-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slots | Array&lt;[NotificationSlot](arkts-notification-notificationslot-i.md)&gt; | Yes | Notification slots to add. |

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
// NotificationSlotArray object
let notificationSlotArray: NotificationManager.NotificationSlot[] = new Array();
notificationSlotArray[0] = notificationSlot;

Notification.addSlots(notificationSlotArray).then(() => {
  console.info("addSlots success");
}).catch((err: Base.BusinessError) => {
  console.error(`addSlot failed, code is ${err}`);
});
```

<!--DelEnd-->
