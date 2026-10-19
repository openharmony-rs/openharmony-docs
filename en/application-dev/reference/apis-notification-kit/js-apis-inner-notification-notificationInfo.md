# NotificationInfo
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @wangsen1994-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=1ded46b3f2c6157598c112b16f192beb1f37cf1d translatedAt=2026-10-08T02:19:42.710Z pushedAt=2026-10-08T09:17:01.235Z -->

Notification information in the [onReceiveMessage](js-apis-notificationSubscriberExtensionAbility.md#onreceivemessage) callback of the [notification subscription](../../notification/notification-glossary.md#notification-subscription) extension ability.

> **NOTE**
>
> The initial APIs of this module are supported since API version 22. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## NotificationInfo

**System capability**: SystemCapability.Notification.Notification

| Name                | Type   | Read-Only| Optional| Description                                           |
| -------------------- | ------ | ---- | ---- | ---------------------------------------------- |
| hashCode             | string | Yes  | No  | Unique identifier of the notification.                              |
| notificationSlotType | [notificationManager.SlotType](js-apis-notificationManager.md#slottype)| Yes | No | Type of the [notification slot](../../notification/notification-glossary.md#notification-slot), which identifies the channel category to which the notification belongs (for example, social communication and service reminder). Different slot types correspond to different reminder modes. |
| content              | [NotificationExtensionContent](js-apis-inner-notification-notificationExtensionContent.md)      | Yes | No | [Notification content](../../notification/notification-glossary.md#notification-content), including the title and body of the notification.     |
| bundleName           | string | Yes   | No   | Bundle name of the application that creates the notification.                                 |
| appIndex             | number | Yes   | No   | Index of the application clone that creates the notification. It takes effect only for application clones.|
| appName              | string | Yes   | Yes   | Name of the application that creates the notification.                          |
| deliveryTime         | number | Yes   | Yes   | Timestamp when the notification is published.<br>Data format: timestamp.<br>Unit: milliseconds.|
| groupName            | string | Yes   | Yes   | Name of the notification group.                                     |
