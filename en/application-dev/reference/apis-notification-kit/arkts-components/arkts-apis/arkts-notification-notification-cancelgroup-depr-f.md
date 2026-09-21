# cancelGroup

## Modules to Import

```TypeScript
```

## cancelGroup

```TypeScript
function cancelGroup(groupName: string, callback: AsyncCallback<void>): void
```

Cancels notifications under a notification group of this application. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [cancelGroup](arkts-notification-notificationmanager-cancelgroup-f.md)

**System capability:** SystemCapability.Notification.Notification

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| groupName | string | Yes | Name of the notification group, which is specified through [NotificationRequest](arkts-notification-notificationrequest-notificationrequest-i.md) when the notification is published. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |


<a id="cancelgroup-1"></a>

## cancelGroup

```TypeScript
function cancelGroup(groupName: string): Promise<void>
```

Cancels notifications under a notification group of this application. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [cancelGroup](arkts-notification-notificationmanager-cancelgroup-f.md)

**System capability:** SystemCapability.Notification.Notification

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| groupName | string | Yes | Name of the notification group. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |
