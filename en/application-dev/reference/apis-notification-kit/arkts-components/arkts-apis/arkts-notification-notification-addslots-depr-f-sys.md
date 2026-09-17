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

**Substitutes:** [addSlots](arkts-notification-notificationmanager-addslots-f-sys.md)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slots | Array&lt;[NotificationSlot](arkts-notification-notificationslot-notificationslot-i.md)&gt; | Yes | Notification slots to add. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |


## addSlots

```TypeScript
function addSlots(slots: Array<NotificationSlot>): Promise<void>
```

Adds an array of notification slots. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [addSlots](arkts-notification-notificationmanager-addslots-f-sys.md)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slots | Array&lt;[NotificationSlot](arkts-notification-notificationslot-notificationslot-i.md)&gt; | Yes | Notification slots to add. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |
