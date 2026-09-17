# getSlots

## Modules to Import

```TypeScript
```

## getSlots

```TypeScript
function getSlots(callback: AsyncCallback<Array<NotificationSlot>>): void
```

Obtains all notification slots. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getSlots](arkts-notification-notificationmanager-getslots-f.md)

**System capability:** SystemCapability.Notification.Notification

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[NotificationSlot](arkts-notification-notificationslot-notificationslot-i.md)&gt;&gt; | Yes | Callback used to return the result. |


## getSlots

```TypeScript
function getSlots(): Promise<Array<NotificationSlot>>
```

Obtains all notification slots of this application. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getSlots](arkts-notification-notificationmanager-getslots-f.md)

**System capability:** SystemCapability.Notification.Notification

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[NotificationSlot](arkts-notification-notificationslot-notificationslot-i.md)&gt;&gt; | Promise used to return the result. |
