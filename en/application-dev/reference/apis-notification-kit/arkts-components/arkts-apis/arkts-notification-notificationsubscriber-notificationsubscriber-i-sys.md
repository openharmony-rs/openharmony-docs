# NotificationSubscriber (System API)

Provides callback methods for subscribers to receive and cancel notifications.

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## onBadgeChanged

```TypeScript
onBadgeChanged?:(data: BadgeNumberCallbackData) => void
```

Listens for changes of the application badge number.

**Since:** 10

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [BadgeNumberCallbackData](arkts-notification-notificationsubscriber-badgenumbercallbackdata-i-sys.md) | Yes |  |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onBadgeChanged: (data) => {
    console.info("bundle: ", data.bundle);
    console.info("uid: ", data.uid);
    console.info("badgeNumber: ", data.badgeNumber);
  }
};

notificationSubscribe.subscribeNotification(subscriber).then(() => {
  console.info("subscribeNotification success");
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```

## onBatchCancel

```TypeScript
onBatchCancel?: (data: Array<SubscribeCallbackData>) => void
```

Called for batch deletion.

**Since:** 11

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | Array&lt;[SubscribeCallbackData](arkts-notification-notificationsubscriber-subscribecallbackdata-i-sys.md)&gt; | Yes |  |

**Examples**

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
  console.info("subscribeNotification success");
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```

## onCancel

```TypeScript
onCancel?:(data: SubscribeCallbackData) => void
```

Called when a notification is canceled.

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [SubscribeCallbackData](arkts-notification-notificationsubscriber-subscribecallbackdata-i-sys.md) | Yes |  |

**Examples**

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
  console.info("subscribeNotification success");
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```

## onConnect

```TypeScript
onConnect?:() => void
```

Called when subscription is complete.

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let onConnectCallback = () => {
  console.info('===> onConnect in test');
}

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onConnect: onConnectCallback
};

notificationSubscribe.subscribeNotification(subscriber).then(() => {
  console.info("subscribeNotification success");
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```

## onConsume

```TypeScript
onConsume?:(data: SubscribeCallbackData) => void
```

Called when a new notification is received.

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [SubscribeCallbackData](arkts-notification-notificationsubscriber-subscribecallbackdata-i-sys.md) | Yes |  |

**Examples**

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
  console.info("subscribeNotification success");
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```

## onDestroy

```TypeScript
onDestroy?:() => void
```

Called when the service is disconnected.

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let onDestroyCallback = () => {
  console.info('===> onDestroy in test');
}

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onDestroy: onDestroyCallback
};

notificationSubscribe.subscribeNotification(subscriber).then(() => {
  console.info("subscribeNotification success");
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```

## onDisconnect

```TypeScript
onDisconnect?:() => void
```

Called when unsubscription is complete.

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

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

// The onConnect callback is invoked when subscription to the notification is complete.
notificationSubscribe.subscribeNotification(subscriber).then(() => {
  console.info("subscribeNotification success");
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
// The onDisconnect callback is invoked when unsubscription to the notification is complete.
notificationSubscribe.unsubscribe(subscriber, unsubscribeCallback);
```

## onDoNotDisturbChanged

```TypeScript
onDoNotDisturbChanged?: (mode: notificationManager.DoNotDisturbDate) => void
```

Called when the DND time settings are changed.

**Since:** 11

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [notificationManager.DoNotDisturbDate](arkts-notification-notificationmanager-donotdisturbdate-i-sys.md) | Yes |  |

**Examples**

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
  console.info("subscribeNotification success");
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```

## onDoNotDisturbDateChange

```TypeScript
onDoNotDisturbDateChange?: (mode: notification.DoNotDisturbDate) => void
```

Called when the DND time settings are changed.

**Since:** 8

**Deprecated since:** 11

**Substitutes:** [onDoNotDisturbChanged](#ondonotdisturbchanged)

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [notification.DoNotDisturbDate](arkts-notification-notification-donotdisturbdate-depr-i-sys.md) | Yes |  |

**Examples**

```TypeScript
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

## onEnabledNotificationChanged

```TypeScript
onEnabledNotificationChanged?:(callbackData: EnabledNotificationCallbackData) => void
```

Listens for the notification enabled state changes.

**Since:** 8

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackData | [EnabledNotificationCallbackData](arkts-notification-notificationsubscriber-enablednotificationcallbackdata-i-sys.md) | Yes |  |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let onEnabledNotificationChangedCallback = (callbackData: notificationSubscribe.EnabledNotificationCallbackData) => {
  console.info("bundle: ", callbackData.bundle);
  console.info("uid: ", callbackData.uid);
  console.info("enable: ", callbackData.enable);
};

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onEnabledNotificationChanged: onEnabledNotificationChangedCallback
};

notificationSubscribe.subscribeNotification(subscriber).then(() => {
  console.info("subscribeNotification success");
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```

## onEnabledPriorityByBundleChanged

```TypeScript
onEnabledPriorityByBundleChanged?: (callbackData: EnabledPriorityNotificationByBundleCallbackData) => void
```

Called when the enabling state of the application priority notification changes.

**Since:** 23

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackData | [EnabledPriorityNotificationByBundleCallbackData](arkts-notification-notificationsubscriber-enabledprioritynotificationbybundlecallbackdata-i-sys.md) | Yes |  |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onEnabledPriorityByBundleChanged: (callbackData: notificationSubscribe.EnabledPriorityNotificationByBundleCallbackData) => {
    console.info(`onEnabledPriorityByBundleChanged: ${JSON.stringify(callbackData)}`);
  }
};
notificationSubscribe.subscribeNotification(subscriber).then(() => {
  console.info("subscribeNotification success");
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```

## onEnabledPriorityChanged

```TypeScript
onEnabledPriorityChanged?: (callbackData: EnabledPriorityNotificationCallbackData) => void
```

Called when the enabling state of the priority notification changes.

**Since:** 23

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackData | [EnabledPriorityNotificationCallbackData](arkts-notification-notificationsubscriber-enabledprioritynotificationcallbackdata-i-sys.md) | Yes |  |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onEnabledPriorityChanged: (callbackData: notificationSubscribe.EnabledPriorityNotificationCallbackData) => {
    console.info(`onEnabledPriorityChanged: ${JSON.stringify(callbackData)}`);
  }
};
notificationSubscribe.subscribeNotification(subscriber).then(() => {
  console.info("subscribeNotification success");
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```

## onEnabledSilentReminderChanged

```TypeScript
onEnabledSilentReminderChanged?: EnabledSilentReminderChangedCallback
```

Returns the changes of the enabling state of the application's silent reminder.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## onNotificationSwitchChanged

```TypeScript
onNotificationSwitchChanged?: NotificationSwitchChangedCallback
```

Returns the changes of the notification switch status set by [notificationManager.setNotificationSwitch]{@link../@ohos.notificationManager:notificationManager.setNotificationSwitch}.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## onSystemUpdate

```TypeScript
onSystemUpdate?: SystemUpdateCallback
```

Returns notification information containing the system property value.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## onUpdate

```TypeScript
onUpdate?:(data: NotificationSortingMap) => void
```

Called when notification sorting is updated. Not supported currently.

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [NotificationSortingMap](arkts-notification-notificationsortingmap-notificationsortingmap-i-sys.md) | Yes |  |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onUpdate: (map) => {
    console.info(`===> onUpdateCallback map: ${JSON.stringify(map)}`);
  }
};

notificationSubscribe.subscribeNotification(subscriber).then(() => {
  console.info("subscribeNotification success");
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```

## onBadgeEnabledChanged

```TypeScript
onBadgeEnabledChanged?: BadgeEnabledChangedCallback
```

Returns the changes of the enabling state of the application's badge.

**Type:** [BadgeEnabledChangedCallback](arkts-notification-notificationsubscriber-badgeenabledchangedcallback-i-sys.md)

**Since:** 12

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
