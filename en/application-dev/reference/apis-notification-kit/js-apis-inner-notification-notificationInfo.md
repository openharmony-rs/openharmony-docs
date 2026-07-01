# NotificationInfo
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=50e734d278c25dbb71273705da516c218b3754a1 translatedAt=2026-06-29T02:36:34.039Z pushedAt=2026-06-30T10:57:37.002Z -->

The **NotificationInfo** module describes the notification information delivered to the [onReceiveMessage](js-apis-notificationSubscriberExtensionAbility.md#onreceivemessage) callback of ExtensionAbility for notification subscriptions.

> **NOTE**
>
> The initial APIs of this module are supported since API version 22. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## NotificationInfo

**System capability**: SystemCapability.Notification.Notification

| Name                | Type   | Read-Only| Optional| Description                                           |
| -------------------- | ------ | ---- | ---- | ---------------------------------------------- |
| hashCode             | string | Yes  | No  | Unique identifier of the notification.                              |
| notificationSlotType | [notificationManager.SlotType](../apis-notification-kit/js-apis-notificationManager.md#slottype)| Yes | No | Notification slot type, which identifies the channel category to which the notification belongs (such as social communication, service reminder, etc.). Different slot types correspond to different reminder methods. |
| content              | [NotificationExtensionContent](js-apis-inner-notification-notificationExtensionContent.md)      | Yes | No | Notification content, which includes the title and body of the notification.     |
| bundleName           | string | Yes  | No  | Name of the bundle that creates the notification.                                |
| appIndex             | number | Yes  | No  | Index of the application clone that creates the notification. It takes effect only for application clones.|
| appName              | string | Yes  | Yes  | Name of the application that creates the notification.                         |
| deliveryTime         | number | Yes   | Yes   | Timestamp when the notification is published.<br>Data format: timestamp.<br>Unit: millisecond.|
| groupName            | string | Yes   | Yes   | Name of the notification group.                                     |