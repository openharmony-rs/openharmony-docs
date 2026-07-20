# subscribe（系统接口）

<a id="subscribe"></a>
## subscribe

```TypeScript
function subscribe(subscriber: NotificationSubscriber, callback: AsyncCallback<void>): void
```

订阅当前用户下所有应用的通知。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** subscribe

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function subscribe(subscriber: NotificationSubscriber, callback: AsyncCallback<void>): void--><!--Device-notification-function subscribe(subscriber: NotificationSubscriber, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscriber | [NotificationSubscriber](arkts-notification-notificationsubscriber-notificationsubscriber-i-sys.md) | 是 | 通知订阅对象。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 订阅动作回调函数。 |


<a id="subscribe-1"></a>
## subscribe

```TypeScript
function subscribe(
    subscriber: NotificationSubscriber,
    info: NotificationSubscribeInfo,
    callback: AsyncCallback<void>
  ): void
```

订阅通知并指定订阅信息。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** subscribe

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function subscribe(
    subscriber: NotificationSubscriber,
    info: NotificationSubscribeInfo,
    callback: AsyncCallback<void>
  ): void--><!--Device-notification-function subscribe(
    subscriber: NotificationSubscriber,
    info: NotificationSubscribeInfo,
    callback: AsyncCallback<void>
  ): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscriber | [NotificationSubscriber](arkts-notification-notificationsubscriber-notificationsubscriber-i-sys.md) | 是 | 通知订阅对象。 |
| info | [NotificationSubscribeInfo](arkts-notification-notificationsubscribeinfo-notificationsubscribeinfo-i-sys.md) | 是 | 通知订阅信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 订阅动作回调函数。 |


<a id="subscribe-2"></a>
## subscribe

```TypeScript
function subscribe(subscriber: NotificationSubscriber, info?: NotificationSubscribeInfo): Promise<void>
```

订阅通知并指定订阅信息。使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** subscribe

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function subscribe(subscriber: NotificationSubscriber, info?: NotificationSubscribeInfo): Promise<void>--><!--Device-notification-function subscribe(subscriber: NotificationSubscriber, info?: NotificationSubscribeInfo): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscriber | [NotificationSubscriber](arkts-notification-notificationsubscriber-notificationsubscriber-i-sys.md) | 是 | 通知订阅对象。 |
| info | [NotificationSubscribeInfo](arkts-notification-notificationsubscribeinfo-notificationsubscribeinfo-i-sys.md) | 否 | 通知订阅信息，默认为空（当为空时，表示订阅当前用户下所有应用的通知，否则表示订阅通知并指定订阅信息）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

