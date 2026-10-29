# subscribe（系统接口）

## 导入模块

```TypeScript
```

## subscribe

```TypeScript
function subscribe(subscriber: NotificationSubscriber, callback: AsyncCallback<void>): void
```

订阅当前用户下所有应用的通知（callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [subscribe](arkts-notification-notificationsubscribe-subscribe-f-sys.md#subscribe-1)(subscriber: NotificationSubscriber, callback: AsyncCallback&lt;void&gt;)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function subscribe(subscriber: NotificationSubscriber, callback: AsyncCallback<void>): void--><!--Device-notification-function subscribe(subscriber: NotificationSubscriber, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscriber | [NotificationSubscriber](arkts-notification-notificationsubscriber-i-sys.md) | 是 | [通知订阅](../../../notification/notification-glossary.md#notification-subscription通知订阅)对象。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 订阅动作回调函数。 |

<!--Del-->
**示例**

```TypeScript
import Base from '@ohos.base';
import NotificationSubscribe from '@ohos.notificationSubscribe';

let subscribeCallback = (err: Base.BusinessError) => {
  if (err) {
    console.error("subscribe failed " + JSON.stringify(err));
  } else {
    console.info("subscribe success");
  }
}
function onConsumeCallback(data: NotificationSubscribe.SubscribeCallbackData) {
  console.info("Consume callback: " + JSON.stringify(data));
}
let subscriber: NotificationSubscribe.NotificationSubscriber = {
  onConsume: onConsumeCallback
};
Notification.subscribe(subscriber, subscribeCallback);
```

<!--DelEnd-->


## subscribe

```TypeScript
function subscribe(
    subscriber: NotificationSubscriber,
    info: NotificationSubscribeInfo,
    callback: AsyncCallback<void>
  ): void
```

订阅通知并指定订阅信息（callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [subscribe](arkts-notification-notificationsubscribe-subscribe-f-sys.md#subscribe-2)(subscriber: NotificationSubscriber, info: NotificationSubscribeInfo, callback: AsyncCallback&lt;void&gt;)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function subscribe(    subscriber: NotificationSubscriber,    info: NotificationSubscribeInfo,    callback: AsyncCallback<void>  ): void--><!--Device-notification-function subscribe(    subscriber: NotificationSubscriber,    info: NotificationSubscribeInfo,    callback: AsyncCallback<void>  ): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscriber | [NotificationSubscriber](arkts-notification-notificationsubscriber-i-sys.md) | 是 | [通知订阅](../../../notification/notification-glossary.md#notification-subscription通知订阅)对象。 |
| info | [NotificationSubscribeInfo](arkts-notification-notificationsubscribeinfo-i-sys.md) | 是 | 通知订阅信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 订阅动作回调函数。 |

<!--Del-->
**示例**

```TypeScript
import Base from '@ohos.base';
import NotificationSubscribe from '@ohos.notificationSubscribe';

// subscribe回调
let subscribeCallback = (err: Base.BusinessError) => {
  if (err) {
    console.error("subscribe failed " + JSON.stringify(err));
  } else {
    console.info("subscribe success");
  }
}
let onConsumeCallback = (data: NotificationSubscribe.SubscribeCallbackData) => {
  console.info("Consume callback: " + JSON.stringify(data));
}
let subscriber: NotificationSubscribe.NotificationSubscriber = {
  onConsume: onConsumeCallback
};
let info: NotificationSubscribe.NotificationSubscribeInfo = {
  bundleNames: ["bundleName1", "bundleName2"]
};
Notification.subscribe(subscriber, info, subscribeCallback);
```

<!--DelEnd-->


## subscribe

```TypeScript
function subscribe(subscriber: NotificationSubscriber, info?: NotificationSubscribeInfo): Promise<void>
```

订阅通知并指定订阅信息（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [subscribe](arkts-notification-notificationsubscribe-subscribe-f-sys.md#subscribe-3)(subscriber: NotificationSubscriber, info?: NotificationSubscribeInfo)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function subscribe(subscriber: NotificationSubscriber, info?: NotificationSubscribeInfo): Promise<void>--><!--Device-notification-function subscribe(subscriber: NotificationSubscriber, info?: NotificationSubscribeInfo): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscriber | [NotificationSubscriber](arkts-notification-notificationsubscriber-i-sys.md) | 是 | [通知订阅](../../../notification/notification-glossary.md#notification-subscription通知订阅)对象。 |
| info | [NotificationSubscribeInfo](arkts-notification-notificationsubscribeinfo-i-sys.md) | 否 | 通知订阅信息，默认为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

<!--Del-->
**示例**

```TypeScript
import Base from '@ohos.base';
import NotificationSubscribe from '@ohos.notificationSubscribe';

function onConsumeCallback(data: NotificationSubscribe.SubscribeCallbackData) {
  console.info("Consume callback: " + JSON.stringify(data));
}
let subscriber: NotificationSubscribe.NotificationSubscriber = {
  onConsume: onConsumeCallback
};
Notification.subscribe(subscriber).then(() => {
  console.info("subscribe success");
}).catch((err: Base.BusinessError) => {
  console.error(`subscribe failed, code is ${err}`);
});
```

<!--DelEnd-->
