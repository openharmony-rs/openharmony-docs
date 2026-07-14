# NotificationMultiLineContent

描述多行文本通知。继承自[NotificationBasicContent](arkts-notification-notificationbasiccontent-i.md)。

> **说明：**
>
> - 当该类型通知与其他通知形成组通知时，该通知显示默认与[普通文本](arkts-notification-notificationbasiccontent-i.md)相同。展开组通知后，标题显示为展开时的标题`longTitle`，多行文本内容`lines`多行显
> 示。

当该类型通知单独呈现时，该通知标题显示为展开时的标题`longTitle`，多行文本内容`lines`多行显示。

> - 实际显示效果依赖于设备能力和通知中心UI样式。

**继承/实现关系：** NotificationMultiLineContent extends [NotificationBasicContent](arkts-notification-notificationbasiccontent-i.md)

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

## lines

```TypeScript
lines: Array<string>
```

通知的多行文本（最多支持三行，每行大小不超过1024字节，超出部分会被截断）。

**类型：** Array<string>

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

## longTitle

```TypeScript
longTitle: string
```

通知展开时的标题（不可为空字符串，大小不超过1024字节，超出部分会被截断）。

**类型：** string

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

