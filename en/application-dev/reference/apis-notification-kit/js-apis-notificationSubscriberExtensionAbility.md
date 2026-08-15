# @ohos.application.NotificationSubscriberExtensionAbility (ExtensionAbility for Notification Subscription)
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=9aa812250f4e9aa6e205822b2fc097b3c5b2a47d translatedAt=2026-07-21T01:11:41.410Z pushedAt=2026-07-21T09:31:30.176Z -->

NotificationSubscriberExtensionAbility is the base class for notification subscriber extension abilities, providing notification subscription-related functionality. Third-party wearable apps (such as companion applications for watches) implement callback logic by inheriting this class, receiving notification information when notifications are published on the local device and forwarding them to the wearable device via Bluetooth, and receiving callbacks for notification cancellation when local notifications are cancelled and forwarding them to the wearable device to delete the corresponding notifications.

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


| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| context | [NotificationSubscriberExtensionContext](js-apis-notificationSubscriberExtensionContext.md)  | No| No| Context for the NotificationSubscriberExtensionAbility.|


### onDestroy

onDestroy(): void

Called when the notification subscription extension is destroyed.

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
| notificationInfo | [NotificationInfo](../apis-notification-kit/js-apis-inner-notification-notificationInfo.md) | Yes | Callback information about the notification received in the notification subscription extension capability. |

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