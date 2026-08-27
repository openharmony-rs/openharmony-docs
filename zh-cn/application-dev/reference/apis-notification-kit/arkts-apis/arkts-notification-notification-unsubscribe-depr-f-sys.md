# unsubscribe（系统接口）

## 导入模块

```TypeScript
```

## unsubscribe

```TypeScript
function unsubscribe(subscriber: NotificationSubscriber, callback: AsyncCallback<void>): void
```

取消订阅（callbcak形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [unsubscribe](arkts-notification-notificationsubscribe-unsubscribe-f-sys.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscriber | [NotificationSubscriber](arkts-notification-notificationsubscriber-notificationsubscriber-i-sys.md) | 是 | 通知订阅对象。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 取消订阅动作回调函数。 |

**示例**

```TypeScript
import Base from '@ohos.base';
import NotificationSubscribe from '@ohos.notificationSubscribe';

let unsubscribeCallback = (err: Base.BusinessError) => {
  if (err) {
    console.error("unsubscribe failed " + JSON.stringify(err));
  } else {
    console.info("unsubscribe success");
  }
}
let onDisconnectCallback = () => {
  console.info("subscribe disconnect");
}
let subscriber: NotificationSubscribe.NotificationSubscriber = {
  onDisconnect: onDisconnectCallback
};
Notification.unsubscribe(subscriber, unsubscribeCallback);
```


## unsubscribe

```TypeScript
function unsubscribe(subscriber: NotificationSubscriber): Promise<void>
```

取消订阅（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [unsubscribe](arkts-notification-notificationsubscribe-unsubscribe-f-sys.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscriber | [NotificationSubscriber](arkts-notification-notificationsubscriber-notificationsubscriber-i-sys.md) | 是 | 通知订阅对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 无返回结果的Promise对象。 |

**示例**

```TypeScript
import Base from '@ohos.base';
import NotificationSubscribe from '@ohos.notificationSubscribe';

function onDisconnectCallback() {
  console.info("subscribe disconnect");
}
let subscriber: NotificationSubscribe.NotificationSubscriber = {
  onDisconnect: onDisconnectCallback
};
Notification.unsubscribe(subscriber).then(() => {
  console.info("unsubscribe success");
}).catch((err: Base.BusinessError) => {
  console.error(`unsubscribe failed, code is ${err}`);
});
```
