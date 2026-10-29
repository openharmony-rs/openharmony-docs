# NotificationPictureContent

```TypeScript
export interface NotificationPictureContent extends NotificationBasicContent
```

Describes the picture-attached notification. This API is inherited from [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md).

> **NOTE:** 
> 
> - When this type of notification forms a [group notification](../../../notification/notification-glossary.md#group-notification) with other notifications,the display effect of this notification type defaults to the collapsed state, and the displayed title and body are the `title` and `text` in the [basic text](arkts-notification-notificationcontent-notificationbasiccontent-i.md) inherited by this type.

When this type of notification is displayed individually without forming a group notification with other notifications, the display effect of this notification type defaults to the expanded state, the displayed title is the expanded title `expandedTitle`, and the displayed body is the `text` in the inherited `basic text` and the picture content `picture` of this type.

> - When the user clicks a notification in grouped display to view the details of each notification, the display effect of this notification changes to the expanded state.
> 
> - The actual display effect depends on the device capability and the UI style of the [notification center](../../../notification/notification-glossary.md#notification-center)<!--RP1--><!--RP1End-->.

**Inheritance/Implementation:** NotificationPictureContent extends [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md)

**Since:** 7

<!--Device-unnamed-export interface NotificationPictureContent extends NotificationBasicContent--><!--Device-unnamed-export interface NotificationPictureContent extends NotificationBasicContent-End-->

**System capability:** SystemCapability.Notification.Notification

## briefText

```TypeScript
briefText: string
```

Notification summary content, which is a summary of the [notification content](../../../notification/notification-glossary.md#notification-content) and is not displayed in the notification center.

Must not be empty, with a size not exceeding 1024 bytes. The overflowing part will be truncated.

**Type:** string

**Since:** 7

<!--Device-NotificationPictureContent-briefText: string--><!--Device-NotificationPictureContent-briefText: string-End-->

**System capability:** SystemCapability.Notification.Notification

## expandedTitle

```TypeScript
expandedTitle: string
```

Title when the notification is expanded.

It cannot be an empty string. The size does not exceed 1024 bytes, and the excess part will be truncated.

**Type:** string

**Since:** 7

<!--Device-NotificationPictureContent-expandedTitle: string--><!--Device-NotificationPictureContent-expandedTitle: string-End-->

**System capability:** SystemCapability.Notification.Notification

## picture

```TypeScript
picture: image.PixelMap
```

Right icon displayed after notification expansion.

The total bytes of the icon pixel must not exceed 2 MB (the total bytes of the icon pixel are obtained through [getPixelBytesNumber](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md#getpixelbytesnumber)).

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**Since:** 7

<!--Device-NotificationPictureContent-picture: image.PixelMap--><!--Device-NotificationPictureContent-picture: image.PixelMap-End-->

**System capability:** SystemCapability.Notification.Notification
