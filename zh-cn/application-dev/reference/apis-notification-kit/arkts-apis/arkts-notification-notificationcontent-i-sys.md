# NotificationContent（系统接口）

```TypeScript
export interface NotificationContent
```

NotificationContent中定义通知的内容结构，提供多种通知类型的内容描述接口。当应用需要发布通知时，可根据通知的展示需求（如普通文本、长文本、多行文本、图片、实况窗），选择对应的内容类型接口构造[通知内容](../../../notification/notification-glossary.md#notification-content通知内容)。

**起始版本：** 7

<!--Device-unnamed-export interface NotificationContent--><!--Device-unnamed-export interface NotificationContent-End-->

**系统能力：** SystemCapability.Notification.Notification

## liveView

```TypeScript
liveView?: NotificationLiveViewContent
```

普通实况窗类型[通知内容](../../../notification/notification-glossary.md#notification-content通知内容)。

**类型：** [NotificationLiveViewContent](arkts-notification-notificationcontent-notificationliveviewcontent-i-sys.md)

**起始版本：** 11

<!--Device-NotificationContent-liveView?: NotificationLiveViewContent--><!--Device-NotificationContent-liveView?: NotificationLiveViewContent-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。
