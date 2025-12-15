# @ohos.notificationExtensionSubscription (notificationExtensionSubscription) (System API)
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

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Notification Error Codes](./errorcode-notification.md).

| ID| Error Message                                             |
| -------- | ---------------------------------------------------- |
| 201      | Permission denied.     |
| 202      | Not system application to call the interface.                                      |
| 1600001  | Internal error.                                      |
| 1600003  | Failed to connect to the service.                    |

**Example**

```ts
notificationExtensionSubscription.getAllSubscriptionBundles().then((data) => {
  console.info(`getAllSubscriptionBundles successfully. Data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`getAllSubscriptionBundles fail: ${JSON.stringify(err)}`);
});
```

## notificationExtensionSubscription.getUserGrantedState

getUserGrantedState(targetBundle: BundleOption): Promise\<boolean\>

Obtains the enabling state of the **Allow access to notification on this device** switch for a specified application. This API uses a promise to return the result.

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
| Promise\<boolean\> | Promise used to return the result. The value **true** indicates that the device notification access for the target application is enabled, and **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Notification Error Codes](./errorcode-notification.md).

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
  console.error(`getUserGrantedState fail: ${JSON.stringify(err)}`);
});
```

## notificationExtensionSubscription.setUserGrantedState

setUserGrantedState(targetBundle: BundleOption, enabled: boolean): Promise\<void\>

Sets the enabling state of the **Allow access to notification on this device** switch for a specified application. This API uses a promise to return the result.

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

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Notification Error Codes](./errorcode-notification.md).

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
  console.error(`setUserGrantedState fail: ${JSON.stringify(err)}`);
});
```

## notificationExtensionSubscription.getUserGrantedEnabledBundles

getUserGrantedEnabledBundles(targetBundle: BundleOption): Promise\<BundleOption[]\>

Obtains applications (**targetBundle**) with device notification access granted by the user. This API uses a promise to return the result.

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
| Promise\<[BundleOption[]](./js-apis-inner-notification-notificationCommonDef.md#bundleoption)\>   | Promise used to return the result.       |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Notification Error Codes](./errorcode-notification.md).

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
notificationExtensionSubscription.getUserGrantedEnabledBundles(targetBundle).then((data) => {
  console.info(`getUserGrantedEnabledBundles successfully. Data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`getUserGrantedEnabledBundles fail: ${JSON.stringify(err)}`);
});
```

## notificationExtensionSubscription.setUserGrantedBundleState

setUserGrantedBundleState(targetBundle: BundleOption, enabledBundles: BundleOption[], enabled:boolean): Promise\<void\>

Sets the enabling state of device notification access for the specified application (**targetBundle**). This API uses a promise to return the result.

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

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Notification Error Codes](./errorcode-notification.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 201      | Permission denied. |
| 202      | Not system application to call the interface.  |
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
  console.error(`setUserGrantedBundleState fail: ${JSON.stringify(err)}`);
});
```
