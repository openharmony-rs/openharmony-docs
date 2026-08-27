# EnabledSilentReminderChangedCallback（系统接口）

```TypeScript
export type EnabledSilentReminderChangedCallback = (callbackData: EnabledSilentReminderCallbackData) => void
```

注册应用通知静默提醒使能状态变化的回调函数类型。 type EnabledSilentReminderChangedCallback = (callbackData: EnabledSilentReminderCallbackData) =&gt; void

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackData | [EnabledSilentReminderCallbackData](arkts-notification-notificationsubscriber-enabledsilentremindercallbackdata-i-sys.md) | 是 | 回调返回监听到的静默提醒使能状态信息。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let onEnabledSilentReminderChangedCallback: notificationSubscribe.EnabledSilentReminderChangedCallback = (callbackData: notificationSubscribe.EnabledSilentReminderCallbackData) => {
  console.info('bundle: ', callbackData.bundle);
  console.info('uid: ', callbackData.uid);
  console.info('enable: ', callbackData.enableStatus);
};

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onEnabledSilentReminderChanged: onEnabledSilentReminderChangedCallback
};

notificationSubscribe.subscribeNotification(subscriber).then(() => {
  console.info('subscribeNotification success');
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```
