# getActiveNotifications

## Modules to Import

```TypeScript
```

<a id="getactivenotifications1"></a>

## getActiveNotifications

```TypeScript
function getActiveNotifications(callback: AsyncCallback<Array<NotificationRequest>>): void
```

Obtains active notifications of this application. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getActiveNotifications](arkts-notification-notificationmanager-getactivenotifications-f.md)

<!--Device-notification-function getActiveNotifications(callback: AsyncCallback<Array<NotificationRequest>>): void--><!--Device-notification-function getActiveNotifications(callback: AsyncCallback<Array<NotificationRequest>>): void-End-->

**System capability:** SystemCapability.Notification.Notification

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[NotificationRequest](arkts-notification-notificationrequest-i.md)&gt;&gt; | Yes | Callback used to return the result. |


<a id="getactivenotifications2"></a>

## getActiveNotifications

```TypeScript
function getActiveNotifications(): Promise<Array<NotificationRequest>>
```

Obtains active notifications of this application. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getActiveNotifications](arkts-notification-notificationmanager-getactivenotifications-f.md)

<!--Device-notification-function getActiveNotifications(): Promise<Array<NotificationRequest>>--><!--Device-notification-function getActiveNotifications(): Promise<Array<NotificationRequest>>-End-->

**System capability:** SystemCapability.Notification.Notification

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[NotificationRequest](arkts-notification-notificationrequest-i.md)&gt;&gt; | Promise used to return the result. |
