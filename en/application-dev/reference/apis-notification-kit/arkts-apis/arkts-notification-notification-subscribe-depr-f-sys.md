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

**Substitutes:** [subscribe](arkts-notification-notificationsubscribe-subscribe-f-sys.md#subscribe-1)(subscriber: NotificationSubscriber, callback: AsyncCallback&lt;void&gt;)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function subscribe(subscriber: NotificationSubscriber, callback: AsyncCallback<void>): void--><!--Device-notification-function subscribe(subscriber: NotificationSubscriber, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| subscriber | [NotificationSubscriber](arkts-notification-notificationsubscriber-i-sys.md) | Yes | [Notification subscription](../../../notification/notification-glossary.md#notification-subscription) object. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

<!--Del-->
**Examples**

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

Subscribes to a notification with the subscription information specified. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [subscribe](arkts-notification-notificationsubscribe-subscribe-f-sys.md#subscribe-2)(subscriber: NotificationSubscriber, info: NotificationSubscribeInfo, callback: AsyncCallback&lt;void&gt;)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function subscribe(    subscriber: NotificationSubscriber,    info: NotificationSubscribeInfo,    callback: AsyncCallback<void>  ): void--><!--Device-notification-function subscribe(    subscriber: NotificationSubscriber,    info: NotificationSubscribeInfo,    callback: AsyncCallback<void>  ): void-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| subscriber | [NotificationSubscriber](arkts-notification-notificationsubscriber-i-sys.md) | Yes | [Notification subscription](../../../notification/notification-glossary.md#notification-subscription) object. |
| info | [NotificationSubscribeInfo](arkts-notification-notificationsubscribeinfo-i-sys.md) | Yes | Notification subscription information. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

<!--Del-->
**Examples**

```TypeScript
import Base from '@ohos.base';
import NotificationSubscribe from '@ohos.notificationSubscribe';

// subscribe callback
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

Subscribes to a notification with the subscription information specified. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [subscribe](arkts-notification-notificationsubscribe-subscribe-f-sys.md#subscribe-3)(subscriber: NotificationSubscriber, info?: NotificationSubscribeInfo)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function subscribe(subscriber: NotificationSubscriber, info?: NotificationSubscribeInfo): Promise<void>--><!--Device-notification-function subscribe(subscriber: NotificationSubscriber, info?: NotificationSubscribeInfo): Promise<void>-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| subscriber | [NotificationSubscriber](arkts-notification-notificationsubscriber-i-sys.md) | Yes | [Notification subscription](../../../notification/notification-glossary.md#notification-subscription) object. |
| info | [NotificationSubscribeInfo](arkts-notification-notificationsubscribeinfo-i-sys.md) | No | Notification subscription information. This parameter is left empty by default. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

<!--Del-->
**Examples**

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
