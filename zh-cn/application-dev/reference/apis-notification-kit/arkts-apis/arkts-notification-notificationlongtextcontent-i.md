# NotificationLongTextContent

描述长文本通知。继承自[NotificationBasicContent](arkts-notification-notificationbasiccontent-i.md)。

> **说明：**
>
> 实际显示效果依赖于设备能力和通知中心UI样式。

**继承/实现关系：** NotificationLongTextContent extends [NotificationBasicContent](arkts-notification-notificationbasiccontent-i.md)

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

## longText

```TypeScript
longText: string
```

通知的长文本（不可为空字符串，大小不超过3072字节，超出部分会被截断）。

**类型：** string

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

