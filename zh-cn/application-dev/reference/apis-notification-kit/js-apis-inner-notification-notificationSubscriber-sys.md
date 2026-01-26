# NotificationSubscriber(系统接口)

作为订阅通知接口[subscribe](./js-apis-notificationSubscribe-sys.md)的入参，提供订阅者接收到新通知、取消通知等的回调方法。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块为系统接口。

## 导入模块

```js
import { notificationSubscribe } from '@kit.NotificationKit';
```

## onConsume

onConsume?: (data: SubscribeCallbackData) => void

接收到新通知的回调函数。

**系统能力**：SystemCapability.Notification.Notification

**系统接口**：此接口为系统接口。

**ArkTS-Dyn起始版本**：7

**ArkTS-Sta起始版本**：20

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------------ | ------------------------ | ---- | -------------------------- |
| onConsume | (data: [SubscribeCallbackData](#subscribecallbackdata)) => void | 否 | 新接收到的通知信息。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let subscribeCallback = (err: BusinessError) => {
  if (err) {
    console.error(`subscribe failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("subscribeCallback");
  }
};

let onConsumeCallback = (data: notificationSubscribe.SubscribeCallbackData) => {
  console.info('===> onConsume in test');
  let req = data.request;
  console.info('===> onConsume callback req.id:' + req.id);
};

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onConsume: onConsumeCallback
};

notificationSubscribe.subscribe(subscriber, subscribeCallback);
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let subscribeCallback = (err: BusinessError | null) => {
  if (err) {
    console.error(`subscribe failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("subscribeCallback");
  }
};

let onConsumeCallback = (data: notificationSubscribe.SubscribeCallbackData) => {
  console.info('===> onConsume in test');
  let req = data.request;
  console.info('===> onConsume callback req.id:' + req.id);
};

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onConsume: onConsumeCallback
};

notificationSubscribe.subscribe(subscriber, subscribeCallback);
```

## onCancel

onCancel?: (data: SubscribeCallbackData) => void

取消通知的回调函数。

**系统能力**：SystemCapability.Notification.Notification

**系统接口**：此接口为系统接口。

**ArkTS-Dyn起始版本**：7

**ArkTS-Sta起始版本**：20

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------------ | ------------------------ | ---- | -------------------------- |
| onCancel | (data: [SubscribeCallbackData](#subscribecallbackdata)) => void | 否 | 需要取消的通知信息。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let subscribeCallback = (err: BusinessError) => {
  if (err) {
    console.error(`subscribe failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("subscribeCallback");
  }
};

let onCancelCallback = (data: notificationSubscribe.SubscribeCallbackData) => {
  console.info('===> onCancel in test');
  let req = data.request;
  console.info('===> onCancel callback req.id:' + req.id);
}

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onCancel: onCancelCallback
};

notificationSubscribe.subscribe(subscriber, subscribeCallback);
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { NotificationSortingMap } from 'notification.notificationSortingMap';

let subscribeCallback = (err: BusinessError | null) => {
  if (err) {
    console.error(`subscribe failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("subscribeCallback");
  }
};

let onCancelCallback = (data: notificationSubscribe.SubscribeCallbackData) => {
  console.info('===> onCancel in test');
  let req = data.request;
  console.info('===> onCancel callback req.id:' + req.id);
}

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onCancel: onCancelCallback
};

notificationSubscribe.subscribe(subscriber, subscribeCallback);
```

## onUpdate

onUpdate?: (data: NotificationSortingMap) => void

更新通知排序的回调函数。预留能力，暂未支持。

**系统能力**：SystemCapability.Notification.Notification

**系统接口**：此接口为系统接口。

**ArkTS-Dyn起始版本**：7

**ArkTS-Sta起始版本**：20

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------------ | ------------------------ | ---- | -------------------------- |
| onUpdate | (data: [NotificationSortingMap](js-apis-inner-notification-notificationSortingMap-sys.md)) => void | 否 | 最新的通知排序列表。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let subscribeCallback = (err: BusinessError) => {
  if (err) {
    console.error(`subscribe failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("subscribeCallback");
  }
};

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onUpdate: (map) => {
    console.info(`===> onUpdateCallback map: ${JSON.stringify(map)}`);
  }
};

notificationSubscribe.subscribe(subscriber, subscribeCallback);
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { NotificationSortingMap } from 'notification.notificationSortingMap';

let subscribeCallback = (err: BusinessError | null) => {
  if (err) {
    console.error(`subscribe failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("subscribeCallback");
  }
};

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onUpdate: (map : NotificationSortingMap) => {
    console.info(`===> onUpdateCallback map: ${JSON.stringify(map)}`);
  }
};

notificationSubscribe.subscribe(subscriber, subscribeCallback);
```

## onConnect

onConnect?: () => void

订阅完成的回调函数。

**系统能力**：SystemCapability.Notification.Notification

**系统接口**：此接口为系统接口。

**ArkTS-Dyn起始版本**：7

**ArkTS-Sta起始版本**：20

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------------ | ------------------------ | ---- | -------------------------- |
| onConnect | () => void | 否 | 订阅完成的回调。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let subscribeCallback = (err: BusinessError) => {
  if (err) {
    console.error(`subscribe failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("subscribeCallback");
  }
};

let onConnectCallback = () => {
  console.info('===> onConnect in test');
}

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onConnect: onConnectCallback
};

notificationSubscribe.subscribe(subscriber, subscribeCallback);
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let subscribeCallback = (err: BusinessError | null) => {
  if (err) {
    console.error(`subscribe failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("subscribeCallback");
  }
};

let onConnectCallback = () => {
  console.info('===> onConnect in test');
}

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onConnect: onConnectCallback
};

notificationSubscribe.subscribe(subscriber, subscribeCallback);
```

## onDisconnect

onDisconnect?: () => void

取消订阅的回调函数。

**系统能力**：SystemCapability.Notification.Notification

**系统接口**：此接口为系统接口。

**ArkTS-Dyn起始版本**：7

**ArkTS-Sta起始版本**：20

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------------ | ------------------------ | ---- | -------------------------- |
| onDisconnect | () => void | 否 | 取消订阅的回调。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let subscribeCallback = (err: BusinessError) => {
  if (err) {
    console.error(`subscribe failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("subscribeCallback");
  }
};
let unsubscribeCallback = (err: BusinessError) => {
  if (err) {
    console.error(`unsubscribe failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("unsubscribeCallback");
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
notificationSubscribe.subscribe(subscriber, subscribeCallback);
// 取消订阅后会收到onDisconnect回调
notificationSubscribe.unsubscribe(subscriber, unsubscribeCallback);
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let subscribeCallback = (err: BusinessError | null) => {
  if (err) {
    console.error(`subscribe failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("subscribeCallback");
  }
};
let unsubscribeCallback = (err: BusinessError | null ) => {
  if (err) {
    console.error(`unsubscribe failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("unsubscribeCallback");
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
notificationSubscribe.subscribe(subscriber, subscribeCallback)
// 取消订阅后会收到onDisconnect回调
notificationSubscribe.unsubscribe(subscriber, unsubscribeCallback);
```

## onDestroy

onDestroy?: () => void

服务失联回调函数。

**系统能力**：SystemCapability.Notification.Notification

**系统接口**：此接口为系统接口。

**ArkTS-Dyn起始版本**：7

**ArkTS-Sta起始版本**：20

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------------ | ------------------------ | ---- | -------------------------- |
| onDestroy | () => void | 否 | 服务失联的回调。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let subscribeCallback = (err: BusinessError) => {
  if (err) {
    console.error(`subscribe failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("subscribeCallback");
  }
};

let onDestroyCallback = () => {
  console.info('===> onDestroy in test');
}

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onDestroy: onDestroyCallback
};

notificationSubscribe.subscribe(subscriber, subscribeCallback);
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let subscribeCallback = (err: BusinessError | null) => {
  if (err) {
    console.error(`subscribe failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("subscribeCallback");
  }
};

let onDestroyCallback = () => {
  console.info('===> onDestroy in test');
}

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onDestroy: onDestroyCallback
};

notificationSubscribe.subscribe(subscriber, subscribeCallback);
```

## onDoNotDisturbDateChange<sup>8+</sup>(deprecated)

onDoNotDisturbDateChange?: (mode: notification.DoNotDisturbDate) => void

免打扰时间选项发生变更时的回调函数。

> **说明：**
>
> 此接口从API version 8开始支持，从API version 11开始不再维护，建议使用[onDoNotDisturbChanged](js-apis-inner-notification-notificationSubscriber-sys.md#ondonotdisturbchanged11)代替。

**系统能力**：SystemCapability.Notification.Notification

**系统接口**：此接口为系统接口。

**ArkTS模式**: 该接口仅适用于ArkTS-Sta。

**ArkTS-Dyn起始版本**：8

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------------ | ------------------------ | ---- | -------------------------- |
| onDoNotDisturbDateChange | (mode: notification.[DoNotDisturbDate](js-apis-notification-sys.md#donotdisturbdate8-deprecated)) => void | 否 | 回调返回免打扰时间选项变更。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import Notification from '@ohos.notification';

let subscribeCallback = (err: BusinessError) => {
  if (err) {
    console.error(`subscribe failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("subscribeCallback");
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

## onDoNotDisturbChanged<sup>11+</sup>

onDoNotDisturbChanged?: (mode: notificationManager.DoNotDisturbDate) => void

免打扰时间选项发生变更时的回调函数。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Notification.Notification

**ArkTS-Dyn起始版本**：11

**ArkTS-Sta起始版本**：20

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------------ | ------------------------ | ---- | -------------------------- |
| onDoNotDisturbChanged | (mode: notificationManager.[DoNotDisturbDate](js-apis-notificationManager-sys.md#donotdisturbdate)) => void | 否 | 回调返回免打扰时间选项变更。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { notificationSubscribe, notificationManager } from '@kit.NotificationKit';

let subscribeCallback = (err: BusinessError) => {
  if (err) {
    console.error(`subscribe failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("subscribeCallback");
  }
};

let onDoNotDisturbChangedCallback = (mode: notificationManager.DoNotDisturbDate) => {
  console.info(`===> onDoNotDisturbChanged: ${JSON.stringify(mode)}`);
}

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onDoNotDisturbChanged: onDoNotDisturbChangedCallback
};

notificationSubscribe.subscribe(subscriber, subscribeCallback);
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { notificationSubscribe, notificationManager } from '@kit.NotificationKit';

let subscribeCallback = (err: BusinessError | null) => {
  if (err) {
    console.error(`subscribe failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("subscribeCallback");
  }
};

let onDoNotDisturbChangedCallback = (mode: notificationManager.DoNotDisturbDate) => {
  console.info(`===> onDoNotDisturbChanged: ${JSON.stringify(mode)}`);
}

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onDoNotDisturbChanged: onDoNotDisturbChangedCallback
};

notificationSubscribe.subscribe(subscriber, subscribeCallback);
```

## onEnabledNotificationChanged<sup>8+</sup>

onEnabledNotificationChanged?: (callbackData: EnabledNotificationCallbackData) => void

监听应用通知使能变化。

**系统能力**：SystemCapability.Notification.Notification

**系统接口**：此接口为系统接口。

**ArkTS-Dyn起始版本**：8

**ArkTS-Sta起始版本**：20

**参数：**

| 参数名 | 类型                                                                                                           | 必填 | 说明 |
| ------------ |--------------------------------------------------------------------------------------------------------------| ---- | -------------------------- |
| onEnabledNotificationChanged | (callbackData: [EnabledNotificationCallbackData](#enablednotificationcallbackdata8)) => void | 否 | 回调返回监听到的应用信息。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let subscribeCallback = (err: BusinessError) => {
  if (err) {
    console.error(`subscribe failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("subscribeCallback");
  }
};

let onEnabledNotificationChangedCallback = (callbackData: notificationSubscribe.EnabledNotificationCallbackData) => {
  console.info("bundle: ", callbackData.bundle);
  console.info("uid: ", callbackData.uid);
  console.info("enable: ", callbackData.enable);
};

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onEnabledNotificationChanged: onEnabledNotificationChangedCallback
};

notificationSubscribe.subscribe(subscriber, subscribeCallback);
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let subscribeCallback = (err: BusinessError | null) => {
  if (err) {
    console.error(`subscribe failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("subscribeCallback");
  }
};

let onEnabledNotificationChangedCallback = (callbackData: notificationSubscribe.EnabledNotificationCallbackData) => {
  console.info("bundle: ", callbackData.bundle);
  console.info("uid: ", callbackData.uid);
  console.info("enable: ", callbackData.enable);
};

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onEnabledNotificationChanged: onEnabledNotificationChangedCallback
};

notificationSubscribe.subscribe(subscriber, subscribeCallback);
```

## onEnabledSilentReminderChanged<sup>24+</sup>

onEnabledSilentReminderChanged?: EnabledSilentReminderChangedCallback

监听应用通知静默提醒的使能状态变化。

**系统能力**：SystemCapability.Notification.Notification

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口**：此接口为系统接口。

**ArkTS-Dyn起始版本**：24

**ArkTS-Sta起始版本**：24

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ----- | ---  | ---- | --- |
| onEnabledSilentReminderChanged | [EnabledSilentReminderChangedCallback](#enabledsilentreminderchangedcallback24) | 否 | 回调返回监听到的应用信息。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let subscribeCallback = (err: BusinessError) => {
  if (err) {
    console.error(`subscribe failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("subscribeCallback");
  }
};

let onEnabledSilentReminderChangedCallback: notificationSubscribe.EnabledSilentReminderChangedCallback = (callbackData: notificationSubscribe.EnabledSilentReminderCallbackData) => {
  console.info("bundle: ", callbackData.bundle);
  console.info("uid: ", callbackData.uid);
  console.info("enable: ", callbackData.enableStatus);
};

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onEnabledSilentReminderChanged: onEnabledSilentReminderChangedCallback
};

notificationSubscribe.subscribe(subscriber, subscribeCallback);
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let subscribeCallback = (err: BusinessError | null) => {
  if (err) {
    console.error(`subscribe failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("subscribeCallback");
  }
};

let onEnabledSilentReminderChangedCallback: notificationSubscribe.EnabledSilentReminderChangedCallback = (callbackData: notificationSubscribe.EnabledSilentReminderCallbackData) => {
  console.info("bundle: ", callbackData.bundle);
  console.info("uid: ", callbackData.uid);
  console.info("enable: ", callbackData.enableStatus);
};

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onEnabledSilentReminderChanged: onEnabledSilentReminderChangedCallback
};

notificationSubscribe.subscribe(subscriber, subscribeCallback);
```

## onBadgeChanged<sup>10+</sup>

onBadgeChanged?: (data: BadgeNumberCallbackData) => void

监听应用角标个数变化。

**系统能力**：SystemCapability.Notification.Notification

**系统接口**：此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：20

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                       |
| -------- | ------------------------------------------------------------ | ---- | -------------------------- |
| onBadgeChanged | (data: [BadgeNumberCallbackData](#badgenumbercallbackdata10)) => void | 否   | 回调返回监听到的应用信息。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let subscribeCallback = (err: BusinessError) => {
  if (err) {
    console.error(`subscribe failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("subscribeCallback");
  }
};

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onBadgeChanged: (data) => {
    console.info("bundle: ", data.bundle);
    console.info("uid: ", data.uid);
    console.info("badgeNumber: ", data.badgeNumber);
  }
};

notificationSubscribe.subscribe(subscriber, subscribeCallback);
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let subscribeCallback = (err: BusinessError | null) => {
  if (err) {
    console.error(`subscribe failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("subscribeCallback");
  }
};

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onBadgeChanged: (data : notificationSubscribe.BadgeNumberCallbackData) => {
    console.info("bundle: ", data.bundle);
    console.info("uid: ", data.uid);
    console.info("badgeNumber: ", data.badgeNumber);
  }
};

notificationSubscribe.subscribe(subscriber, subscribeCallback);
```

## onBadgeEnabledChanged<sup>12+</sup>

onBadgeEnabledChanged?: BadgeEnabledChangedCallback

监听应用角标使能状态变化。

**系统能力**：SystemCapability.Notification.Notification

**系统接口**：此接口为系统接口。

**ArkTS-Dyn起始版本**：12

**ArkTS-Sta起始版本**：20

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                       |
| -------- | ------------------------------------------------------------ | ---- | -------------------------- |
| onBadgeEnabledChanged | [BadgeEnabledChangedCallback](#badgeenabledchangedcallback12) | 否   | 回调应用角标使能状态变化。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let subscribeCallback = (err: BusinessError) => {
  if (err) {
    console.error(`subscribe failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('subscribeCallback');
  }
};

let BadgeEnabledChangedCallback = (data: notificationSubscribe.EnabledNotificationCallbackData) => {
  console.info(`onBadgeEnabledChanged, badge enabled state change to: ${JSON.stringify(data)}`);
};
let subscriber: notificationSubscribe.NotificationSubscriber = {
  onBadgeEnabledChanged: BadgeEnabledChangedCallback
};

notificationSubscribe.subscribe(subscriber, subscribeCallback);
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let subscribeCallback = (err: BusinessError | null) => {
  if (err) {
    console.error(`subscribe failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('subscribeCallback');
  }
};

let BadgeEnabledChangedCallback = (data: notificationSubscribe.EnabledNotificationCallbackData) => {
  console.info(`onBadgeEnabledChanged, badge enabled state change to: ${JSON.stringify(data)}`);
};
let subscriber: notificationSubscribe.NotificationSubscriber = {
  onBadgeEnabledChanged: BadgeEnabledChangedCallback
};

notificationSubscribe.subscribe(subscriber, subscribeCallback);
```


## onBatchCancel<sup>11+</sup>

onBatchCancel?: (data: Array<SubscribeCallbackData\>) => void

批量删除的回调函数。

**系统能力**：SystemCapability.Notification.Notification

**系统接口**：此接口为系统接口。

**ArkTS-Dyn起始版本**：11

**ArkTS-Sta起始版本**：20

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                       |
| -------- | ------------------------------------------------------------ | ---- | -------------------------- |
| onBatchCancel | (data: Array<[SubscribeCallbackData](#subscribecallbackdata)>) => void | 否   | 批量删除的通知信息。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let subscribeCallback = (err: BusinessError) => {
  if (err) {
    console.error(`subscribe failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("subscribeCallback");
  }
};

let onBatchCancelCallBack = (data: Array<notificationSubscribe.SubscribeCallbackData>) => {
  console.info('===> onBatchCancel in test');
  let req = data[0].request;
  console.info('===> onBatchCancel callback req.id:' + req.id);
};

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onBatchCancel: onBatchCancelCallBack
};

notificationSubscribe.subscribe(subscriber, subscribeCallback);
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let subscribeCallback = (err: BusinessError | null) => {
  if (err) {
    console.error(`subscribe failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("subscribeCallback");
  }
};

let onBatchCancelCallBack = (data: Array<notificationSubscribe.SubscribeCallbackData>) => {
  console.info('===> onBatchCancel in test');
  let req = data[0].request;
  console.info('===> onBatchCancel callback req.id:' + req.id);
};

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onBatchCancel: onBatchCancelCallBack
};

notificationSubscribe.subscribe(subscriber, subscribeCallback);

```

## onEnabledPriorityChanged<sup>23+</sup>

onEnabledPriorityChanged?: (callbackData: EnabledPriorityNotificationCallbackData) => void

通知优先级总开关状态变化的回调函数。使用callback异步同调。

**系统能力**：SystemCapability.Notification.Notification

**系统接口**：此接口为系统接口。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                       |
| -------- | ------------------------------------------------------------ | ---- | -------------------------- |
| onEnabledPriorityChanged | (callbackData: [EnabledPriorityNotificationCallbackData](#enabledprioritynotificationcallbackdata23)>) => void | 否   | 回调函数，返回通知优先级总开关状态。 |

**示例：**

ArkTS-Dyn示例：
```ts
let subscriber: notificationSubscribe.NotificationSubscriber = {
  onEnabledPriorityChanged: (callbackData: notificationSubscribe.EnabledPriorityNotificationCallbackData) => {
    console.info(`onEnabledPriorityChanged: ${JSON.stringify(callbackData)}`);
  }
};
try {
  notificationSubscribe.subscribe(subscriber);
} catch (error) {
  console.error("subscribe failed");
}
```

ArkTS-Sta示例：
```ts
let subscriber: notificationSubscribe.NotificationSubscriber = {
  onEnabledPriorityChanged: (callbackData: notificationSubscribe.EnabledPriorityNotificationCallbackData) => {
    console.info(`onEnabledPriorityChanged: ${JSON.stringify(callbackData)}`);
  }
};
try {
  notificationSubscribe.subscribe(subscriber);
} catch (error) {
  console.error("subscribe failed");
}
```

## onEnabledPriorityByBundleChanged<sup>23+</sup>

onEnabledPriorityByBundleChanged?: (callbackData: EnabledPriorityNotificationByBundleCallbackData) => void

应用通知优先级开关状态变化的回调函数。使用callback回调。

**系统能力**：SystemCapability.Notification.Notification

**系统接口**：此接口为系统接口。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                       |
| -------- | ------------------------------------------------------------ | ---- | -------------------------- |
| onEnabledPriorityByBundleChanged | (callbackData: [EnabledPriorityNotificationByBundleCallbackData](#enabledprioritynotificationbybundlecallbackdata23)>) => void | 否   | 回调函数，返回应用通知优先级开关状态。 |

**示例：**

ArkTS-Dyn示例：
```ts
let subscriber: notificationSubscribe.NotificationSubscriber = {
  onEnabledPriorityByBundleChanged: (callbackData: notificationSubscribe.EnabledPriorityNotificationByBundleCallbackData) => {
    console.info(`onEnabledPriorityByBundleChanged: ${JSON.stringify(callbackData)}`);
  }
};
try {
  notificationSubscribe.subscribe(subscriber);
} catch (error) {
  console.error("subscribe failed");
}
```

ArkTS-Sta示例：
```ts
let subscriber: notificationSubscribe.NotificationSubscriber = {
  onEnabledPriorityByBundleChanged: (callbackData: notificationSubscribe.EnabledPriorityNotificationByBundleCallbackData) => {
    console.info(`onEnabledPriorityByBundleChanged: ${JSON.stringify(callbackData)}`);
  }
};
try {
  notificationSubscribe.subscribe(subscriber);
} catch (error) {
  console.error("subscribe failed");
}
```

## SubscribeCallbackData

**系统能力**：SystemCapability.Notification.Notification

**系统接口**：此接口为系统接口。

**ArkTS-Dyn起始版本**：7

**ArkTS-Sta起始版本**：20

| 名称            | 类型                                                                 | 只读 | 可选 | 说明     |
| --------------- |--------------------------------------------------------------------| ---- | --- | -------- |
| request         | [NotificationRequest](js-apis-inner-notification-notificationRequest-sys.md#notificationrequest) | 是  | 否  | 通知内容。 |
| sortingMap      | [NotificationSortingMap](js-apis-inner-notification-notificationSortingMap-sys.md) | 是  | 是  | 通知排序信息。 |
| reason          | ArkTS-Dyn:number <br/>ArkTS-Sta:int                                | 是  | 是  | 删除原因（1:点击通知后删除通知，2:用户删除通知） 。|
| sound           | string                                                             | 是  | 是  | 通知声音。 |
| vibrationValues | ArkTS-Dyn:Array\<number\> <br/>ArkTS-Sta:Array\<long\>               | 是  | 是  | 通知震动。 |


## EnabledNotificationCallbackData<sup>8+</sup>

**系统能力**：SystemCapability.Notification.Notification

**系统接口**：此接口为系统接口。

**ArkTS-Dyn起始版本**：8

**ArkTS-Sta起始版本**：20

| 名称   | 类型    | 只读 | 可选 | 说明             |
| ------ | ------- | ---- | --- | ---------------- |
| bundle | string  | 是  | 否  | 应用的包名。       |
| uid    | ArkTS-Dyn:number <br/>ArkTS-Sta:int  | 是  | 否  | 应用的uid。        |
| enable | boolean | 是  | 否  | 应用通知使能状态。<br> - true：允许。<br> - false：禁止。 |

## EnabledSilentReminderCallbackData<sup>24+</sup>

**系统能力**：SystemCapability.Notification.Notification

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口**：此接口为系统接口。

**ArkTS-Dyn起始版本**：24

**ArkTS-Sta起始版本**：24

| 名称   | 类型    | 只读 | 可选 | 说明             |
| ------ | ------- | ---- | --- | ---------------- |
| bundle | string  | 是  | 否  | 应用的包名。       |
| uid    | ArkTS-Dyn: number <br/>ArkTS-Sta: int  | 是  | 否  | 应用的uid。        |
| enableStatus | [SwitchState](js-apis-notificationManager-sys.md#switchstate20) | 是  | 否  | 应用通知的静默提醒开关状态。<br> - USER_MODIFIED_OFF：用户设置的关闭状态。<br> - USER_MODIFIED_ON：用户设置的开启状态。<br> - SYSTEM_DEFAULT_OFF：用户设置前的初始关闭状态。<br> - SYSTEM_DEFAULT_ON：用户设置前的初始开启状态。|

## EnabledSilentReminderChangedCallback<sup>24+</sup>

EnabledSilentReminderChangedCallback = (callbackData: EnabledSilentReminderCallbackData)<sup>24+</sup>

(callbackData: EnabledSilentReminderCallbackData): void

注册应用通知静默提醒使能状态变化的回调函数类型。

**系统能力**：SystemCapability.Notification.Notification

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口**：此接口为系统接口。

**ArkTS-Dyn起始版本**：24

**ArkTS-Sta起始版本**：24

**参数**：

| 参数名        | 类型   | 必填 | 说明     |
| --------- | ------ | ---- | ------------ |
| callbackData        | [EnabledSilentReminderCallbackData](#enabledsilentremindercallbackdata24) | 是    |   回调返回监听到的静默提醒使能状态信息。 |

## BadgeNumberCallbackData<sup>10+</sup>

**系统能力**：SystemCapability.Notification.Notification

**系统接口**：此接口为系统接口。

| 名称        | 类型   | 只读 | 可选 | 说明         |
| ----------- | ------ | ---- | ---- | ------------ |
| bundle      | string | 是   | 否   | 应用的包名。 <br/> **ArkTS-Dyn起始版本**：10<br/>**ArkTS-Sta起始版本**：20 |
| uid         | ArkTS-Dyn: number <br/>ArkTS-Sta: int | 是   | 否   | 应用的uid。 <br/> **ArkTS-Dyn起始版本**：10<br/>**ArkTS-Sta起始版本**：20 |
| badgeNumber | ArkTS-Dyn: number <br/>ArkTS-Sta: int | 是   | 否   | 角标个数。 <br/> **ArkTS-Dyn起始版本**：10<br/>**ArkTS-Sta起始版本**：20 |
| instanceKey<sup>(deprecated)</sup>  | number | 是   | 是   | 应用实例键值。<br>从API version 12开始支持，从API version 15开始废弃，建议使用替代。 <br/>**ArkTS模式：** 该属性仅适用于ArkTS-Dyn<br/>**ArkTS-Dyn起始版本**：12  |
| appInstanceKey<sup>15+</sup>  | string | 是   | 是   | 应用实例键值。 <br/> **ArkTS-Dyn起始版本**：15<br/>**ArkTS-Sta起始版本**：20 |


## BadgeEnabledChangedCallback<sup>12+</sup>

**系统能力**：SystemCapability.Notification.Notification

**系统接口**：此接口为系统接口。

| 名称        | 类型   | 只读 | 可选 | 说明     |
| ----------- | ------ | ---- | ---- |------------ |
| data        | [EnabledNotificationCallbackData](#enablednotificationcallbackdata8) | 是   | 是    |   回调返回监听到的角标使能状态信息。 |

## EnabledPriorityNotificationCallbackData<sup>23+</sup>

**系统能力**：SystemCapability.Notification.Notification

**系统接口**：此接口为系统接口。

**ArkTS-Dyn起始版本**：23

**ArkTS-Sta起始版本**：23

| 名称        | 类型   | 只读 | 可选 | 说明         |
| ----------- | ------ | ---- | ---- | ------------ |
| enable | boolean | 是  | 否  | 所有通知的优先使能状态。<br> - true：允许设置为优先通知。<br> - false：禁止设置为优先通知。 |

## EnabledPriorityNotificationByBundleCallbackData<sup>23+</sup>

**系统能力**：SystemCapability.Notification.Notification

**系统接口**：此接口为系统接口。

**ArkTS-Dyn起始版本**：23

**ArkTS-Sta起始版本**：23

| 名称        | 类型   | 只读 | 可选 | 说明         |
| ----------- | ------ | ---- | ---- | ------------ |
| bundle      | string | 是   | 否   | 应用的包名。 |
| uid         | ArkTS-Dyn:number <br/>ArkTS-Sta:int | 是   | 否   | 应用的uid。  |
| enableStatus | [PriorityEnableStatus](js-apis-notificationManager-sys.md#priorityenablestatus23) | 是  | 否  | 应用通知的优先使能状态。<br> - DISABLE：不允许设置为优先通知。<br> - ENABLE_BY_INTELLIGENT：允许经智能识别、用户关键词匹配、应用规则匹配等方式设置为优先通知。<br> - ENABLE：应用通知均设置为优先通知。 |