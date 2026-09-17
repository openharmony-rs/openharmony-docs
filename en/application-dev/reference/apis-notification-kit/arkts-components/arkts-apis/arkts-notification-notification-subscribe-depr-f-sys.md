# subscribe (System API)

## Modules to Import

```TypeScript
```

## subscribe

```TypeScript
function subscribe(subscriber: NotificationSubscriber, callback: AsyncCallback<void>): void
```

Subscribes to notifications of all applications under this user. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [subscribe](arkts-notification-notificationsubscribe-subscribe-f-sys.md)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| subscriber | [NotificationSubscriber](arkts-notification-notificationsubscriber-notificationsubscriber-i-sys.md) | Yes | Notification subscriber. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |


## subscribe

```TypeScript
function subscribe(
    subscriber: NotificationSubscriber,
    info: NotificationSubscribeInfo,
    callback: AsyncCallback<void>
  ): void
```

Subscribes to a notification with the subscription information specified. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [subscribe](arkts-notification-notificationsubscribe-subscribe-f-sys.md)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| subscriber | [NotificationSubscriber](arkts-notification-notificationsubscriber-notificationsubscriber-i-sys.md) | Yes | Notification subscriber. |
| info | [NotificationSubscribeInfo](arkts-notification-notificationsubscribeinfo-notificationsubscribeinfo-i-sys.md) | Yes | Notification subscription information. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |


## subscribe

```TypeScript
function subscribe(subscriber: NotificationSubscriber, info?: NotificationSubscribeInfo): Promise<void>
```

Subscribes to a notification with the subscription information specified. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [subscribe](arkts-notification-notificationsubscribe-subscribe-f-sys.md)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| subscriber | [NotificationSubscriber](arkts-notification-notificationsubscriber-notificationsubscriber-i-sys.md) | Yes | Notification subscriber. |
| info | [NotificationSubscribeInfo](arkts-notification-notificationsubscribeinfo-notificationsubscribeinfo-i-sys.md) | No | Notification subscription information. This parameter is left empty by default. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |
