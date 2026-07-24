# @ohos.notificationExtensionSubscription (notificationExtensionSubscription) (System API)

<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=9aa812250f4e9aa6e205822b2fc097b3c5b2a47d translatedAt=2026-07-21T01:10:01.660Z pushedAt=2026-07-21T01:39:23.329Z -->

The **notificationExtensionSubscription** module provides capabilities for managing notification extension, including opening the extension settings screen, subscribing to/unsubscribing from notification extension, and obtaining/setting the notification authorization status.

> **NOTE**
>
> The initial APIs of this module are supported since API version 22. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This topic describes only the system APIs provided by the module. For details about its public APIs, see [notificationExtensionSubscription](./js-apis-notificationExtensionSubscription.md).

## Modules to Import

```ts
import { notificationExtensionSubscription } from '@kit.NotificationKit';
import { BusinessError } from '@kit.BasicServicesKit';
```

## notificationExtensionSubscription.getAllSubscriptionBundles

getAllSubscriptionBundles(): Promise\<BundleOption[]\>

Obtains all applications that have requested the [ohos.permission.SUBSCRIBE_NOTIFICATION](../../security/AccessToken/restricted-permissions.md#ohospermissionsubscribe_notification) permission and implemented [NotificationSubscriberExtensionAbility](./js-apis-notificationSubscriberExtensionAbility.md). This API uses a promise to return the result.

**System capability**: SystemCapability.Notification.Notification

**Required permissions**: ohos.permission.NOTIFICATION_CONTROLLER

**System API**: This is a system API.

**Return value**

| Type    | Description       | 
| ------- |-----------|
| Promise\<[BundleOption[]](./js-apis-inner-notification-notificationCommonDef.md#bundleoption)\>   | Promise used to return the applications that have requested the [ohos.permission.SUBSCRIBE_NOTIFICATION](../../security/AccessToken/restricted-permissions.md#ohospermissionsubscribe_notification) permission and implemented [NotificationSubscriberExtensionAbility](./js-apis-notificationSubscriberExtensionAbility.md).       |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Notification Error Codes](errorcode-notification.md).

| ID| Error Message                                             |
| -------- | ---------------------------------------------------- |
| 201      | Permission denied.     |  
| 202      | Not system application to call the interface.                                      |  
| 1600001  | Internal error.                                      |
| 1600003  | Failed to connect to the service.                    |

**Example**

```ts
notificationExtensionSubscription.getAllSubscriptionBundles().then((data: notificationExtensionSubscription.BundleOption[]) => {
  console.info(`getAllSubscriptionBundles successfully. Data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`getAllSubscriptionBundles fail, code is ${err.code}, message is ${err.message}`);
});
```

## notificationExtensionSubscription.getUserGrantedState

getUserGrantedState(targetBundle: BundleOption): Promise\<boolean\>

Obtains the enabling state of the **Allow access to notifications on this device** switch of a specified application. This API uses a promise to return the result.

**System capability**: SystemCapability.Notification.Notification

**Required permissions**: ohos.permission.NOTIFICATION_CONTROLLER

**System API**: This is a system API.

**Parameters**

| Name    | Type                 | Mandatory| Description                |
| -------- | --------------------- | ---- | -------------------- |
| targetBundle    | [BundleOption](./js-apis-inner-notification-notificationCommonDef.md#bundleoption)       | Yes  | Information about the target application. The application must have requested the [ohos.permission.SUBSCRIBE_NOTIFICATION](../../security/AccessToken/restricted-permissions.md#ohospermissionsubscribe_notification) permission and implemented [NotificationSubscriberExtensionAbility](../apis-notification-kit/js-apis-notificationSubscriberExtensionAbility.md). Otherwise, error code 1600022 is returned.|

**Return value**

| Type    | Description       | 
| ------- |-----------|
| Promise\<boolean\> | Promise used to return the result. The value **true** indicates that the device notification access is enabled, and **false** indicates the opposite.| 

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Notification Error Codes](errorcode-notification.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 201      | Permission denied.     |  
| 202      | Not system application to call the interface.                                      |  
| 1600001  | Internal error.                     |
| 1600003  | Failed to connect to the service.          |
| 1600022  | The specified bundle is invalid.                          |

**Example**

```ts
let targetBundle: notificationExtensionSubscription.BundleOption =
{
  // Use the actual target application information.
  bundle: 'com.example.testnotification',
};
notificationExtensionSubscription.getUserGrantedState(targetBundle).then((isOpen: boolean) => {
  if (isOpen) {
    console.info('GrantedState true');
  } else {
    console.info('GrantedState false');
  }
}).catch((err: BusinessError) => {
  console.error(`getUserGrantedState fail, code is ${err.code}, message is ${err.message}`);
});
```

## notificationExtensionSubscription.setUserGrantedState

setUserGrantedState(targetBundle: BundleOption, enabled: boolean): Promise\<void\>

Sets the enabling state of the **Allow access to notifications on this device** switch for a specified application. This API uses a promise to return the result.

**System capability**: SystemCapability.Notification.Notification

**Required permissions**: ohos.permission.NOTIFICATION_CONTROLLER

**System API**: This is a system API.

**Parameters**

| Name    | Type                 | Mandatory| Description                |
| -------- | --------------------- | ---- | -------------------- |
| targetBundle    | [BundleOption](./js-apis-inner-notification-notificationCommonDef.md#bundleoption)       | Yes  | Information about the target application. The application must have requested the [ohos.permission.SUBSCRIBE_NOTIFICATION](../../security/AccessToken/restricted-permissions.md#ohospermissionsubscribe_notification) permission and implemented [NotificationSubscriberExtensionAbility](../apis-notification-kit/js-apis-notificationSubscriberExtensionAbility.md). Otherwise, error code 1600022 is returned.|
| enable   | boolean | Yes  | Whether to enable the device notification access. The value **true** indicates that this functionality is enabled, and **false** indicates the opposite.|

**Return value**

| Type    | Description       |
| ------- |-----------|
| Promise\<void\> |Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Notification Error Codes](errorcode-notification.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 201      | Permission denied.     |  
| 202      | Not system application to call the interface.                                      |  
| 1600001  | Internal error.                     |
| 1600003  | Failed to connect to the service.          |
| 1600022  | The specified bundle is invalid.                          |

**Example**

```ts
let targetBundle: notificationExtensionSubscription.BundleOption =
{
  // Use the actual target application information.
  bundle: 'com.example.testnotification',
};
notificationExtensionSubscription.setUserGrantedState(targetBundle, true).then(() => {
  console.info(`setUserGrantedState successfully.`);
}).catch((err: BusinessError) => {
  console.error(`setUserGrantedState fail, code is ${err.code}, message is ${err.message}`);
});
```

## notificationExtensionSubscription.getUserGrantedEnabledBundles

getUserGrantedEnabledBundles(targetBundle: BundleOption): Promise\<BundleOption[]\>

Obtains the applications that are allowed to access device notifications. This API uses a promise to return the result.

**System capability**: SystemCapability.Notification.Notification

**Required permissions**: ohos.permission.NOTIFICATION_CONTROLLER

**System API**: This is a system API.

**Parameters**

| Name    | Type                 | Mandatory| Description                |
| -------- | --------------------- | ---- | -------------------- |
| targetBundle    | [BundleOption](./js-apis-inner-notification-notificationCommonDef.md#bundleoption)       | Yes  | Information about the target application. The application must have requested the [ohos.permission.SUBSCRIBE_NOTIFICATION](../../security/AccessToken/restricted-permissions.md#ohospermissionsubscribe_notification) permission and implemented [NotificationSubscriberExtensionAbility](../apis-notification-kit/js-apis-notificationSubscriberExtensionAbility.md). Otherwise, error code 1600022 is returned.|

**Return value**

| Type    | Description       |
| ------- |-----------|
| Promise\<[BundleOption[]](./js-apis-inner-notification-notificationCommonDef.md#bundleoption)\>   | Promise used to return the applications obtained.       |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Notification Error Codes](errorcode-notification.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 201      | Permission denied.     |
| 202      | Not system application to call the interface. |
| 1600001  | Internal error. |
| 1600003  | Failed to connect to the service. |
| 1600022  | The specified bundle is invalid. |

**Example**

```ts
let targetBundle: notificationExtensionSubscription.BundleOption =
{
  // Use the actual target application information.
  bundle: 'com.example.testnotification',
};
notificationExtensionSubscription.getUserGrantedEnabledBundles(targetBundle).then((data: notificationExtensionSubscription.BundleOption[]) => {
  console.info(`getUserGrantedEnabledBundles successfully. Data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`getUserGrantedEnabledBundles fail, code is ${err.code}, message is ${err.message}`);
});
```

## notificationExtensionSubscription.setUserGrantedBundleState

setUserGrantedBundleState(targetBundle: BundleOption, enabledBundles: BundleOption[], enabled:boolean): Promise\<void\>

Sets the enabling state of device notification access for the specified application. This API uses a promise to return the result.

**System capability**: SystemCapability.Notification.Notification

**Required permissions**: ohos.permission.NOTIFICATION_CONTROLLER

**System API**: This is a system API.

**Parameters**

| Name    | Type                 | Mandatory| Description                |
| -------- | --------------------- | ---- | -------------------- |
| targetBundle    | [BundleOption](./js-apis-inner-notification-notificationCommonDef.md#bundleoption)       | Yes  | Information about the target application. The application must have requested the [ohos.permission.SUBSCRIBE_NOTIFICATION](../../security/AccessToken/restricted-permissions.md#ohospermissionsubscribe_notification) permission and implemented [NotificationSubscriberExtensionAbility](../apis-notification-kit/js-apis-notificationSubscriberExtensionAbility.md). Otherwise, error code 1600022 is returned.|
| enabledBundles    | [BundleOption[]](./js-apis-inner-notification-notificationCommonDef.md#bundleoption)       | Yes  | Authorized applications.|
| enabled    | boolean       | Yes  | Whether the device notification access for the specified application is enabled. The value **true** indicates that this functionality is enabled, and **false** indicates the opposite.|

**Return value**

| Type    | Description       | 
| ------- |-----------|
| Promise\<void\> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Notification Error Codes](errorcode-notification.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 201      | Permission denied. |
| 202      | Not system application to call the interface. |
| 1600001  | Internal error. |
| 1600003  | Failed to connect to the service. |
| 1600022  | The specified bundle is invalid. |

**Example**

```ts
let targetBundle: notificationExtensionSubscription.BundleOption =
  {
    // Use the actual target application information.
    bundle: 'com.example.testnotification',
  };
let enabledBundles: notificationExtensionSubscription.BundleOption[] = [
  // Use the actual source application information.
  { bundle: 'com.example.xxx', uid: 11111111 },
  { bundle: 'com.example.xxxx', uid: 11111111 },
  { bundle: 'com.example.xxxxx' },
];
notificationExtensionSubscription.setUserGrantedBundleState(targetBundle, enabledBundles, true).then(() => {
  console.info(`setUserGrantedBundleState successfully.`);
}).catch((err: BusinessError) => {
  console.error(`setUserGrantedBundleState fail, code is ${err.code}, message is ${err.message}`);
});
```

## notificationExtensionSubscription.subscribeNotification

subscribeNotification(priorityStrategy?: number): Promise\<void\>

Subscribes to notifications based on the priority strategy. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can only be used in the stage model.

**System capability:** SystemCapability.Notification.Notification

**Required permission:** ohos.permission.NOTIFICATION_SYSTEM_SUBSCRIBER

**System API:** This is a system API.

**Parameters**

| Name            | Type   | Mandatory | Description                                                                                                                                                                                                                                                                                                                                                                                                                         |
| --------------- | ------ | --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| priorityStrategy | number | No        | Priority strategy for filtering the notifications. The default value is **0**. This parameter is obtained by performing a bitwise OR operation on the enums of [PriorityStrategyStatus](js-apis-notificationManager-sys.md#prioritystrategystatus23).<br>After an application subscribes to a specific priority strategy, the system returns only notifications matching the corresponding strategy when the application publishes notifications.<br>Subscribing to the default priority strategy **STATUS_SYSTEM_DEFAULT** means subscribing simultaneously to the following strategies: **STATUS_SYSTEM_RULE**, **STATUS_INTELLIGENT**, **STATUS_USER_DEFINED**, and **STATUS_APPLICATION_DEFINED**.<br>When **priorityStrategy** is set to **0**, no priority strategy is applied, and all notifications published by the application can be received. |

**Return value**

| Type          | Description                      |
| ------------- | -------------------------------- |
| Promise\<void\> | Promise that returns no value. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [Notification Error Codes](errorcode-notification.md).

| ID      | Error Message                                                         |
| ------- | --------------------------------------------------------------------- |
| 201     | Permission denied or current device not supported.                   |
| 202     | Not system application to call the interface.                        |
| 1600001 | Internal error. Possible cause: 1.IPC communication failed. 2.Memory operation error. 3.The user does not exist. |
| 1600002 | Marshalling or unmarshalling error.                                   |
| 1600003 | Failed to connect to the service.                                     |
| 1600022 | The application does not implement the NotificationSubscriberExtensionAbility. |

**Example**

```ts
notificationExtensionSubscription.subscribeNotification(0).then(() => {
  console.info(`subscribeNotification successfully.`);
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```