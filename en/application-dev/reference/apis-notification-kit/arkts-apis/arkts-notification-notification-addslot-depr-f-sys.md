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

**Substitutes:** [addSlot](arkts-notification-notificationmanager-addslot-f.md)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slot | [NotificationSlot](arkts-notification-notificationslot-notificationslot-i.md) | Yes | Notification slot to add. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |


## addSlot

```TypeScript
function addSlot(slot: NotificationSlot): Promise<void>
```

Adds a notification slot. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [addSlot](arkts-notification-notificationmanager-addslot-f.md)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slot | [NotificationSlot](arkts-notification-notificationslot-notificationslot-i.md) | Yes | Notification slot to add. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |
