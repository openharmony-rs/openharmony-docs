# NotificationSubscriber (System API)

<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=50e734d278c25dbb71273705da516c218b3754a1 translatedAt=2026-06-29T02:38:20.363Z pushedAt=2026-06-30T10:57:37.018Z -->

The **NotificationSubscriber** module serves as the input parameter of [subscribeNotification](js-apis-notificationSubscribe-sys.md#notificationsubscribesubscribenotification) and provides callbacks for receiving or removing notifications.

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs provided by this module are system APIs.

## Modules to Import

```js
import { notificationSubscribe } from '@kit.NotificationKit';
```

## NotificationSubscriber

Provides callback methods for subscribers to receive and cancel notifications.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

### onConsume

onConsume?: (data: SubscribeCallbackData) => void

Called when a new notification is received.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| ------------ | ------------------------ | ---- | -------------------------- |
| onConsume | (data: [SubscribeCallbackData](#subscribecallbackdata)) => void | No| Information about the notification received.|

**Example**

```ts
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

### onCancel

onCancel?: (data: SubscribeCallbackData) => void

Called when a notification is canceled.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| ------------ | ------------------------ | ---- | -------------------------- |
| onCancel | (data: [SubscribeCallbackData](#subscribecallbackdata)) => void | No| Information about the notification to cancel.|

**Example**

```ts
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

### onUpdate

onUpdate?: (data: NotificationSortingMap) => void

Called when notification sorting is updated. Not supported currently.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| ------------ | ------------------------ | ---- | -------------------------- |
| onUpdate | (data: [NotificationSortingMap](js-apis-inner-notification-notificationSortingMap-sys.md)) => void | No| Latest notification sorting list.|

**Example**

```ts
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

### onConnect

onConnect?: () => void

Called when subscription is complete.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| ------------ | ------------------------ | ---- | -------------------------- |
| onConnect | () => void | No| Callback invoked when subscription is complete.|

**Example**

```ts
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

### onDisconnect

onDisconnect?: () => void

Called when unsubscription is complete.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| ------------ | ------------------------ | ---- | -------------------------- |
| onDisconnect | () => void | No| Callback invoked when unsubscription is complete.|

**Example**

```ts
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

### onDestroy

onDestroy?: () => void

Called when the service is disconnected.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| ------------ | ------------------------ | ---- | -------------------------- |
| onDestroy | () => void | No| Callback to be invoked when the service is disconnected.|

**Example**

```ts
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

### onDoNotDisturbDateChange<sup>(deprecated)</sup>

onDoNotDisturbDateChange?: (mode: notification.DoNotDisturbDate) => void

Called when the DND time settings are changed.

> **NOTE**
>
> This API is supported since API version 8 and is deprecated since API version 11. You are advised to use [onDoNotDisturbChanged](js-apis-inner-notification-notificationSubscriber-sys.md#ondonotdisturbchanged11) instead.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| ------------ | ------------------------ | ---- | -------------------------- |
| onDoNotDisturbDateChange | (mode: notification.[DoNotDisturbDate](js-apis-notification-sys.md#donotdisturbdate8-deprecated)) => void | No| Callback used to return DND time setting updates.|

**Example**

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

### onDoNotDisturbChanged<sup>11+</sup>

onDoNotDisturbChanged?: (mode: notificationManager.DoNotDisturbDate) => void

Called when the DND time settings are changed.

**System API**: This is a system API.

**System capability**: SystemCapability.Notification.Notification

**Parameters**

| Name| Type| Mandatory| Description|
| ------------ | ------------------------ | ---- | -------------------------- |
| onDoNotDisturbChanged | (mode: notificationManager.[DoNotDisturbDate](js-apis-notificationManager-sys.md#donotdisturbdate)) => void | No| Callback used to return DND time setting updates.|

**Example**

```ts
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

### onEnabledNotificationChanged<sup>8+</sup>

onEnabledNotificationChanged?: (callbackData: EnabledNotificationCallbackData) => void

Listens for the notification enabled state changes.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

**Parameters**

| Name| Type                                                                                                          | Mandatory| Description|
| ------------ |--------------------------------------------------------------------------------------------------------------| ---- | -------------------------- |
| onEnabledNotificationChanged | (callbackData: [EnabledNotificationCallbackData](#enablednotificationcallbackdata8)) => void | No| Callback used to return the listened application information.|

**Example**

```ts
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

### onBadgeChanged<sup>10+</sup>

onBadgeChanged?: (data: BadgeNumberCallbackData) => void

Listens for changes of the application badge number.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

**Parameters**

| Name  | Type                                                        | Mandatory| Description                      |
| -------- | ------------------------------------------------------------ | ---- | -------------------------- |
| onBadgeChanged | (data: [BadgeNumberCallbackData](#badgenumbercallbackdata10)) => void | No   | Callback used to return the application badge number changes. |

**Example**

```ts
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

### onBatchCancel<sup>11+</sup>

onBatchCancel?: (data: Array<SubscribeCallbackData\>) => void

Called for batch deletion.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

**Parameters**

| Name  | Type                                                        | Mandatory| Description                      |
| -------- | ------------------------------------------------------------ | ---- | -------------------------- |
| onBatchCancel | (data: Array<[SubscribeCallbackData](#subscribecallbackdata)>) => void | No  | Notification information of batch deletion.|

**Example**

```ts
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

### onEnabledPriorityChanged<sup>23+</sup>

onEnabledPriorityChanged?: (callbackData: EnabledPriorityNotificationCallbackData) => void

Called when the enabling state of the priority notification changes.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

**Parameters**

| Name  | Type                                                        | Mandatory| Description                      |
| -------- | ------------------------------------------------------------ | ---- | -------------------------- |
| onEnabledPriorityChanged | (callbackData: [EnabledPriorityNotificationCallbackData](#enabledprioritynotificationcallbackdata23)>) => void | No  | Callback used to return the result.|

**Example**

```ts
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

### onEnabledPriorityByBundleChanged<sup>23+</sup>

onEnabledPriorityByBundleChanged?: (callbackData: EnabledPriorityNotificationByBundleCallbackData) => void

Called when the enabling state of the application priority notification changes.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

**Parameters**

| Name  | Type                                                        | Mandatory| Description                      |
| -------- | ------------------------------------------------------------ | ---- | -------------------------- |
| onEnabledPriorityByBundleChanged | (callbackData: [EnabledPriorityNotificationByBundleCallbackData](#enabledprioritynotificationbybundlecallbackdata23)>) => void | No  | Callback used to return the result.|

**Example**

```ts
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

### Attributes

Callback function for notifications of system property value changes.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

| Name  | Type   | Read Only| Optional| Description            |
| ------ | ------- | ---- | --- | ---------------- |
| onSystemUpdate | [SystemUpdateCallback](#systemupdatecallback23) | No| Yes| Returns notification information containing the system property value.|
| onEnabledSilentReminderChanged | [EnabledSilentReminderChangedCallback](#enabledsilentreminderchangedcallback24) | No| Yes| Returns the changes of the enabling state of the application's silent reminder.|
| onBadgeEnabledChanged | [BadgeEnabledChangedCallback](#badgeenabledchangedcallback12) | No| Yes| Returns the changes of the enabling state of the application's badge.|
| onNotificationSwitchChanged | [NotificationSwitchChangedCallback](#notificationswitchchangedcallback) | No | Yes | Returns the changes of the notification switch status set by [notificationManager.setNotificationSwitch](js-apis-notificationManager-sys.md#notificationmanagersetnotificationswitch).<br> **Since:** 26.0.0<br> **Model restriction:** This API can be used only in the stage model. |

## SubscribeCallbackData

Returns notification information carrying system property values.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

| Name           | Type                                                                | Read Only| Optional| Description    |
| --------------- |--------------------------------------------------------------------| ---- | --- | -------- |
| request         | [NotificationRequest](js-apis-inner-notification-notificationRequest-sys.md#notificationrequest) | Yes | No | Notification content.|
| sortingMap      | [NotificationSortingMap](js-apis-inner-notification-notificationSortingMap-sys.md) | Yes | Yes | Notification sorting information.|
| reason          | number                                                             | Yes | Yes | Reason for deletion. The options are as follows:<br>**1**: The notification is deleted after being tapped.<br>**2**: The notification is deleted by the user.|
| sound           | string                                                             | Yes | Yes | Notification sound.|
| vibrationValues | Array\<number\> | Yes | Yes | Notification vibration. |
| voiceContent | [VoiceContent](#voicecontent)                                              | Yes | Yes | Voice broadcast content of the notification.<br> **Since**: 26.0.0<br> **Model restriction**: This API can be used only in the stage model.|
| notificationClassification | [NotificationClassification](#notificationclassification) | Yes | Yes | Notification classification information. It exists only when **enableClassification** in [NotificationSubscribeInfo](js-apis-inner-notification-notificationSubscribeInfo-sys.md#notificationsubscribeinfo) is **true**.<br> **Since:** 26.0.0<br> **Model restriction:** This API can be used only in the stage model.|

## EnabledNotificationCallbackData<sup>8+</sup>

Returns the changes of the application badge enabling state.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

| Name  | Type   | Read Only| Optional| Description            |
| ------ | ------- | ---- | --- | ---------------- |
| bundle | string  | Yes | No | Bundle name of the application.      |
| uid    | number  | Yes | No | UID of the application.       |
| enable | boolean | Yes | No | Whether the application notification is enabled.<br> - **true**: enabled.<br> - **false**: disabled.|

## EnabledSilentReminderCallbackData<sup>24+</sup>

Returns the application
notification silent reminder switch state.

**System capability**: SystemCapability.Notification.Notification

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

| Name  | Type   | Read Only| Optional| Description            |
| ------ | ------- | ---- | --- | ---------------- |
| bundle | string  | Yes | No | Bundle name of the application.      |
| uid    | number  | Yes | No | UID of the application.       |
| enableStatus | [notificationManager.SwitchState](js-apis-notificationManager-sys.md#switchstate20) | Yes | No | Enabling state of the application's silent reminder.<br> - **USER_MODIFIED_OFF**: disabled state set by the user.<br> - **USER_MODIFIED_ON**: enabled state set by the user.<br> - **SYSTEM_DEFAULT_OFF**: initial disabled state before user setting.<br> - **SYSTEM_DEFAULT_ON**: initial enabled state before user setting.|

## BadgeNumberCallbackData<sup>10+</sup>

Returns the changes of the application badge number.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

| Name       | Type  | Read Only| Optional| Description        |
| ----------- | ------ | ---- | ---- | ------------ |
| bundle      | string | Yes  | No  | Bundle name of the application.|
| uid         | number | Yes  | No  | UID of the application. |
| badgeNumber | number | Yes  | No  | Number of notifications displayed on the application icon.  |
| instanceKey<sup>(deprecated)</sup>  | number | Yes  | Yes  | Key value of an application instance. This parameter is supported since API version 12 and deprecated since API version 15. You are advised to use **appInstanceKey** instead.  |
| appInstanceKey<sup>15+</sup>  | string | Yes  | Yes  | Key value of an application instance.  |

## EnabledPriorityNotificationCallbackData<sup>23+</sup>

Returns the notification priority master switch state.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

| Name       | Type  | Read Only| Optional| Description        |
| ----------- | ------ | ---- | ---- | ------------ |
| enable | boolean | Yes | No | Whether the priority notification is enabled.<br> - **true**: The priority notification is enabled.<br> - **false**: The priority notification is disabled.|

## EnabledPriorityNotificationByBundleCallbackData<sup>23+</sup>

Returns the notification priority switch state.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

| Name       | Type  | Read Only| Optional| Description        |
| ----------- | ------ | ---- | ---- | ------------ |
| bundle      | string | Yes  | No  | Bundle name of the application.|
| uid         | number | Yes  | No  | UID of the application. |
| enableStatus | [PriorityEnableStatus](js-apis-notificationManager-sys.md#priorityenablestatus23) | Yes | No | Whether the priority notification for an application is enabled.<br> - **DISABLE**: The priority notification is disabled.<br> - **ENABLE_BY_INTELLIGENT**: The priority notification can be enabled through intelligent recognition, user keyword matching, or application rule matching.<br> - **ENABLE**: The priority notification is enabled for all applications.|

## NotificationSwitchChangedCallbackData

Returns the changes of the notification switch state.

**Since:** 26.0.0

**System capability**: SystemCapability.Notification.Notification

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

| Name        | Type   | Read Only | Optional | Description         |
| ----------- | ------ | ---- | ---- | ------------ |
| userId | number | Yes | No | User ID. |
| switchName | string | Yes | No | Notification switch name. The value can be **DEAL** (aggregated switch for transaction notifications) or **LOGISTICS** (aggregated switch for logistics notifications). |
| enableStatus | [notificationManager.SwitchState](js-apis-notificationManager-sys.md#switchstate20) | Yes | No | Notification switch state. |

## VoiceContent

Returns the notification voice broadcast content.

**Since:** 26.0.0

**System capability**: SystemCapability.Notification.Notification

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

| Name           | Type                                                                | Read Only| Optional| Description    |
| --------------- |--------------------------------------------------------------------| ---- | --- | -------- |
| textContent | string                                             | Yes | Yes | Text voice broadcast content.|

## NotificationClassification

Returns the notification classification information.

**Since:** 26.0.0

**System capability**: SystemCapability.Notification.Notification

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

| Name            | Type   | Read Only | Optional | Description     |
| --------------- | ------ | ---- | --- | -------- |
| classification | string | Yes | Yes | Notification classification identified by the system. |
| subClassification | string | Yes | Yes | Notification sub-classification identified by the system. |

## BadgeEnabledChangedCallback<sup>12+</sup>

type BadgeEnabledChangedCallback = (data: EnabledNotificationCallbackData) => void

Defines a callback function to listen for the enabling state changes of the application badge.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

**Parameters**

| Name       | Type  | Mandatory| Description    |
| --------- | ------ | ---- | ------------ |
| data        | [EnabledNotificationCallbackData](#enablednotificationcallbackdata8) | Yes   |   Callback used to return the listened badge enabling state.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let BadgeEnabledChangedCallback = (data: notificationSubscribe.EnabledNotificationCallbackData) => {
  console.info(`onBadgeEnabledChanged, badge enabled state change to: ${JSON.stringify(data)}`);
};
let subscriber: notificationSubscribe.NotificationSubscriber = {
  onBadgeEnabledChanged: BadgeEnabledChangedCallback
};

notificationSubscribe.subscribeNotification(subscriber).then(() => {
  console.info("subscribeNotification success");
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```

## SystemUpdateCallback<sup>23+</sup>

type SystemUpdateCallback = (data: SubscribeCallbackData) => void

Returns the notification information carrying system property values.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

**Parameters**

| Name      | Type  | Mandatory| Description        |
| ----------- | ------ | ---- | ------------ |
| data | [SubscribeCallbackData](#subscribecallbackdata) | Yes| Notification information that carries the system property value.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onSystemUpdate: (data: notificationSubscribe.SubscribeCallbackData) => {
    let req = data.request;
    console.info(`onSystemUpdate callback req.priorityType: ${req.priorityNotificationType}`);
  }
};
notificationSubscribe.subscribeNotification(subscriber).then(() => {
  console.info("subscribeNotification success");
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```

## EnabledSilentReminderChangedCallback<sup>24+</sup>

type EnabledSilentReminderChangedCallback = (callbackData: EnabledSilentReminderCallbackData) => void

Defines a callback function to listen for the enabling state changes of the application's silent reminder.

**System capability**: SystemCapability.Notification.Notification

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Parameters**

| Name       | Type  | Mandatory| Description    |
| --------- | ------ | ---- | ------------ |
| callbackData        | [EnabledSilentReminderCallbackData](#enabledsilentremindercallbackdata24) | Yes   |   Callback used to return the listened silent reminder enabling state.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let onEnabledSilentReminderChangedCallback: notificationSubscribe.EnabledSilentReminderChangedCallback = (callbackData: notificationSubscribe.EnabledSilentReminderCallbackData) => {
  console.info("bundle: ", callbackData.bundle);
  console.info("uid: ", callbackData.uid);
  console.info("enable: ", callbackData.enableStatus);
};

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onEnabledSilentReminderChanged: onEnabledSilentReminderChangedCallback
};

notificationSubscribe.subscribeNotification(subscriber).then(() => {
  console.info("subscribeNotification success");
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```

## NotificationSwitchChangedCallback

type NotificationSwitchChangedCallback = (callbackData: NotificationSwitchChangedCallbackData) => void

Registers the callback for notification switch state changes set by the [notificationManager.setNotificationSwitch](js-apis-notificationManager-sys.md#notificationmanagersetnotificationswitch) API.

**Since:** 26.0.0

**System capability**: SystemCapability.Notification.Notification

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**Parameters**

| Name        | Type   | Mandatory | Description     |
| --------- | ------ | ---- | ------------ |
| callbackData | [NotificationSwitchChangedCallbackData](#notificationswitchchangedcallbackdata) | Yes | Callback that returns the notification switch state change information set by the [notificationManager.setNotificationSwitch](js-apis-notificationManager-sys.md#notificationmanagersetnotificationswitch) API. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onNotificationSwitchChanged: (callbackData: notificationSubscribe.NotificationSwitchChangedCallbackData) => {
    console.info(`onNotificationSwitchChanged: ${JSON.stringify(callbackData)}`);
  }
};

notificationSubscribe.subscribeNotification(subscriber).then(() => {
  console.info('subscribeNotification success');
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```