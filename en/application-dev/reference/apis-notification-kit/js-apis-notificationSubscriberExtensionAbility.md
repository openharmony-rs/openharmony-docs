# @ohos.application.NotificationSubscriberExtensionAbility (ExtensionAbility for Notification Subscription)
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @cheerful_ricky-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

NotificationSubscriberExtensionAbility is the base class for notification subscription extensions, providing the core functionality for subscribing to notifications.

> **NOTE**
>
> The initial APIs of this module are supported since API version 22. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { hilog } from '@kit.PerformanceAnalysisKit';
import NotificationSubscriberExtensionAbility from '@ohos.application.NotificationSubscriberExtensionAbility'
import extensionSubscription from '@ohos.notificationExtensionSubscription';
```

## NotificationSubscriberExtensionAbility

### Properties

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
const DOMAIN = 0x0000;
const TAG = 'NotificationSubscriberExtAbility';

export default class NotificationSubscriberExtAbility extends NotificationSubscriberExtensionAbility {
  onDestroy(): void {
    hilog.info(DOMAIN, 'testTag', `${TAG} onDestroy`);
  }
}
```

### onReceiveMessage

onReceiveMessage(notificationInfo: NotificationInfo): void

Called when the system receives a notification.

**System capability**: SystemCapability.Notification.Notification

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| notificationInfo |  [NotificationInfo](../apis-notification-kit/js-apis-inner-notification-notificationInfo.md) | Yes| Ability name, bundle name, and so on.|

**Example**:

```ts
const DOMAIN = 0x0000;
const TAG = 'NotificationSubscriberExtAbility';

export default class NotificationSubscriberExtAbility extends NotificationSubscriberExtensionAbility {
  onReceiveMessage(notificationInfo: extensionSubscription.NotificationInfo): void {
    hilog.info(DOMAIN, 'testTag', `${TAG} onReceiveMessage. notificationInfo: ${JSON.stringify(notificationInfo)}`);
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
| hashCodes |  Array\<string\>| Yes| Array of hash codes representing the notifications to be canceled.|

**Example**:

```ts
const DOMAIN = 0x0000;
const TAG = 'NotificationSubscriberExtAbility';

export default class NotificationSubscriberExtAbility extends NotificationSubscriberExtensionAbility {
    onCancelMessages(hashCodes: Array<string>): void {
        hilog.info(DOMAIN, 'testTag', `${TAG} onReceiveMessage. hashCodes: ${JSON.stringify(hashCodes)}`);
    }
}
```
