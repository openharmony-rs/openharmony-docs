# NotificationSystemLiveViewContent

描述系统实况窗通知内容，用于在实况窗中展示实时状态信息。不支持三方应用直接创建该类型通知，可以由系统代理创建系统实况窗类型通知后，三方应用发布同ID的通知来更新指定内容。继承自[NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md)。

> **说明：**  
>  
> 实际显示效果依赖于设备能力和通知中心UI样式。

**继承/实现关系：** NotificationSystemLiveViewContent extends [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md)

**起始版本：** 11

<!--Device-unnamed-export interface NotificationSystemLiveViewContent extends NotificationBasicContent--><!--Device-unnamed-export interface NotificationSystemLiveViewContent extends NotificationBasicContent-End-->

**系统能力：** SystemCapability.Notification.Notification

## cardButtons

```TypeScript
cardButtons?: Array<NotificationIconButton>
```

实况窗按钮（最多支持3个）。默认为空。

**类型：** Array&lt;NotificationIconButton&gt;

**起始版本：** 18

<!--Device-NotificationSystemLiveViewContent-cardButtons?: Array<NotificationIconButton>--><!--Device-NotificationSystemLiveViewContent-cardButtons?: Array<NotificationIconButton>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## liveViewType

```TypeScript
liveViewType?: LiveViewTypes
```

实况窗类型。默认值为LIVE_VIEW_ACTIVITY。

**类型：** LiveViewTypes

**起始版本：** 18

<!--Device-NotificationSystemLiveViewContent-liveViewType?: LiveViewTypes--><!--Device-NotificationSystemLiveViewContent-liveViewType?: LiveViewTypes-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

