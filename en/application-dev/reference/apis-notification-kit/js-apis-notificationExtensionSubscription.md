# @ohos.notificationExtensionSubscription (notificationExtensionSubscription)
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @cheerful_ricky-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

The **notificationExtensionSubscription** module provides notification management capabilities for opening the settings page, subscribing to and unsubscribing from notifications, obtaining and setting the notification authorization status, and obtaining notification information.

> **NOTE**
>
> The initial APIs of this module are supported since API version 22. Newly added APIs will be marked with a superscript to indicate their earliest API version.
## Modules to Import

```ts
import { notificationExtensionSubscription } from '@kit.NotificationKit';
```

## notificationExtensionSubscription.openSubscriptionSettings

openSubscriptionSettings(context: UIAbilityContext): Promise\<void\>

Opens the page for setting notification extension subscription in a semi-modal dialog box. On this page, users can set the notification enabling status and mode. This API uses a promise to return the result.

**System capability**: SystemCapability.Notification.Notification

**Required permissions**: ohos.permission.SUBSCRIBE_NOTIFICATION

**Parameters**

| Name  | Type                    | Mandatory| Description                |
| -------- | ------------------------ | ---- |--------------------|
| context | [UIAbilityContext](../../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) | Yes  | Ability context bound to the notification settings page.|

**Return value**

| Type    | Description| 
| ------- |--|
| Promise\<void\> | Promise that returns no value.| 

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Notification Error Codes](./errorcode-notification.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 201      | Permission denied.     |  
| 1600001  | Internal error.                     |
| 1600018  | the notification settings window is already displayed.           |
| 1600023  | The application does not implement the NotificationSubscriberExtensionAbility.           |

**Example**

```ts
import notificationExtensionSubscription from '@ohos.notificationExtensionSubscription'
import { common } from '@kit.AbilityKit';

try {
  await notificationExtensionSubscription.openSubscriptionSettings(getContext(this) as common.UIAbilityContext);
  } catch (error) {
    console.error("xxxxx failed to call openSubscriptionSettings")
    }
    console.log("xxxxx userGranted result");
```

## notificationExtensionSubscription.subscribe

subscribe(info: NotificationExtensionSubscriptionInfo[]): Promise\<void\>

Subscribes to notifications after connecting to a Bluetooth address. This API uses a promise to return the result.

**System capability**: SystemCapability.Notification.Notification

**Required permissions**: ohos.permission.SUBSCRIBE_NOTIFICATION

**Parameters**

| Name    | Type                                       | Mandatory| Description                                       |
| -------- | ------------------------------------------- | ---- | ------------------------------------------- |
| info  | [NotificationExtensionSubscriptionInfo](js-apis-inner-notificationExtensionSubscriptionInfo.md) | Yes  | List of subscribed notifications (in array).|

**Return value**

| Type    | Description| 
| ------- |--|
| Promise\<void\> | Promise that returns no value.| 

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Notification Error Codes](./errorcode-notification.md).

| ID| Error Message                                             |
| -------- | ---------------------------------------------------- |
| 201      | Permission denied. |
| 1600001  | Internal error.                                      |
| 1600003  | Failed to connect to the service.                    |
| 1600023  | The application does not implement the NotificationSubscriberExtensionAbility.           |

**Example**

```ts
import { notificationExtensionSubscription } from '@kit.NotificationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let infos: notificationExtensionSubscription.NotificationExtensionSubscriptionInfo[] = [
  {
    addr: '01:23:45:67:89:AB', // Use the dynamically obtained Bluetooth address.
    type: notificationExtensionSubscription.SubscribeType.BLUETOOTH
  }
];
notificationExtensionSubscription.subscribe(infos).then(() => {
  console.info("subscribe success");
}).catch((err: BusinessError) => {
  console.error(`subscribe fail: ${JSON.stringify(err)}`);
});

```

## notificationExtensionSubscription.unsubscribe

unsubscribe(): Promise\<void\>

Unsubscribes from notifications. This API uses a promise to return the result.

**System capability**: SystemCapability.Notification.Notification

**Required permissions**: ohos.permission.SUBSCRIBE_NOTIFICATION

**Return value**

| Type    | Description| 
| ------- |--|
| Promise\<void\> | Promise that returns no value.| 

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Notification Error Codes](./errorcode-notification.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 201      | Permission denied. |
| 1600001  | Internal error.                     |
| 1600003  | Failed to connect to the service. |

**Example**

```ts
import { notificationExtensionSubscription } from '@kit.NotificationKit';
import { BusinessError } from '@kit.BasicServicesKit';

notificationExtensionSubscription.unsubscribe().then(() => {
  console.info("unsubscribe success");
}).catch((err: BusinessError) => {
  console.error(`unsubscribe fail: ${JSON.stringify(err)}`);
});
```

## notificationExtensionSubscription.getSubscribeInfo

getSubscribeInfo(): Promise\<NotificationExtensionSubscriptionInfo[]\>

Obtains the notification subscription information of this application. This API uses a promise to return the result.

**System capability**: SystemCapability.Notification.Notification

**Required permissions**: ohos.permission.SUBSCRIBE_NOTIFICATION

**Return value**

| Type    | Description       | 
| ------- |-----------|
| Promise\<[NotificationExtensionSubscriptionInfo](js-apis-inner-notificationExtensionSubscriptionInfo.md)\> | Promise used to return the [NotificationExtensionSubscriptionInfo](js-apis-inner-notificationExtensionSubscriptionInfo.md) array.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Notification Error Codes](./errorcode-notification.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 201      | Permission denied. |
| 1600001  | Internal error.                     |
| 1600003  | Failed to connect to the service. |

**Example**

```ts
import { notificationExtensionSubscription } from '@kit.NotificationKit';
import { BusinessError } from '@kit.BasicServicesKit';

notificationExtensionSubscription.getSubscribeInfo().then((data) => {
  console.info('getSubscribeInfo successfully. Data: ' + JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error(`getSubscribeInfo fail: ${JSON.stringify(err)}`);
});
```

## notificationExtensionSubscription.isUserGranted

isUserGranted(): Promise\<boolean\>

Checks whether the notification extension subscription is granted by the user. This API uses a promise to return the result.

**System capability**: SystemCapability.Notification.Notification

**Required permissions**: ohos.permission.SUBSCRIBE_NOTIFICATION

**Return value**

| Type    | Description       | 
| ------- |-----------|
| Promise\<boolean\> | Promise used to return the result. The value **true** indicates that this feature is enabled, and the value **false** indicates the opposite.| 

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Notification Error Codes](./errorcode-notification.md).

| ID| Error Message                                             |
| -------- | ---------------------------------------------------- |
| 201      | Permission denied. | 
| 1600001  | Internal error.                                      |
| 1600003  | Failed to connect to the service.                           |

**Example**

```ts
import { notificationExtensionSubscription } from '@kit.NotificationKit';
import { BusinessError } from '@kit.BasicServicesKit';

notificationExtensionSubscription.isUserGranted().then((isOpen: boolean) => {
  if (isOpen) {
    console.info('isUserGranted true');
  } else {
    console.info('isUserGranted false');
  }
}).catch((err: BusinessError) => {
  console.error(`isUserGranted fail: ${JSON.stringify(err)}`);
});
```

## notificationExtensionSubscription.getUserGrantedEnabledBundles

getUserGrantedEnabledBundles(): Promise\<String[]\>

Obtains the source applications authorized to send notifications to this application. This API uses a promise to return the result.

**System capability**: SystemCapability.Notification.Notification

**Required permissions**: ohos.permission.SUBSCRIBE_NOTIFICATION

**Return value**

| Type    | Description       | 
| ------- |-----------|
| Promise\<String[]\>   | Promise used to return the result.       |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Notification Error Codes](./errorcode-notification.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 201      | Permission denied.     |  
| 1600001  | Internal error.                     |
| 1600003  | Failed to connect to the service.          |

**Example**

```ts
import { notificationExtensionSubscription } from '@kit.NotificationKit';
import { BusinessError } from '@kit.BasicServicesKit';

notificationExtensionSubscription.getUserGrantedEnabledBundles().then((data) => {
  console.info('getUserGrantedEnabledBundles successfully. Data: ' + JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error(`getUserGrantedEnabledBundles fail: ${JSON.stringify(err)}`);
});
```

## NotificationExtensionSubscriptionInfo

type NotificationExtensionSubscriptionInfo = _NotificationExtensionSubscriptionInfo

Describes the information about the notification extension subscription. This API uses a promise to return the result.

**System capability**: SystemCapability.Notification.Notification

| Type| Description|
| --- | --- |
| [_NotificationExtensionSubscriptionInfo](js-apis-inner-notificationExtensionSubscriptionInfo.md) | Information about the notification extension subscription.|

## SubscribeType

Describes the type that enables notification extension subscription.

**System capability**: SystemCapability.Notification.Notification

**Type**

| Name                | Value      | Description      |
| -------------------- | -------- | ---------- |
| BLUETOOTH          | 0 | Bluetooth.|

## BundleOption

type BundleOption = _BundleOption

Describes the bundle information of an application.

**System capability**: SystemCapability.Notification.Notification

| Type| Description|
| --- | --- |
| [_BundleOption](js-apis-inner-notification-notificationCommonDef.md#bundleoption) | Bundle information.|
