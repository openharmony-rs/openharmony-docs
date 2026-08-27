# SystemUpdateCallback（系统接口）

```TypeScript
export type SystemUpdateCallback = (data: SubscribeCallbackData) => void
```

type SystemUpdateCallback = (data: SubscribeCallbackData) =&gt; void 返回携带系统属性值通知信息的回调函数类型。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [SubscribeCallbackData](arkts-notification-notificationsubscriber-subscribecallbackdata-i-sys.md) | 是 | 返回携带系统属性值的通知信息。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onSystemUpdate: (data: notificationSubscribe.SubscribeCallbackData) => {
    let req = data.request;
    console.info(`onSystemUpdate callback req.priorityType: ${req.priorityNotificationType}`);
  }
};
notificationSubscribe.subscribeNotification(subscriber).then(() => {
  console.info('subscribeNotification success');
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```
