# @ohos.application.NotificationSubscriberExtensionAbility (ExtensionAbility for Notification Subscription)
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @wangsen1994-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=1ded46b3f2c6157598c112b16f192beb1f37cf1d translatedAt=2026-10-08T02:33:08.041Z pushedAt=2026-10-08T10:04:08.571Z -->

NotificationSubscriberExtensionAbility is the base class of the [notification subscription](../../notification/notification-glossary.md#notification-subscription) extension ability, providing notification subscription related capabilities. Third-party wearable applications (such as companion applications for watches) implement callback logic by inheriting from this class, receive notification information when a notification is published on the local device and forward it to the wearable device over Bluetooth. When a local notification is canceled, they receive the cancellation callback and forward it to the wearable device to delete the corresponding notification.

Use this module when your wearable application needs to obtain local notifications and sync them to a paired wearable device. This module is used together with the **notificationExtensionSubscription** module. This module is responsible for receiving and processing notification data in callbacks, while the **notificationExtensionSubscription** module is responsible for management operations such as authorization, subscription, and unsubscription.

> **NOTE**
>
> The initial APIs of this module are supported since API version 22. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { notificationExtensionSubscription, NotificationSubscriberExtensionAbility } from '@kit.NotificationKit';
```

## NotificationSubscriberExtensionAbility

**System capability**: SystemCapability.Notification.Notification

### Attributes

**System capability**: SystemCapability.Notification.Notification

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| context | [NotificationSubscriberExtensionContext](js-apis-notificationSubscriberExtensionContext.md)  | No| No| Context for the NotificationSubscriberExtensionAbility.|


### onDestroy

onDestroy(): void

Triggered when the [notification subscription](../../notification/notification-glossary.md#notification-subscription) extension is destroyed.

**System capability**: SystemCapability.Notification.Notification

**Example**:

```ts
const TAG = 'NotificationSubscriberExtAbility';

export default class NotificationSubscriberExtAbility extends NotificationSubscriberExtensionAbility {
  onDestroy(): void {
    console.info(`${TAG} onDestroy`);
  }
}
```

### onReceiveMessage

onReceiveMessage(notificationInfo: NotificationInfo): void

Called when a notification is received.

**System capability**: SystemCapability.Notification.Notification

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| notificationInfo | [NotificationInfo](../apis-notification-kit/js-apis-inner-notification-notificationInfo.md) | Yes | Callback information about the notification received in the notification subscription extension ability. |

**Example**:

```ts
const TAG = 'NotificationSubscriberExtAbility';

export default class NotificationSubscriberExtAbility extends NotificationSubscriberExtensionAbility {
  onReceiveMessage(notificationInfo: notificationExtensionSubscription.NotificationInfo): void {
    console.info(`${TAG} onReceiveMessage. notificationInfo: ${JSON.stringify(notificationInfo)}`);
  }
}
```

### onCancelMessages

onCancelMessages(hashCodes: Array\<string>): void

Called when notifications are canceled.

**System capability**: SystemCapability.Notification.Notification

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| hashCodes | Array\<string\> | Yes | List of hash codes of the notifications to cancel, obtained through [onReceiveMessage](#onreceivemessage). |

**Example**:

```ts
const TAG = 'NotificationSubscriberExtAbility';

export default class NotificationSubscriberExtAbility extends NotificationSubscriberExtensionAbility {
  onCancelMessages(hashCodes: Array<string>): void {
    console.info(`${TAG} onCancelMessages. hashCodes: ${JSON.stringify(hashCodes)}`);
  }
}
```