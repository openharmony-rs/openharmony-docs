# NotificationInfo

<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=9aa812250f4e9aa6e205822b2fc097b3c5b2a47d translatedAt=2026-07-21T01:08:47.338Z pushedAt=2026-07-21T09:31:53.844Z -->

The **NotificationInfo** module describes the notification information delivered to the [onReceiveMessage](js-apis-notificationSubscriberExtensionAbility.md#onreceivemessage) callback of ExtensionAbility for notification subscriptions.

> **NOTE**
>
> The initial APIs of this module are supported since API version 22. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## NotificationInfo

**System capability**: SystemCapability.Notification.Notification

| Name                | Type   | Read-Only| Optional| Description                                           |
| -------------------- | ------ | ---- | ---- | ---------------------------------------------- |
| hashCode             | string | Yes  | No  | Unique identifier of the notification.                              |
| notificationSlotType | [notificationManager.SlotType](js-apis-notificationManager.md#slottype)| Yes | No | Notification slot type, which identifies the slot category of the notification (such as social communication and service reminder). Different slot types correspond to different reminder types. |
| content              | [NotificationExtensionContent](js-apis-inner-notification-notificationExtensionContent.md)      | Yes | No | Notification content, which includes the title and body of the notification.     |
| bundleName           | string | Yes   | No   | Bundle name of the application that creates the notification.                                 |
| appIndex             | number | Yes   | No   | Index of the application clone that creates the notification. It takes effect only for application clones.|
| appName              | string | Yes   | Yes   | Name of the application that creates the notification.                          |
| deliveryTime         | number | Yes   | Yes   | Timestamp when the notification is published.<br>Data format: timestamp.<br>Unit: millisecond.|
| groupName            | string | Yes   | Yes   | Name of the notification group.                                     |