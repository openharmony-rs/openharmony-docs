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

## lineWantAgents

```TypeScript
lineWantAgents?: Array<WantAgent>
```

点击多行文本中某一行文本消息触发的wantAgent。不同行的文本分别对应于不同的wantAgent。该字段配置的行数不能大于
[lines](arkts-notification-notificationmultilinecontent-i.md)字段配置的行数。默认为空。

**类型：** Array<WantAgent>

**起始版本：** 20

**需要权限：** ohos.permission.NOTIFICATION_AGENT_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

