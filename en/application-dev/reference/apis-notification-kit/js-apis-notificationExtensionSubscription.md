# @ohos.notificationExtensionSubscription (notificationExtensionSubscription)
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @cheerful_ricky-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

The **notificationExtensionSubscription** module provides capabilities for managing notification extension, including opening the extension settings screen, subscribing to/unsubscribing from notification extension, and obtaining/setting the notification authorization status.

> **NOTE**
>
> The initial APIs of this module are supported since API version 22. Newly added APIs will be marked with a superscript to indicate their earliest API version.
## Modules to Import

```ts
import { notificationExtensionSubscription } from '@kit.NotificationKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';
```

## notificationExtensionSubscription.openSubscriptionSettings

openSubscriptionSettings(context: UIAbilityContext): Promise\<void\>

Opens the settings screen of notification extension subscription in a semi-modal dialog box. On this screen, the user can turn on the **Allow access to notifications on this device** switch and allows notifications of specified applications to be accessed. This API uses a promise to return the result.

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
import { common } from '@kit.AbilityKit';

const DOMAIN = 0x0000;

try {
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  notificationExtensionSubscription.openSubscriptionSettings(context).then(() => {
    hilog.info(DOMAIN, 'testTag', `openSubscriberSettings success`);
  }).catch((e:Error) => {
    let error = e as BusinessError
    hilog.error(DOMAIN, 'testTag', `failed to call openSubscriptionSettings ${JSON.stringify(error)}`)
  });
} catch (error) {
  hilog.error(DOMAIN, 'testTag', `failed to call openSubscriptionSettings ${JSON.stringify(error)}`)
}
```

## notificationExtensionSubscription.subscribe

subscribe(info: NotificationExtensionSubscriptionInfo[]): Promise\<void\>

Subscribes to the notification extension. You can subscribe to the notification extension only after obtaining the unique address of the Bluetooth device by calling the APIs related to the [Bluetooth modules](../../connectivity/connectivity-kit-intro.md#bluetooth). This API uses a promise to return the result.

**System capability**: SystemCapability.Notification.Notification

**Required permissions**: ohos.permission.SUBSCRIBE_NOTIFICATION

**Parameters**

| Name    | Type                                       | Mandatory| Description                                       |
| -------- | ------------------------------------------- | ---- | ------------------------------------------- |
| info  | [NotificationExtensionSubscriptionInfo[]](js-apis-inner-notificationExtensionSubscriptionInfo.md) | Yes  | List of subscribed notifications (in array).|

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

Unsubscribes from the notification extension. This API uses a promise to return the result.

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
notificationExtensionSubscription.unsubscribe().then(() => {
  console.info("unsubscribe success");
}).catch((err: BusinessError) => {
  console.error(`unsubscribe fail: ${JSON.stringify(err)}`);
});
```

## notificationExtensionSubscription.getSubscribeInfo

getSubscribeInfo(): Promise\<NotificationExtensionSubscriptionInfo[]\>

Obtains the subscription information about the notification extension of this application. This API uses a promise to return the result.

**System capability**: SystemCapability.Notification.Notification

**Required permissions**: ohos.permission.SUBSCRIBE_NOTIFICATION

**Return value**

| Type    | Description       | 
| ------- |-----------|
| Promise\<[NotificationExtensionSubscriptionInfo[]](js-apis-inner-notificationExtensionSubscriptionInfo.md)\> | Promise used to return the [NotificationExtensionSubscriptionInfo[]](js-apis-inner-notificationExtensionSubscriptionInfo.md) array.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Notification Error Codes](./errorcode-notification.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 201      | Permission denied. |
| 1600001  | Internal error.                     |
| 1600003  | Failed to connect to the service. |

**Example**

```ts
notificationExtensionSubscription.getSubscribeInfo().then((data) => {
  console.info(`getSubscribeInfo successfully. Data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`getSubscribeInfo fail: ${JSON.stringify(err)}`);
});
```

## notificationExtensionSubscription.isUserGranted

isUserGranted(): Promise\<boolean\>

Checks whether the user has granted the permission to access notifications on this device. This API uses a promise to return the result.

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

getUserGrantedEnabledBundles(): Promise\<GrantedBundleInfo[]\>

Obtains the applications whose notifications can be accessed. This API uses a promise to return the result.

**System capability**: SystemCapability.Notification.Notification

**Required permissions**: ohos.permission.SUBSCRIBE_NOTIFICATION

**Return value**

| Type    | Description       | 
| ------- |-----------|
| Promise\<[GrantedBundleInfo[]](./js-apis-inner-notification-notificationCommonDef.md#grantedbundleinfo22)\>   | Promise used to return the applications whose notifications can be accessed.       |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Notification Error Codes](./errorcode-notification.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 201      | Permission denied.     |  
| 1600001  | Internal error.                     |
| 1600003  | Failed to connect to the service.          |

**Example**

```ts
notificationExtensionSubscription.getUserGrantedEnabledBundles().then((data) => {
  console.info(`getUserGrantedEnabledBundles successfully. Data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`getUserGrantedEnabledBundles fail: ${JSON.stringify(err)}`);
});
```

## NotificationExtensionSubscriptionInfo

type NotificationExtensionSubscriptionInfo = _NotificationExtensionSubscriptionInfo

Describes the information about the notification extension subscription.

**System capability**: SystemCapability.Notification.Notification

| Type| Description|
| --- | --- |
| [_NotificationExtensionSubscriptionInfo](js-apis-inner-notificationExtensionSubscriptionInfo.md) | Information about the notification extension subscription.|

## SubscribeType

Describes the type that enables notification extension subscription.

**System capability**: SystemCapability.Notification.Notification

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

## GrantedBundleInfo

type GrantedBundleInfo = _GrantedBundleInfo

Describes the bundle information of the authorized application.

**System capability**: SystemCapability.Notification.Notification

| Type| Description|
| --- | --- |
| [_GrantedBundleInfo](js-apis-inner-notification-notificationCommonDef.md#grantedbundleinfo22) | Bundle information of the authorized application.|
