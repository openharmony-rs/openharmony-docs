# NotificationInfo
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @cheerful_ricky-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

The **NotificationInfo** module describes the content shared with third-party wearables.

> **NOTE**
>
> The initial APIs of this module are supported since API version 22. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## NotificationInfo

**System capability**: SystemCapability.Notification.Notification

| Name| Type| Read-Only| Optional| Description| 
| -------- | -------- | -------- | -------- | -------- |
| hashCode | string | Yes| No| Unique identifier of the notification.|
| notificationSlotType | [notificationManager.SlotType](../apis-notification-kit/js-apis-notificationManager.md#slottype)| Yes| No| Notification slot type. The default value is **OTHER_TYPES**.|
| content | [NotificationExtensionContent](js-apis-inner-notification-notificationExtensionContent.md) | Yes| No| Notification content.|
| bundleName | string | Yes| No| Name of the bundle that creates the notification.|
| appName | string | Yes| Yes| Name of the application that creates the notification.|
| deliveryTime | long | Yes| Yes| Timestamp (in milliseconds) when the notification is published.|
| groupName | string | Yes| Yes| Notification group name, which is left empty by default.|
| appIndex | int | Yes| No| Index of the application clone that creates the notification. It takes effect only for application clones.|
