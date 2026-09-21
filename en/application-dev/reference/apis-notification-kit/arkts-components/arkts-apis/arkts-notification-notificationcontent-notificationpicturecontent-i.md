# NotificationPictureContent

```TypeScript
export interface NotificationPictureContent extends NotificationBasicContent
```

Describes the picture-attached notification. This API is inherited from NotificationBasicContent.

> **NOTE:** 
> 
> - When this notification type forms a group notification with other notifications, its display effect defaults to the collapsed state, and the displayed title and body are the **title** and **text** inherited from NotificationBasicContent. When this notification type is displayed alone and does not form a group notification with other notifications, its display effect defaults to the expanded state, where the displayed title is the expanded title **expandedTitle**, and the displayed body is the **text** inherited from NotificationBasicContent and the picture content **picture** of this type.
> 
> - When a user taps a group notification to view the notification details, the display effect of this notification changes to the expanded state.
> 
> - The actual display effect depends on the device capabilities and the notification center UI style&lt;!--RP1--&gt;&lt;!--RP1End--&gt;.

**Inheritance/Implementation:** NotificationPictureContent extends [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md)

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

## picture

```TypeScript
picture: image.PixelMap
```

Right icon displayed after notification expansion. The total bytes of the image pixels (obtained through getPixelBytesNumber) cannot exceed 2 MB.

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**Since:** 7

**System capability:** SystemCapability.Notification.Notification
