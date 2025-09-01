# NotificationSubscriber (System API)

The **NotificationSubscriber** module provides callbacks for receiving or removing notifications and serves as the input parameter of [subscribe](./js-apis-notificationSubscribe-sys.md).

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs provided by this module are system APIs.

## Modules to Import

```js
import { notificationSubscribe } from '@kit.NotificationKit';
```

## onConsume

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

## onCancel

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

## onUpdate

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

let subscribeCallback = (err: BusinessError) => {
  if (err) {
    console.error(`subscribe failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("subscribeCallback");
  }
};

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onUpdate: (map) => {
    console.info('===> onUpdateCallback map:' + JSON.stringify(map));
  }
};

notificationSubscribe.subscribe(subscriber, subscribeCallback);
```

## onConnect

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

## onDisconnect

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

// The onConnect callback is invoked when subscription to the notification is complete.
notificationSubscribe.subscribe(subscriber, subscribeCallback);
// The onDisconnect callback is invoked when unsubscription to the notification is complete.
notificationSubscribe.unsubscribe(subscriber, unsubscribeCallback);
```

## onDestroy

onDestroy?: () => void

Called when the service is disconnected.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| ------------ | ------------------------ | ---- | -------------------------- |
| onDestroy | () => void | No| Callback used when the service is disconnected.|

**Example**

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

## onDoNotDisturbDateChange<sup>8+</sup> (deprecated)

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

## onDoNotDisturbChanged<sup>11+</sup>

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

let subscribeCallback = (err: BusinessError) => {
  if (err) {
    console.error(`subscribe failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("subscribeCallback");
  }
};

let onDoNotDisturbChangedCallback = (mode: notificationManager.DoNotDisturbDate) => {
  console.info('===> onDoNotDisturbChanged:' + JSON.stringify(mode));
}

let subscriber: notificationSubscribe.NotificationSubscriber = {
  onDoNotDisturbChanged: onDoNotDisturbChangedCallback
};

notificationSubscribe.subscribe(subscriber, subscribeCallback);
```

## onEnabledNotificationChanged<sup>8+</sup>

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

## onBadgeChanged<sup>10+</sup>

onBadgeChanged?: (data: BadgeNumberCallbackData) => void

Listens for the change of the notification badge number.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

**Parameters**

| Name  | Type                                                        | Mandatory| Description                      |
| -------- | ------------------------------------------------------------ | ---- | -------------------------- |
| onBadgeChanged | (data: [BadgeNumberCallbackData](#badgenumbercallbackdata10)) => void | No  | Callback used to return the listened application information.|

**Example**

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

## onBadgeEnabledChanged<sup>12+</sup>

onBadgeEnabledChanged?: BadgeEnabledChangedCallback

Listens for the change of the notification badge enabling state.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

**Parameters**

| Name  | Type                                                        | Mandatory| Description                      |
| -------- | ------------------------------------------------------------ | ---- | -------------------------- |
| onBadgeEnabledChanged | [BadgeEnabledChangedCallback](#badgeenabledchangedcallback12) | No  | Callback used to return the change of the notification badge enabling state.|

**Example**

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
  console.info('onBadgeEnabledChanged, badge enabled state change to: ', JSON.stringify(data));
};
let subscriber: notificationSubscribe.NotificationSubscriber = {
  onBadgeEnabledChanged: BadgeEnabledChangedCallback
};

notificationSubscribe.subscribe(subscriber, subscribeCallback);
```


## onBatchCancel<sup>11+</sup>

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
## SubscribeCallbackData

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

| Name           | Type                                                                | Read Only| Optional| Description    |
| --------------- |--------------------------------------------------------------------| ---- | --- | -------- |
| request         | [NotificationRequest](js-apis-inner-notification-notificationRequest-sys.md#notificationrequest) | Yes | No | Notification content.|
| sortingMap      | [NotificationSortingMap](js-apis-inner-notification-notificationSortingMap-sys.md) | Yes | Yes | Notification sorting information.|
| reason          | number                                                             | Yes | Yes | Reason for deletion. The options are as follows:<br>**1**: The notification is deleted after being clicked.<br>**2**: The notification is deleted by the user.|
| sound           | string                                                             | Yes | Yes | Sound used for notification.|
| vibrationValues | Array\<number\>                                                    | Yes | Yes | Vibration used for notification.|


## EnabledNotificationCallbackData<sup>8+</sup>

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

| Name  | Type   | Read Only| Optional| Description            |
| ------ | ------- | ---- | --- | ---------------- |
| bundle | string  | Yes | No | Bundle name of the application.      |
| uid    | number  | Yes | No | UID of the application.       |
| enable | boolean | Yes | No | Whether the application notification is enabled.<br> - **true**: enabled.<br> - **false**: disabled.|


## BadgeNumberCallbackData<sup>10+</sup>

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

| Name       | Type  | Read Only| Optional| Description        |
| ----------- | ------ | ---- | ---- | ------------ |
| bundle      | string | Yes  | No  | Bundle name of the application.|
| uid         | number | Yes  | No  | UID of the application. |
| badgeNumber | number | Yes  | No  | Number of notifications displayed on the application icon.  |
| instanceKey<sup>(deprecated)</sup>  | number | Yes  | Yes  | Key value of an application instance.  |
| appInstanceKey<sup>15+</sup>  | string | Yes  | Yes  | Key value of an application instance.  |


## BadgeEnabledChangedCallback<sup>12+</sup>

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

| Name       | Type  | Read Only| Optional| Description    |
| ----------- | ------ | ---- | ---- |------------ |
| data        | [EnabledNotificationCallbackData](#enablednotificationcallbackdata8) | Yes  | Yes   |   Callback used to return the listened badge enabling state.|
