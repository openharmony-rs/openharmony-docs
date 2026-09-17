# NotificationSubscriber（系统接口）

提供订阅者接收到新通知、取消通知等的回调方法。

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onBadgeChanged

```TypeScript
onBadgeChanged?:(data: BadgeNumberCallbackData) => void
```

回调返回监听到的应用角标数量变化。

**起始版本：** 10

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [BadgeNumberCallbackData](arkts-notification-notificationsubscriber-badgenumbercallbackdata-i-sys.md) | 是 |  |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onBadgeChanged: (data) => {
    console.info('bundle: ', data.bundle);
    console.info('uid: ', data.uid);
    console.info('badgeNumber: ', data.badgeNumber);
  }
};

notificationSubscribe.subscribeNotification(subscriber).then(() => {
  console.info('subscribeNotification success');
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```

## onBatchCancel

```TypeScript
onBatchCancel?: (data: Array<SubscribeCallbackData>) => void
```

批量删除的通知信息。

**起始版本：** 11

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Array&lt;[SubscribeCallbackData](arkts-notification-notificationsubscriber-subscribecallbackdata-i-sys.md)&gt; | 是 |  |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let onBatchCancelCallBack = (data: Array<notificationSubscribe.SubscribeCallbackData>) => {
  console.info('===> onBatchCancel in test');
  let req = data[0].request;
  console.info('===> onBatchCancel callback req.id:' + req.id);
};

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onBatchCancel: onBatchCancelCallBack
};

notificationSubscribe.subscribeNotification(subscriber).then(() => {
  console.info('subscribeNotification success');
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```

## onCancel

```TypeScript
onCancel?:(data: SubscribeCallbackData) => void
```

需要取消的通知信息。

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [SubscribeCallbackData](arkts-notification-notificationsubscriber-subscribecallbackdata-i-sys.md) | 是 |  |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let onCancelCallback = (data: notificationSubscribe.SubscribeCallbackData) => {
  console.info('===> onCancel in test');
  let req = data.request;
  console.info('===> onCancel callback req.id:' + req.id);
}

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onCancel: onCancelCallback
};

notificationSubscribe.subscribeNotification(subscriber).then(() => {
  console.info('subscribeNotification success');
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```

## onConnect

```TypeScript
onConnect?:() => void
```

订阅完成的回调。

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let onConnectCallback = () => {
  console.info('===> onConnect in test');
}

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onConnect: onConnectCallback
};

notificationSubscribe.subscribeNotification(subscriber).then(() => {
  console.info('subscribeNotification success');
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```

## onConsume

```TypeScript
onConsume?:(data: SubscribeCallbackData) => void
```

新接收到的通知信息。

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [SubscribeCallbackData](arkts-notification-notificationsubscriber-subscribecallbackdata-i-sys.md) | 是 |  |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let onConsumeCallback = (data: notificationSubscribe.SubscribeCallbackData) => {
  console.info('===> onConsume in test');
  let req = data.request;
  console.info('===> onConsume callback req.id:' + req.id);
};

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onConsume: onConsumeCallback
};

notificationSubscribe.subscribeNotification(subscriber).then(() => {
  console.info('subscribeNotification success');
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```

## onDestroy

```TypeScript
onDestroy?:() => void
```

服务失联的回调。

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let onDestroyCallback = () => {
  console.info('===> onDestroy in test');
}

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onDestroy: onDestroyCallback
};

notificationSubscribe.subscribeNotification(subscriber).then(() => {
  console.info('subscribeNotification success');
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```

## onDisconnect

```TypeScript
onDisconnect?:() => void
```

取消订阅的回调。

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let unsubscribeCallback = (err: BusinessError) => {
  if (err) {
    console.error(`unsubscribe failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('unsubscribeCallback');
  }
};

let onConnectCallback = () => {
  console.info('===> onConnect in test');
}
let onDisconnectCallback = () => {
  console.info('===> onDisconnect in test');
}

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onConnect: onConnectCallback,
  onDisconnect: onDisconnectCallback
};

// 订阅通知后会收到onConnect回调
notificationSubscribe.subscribeNotification(subscriber).then(() => {
  console.info('subscribeNotification success');
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
// 取消订阅后会收到onDisconnect回调
notificationSubscribe.unsubscribe(subscriber, unsubscribeCallback);
```

## onDoNotDisturbChanged

```TypeScript
onDoNotDisturbChanged?: (mode: notificationManager.DoNotDisturbDate) => void
```

回调返回免打扰时间选项变更。

**起始版本：** 11

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [notificationManager.DoNotDisturbDate](arkts-notification-notificationmanager-donotdisturbdate-i-sys.md) | 是 |  |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { notificationSubscribe, notificationManager } from '@kit.NotificationKit';

let onDoNotDisturbChangedCallback = (mode: notificationManager.DoNotDisturbDate) => {
  console.info(`===> onDoNotDisturbChanged: ${JSON.stringify(mode)}`);
}

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onDoNotDisturbChanged: onDoNotDisturbChangedCallback
};

notificationSubscribe.subscribeNotification(subscriber).then(() => {
  console.info('subscribeNotification success');
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```

## onDoNotDisturbDateChange

```TypeScript
onDoNotDisturbDateChange?: (mode: notification.DoNotDisturbDate) => void
```

回调返回免打扰时间选项变更。

**起始版本：** 8

**废弃版本：** 11

**替代接口：** [onDoNotDisturbChanged](#ondonotdisturbchanged)

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [notification.DoNotDisturbDate](arkts-notification-notification-donotdisturbdate-depr-i-sys.md) | 是 |  |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import Notification from '@ohos.notification';

let subscribeCallback = (err: BusinessError) => {
  if (err) {
    console.error(`subscribe failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('subscribeCallback');
  }
};

let onDoNotDisturbDateChangeCallback = (mode: Notification.DoNotDisturbDate) => {
  console.info('===> onDoNotDisturbDateChange:' + mode);
}

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onDoNotDisturbDateChange: onDoNotDisturbDateChangeCallback
};

notificationSubscribe.subscribe(subscriber, subscribeCallback);
```

## onEnabledNotificationChanged

```TypeScript
onEnabledNotificationChanged?:(callbackData: EnabledNotificationCallbackData) => void
```

回调返回监听到的应用信息。

**起始版本：** 8

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackData | [EnabledNotificationCallbackData](arkts-notification-notificationsubscriber-enablednotificationcallbackdata-i-sys.md) | 是 |  |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let onEnabledNotificationChangedCallback = (callbackData: notificationSubscribe.EnabledNotificationCallbackData) => {
  console.info('bundle: ', callbackData.bundle);
  console.info('uid: ', callbackData.uid);
  console.info('enable: ', callbackData.enable);
};

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onEnabledNotificationChanged: onEnabledNotificationChangedCallback
};

notificationSubscribe.subscribeNotification(subscriber).then(() => {
  console.info('subscribeNotification success');
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```

## onEnabledPriorityByBundleChanged

```TypeScript
onEnabledPriorityByBundleChanged?: (callbackData: EnabledPriorityNotificationByBundleCallbackData) => void
```

返回应用通知优先级开关状态。

**起始版本：** 23

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackData | [EnabledPriorityNotificationByBundleCallbackData](arkts-notification-notificationsubscriber-enabledprioritynotificationbybundlecallbackdata-i-sys.md) | 是 |  |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onEnabledPriorityByBundleChanged: (callbackData: notificationSubscribe.EnabledPriorityNotificationByBundleCallbackData) => {
    console.info(`onEnabledPriorityByBundleChanged: ${JSON.stringify(callbackData)}`);
  }
};
notificationSubscribe.subscribeNotification(subscriber).then(() => {
  console.info('subscribeNotification success');
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```

## onEnabledPriorityChanged

```TypeScript
onEnabledPriorityChanged?: (callbackData: EnabledPriorityNotificationCallbackData) => void
```

返回通知优先级总开关状态。

**起始版本：** 23

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackData | [EnabledPriorityNotificationCallbackData](arkts-notification-notificationsubscriber-enabledprioritynotificationcallbackdata-i-sys.md) | 是 |  |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onEnabledPriorityChanged: (callbackData: notificationSubscribe.EnabledPriorityNotificationCallbackData) => {
    console.info(`onEnabledPriorityChanged: ${JSON.stringify(callbackData)}`);
  }
};
notificationSubscribe.subscribeNotification(subscriber).then(() => {
  console.info('subscribeNotification success');
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```

## onEnabledSilentReminderChanged

```TypeScript
onEnabledSilentReminderChanged?: EnabledSilentReminderChangedCallback
```

返回应用通知静默提醒的使能状态变化。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onNotificationSwitchChanged

```TypeScript
onNotificationSwitchChanged?: NotificationSwitchChangedCallback
```

返回由[notificationManager.setNotificationSwitch]{@link../@ohos.notificationManager:notificationManager.setNotificationSwitch}接口设置的通知开关状态变化。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onSystemUpdate

```TypeScript
onSystemUpdate?: SystemUpdateCallback
```

返回携带系统属性值的通知信息。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## onUpdate

```TypeScript
onUpdate?:(data: NotificationSortingMap) => void
```

最新的通知排序列表。

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [NotificationSortingMap](arkts-notification-notificationsortingmap-notificationsortingmap-i-sys.md) | 是 |  |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onUpdate: (map) => {
    console.info(`===> onUpdateCallback map: ${JSON.stringify(map)}`);
  }
};

notificationSubscribe.subscribeNotification(subscriber).then(() => {
  console.info('subscribeNotification success');
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```

## onBadgeEnabledChanged

```TypeScript
onBadgeEnabledChanged?: BadgeEnabledChangedCallback
```

返回应用角标的使能状态变化。

**类型：** [BadgeEnabledChangedCallback](arkts-notification-notificationsubscriber-badgeenabledchangedcallback-i-sys.md)

**起始版本：** 12

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。
