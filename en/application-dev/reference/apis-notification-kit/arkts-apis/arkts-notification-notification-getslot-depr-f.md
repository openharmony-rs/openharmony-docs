# getSlot

## Modules to Import

```TypeScript
```

## getSlot

```TypeScript
function getSlot(slotType: SlotType, callback: AsyncCallback<NotificationSlot>): void
```

Obtains a notification slot of a specified type. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getSlot](arkts-notification-notificationmanager-getslot-f.md#getslot-1)(slotType: SlotType, callback: AsyncCallback&lt;NotificationSlot&gt;)

<!--Device-notification-function getSlot(slotType: SlotType, callback: AsyncCallback<NotificationSlot>): void--><!--Device-notification-function getSlot(slotType: SlotType, callback: AsyncCallback<NotificationSlot>): void-End-->

**System capability:** SystemCapability.Notification.Notification

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotType | SlotType | Yes | [Notification slot](../../../notification/notification-glossary.md#notification-slot) type, currently divided into social communication, service reminder, content consultation, and other types. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[NotificationSlot](arkts-notification-notificationslot-i.md)&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import Base from '@ohos.base';

// getSlot callback
let getSlotCallback = (err: Base.BusinessError) => {
  if (err) {
    console.error("getSlot failed " + JSON.stringify(err));
  } else {
    console.info("getSlot success");
  }
}
let slotType: Notification.SlotType = Notification.SlotType.SOCIAL_COMMUNICATION;
Notification.getSlot(slotType, getSlotCallback);
```


## getSlot

```TypeScript
function getSlot(slotType: SlotType): Promise<NotificationSlot>
```

Obtains a notification slot of a specified type. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getSlot](arkts-notification-notificationmanager-getslot-f.md#getslot-3)(slotType: SlotType)

<!--Device-notification-function getSlot(slotType: SlotType): Promise<NotificationSlot>--><!--Device-notification-function getSlot(slotType: SlotType): Promise<NotificationSlot>-End-->

**System capability:** SystemCapability.Notification.Notification

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotType | SlotType | Yes | Type of the [Notification slot](../../../notification/notification-glossary.md#notification-slot), currently divided into social communication, service reminder, content consultation, and other types. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[NotificationSlot](arkts-notification-notificationslot-i.md)&gt; | Promise used to return the result. |

**Examples**

```TypeScript
import Base from '@ohos.base';

let slotType: Notification.SlotType = Notification.SlotType.SOCIAL_COMMUNICATION;
Notification.getSlot(slotType).then((data) => {
  console.info("getSlot success, data: " + JSON.stringify(data));
}).catch((err: Base.BusinessError) => {
  console.error(`getSlot failed, code is ${err}`);
});
```
