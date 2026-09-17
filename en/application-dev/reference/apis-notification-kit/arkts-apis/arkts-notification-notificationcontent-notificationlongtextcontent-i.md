# NotificationLongTextContent

Describes the long text notification. This API is inherited from NotificationBasicContent.

> **NOTE:** 
> 
> - When this notification type forms a group notification with other notifications, its display effect defaults to the collapsed state, and the displayed title and body are the **title** and **text** inherited from NotificationBasicContent. When this notification type is displayed alone and does not form a group notification with other notifications, its display effect defaults to the expanded state, where the displayed title is the expanded title **expandedTitle**, and the displayed body content is the long text **longText**.
> 
> - When a user taps a group notification to view the notification details, the display effect of this notification changes to the expanded state.
> 
> - The actual display effect depends on the device capabilities and the notification center UI style.

**Inheritance/Implementation:** NotificationLongTextContent extends [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md)

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

## briefText

```TypeScript
briefText: string
```

Notification summary content, which is a summary of the notification content and is not displayed in the notification center. It cannot be an empty string. The size does not exceed 1024 bytes, and the excess part will be truncated.

**Type:** string

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

## expandedTitle

```TypeScript
expandedTitle: string
```

Title when the notification is expanded. It cannot be an empty string. The size does not exceed 1024 bytes, and the excess part will be truncated.

**Type:** string

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

## longText

```TypeScript
longText: string
```

Full long text content displayed after the notification is expanded. It cannot be an empty string. The size does not exceed 3072 bytes, and the excess part will be truncated.

**Type:** string

**Since:** 7

**System capability:** SystemCapability.Notification.Notification
