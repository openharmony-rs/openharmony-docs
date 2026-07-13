# NotificationPictureContent

描述附有图片的通知。继承自[NotificationBasicContent](arkts-notification-notificationbasiccontent-i.md)。

> **说明：**
>
> 实际显示效果依赖于设备能力和通知中心UI样式。

**继承/实现关系：** NotificationPictureContent extends [NotificationBasicContent](arkts-notification-notificationbasiccontent-i.md)

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

## briefText

```TypeScript
briefText: string
```

通知概要内容，是对通知内容的总结（不可为空字符串，大小不超过1024字节，超出部分会被截断）。

**类型：** string

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

## expandedTitle

```TypeScript
expandedTitle: string
```

通知展开时的标题（不可为空字符串，大小不超过1024字节，超出部分会被截断）。

**类型：** string

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

## picture

```TypeScript
picture: image.PixelMap
```

通知的图片内容（图像像素的总字节数不能超过2MB）。

**类型：** image.PixelMap

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

