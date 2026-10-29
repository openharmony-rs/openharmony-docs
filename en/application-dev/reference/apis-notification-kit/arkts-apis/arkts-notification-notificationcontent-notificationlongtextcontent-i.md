# NotificationLongTextContent

```TypeScript
export interface NotificationLongTextContent extends NotificationBasicContent
```

Describes the long text notification. This API is inherited from [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md).

> **NOTE:** 
> 
> - When this type of notification forms a [group notification](../../../notification/notification-glossary.md#group-notification) with other notifications,the display effect of this notification type defaults to the collapsed state, and the displayed title and content are the `title` and `text` in the [basic text](arkts-notification-notificationcontent-notificationbasiccontent-i.md) inherited by this type.

When this type of notification is displayed individually and does not form a group notification with other notifications, the display effect of this notification type defaults to the expanded state, the displayed title is the expanded title `expandedTitle`, and the displayed content is the long text `longText`.

> - When the user clicks a notification in grouped display to view each notification's details, the display effect of this notification changes to the expanded state.
> 
> - The actual display effect depends on the device capability and the [notification center](../../../notification/notification-glossary.md#notification-center) UI style.

**Inheritance/Implementation:** NotificationLongTextContent extends [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md)

**Since:** 7

<!--Device-unnamed-export interface NotificationLongTextContent extends NotificationBasicContent--><!--Device-unnamed-export interface NotificationLongTextContent extends NotificationBasicContent-End-->

**System capability:** SystemCapability.Notification.Notification

## briefText

```TypeScript
briefText: string
```

Notification summary, which is a summary of the [notification content](../../../notification/notification-glossary.md#notification-content) and is not displayed in the notification center.

It must not be an empty string, with a size not exceeding 1024 bytes. The overflowing part will be truncated.

**Type:** string

**Since:** 7

<!--Device-NotificationLongTextContent-briefText: string--><!--Device-NotificationLongTextContent-briefText: string-End-->

**System capability:** SystemCapability.Notification.Notification

## expandedTitle

```TypeScript
expandedTitle: string
```

Title when the notification is expanded.

It cannot be an empty string. The size does not exceed 1024 bytes, and the excess part will be truncated.

**Type:** string

**Since:** 7

<!--Device-NotificationLongTextContent-expandedTitle: string--><!--Device-NotificationLongTextContent-expandedTitle: string-End-->

**System capability:** SystemCapability.Notification.Notification

## longText

```TypeScript
longText: string
```

Full long text content displayed after the notification is expanded.

It cannot be an empty string. The size does not exceed 3072 bytes, and the excess part will be truncated.

**Type:** string

**Since:** 7

<!--Device-NotificationLongTextContent-longText: string--><!--Device-NotificationLongTextContent-longText: string-End-->

**System capability:** SystemCapability.Notification.Notification
