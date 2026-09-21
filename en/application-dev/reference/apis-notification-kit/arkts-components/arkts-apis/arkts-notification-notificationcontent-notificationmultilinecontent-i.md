# NotificationMultiLineContent

```TypeScript
export interface NotificationMultiLineContent extends NotificationBasicContent
```

Describes the multi-line text notification. This API is inherited from NotificationBasicContent.

> **NOTE:** 
> 
> - When this notification type forms a group notification with other notifications, its display effect defaults to the collapsed state, and the displayed title and body are the **title** and **text** inherited from NotificationBasicContent. When this notification type is displayed alone and does not form a group notification with other notifications, its display effect defaults to the expanded state, where the displayed title is the expanded title **longTitle**, and the multi-line text content **lines** is displayed as the body.
> 
> - When a user taps a group notification to view the notification details, the display effect of this notification changes to the expanded state.
> 
> - The actual display effect depends on the device capabilities and the notification center UI style.

**Inheritance/Implementation:** NotificationMultiLineContent extends [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md)

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

## lines

```TypeScript
lines: Array<string>
```

List of multi-line text displayed after the notification is expanded. Each line is displayed as an independent entry and supports up to three lines. Each line size does not exceed 1024 bytes, excess part will be truncated.

**Type:** Array&lt;string&gt;

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

## longTitle

```TypeScript
longTitle: string
```

Title when the notification is expanded. It cannot be an empty string. The size does not exceed 1024 bytes, and the excess part will be truncated.

**Type:** string

**Since:** 7

**System capability:** SystemCapability.Notification.Notification
